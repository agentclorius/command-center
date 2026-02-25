# Returna — Company Context

## What Returna Is

Global orchestration and execution platform for IT asset end-of-life (EOL) and device returns. When enterprises need laptops back from departing employees, refresh hardware, or close offices — Returna coordinates the entire workflow across all parties.

**Not** an ITAD provider, logistics carrier, resale marketplace, or CMDB replacement. It's the neutral execution and settlement layer that the fragmented ITAD industry is missing.

## The Problem

- 250M corporate devices leave company control yearly
- Enterprises face data risk, lost value, and ESG/compliance pressure
- Managed with fragmented local vendors, no single system of record, no global visibility
- Box programs (ship-to-employee returns) promised hands-off returns but multiplied coordination
- Without software, box programs scale with headcount, not volume

## Platform Model

**Enterprises** → Returna → **Return Hubs** (ITAD contractors) → logistics → processing → disposition

Returna orchestrates, standardizes, proves, and settles.

## Core Modules

1. **Dashboard** — Operational control surface, role-aware, action-oriented widgets
2. **Tickets** — Orchestration containers (box return, bulk return, redeployment, relocation)
3. **Warehouse** — Return Hub ERP (logistics, intake, processing, disposition)
4. **Assets** — Enterprise decision layer (inventory, repair approval, redeployment, relocation)
5. **Employee Return Portal** — Self-service for device holders (verification, pickup booking, AI support)
6. **Support & Communication** — Unified inbox, ticket-linked, AI-assisted
7. **Automation & Policy Engine** — Routing, qualification, approval, communication policies
8. **Integrations** — API-first (ITSM, ITAM, ERP, MDM, HRIS)
9. **Reporting, Invoicing & ESG** — Live + recurring commercial reports, CO₂ data
10. **Settings** — Users, contracts, routing, pricing, email flows, packaging
11. **AI Workflows** — Support agents, decision support, engineering agents, policy interpretation
12. **Data Intelligence** — Anonymized execution data, lifecycle insights, future monetization

## Commercial Model

- **Tickets** are orchestration containers; **devices** are the billable units
- All execution pricing is per device within a ticket
- Resale outcome discovered post-processing, not pre-declared

### Self-Serve Plans

- **Essential** (50–500 employees): €99/mo + €195/device
- **Growth** (500–3,000 employees): €399/mo + €185/device box, €110/device bulk

### Enterprise

- Annual platform commitment (€50K–€250K/yr)
- Tiered per-device execution pricing
- Minimum volume commitments

### Platform Economics

- **10% platform fee** taken from enterprise invoice before contractor payout
- **Resale split**: 70% enterprise / 30% Return Hub — Returna takes zero resale upside
- Returna monetizes resale execution/settlement, not market upside (preserves neutrality)
- Settlement: Returna acts as clearing layer, netting proceeds against invoices

## Fundraising

- **Round:** Seed
- **Amount:** 5M DKK (~€670K)
- **Runway:** 24 months (26 months budgeted)
- **Burn:** ~165K DKK/month
- **Use:** Engineering (2 devs), cloud/tooling, legal/ISO27001, Scandic IT software transfer, sales/GTM

## Team

- **Christina Hove** — CEO, enterprise sales since ~2000, leading fundraising
- **Kasper Horn** — Co-founder, ITAD operator since ~2007, ITAD sales / GTM for contractors
- **Mike Andersen** — Co-founder, ITAD operator since ~2007, operations / finance / onboarding
- **Chris Zimmerman** — CSO, digital ITAD pioneer since ~2000, development / marketing / product
- **Lasse Schriver** — CPO, 5+ years data erasure/compliance, product specs / strategy
- **Christian Bjerg** — CTO, 5+ years box program automations, manages the main repo

### Origin Story

Built from real ITAD execution at Scandic IT → evolved into platform. Software transfer from Scandic IT to Returna is part of the seed round budget. Kasper and Mike founded Scandic IT in 2016 and ran the first large-scale box programs from 2020.

## Target Customers

1. **Global enterprises** (5K+ devices, multi-country, hybrid workforce)
2. **Regulated industries** (pharma, healthcare, finance, defense)
3. **Lifecycle service providers** (MSPs, large ITAD networks)

## Growth Projections (Illustrative)

- Year 1: ~5 enterprise customers
- Year 3: ~25
- Year 5: ~75
- At scale with mix: ~120M DKK ARR

## Key Design Principles

- Execution over visibility
- Policy-driven automation
- Event-based state transitions
- Chain-of-custody by default
- Vendor-agnostic orchestration
- API-first architecture
- Audit-ready by default
- Enterprise trust over visual novelty

## Development Workflow

- **Main repo:** returnaaps/returna (umbrella with api/ and web/ submodules)
- **CTO:** Christian Bjerg manages the repo
- **Process:** Create branch on returnaaps/returna → work on branch → PR to branch (never to main)
- **Stack:** NestJS backend + Mongoose (MongoDB) / Angular frontend

## Competitive Position

Returna is NOT competing with:
- ITAD providers (we orchestrate them)
- ServiceNow/ITSM tools (we integrate with them)
- Resale marketplaces (we connect to them)

Returna IS the missing layer between enterprise IT and fragmented ITAD execution. No platform currently standardizes this workflow globally.

## Key Business Priorities (Current)

1. Close seed round (5M DKK)
2. Complete platform development (orchestration layer, warehouse module, employee portal)
3. Onboard first enterprise customers
4. Build Return Hub (contractor) network
5. Achieve ISO 27001 certification
6. Transfer software from Scandic IT to Returna

---

## Scandic IT — Sister Company

**Scandic IT** (scandic-it.com) is an ITAD company co-founded by Kasper Horn and Mike Andersen in 2016. It operates as both a standalone business and the proving ground for Returna's platform.

### Full Lifecycle Services

**Depot Services:**
- Secure data erasure (NIST 800-88 compliant)
- Diagnostics and testing
- Repairs including keyboard replacements
- Re-imaging and configuration
- Asset grading and stocking
- Redeployment preparation

**Reverse Logistics:**
- Office pickups (bulk collection from enterprise locations)
- Employee home pickups (individual device collection)
- Scalable box programme:
  - Home collection via courier
  - Parcel shop drop-off network
- Cross-border and domestic shipping

**Circular IT Partnerships:**
- Full lifecycle management for enterprise clients
- Resale and value recovery
- Certified recycling and destruction
- Sustainability reporting and certificates

### Technology & Integration

- **Live portal:** Powered by Returna platform
- **Courier integrations:** Multiple carriers for pickup and delivery
- **Erasure tool integrations:** Certified data sanitization
- **Diagnostics integrations:** Automated testing and grading
- **ERP integration:** Inventory, processing, and financial tracking

### Partner Network

- Collaboration with vetted global partners for international coverage
- Can handle devices across Europe and beyond through partner network

### Capabilities

- Deep ITAD industry expertise (founded 2016, operators since 2007)
- Proven client base of Danish and Nordic enterprises
- In-house technical repair capabilities
- Full chain-of-custody documentation
- Audit-ready compliance processes

### Relationship to Returna

Scandic IT is:
- A live customer of Returna (uses the platform daily)
- The original development partner (platform built for Scandic IT's operations)
- A case study for how Return Hubs operate
- Source of industry insights that inform Returna's product
- Part of the seed round: software transfer from Scandic IT to Returna included in budget
