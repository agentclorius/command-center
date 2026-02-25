# Partner CRM System Design

_Created: 2026-02-25 | Status: Ready for Implementation_

## Purpose

A lightweight CRM to track Return Hub partners from prospect to active hub. Designed for the current stage (43 prospects, 31 contacts) with room to scale.

---

## Core Requirements

1. **Pipeline tracking** — Know where every prospect stands
2. **Contact management** — Never lose a decision-maker
3. **Follow-up scheduling** — No prospect falls through cracks
4. **Conversion metrics** — Track funnel performance
5. **Geographic coverage** — Identify gaps visually
6. **Team collaboration** — Kasper + Clorius can both update

---

## Recommended Tool: Google Sheets

**Why Sheets over Notion/Airtable/HubSpot:**
- Free, already in use at Returna
- Easy sharing with team
- Works offline (important for travel)
- Simple automation via Apps Script
- CSV import/export (existing pipeline data)
- No learning curve

**Later migration path:** When >100 prospects or multiple team members doing outreach → Pipedrive or HubSpot CRM Free.

---

## Sheet Structure

### Sheet 1: Pipeline (Master View)

| Column | Purpose | Values |
|--------|---------|--------|
| Company | Partner name | Text |
| Country | Location | Country code |
| Region | Grouping | Nordics / DACH / UK&IE / Benelux / Southern / Eastern / NA |
| Stage | Pipeline stage | Prospect → Qualified → Contacted → Meeting → Contract → Setup → Active |
| Score | Capability score | 0-100 |
| Priority | Outreach priority | 🔴 High / 🟡 Medium / 🟢 Low |
| Contact Name | Decision-maker | Text |
| Contact Email | Email | Email |
| Contact LinkedIn | Profile URL | URL |
| Contact Phone | Phone | Phone |
| Last Contact | Date of last touch | Date |
| Next Action | What's next | Text |
| Next Action Date | When | Date |
| Owner | Who's handling | Kasper / Clorius |
| Notes | Context | Text |

### Sheet 2: Activity Log

| Column | Purpose |
|--------|---------|
| Date | When |
| Company | Which partner |
| Activity Type | Email / Call / Meeting / LinkedIn / Research |
| Direction | Outbound / Inbound |
| Summary | What happened |
| Next Step | Follow-up needed |
| By | Who did it |

### Sheet 3: Contacts Database

| Column | Purpose |
|--------|---------|
| Name | Full name |
| Company | Associated partner |
| Title | Job title |
| Email | Email address |
| Phone | Phone number |
| LinkedIn | Profile URL |
| Source | How we found them |
| Verified | Yes/No |
| Notes | Relationship notes |

### Sheet 4: Regional Dashboard

| Region | Prospects | Contacted | Meetings | Contracts | Active | Coverage % |
|--------|-----------|-----------|----------|-----------|--------|------------|
| Nordics | 6 | 2 | 0 | 0 | 1 | 17% |
| DACH | 7 | 0 | 0 | 0 | 0 | 0% |
| UK & Ireland | 10 | 0 | 0 | 0 | 0 | 0% |
| etc. | ... | ... | ... | ... | ... | ... |

### Sheet 5: Metrics

**Key formulas to implement:**

```
Conversion Rate (Prospect → Contact) = COUNTIF(Stage, "Contacted+")/COUNTIF(Stage, "*")
Average Days in Stage = AVERAGE of (Next Stage Date - Current Stage Date)
Response Rate = Responses / Outreach Attempts
Win Rate = Active Hubs / Total Prospects Contacted
```

---

## Pipeline Stages (Detailed)

### Stage 1: Prospect
- **Definition:** Identified as potential partner, not yet contacted
- **Entry criteria:** Company researched, meets basic requirements
- **Exit criteria:** First outreach sent
- **Typical duration:** 0-14 days

### Stage 2: Contacted
- **Definition:** First outreach sent, awaiting response
- **Entry criteria:** Email/LinkedIn sent
- **Exit criteria:** Response received (positive or negative)
- **Typical duration:** 7-21 days
- **Follow-up:** Day 7, Day 14, Day 21

### Stage 3: Engaged
- **Definition:** Responded positively, in conversation
- **Entry criteria:** Positive response received
- **Exit criteria:** Meeting scheduled or declined
- **Typical duration:** 7-14 days

### Stage 4: Meeting
- **Definition:** Meeting scheduled or completed
- **Entry criteria:** Calendar invite sent/accepted
- **Exit criteria:** Meeting completed, decision made
- **Typical duration:** 7-30 days

### Stage 5: Contract
- **Definition:** Terms being negotiated
- **Entry criteria:** Verbal commitment to proceed
- **Exit criteria:** Agreement signed
- **Typical duration:** 14-30 days

### Stage 6: Setup
- **Definition:** Technical onboarding in progress
- **Entry criteria:** Contract signed
- **Exit criteria:** First ticket processed
- **Typical duration:** 7-14 days

### Stage 7: Active Hub
- **Definition:** Live and processing tickets
- **Entry criteria:** First ticket completed
- **Exit criteria:** N/A (or churned)

---

## Follow-up Cadence

### Initial Outreach Sequence

| Day | Action | Template |
|-----|--------|----------|
| 0 | Initial email | `outreach-01-intro.md` |
| 7 | Follow-up 1 | `outreach-02-value.md` |
| 14 | Follow-up 2 (LinkedIn) | Connect + message |
| 21 | Final follow-up | `outreach-03-final.md` |
| 28 | Mark as "No Response" | Move to nurture list |

### Engaged Prospect Cadence

| Trigger | Action |
|---------|--------|
| After positive reply | Schedule meeting within 5 days |
| After meeting | Send summary + next steps within 24h |
| After proposal sent | Follow up Day 3, Day 7 |
| Radio silence >7 days | Check in email |

---

## Automation Opportunities

### Google Apps Script Functions

1. **Auto-highlight overdue follow-ups**
   - Conditional formatting: Next Action Date < Today → Red
   
2. **Daily digest email**
   - List of follow-ups due today/tomorrow
   
3. **Auto-calculate days since last contact**
   - Formula: `=TODAY()-[Last Contact]`
   
4. **Stage change timestamp**
   - Log when stage changes

### Future: n8n/Zapier Integration

When scaling:
- New prospect added → Slack notification
- Stage change → Log to Activity sheet
- Meeting scheduled → Calendar event
- Contract signed → Notify team

---

## Data Migration

### From Current CSV

The existing `partner-pipeline.csv` maps directly:

| Current Column | CRM Column |
|----------------|------------|
| Company | Company |
| Country | Country |
| Region | Region |
| Status | Stage (convert "Prospect" → "Prospect") |
| Contact Name | Contact Name |
| Contact Email | Contact Email |
| Priority | Priority |
| Notes | Notes |
| First Contact | First Contact Date |
| Last Contact | Last Contact Date |
| Next Action | Next Action |

### Missing Data to Add

For each of 43 prospects, verify:
- [ ] Contact LinkedIn URL
- [ ] Contact phone (where available)
- [ ] Contact verified (Yes/No)
- [ ] Score (re-verify against 100-point rubric)

---

## Views / Filters

### Saved Filters (Google Sheets)

1. **My Follow-ups Today**
   - Next Action Date = Today
   - Owner = [current user]

2. **Overdue Actions**
   - Next Action Date < Today
   
3. **High Priority Uncontacted**
   - Priority = High
   - Stage = Prospect

4. **By Region**
   - Filter by Region column

5. **Ready for Outreach**
   - Stage = Prospect
   - Contact Email ≠ blank

---

## Reporting

### Weekly Metrics (Monday)

| Metric | Calculation |
|--------|-------------|
| New prospects added | Count where Created Date = last 7 days |
| Outreach sent | Count Activity Log where Type = Email, Direction = Outbound |
| Responses received | Count stage changes Prospect → Contacted |
| Meetings scheduled | Count stage changes → Meeting |
| Conversion rate | Meetings / Outreach |

### Monthly Report

- Pipeline by stage (waterfall)
- Regional coverage map
- Top prospects by score
- Stale prospects (>30 days no activity)
- Win/loss analysis

---

## Implementation Checklist

### Phase 1: Setup (1-2 hours)
- [ ] Create Google Sheet from template
- [ ] Import `partner-pipeline.csv`
- [ ] Add conditional formatting for overdue items
- [ ] Create regional dashboard with formulas
- [ ] Share with Kasper (edit access)

### Phase 2: Data Enrichment (2-3 hours)
- [ ] Verify all 31 contacts (LinkedIn lookup)
- [ ] Add missing LinkedIn URLs
- [ ] Update scores based on latest rubric
- [ ] Set initial Next Action dates

### Phase 3: Process (Ongoing)
- [ ] Log all activities in Activity Log
- [ ] Update stages as prospects progress
- [ ] Weekly review of pipeline metrics
- [ ] Monthly regional coverage review

---

## Template Links (To Create)

1. **Google Sheet Template** — Will create when approved
2. **Activity Log Template** — Included in main sheet
3. **Weekly Report Template** — Dashboard view

---

## Alternatives Considered

| Tool | Pros | Cons | Verdict |
|------|------|------|---------|
| Google Sheets | Free, simple, offline | Manual, no automation | ✅ Best for now |
| Notion | Flexible, nice UI | Learning curve, no offline | Maybe later |
| Airtable | Powerful, automations | Paid for good features | Overkill now |
| Pipedrive | Purpose-built CRM | €15/user/mo | When scaling |
| HubSpot Free | Full CRM, free | Complex, overkill | When >100 prospects |

---

## Next Steps

1. **Kasper approval** — Review this design
2. **Create Sheet** — Build from template
3. **Import data** — Migrate current CSV
4. **Enrich contacts** — LinkedIn verification
5. **Set cadence** — Define follow-up schedule
6. **Go live** — When outreach resumes

---

_This CRM is designed for the 43-prospect, 2-person (Kasper + Clorius) stage. Will recommend migration to dedicated CRM when hitting 100+ prospects or adding sales team members._
