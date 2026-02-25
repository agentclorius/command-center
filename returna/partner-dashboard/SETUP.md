# Returna Partner Dashboard — Setup Guide

## Quick Start

1. Go to [Google Sheets](https://sheets.google.com)
2. Create new spreadsheet: "Returna Partner Pipeline"
3. Import each CSV as a separate tab:
   - File → Import → Upload → Select CSV
   - Choose "Insert new sheet"
   - Repeat for each CSV file

## Tab Structure

| Tab | File | Purpose |
|-----|------|---------|
| Pipeline | 1-pipeline.csv | All prospects with scores and status |
| Coverage | 2-regional-coverage.csv | Regional gap analysis |
| Activity | 3-activity-log.csv | Outreach history |
| Disqualified | 4-disqualified.csv | Companies we've ruled out and why |
| Dashboard | (create manually) | Charts and summary stats |

## Pipeline Statuses

```
Research → Contacted → Meeting → Negotiation → Onboarding → Active
```

## Scoring System (0-100)

| Category | Max | What It Measures |
|----------|-----|------------------|
| Size & Independence | 30 | Sweet spot: 10-200 employees, €1-30M revenue |
| Certifications | 25 | ISO 27001, ISO 14001, R2, ADISA |
| Technology Gap | 20 | No own platform = high score |
| Market Position | 15 | Existing relationship, reputation |
| Capabilities | 10 | Erasure, diagnostics, logistics, resale |

### Score Thresholds
- 🟢 80-100: Priority — fast-track outreach
- 🟡 60-79: Standard — qualified, proceed normally  
- 🟠 40-59: Research — needs more info before deciding
- 🔴 <40: Disqualify — move to Disqualified tab

## Auto-Calculate Score Formula

In Pipeline tab, add this formula in the Score column (assuming row 2):

```
=E2+F2+G2+H2+I2
```

Where E-I are the individual score columns.

## Dashboard Tab — Create These Charts

### 1. Pipeline by Status (Pie Chart)
- Data: Count of companies per status
- Shows: Where prospects are in funnel

### 2. Regional Coverage (Bar Chart)  
- Data: From Coverage tab — Active vs Gap by country
- Shows: Where we need partners

### 3. Pipeline by Score Tier (Pie Chart)
- Data: Count by score range (80+, 60-79, 40-59, <40)
- Shows: Quality of pipeline

### 4. Monthly Activity (Line Chart)
- Data: Count of activities per week/month
- Shows: Outreach velocity

## Key Metrics to Track

| Metric | Formula | Target |
|--------|---------|--------|
| Total Pipeline | =COUNTA(Pipeline!A:A)-1 | 50+ |
| Qualified (60+) | =COUNTIF(Pipeline!E:E,">=60") | 30+ |
| Priority (80+) | =COUNTIF(Pipeline!E:E,">=80") | 10+ |
| Active Hubs | =COUNTIF(Pipeline!D:D,"Active") | TBD |
| Conversion Rate | =Active/Total Contacted | 20%+ |

## Sharing

1. Click "Share" in top right
2. Add team members:
   - christina.hove@returna.com
   - mike.andersen@returna.com
   - chris.zimmerman@returna.com
   - lasse.schriver@returna.com
3. Set to "Editor" for full access

## Maintenance

- **Daily:** Log all outreach in Activity tab
- **Weekly:** Update statuses, review scores
- **Monthly:** Review coverage gaps, adjust priorities

---

Built by Forge 🔨 | 2026-02-05
