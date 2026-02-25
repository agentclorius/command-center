# Warehouse Module Feature Specs — v1
*Date: 2026-02-06*
*Author: Forge (Kasper's AI)*
*For review by: Christian Bjerg, Lasse Schriver*

---

## Strategic Context

### The Challenge
Return Hubs (ITAD partners) are the supply side of Returna. For the platform to succeed, they need to actively use our warehouse and logistics module — not just receive tickets, but run their operations through Returna.

### The Problem
Most ITADs already have tools:
- Spreadsheets and manual tracking
- Basic ERP systems
- Custom-built databases
- Established workflows (even if inefficient)

Switching costs are real. They won't move to Returna's module unless it offers **clear advantages they can't get elsewhere**.

### The Opportunity
If we build features that genuinely make their operations smarter and faster, we:
1. **Increase stickiness** — harder to leave once workflows depend on us
2. **Get better data** — more visibility into the ITAD process
3. **Differentiate** — no other platform offers this level of operational intelligence
4. **Align incentives** — when Return Hubs succeed, Returna succeeds

### Design Principle
Every feature should pass this test: *"Would an ITAD operator look at this and say: I can't do this with my current tools"?*

---

## Feature 1: Smart Triage Routing

### Problem
When devices arrive at a Return Hub, workers must decide how to process each item:
- Does it need an asset tag?
- Does it need data erasure?
- Is it worth full diagnostics, or just bulk recycling?

Currently this requires manual judgment on every item, which is slow and inconsistent.

### Solution
**Automated intake categorization** that routes devices to the right processing track.

### Categories
| Category | Description | Processing Track |
|----------|-------------|------------------|
| **A: Data + High Value** | Laptops, phones, servers with storage | Full processing: tag → wipe → diagnose → grade → stock |
| **B: Data + Low Value** | Old HDDs, low-spec machines | Wipe → certify destruction → recycle |
| **C: No Data + High Value** | Monitors, docking stations, new peripherals | Test → grade → stock (skip erasure) |
| **D: No Data + Low Value** | Cables, mice, keyboards, broken e-waste | Bulk receipt → weigh → recycle (no individual tracking) |

### How It Works
1. **Scan barcode or enter device type**
2. **System auto-categorizes** based on:
   - Device type (laptop vs. cable)
   - Model (if identifiable)
   - Age/generation
   - Customer rules (some enterprises require tagging everything)
3. **Worker sees routing instruction**: "Category A — full processing" or "Category D — bulk bin"
4. **Override available** for edge cases

### Value for ITAD
- **30-50% faster intake** on high-volume, low-value items
- **Consistent decisions** across shifts and workers
- **Audit trail** — "why wasn't this device tagged?" → system decided, logged
- **Customer-specific rules** — enterprise clients can require stricter handling

### Technical Notes
- Needs device type taxonomy
- Rules engine for categorization logic
- Customer-level overrides (per enterprise client)
- Category can change mid-process if new info emerges (e.g., found hidden HDD)

---

## Feature 2: Photo Device ID (Data Risk Detection)

### Problem
Warehouse workers encounter unfamiliar devices:
- "Does this device have a hard drive?"
- "Is there data stored on this?"
- "Do I need to wipe this or just recycle it?"

Wrong decisions = data breach risk (missed HDD) or wasted time (wiping a device with no storage).

### Solution
**Photo-based device identification** that tells workers if a device contains data storage.

### How It Works
1. **Worker takes photo** of unknown device
2. **System identifies** make/model via:
   - Image recognition (if sophisticated)
   - Barcode/serial lookup (if visible)
   - Manual selection from visual catalog
3. **System returns**:
   - Device identification (make, model, year)
   - **Data storage: YES/NO**
   - Storage type (HDD, SSD, NVMe, eMMC, RAM with data persistence)
   - **Diagram showing where storage is located** (optional)
   - Recommended processing track

### Example Output
```
📱 Device: Dell OptiPlex 7080 Micro
📅 Year: 2020
💾 Data Storage: YES
   - 256GB NVMe SSD (M.2 slot, bottom panel)
   - 16GB DDR4 RAM (no persistent data)
⚠️  Recommendation: Category A — requires certified erasure
```

### Value for ITAD
- **Eliminate guesswork** on data risk
- **Train new workers faster** — system knows what they don't
- **Reduce breach risk** — no more "I didn't know it had a drive"
- **Handle diverse inventory** — ITADs receive everything, can't know every device

### Technical Notes
- Device database needed (model → storage specs)
  - Could start with top 500 enterprise models (covers 80%)
  - Expand based on "unknown device" submissions
- Image recognition is nice-to-have, not required for v1
- Serial number → specs lookup via OEM APIs where available

### Data Sources to Research
- ICECAT (open catalog)
- OEM product databases (Dell, HP, Lenovo APIs)
- PartnerNet / distributor feeds
- Community-contributed specs

---

## Feature 3: Price Estimation

### Problem
ITADs need to know what a device is worth:
- For quoting customers
- For grading decisions (repair vs. recycle?)
- For resale pricing
- For inventory valuation

Currently relies on worker experience or manual market research.

### Solution
**Model + condition → estimated resale value** in real-time.

### How It Works
1. **Device identified** (from intake or photo ID)
2. **Condition graded** (A/B/C/D or detailed checklist)
3. **System returns**:
   - Estimated resale price range (low / mid / high)
   - Price trend (rising, stable, falling)
   - Confidence level
   - Comparable sales data (optional)

### Example Output
```
💻 Dell Latitude 5520 (2021)
🔋 Condition: B (minor wear, functional)
💰 Estimated Value: €180 - €220
📈 Trend: Stable (±5% last 30 days)
🎯 Confidence: High (200+ recent sales)
```

### Value for ITAD
- **Faster quoting** — instant ballpark for customer discussions
- **Better decisions** — is it worth repairing this screen? (check resale value)
- **Inventory insights** — total portfolio value at a glance
- **Pricing confidence** — reduce margin guesswork

### Technical Notes
- Needs resale price data:
  - Back Market API (if available)
  - eBay completed listings
  - Refurbed
  - B2B broker prices
  - Historical Returna transaction data (long-term)
- Model + specs + condition → price algorithm
- Regularly updated (prices change)

---

## Feature 4: Resale Channel Routing

### Problem
ITADs have multiple resale options:
- B2B wholesale
- Back Market
- eBay
- Refurbed
- Amazon Renewed
- Direct to customer
- Own webshop

Choosing the right channel affects margin. Wrong choice = money left on table.

### Solution
**Automated channel recommendation** based on device, condition, and channel economics.

### How It Works
1. **Device graded and valued**
2. **System analyzes channels**:
   - Expected sale price per channel
   - Fees and commissions
   - Time to sell (inventory turnover)
   - Logistics cost
3. **Recommends optimal channel** (or top 3 ranked)

### Example Output
```
💻 Dell Latitude 5520 (Grade B)

Recommended Channels:
1. 🥇 Back Market — €195 net (€220 - 11% fee), ~7 days to sell
2. 🥈 B2B Wholesale — €175 net (bulk, instant)
3. 🥉 eBay — €205 net (€240 - 13% fee - shipping), ~14 days

💡 Suggestion: Back Market (best balance of price + speed)
```

### Value for ITAD
- **Maximize margin** — right device to right channel
- **Reduce decision fatigue** — system recommends, worker confirms
- **Balance speed vs. price** — need cash? Go B2B. Can wait? List retail.
- **Learn over time** — track which channels perform for which devices

### Technical Notes
- Needs channel economics data:
  - Fee structures per platform
  - Average time to sell per device category
  - Historical performance (what sold where, for how much)
- Could integrate with marketplace APIs for listing (future)
- Start with recommendation, later add one-click listing

---

## Implementation Priority (Suggestion)

| Feature | Value | Effort | Recommendation |
|---------|-------|--------|----------------|
| Smart Triage Routing | High | Medium | **Start here** — foundational for efficiency |
| Photo Device ID | High | Medium-High | Second priority — big UX win, needs device DB |
| Price Estimation | Medium-High | High | Third — needs external data integration |
| Resale Channel Routing | Medium | High | Fourth — builds on price estimation |

### Suggested Sequence
1. **Triage Routing** — can build with internal logic, no external dependencies
2. **Photo Device ID** — start simple (serial lookup), add image recognition later
3. **Price Estimation** — integrate one data source first (eBay?), expand
4. **Resale Channel Routing** — layer on top of pricing

---

## Questions for Discussion

1. **Device database** — build vs. buy? ICECAT? OEM APIs?
2. **Pricing data** — which sources are accessible? Back Market API?
3. **MVP scope** — which feature delivers quickest value for pilot Return Hubs?
4. **Customer rules** — how flexible does the rules engine need to be?

---

## Next Steps

1. **Lasse**: Product perspective — does this align with roadmap? What's missing?
2. **Christian**: Technical feasibility — any blockers? Effort estimates?
3. **All**: Which feature should we prototype first?

Looking forward to your feedback.

— Forge
