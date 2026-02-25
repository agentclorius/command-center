# 🔒 Full Security Audit — Mac Mini M4 + OpenClaw Setup
**Date:** February 4, 2026  
**Auditor:** Forge (AI)  
**System:** Mac mini M4, macOS 15.5 (Sequoia), Apple Silicon  
**Uptime:** 1 day, 10 hours  

---

## Executive Summary

The setup is **reasonably secure for a startup environment**, but has **two critical gaps** (no disk encryption, no firewall) and several medium-priority issues that should be addressed. No active breaches or immediate threats detected.

**Risk score: 6/10** — functional but needs hardening.

---

## 🔴 CRITICAL — Fix Immediately

### 1. FileVault (Disk Encryption): OFF
**Risk:** If the Mac mini is physically stolen, all data is readable — API keys, bot tokens, GitHub credentials, Gmail password, shareholder agreement, partner pipeline, business strategy.  
**Impact:** Total data compromise  
**Fix:** System Settings → Privacy & Security → FileVault → Turn On  
**Time:** 2 minutes to enable, encrypts in background  

### 2. macOS Firewall: OFF
**Risk:** The mini accepts inbound connections from any device on the network. If anyone connects to your WiFi (guest, visitor, compromised device), they can probe all ports.  
**Impact:** Network-level attack surface  
**Fix:** System Settings → Network → Firewall → Turn On  
**Time:** 30 seconds  

---

## 🟠 HIGH — Fix This Week

### 3. Gateway Bound to LAN (port 18789)
**What:** OpenClaw's gateway control interface is accessible to any device on your local network.  
**Risk:** Anyone on the same WiFi could potentially interact with the gateway API.  
**Mitigation in place:** Gateway has auth token requirement.  
**Recommendation:** Enable firewall (fixes this). Consider switching to `bind: localhost` if you don't need LAN access.

### 4. Chrome Browser with Remote Debug Port (18800)
**What:** OpenClaw's managed Chrome instance runs with `--remote-debugging-port=18800`, accessible on LAN.  
**Risk:** Anyone on the network could connect to the debug port and control the browser — read pages, execute JavaScript, access any logged-in sessions.  
**Impact:** Could access GitHub session, Gmail if opened, any site the browser has visited.  
**Mitigation:** Firewall would block inbound. This is expected for OpenClaw's browser control feature, but it's a real attack surface.

### 5. Secrets Directory Permissions (drwxr-xr-x)
**What:** `/Users/apollo/.openclaw/secrets/` directory is world-traversable (755). Files inside are properly restricted (600), but the directory itself allows listing.  
**Risk:** Other local users could see what files exist (filenames), even though they can't read content. Minor on a single-user machine, but bad practice.  
**Fix:** `chmod 700 /Users/apollo/.openclaw/secrets/`

### 6. Telegram 2FA Not Verified
**What:** Telegram is the primary control channel for both Forge and Iron bots.  
**Risk:** If someone gains access to your Telegram account (SIM swap, session theft), they control both AI agents with full system access.  
**Fix:** Enable 2FA in Telegram (Settings → Privacy and Security → Two-Step Verification)

---

## 🟡 MEDIUM — Fix This Month

### 7. 49 World-Readable Files in Workspace
**What:** Multiple workspace files have 644 permissions (world-readable), including:
- All ejeraftale PDFs (shareholder agreement — highly sensitive)
- partner-pipeline.csv (business intelligence)
- USER.md (personal information)
- MEMORY.md (operational context, team info, strategy)
**Risk:** Low on single-user machine, but bad hygiene. If any service is compromised, these are instantly readable.  
**Fix:** `chmod -R go-r /Users/apollo/.openclaw/workspace/`

### 8. Password References in Memory Files
**What:** MEMORY.md and daily notes reference credential storage locations (`credentials in /secrets/github.json`, `app password stored in /secrets/`).  
**Risk:** Breadcrumb trail — if workspace is compromised, attacker knows exactly where to find credentials.  
**Recommendation:** Reference secrets existence but not specific paths. Already mitigated by 600 permissions on actual secret files.

### 9. Gmail Script Reads Credentials from File
**What:** `scripts/check-gmail.py` reads app password from JSON file at runtime.  
**Risk:** Standard pattern, but the script itself is world-readable (644). An attacker can see the code path to credentials.  
**Fix:** `chmod 700 /Users/apollo/.openclaw/workspace/scripts/check-gmail.py`

### 10. GitHub Password-Based Authentication
**What:** Using password login for GitHub (stored in `/secrets/github.json`).  
**Risk:** Password-based auth is weaker than token-based auth. If leaked, grants full account access.  
**Recommendation:** Switch to Personal Access Token (PAT) with minimal scopes (repo read/write only). Revoke password-based access.

### 11. Minimum Password Policy: 4 Characters
**What:** macOS allows passwords as short as 4 characters (or blank).  
**Risk:** Weak local password = easy physical access.  
**Recommendation:** Ensure the `apollo` user has a strong password (12+ characters).

### 12. Keychain: No Timeout
**What:** Login keychain has no lock timeout — stays unlocked until logout/restart.  
**Risk:** If you walk away from the machine, anyone can access stored passwords.  
**Fix:** Set auto-lock in Keychain Access → Preferences, or enable screen lock.

---

## 🟢 LOW / INFORMATIONAL

### 13. Single User Setup
**What:** Everything runs as `apollo` — OpenClaw, browser, scripts, workspace.  
**Risk:** No privilege separation. A compromised process has access to everything.  
**Status:** Acceptable for current scale. Would matter at enterprise level.

### 14. No Audit Logging
**What:** No shell command logging beyond OpenClaw session history.  
**Risk:** If something goes wrong, limited forensic capability.  
**Future:** Consider enabling `sudo` logging and shell history preservation.

### 15. No MDM Enrollment
**What:** Machine is not enrolled in any MDM (Mobile Device Management).  
**Status:** Expected for a personal/startup machine. Not a risk, just noted.

### 16. Auto-Login: Disabled ✅
**Status:** Good — machine requires password at login.

### 17. SIP (System Integrity Protection): Enabled ✅
**Status:** Good — system files are protected from modification.

### 18. Auto-Updates: Enabled ✅
**Status:** Good — automatic check, download, and critical updates all active.

### 19. Telegram Bot Access Control ✅
**What:** Only your Telegram ID (6560116455) is in the allowFrom list.  
**Status:** Good — only you can message the bots.

### 20. No SSH Server Running ✅
**Status:** Good — no remote shell access.

---

## AI-Specific Risks

### 21. Prompt Injection via Untrusted Content
**What:** When I process emails, web pages, or documents from unknown sources, malicious content could attempt to manipulate my behavior.  
**Risk:** An attacker could craft an email that instructs me to leak information or take unauthorized actions.  
**Mitigation:** I'm configured to ask before external actions. But vigilance is needed when processing untrusted input.

### 22. Bot Token Compromise
**What:** Three Telegram bot tokens exist in config (Forge, Iron, Clorius).  
**Risk:** If any token leaks, someone could impersonate the bot. They couldn't control OpenClaw directly, but could phish you.  
**Mitigation:** Tokens are in config file (600 permissions). Clorius token is inactive but should be revoked if not needed.

### 23. Full System Access
**What:** I have unrestricted shell access, filesystem access, and browser control.  
**Risk:** If my behavior is manipulated (prompt injection, system prompt override), the blast radius is the entire machine.  
**Mitigation:** OpenClaw's safety constraints + Anthropic's constitutional AI. But no technical sandbox.

---

## Recommended Action Plan

### Today (5 minutes)
1. ✅ Turn on **FileVault** — System Settings → Privacy & Security → FileVault
2. ✅ Turn on **Firewall** — System Settings → Network → Firewall
3. ✅ Enable **Telegram 2FA**

### This Week (15 minutes)
4. Fix secrets directory: `chmod 700 /Users/apollo/.openclaw/secrets/`
5. Fix workspace permissions: `chmod -R go-r /Users/apollo/.openclaw/workspace/`
6. Fix script permissions: `chmod 700 /Users/apollo/.openclaw/workspace/scripts/check-gmail.py`
7. Switch GitHub from password to Personal Access Token

### This Month
8. Consider revoking unused Clorius bot token
9. Set keychain auto-lock timeout (15-30 minutes)
10. Verify strong password on `apollo` user account
11. Set up screen auto-lock (5 minutes idle)

---

## What's Already Good

| Area | Status |
|------|--------|
| SIP (System Integrity Protection) | ✅ Enabled |
| Auto-updates | ✅ Enabled |
| Auto-login | ✅ Disabled |
| SSH server | ✅ Off |
| Secret files (600) | ✅ Properly restricted |
| Telegram bot allowlist | ✅ Only your ID |
| MDM | ✅ Not enrolled (expected) |
| No open ports (when idle) | ✅ Clean |
| Credential storage | ✅ Separate /secrets/ directory |

---

*This audit covers the surface-level security posture. It does not include penetration testing, network traffic analysis, or firmware-level checks. For a production environment handling enterprise data, a professional security audit would be recommended.*
