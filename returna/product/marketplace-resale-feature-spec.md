# Returna Marketplace Resale — Product Spec

*Draft v0.1 — February 2026*

---

## Overview

Returna acts as **3rd party seller** on major refurbished device marketplaces, listing enterprise devices that won't be reused. Return Hubs provide fulfillment (storage, shipping) and receive a fee per sale.

---

## Business Model

```
Enterprise → Returna Platform → Marketplace Listing → Sale
                                      ↓
                              Return Hub Fulfills
                                      ↓
                         Returna Pays Hub + Keeps Margin
```

### Revenue Flow Example (€500 device sale)

| Party | Amount | % |
|-------|--------|---|
| Marketplace fee (Back Market ~12%) | €60 | 12% |
| Return Hub fulfillment fee | €40 | 8% |
| **Returna margin** | €50 | 10% |
| **Enterprise payout** | €350 | 70% |

*Percentages adjustable based on device value, marketplace, volume*

---

## Value Proposition

### For Enterprises
- **Better return value** — Multi-marketplace exposure = higher prices
- **Single partner** — Returna handles all resale complexity
- **Transparency** — See listing status, sale price, payout

### For Return Hubs
- **Steady revenue** — Fulfillment fees for storage + shipping
- **No sales effort** — Returna brings the listings
- **Simple ops** — Pick, pack, ship on notification

### For Returna
- **New revenue stream** — Margin on every sale
- **Platform stickiness** — Enterprises + Hubs more dependent
- **Data advantage** — Pricing intelligence across marketplaces

---

## Core Features

### 1. Device Listing Engine

**Inputs from Return Hub (post-processing):**
- Device type, make, model
- Condition grade (A/B/C)
- Specs (RAM, storage, etc.)
- Photos (automated or manual)
- Serial number / IMEI
- Erasure certificate

**Listing Logic:**
- Auto-match to marketplace categories
- Dynamic pricing based on:
  - Marketplace price data
  - Condition grade
  - Device age
  - Current inventory levels
- Multi-marketplace syndication (list on 2-3 simultaneously)

### 2. Marketplace Integrations

**Phase 1 (MVP):**
| Marketplace | Why | API Status |
|-------------|-----|------------|
| **Back Market** | Largest EU refurb marketplace | Seller API available |
| **eBay** | Massive reach, proven API | Robust API |

**Phase 2:**
| Marketplace | Why |
|-------------|-----|
| **Amazon Renewed** | Huge volume (invite-only) |
| **Refurbed** | Strong in DACH |
| **Swappie** | Phones (if volume justifies) |

**Phase 3:**
- B2B wholesale channels (bulk lots)
- Regional marketplaces

### 3. Fulfillment Workflow

```
1. Device sold on marketplace
2. Returna notifies Return Hub (API + email)
3. Return Hub picks device from inventory
4. Return Hub ships (Returna-provided label or Hub's carrier)
5. Return Hub confirms shipment
6. Marketplace confirms delivery
7. Returna receives payout
8. Returna pays Return Hub fee
9. Returna pays Enterprise share
```

### 4. Inventory Management

**Return Hub Dashboard:**
- Devices in stock (by grade, type)
- Devices listed (by marketplace)
- Sales pending shipment
- Fulfillment SLA tracking

**Returna Central View:**
- Global inventory across all Hubs
- Routing logic (which Hub fulfills which region)
- Stock balancing alerts

### 5. Pricing Intelligence

**Data collected:**
- Sale prices across marketplaces
- Time-to-sale by device type/grade
- Price trends over time
- Marketplace fee structures

**Used for:**
- Dynamic pricing optimization
- Enterprise value estimates (pre-processing)
- Return Hub performance benchmarking

---

## Technical Architecture

### API Integrations Required

```
┌─────────────────────────────────────────────────────┐
│                  RETURNA PLATFORM                    │
├─────────────────────────────────────────────────────┤
│  Listing Service  │  Order Service  │  Payout Svc   │
└────────┬──────────┴────────┬────────┴───────┬───────┘
         │                   │                │
    ┌────▼────┐         ┌────▼────┐     ┌────▼────┐
    │ Market- │         │ Return  │     │ Payment │
    │ places  │         │  Hubs   │     │ Gateway │
    └─────────┘         └─────────┘     └─────────┘
    
Marketplaces:           Return Hubs:      Payments:
- Back Market API       - Webhook/API     - Stripe
- eBay API              - Email fallback  - Bank transfer
- Amazon SP-API         - Mobile app
- Refurbed API
```

### Key API Capabilities Needed

**Per Marketplace:**
- Create/update/delete listings
- Receive order notifications (webhook)
- Update order status (shipped, tracking)
- Receive payout notifications

**Estimated Dev Effort:**
| Component | Effort |
|-----------|--------|
| Back Market integration | 2-3 weeks |
| eBay integration | 2-3 weeks |
| Listing engine + pricing | 3-4 weeks |
| Fulfillment workflow | 2-3 weeks |
| Payout system | 2 weeks |
| Return Hub dashboard | 2 weeks |
| **Total MVP** | **~12-16 weeks** |

---

## Pricing Strategy

### Marketplace Fee Benchmarks

| Marketplace | Seller Fee | Notes |
|-------------|------------|-------|
| Back Market | 10-15% | Varies by category |
| eBay | 12-15% | Final value fee |
| Amazon Renewed | 15% | Referral fee |
| Refurbed | 12-15% | Similar to Back Market |

### Returna Margin Options

**Option A: Fixed %**
- Returna takes 8-12% of sale price
- Simple, predictable

**Option B: Tiered by Value**
| Device Value | Returna Margin |
|--------------|----------------|
| <€200 | 15% |
| €200-500 | 10% |
| >€500 | 8% |

**Option C: Performance-based**
- Lower margin if Returna achieves price above estimate
- Aligns incentives with enterprise

### Return Hub Fulfillment Fee

**Option A: Fixed per device**
| Device Type | Fee |
|-------------|-----|
| Phone | €15 |
| Laptop | €25 |
| Desktop | €35 |
| Monitor | €30 |

**Option B: % of sale**
- 5-8% of sale price
- Scales with device value

---

## Risks & Mitigations

| Risk | Mitigation |
|------|------------|
| Marketplace account suspension | Multiple accounts, compliance focus |
| Return Hub fulfillment delays | SLA requirements, backup Hubs |
| Pricing errors (sell too low) | Minimum price floors, human review for high-value |
| Returns/refunds | Clear condition grading, Return Hub handles |
| Cash flow (payout timing) | Marketplace payouts vary; may need float |

---

## Success Metrics

**Phase 1 (3 months post-launch):**
- 500+ devices listed/month
- 70%+ sell-through rate
- <3 day avg time-to-ship
- <5% return rate

**Phase 2 (12 months):**
- 5,000+ devices listed/month
- 3+ marketplaces active
- €500K+ GMV/month
- Positive unit economics proven

---

## Open Questions

1. **Seller entity** — Returna ApS as seller, or separate entity?
2. **Liability** — Who handles returns/refunds/disputes?
3. **Branding** — Sell as "Returna" or white-label?
4. **Exclusivity** — Can Return Hubs also sell direct?
5. **Geographic routing** — Hub in Germany fulfills German orders only?

---

## Next Steps

1. [ ] Validate marketplace API access (Back Market, eBay)
2. [ ] Define MVP scope with Lasse/Christian
3. [ ] Financial model for unit economics
4. [ ] Legal review (seller obligations, VAT)
5. [ ] Pilot with 1 Return Hub + 1 marketplace

---

*Prepared by Clorius for Returna product planning*
