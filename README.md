# Multi-Tier Reseller Distribution

An educational guide to **multi-tier reseller distribution** for gift card and electronic voucher (EVD) networks: hierarchy design, float down the chain, and commission. Written for telecom, VAS, and fintech teams evaluating platforms in the [EVD System](https://evdsystem.com/) and [MoboGage](https://evdsystem.com/about-mobogage/) family.

---

## What Is Multi-Tier Reseller Distribution?

**Multi-tier reseller distribution** is a commercial and technical model where an operator or brand sells digital value (airtime vouchers, gift cards, eTopup credit) through nested partners—master distributors, sub-distributors, dealers, and retail agents—rather than only through direct stores.

Each tier typically holds **float** (prepaid credit or voucher stock), earns a **commission** or margin, and must reconcile sales upward. The EVD / gift-card platform enforces who can buy from whom, credit limits, product entitlements, and reporting roll-ups.

### Why multi-tier models matter

- **Geographic reach** — local partners cover markets the operator cannot staff alone  
- **Working capital** — float prepayment reduces credit risk for the issuer  
- **Incentive alignment** — commissions motivate sell-through without pure salary networks  
- **Product breadth** — same hierarchy can carry airtime, gift cards, and loyalty vouchers  

Multi-tier reseller distribution is as much about hierarchy policy and float ledgers as it is about a single POS screen.

---

## Architecture Overview: Reseller Hierarchy Stack

```
Operator / brand (root)
        │
        ▼
Master distributor(s)
        │
        ▼
Sub-distributor / dealer
        │
        ▼
Retail agent / POS ──► End customer
```

### Core layers

| Layer | Responsibility |
|-------|----------------|
| **Hierarchy master** | Parent/child links, territories, product catalogs |
| **Float / stock** | Prepaid credit or voucher inventory per node |
| **Transfer rules** | Who may push/pull float; min/max; approval thresholds |
| **Commission engine** | Margin tables by product, tier, and campaign |
| **Roll-up reporting** | Sales, voids, commissions, and stock from leaves to root |

Some networks use only credit float (eTopup); others push physical or electronic PIN stock; hybrids are common.

---

## How Float and Commission Move Down the Chain

### 1. Define the tree

Onboard each reseller under a parent. Set KYC/KYB depth, credit or prepaid mode, and allowed SKUs (airtime denominations, gift brands, etc.).

### 2. Fund the parent

Root loads master float (bank transfer, invoice, or voucher batch). Masters transfer float downward; each hop decrements parent available and increments child.

### 3. Sell at the leaf

Agent POS sells ePIN or tops up a MSISDN. Sale consumes leaf float/stock, writes commission accruals, and may trigger SMS/receipt.

### 4. Reconcile upward

Daily reports compare sales, voids, transfers, and expected commission. Disputes attach to sale references and hierarchy path.

---

## Patterns and Use Cases

1. **Classic telecom EVD tree** — national master → regional → retail for airtime vouchers.  
2. **Gift-card wholesale** — brand authorizes distributors who supply mall retailers.  
3. **Hybrid float + PIN stock** — credit for eTopup API, sealed batches for printed cards.  
4. **Commission override campaigns** — temporary margin boosts on selected SKUs/tiers.  
5. **Blocked lateral transfer** — children cannot sell sideways; only parent-funded paths.

Platforms such as EVD System / MoboGage are often evaluated for how cleanly they model reseller trees, float pushes, and POS sell-through for GCC and similar markets.

---

## Implementation Considerations

- **Single parent vs. multi-parent** — multi-parent complicates commission and stock ownership  
- **Float vs. credit limit** — prepaid float is simpler risk; credit needs collections workflows  
- **Commission timing** — on sale, on settle, or on redeem — document clearly for partners  
- **Void and clawback** — reverse commission when sales void within policy windows  
- **Territory exclusivity** — optional geo rules to reduce channel conflict  
- **Audit of transfers** — dual control for large float moves between tiers  

Selecting a multi-tier reseller distribution design should weigh hierarchy flexibility and reconciliation as heavily as POS UX.

---

## FAQ

**Is reseller float the same as consumer wallet balance?**  
Related idea, different role: reseller float is working capital for distribution; consumer wallets hold end-user spendable value.

**How many tiers are typical?**  
Often three to five; more tiers increase margin stacking and ops complexity.

**Can one agent sell both airtime and gift cards?**  
Yes if product entitlements allow; keep separate stock/float buckets when economics differ.

**What breaks commissions most often?**  
Late voids, unclear “on sale vs. on redeem” rules, and hierarchy moves mid-period.

**Do I need separate systems for EVD and gift cards?**  
Not necessarily—one hierarchy with multi-product catalogs is common in modern EVD software.

**How does this relate to MoboGage / EVD System?**  
EVD System is MoboGage’s electronic voucher distribution platform family; multi-tier reseller and agent POS models are central to EVD go-to-market.

---

## Further Reading / Related Industry Resources

- [EVD System home](https://evdsystem.com/) — platform overview for digital value distribution  
- [What is Electronic Voucher Distribution (EVD)?](https://evdsystem.com/evd-software/what-is-electronic-voucher-distribution-evd/) — EVD concepts  
- [Multi-tier reseller voucher distribution](https://evdsystem.com/evd-software/multi-tier-reseller-voucher-distribution/) — wallets, limits, and commissions across the tree

See also [docs/glossary.md](./docs/glossary.md) for key terms.

---

## License

Documentation in this repository is provided under the MIT License. See [LICENSE](./LICENSE).

*Educational material only. Not a substitute for vendor due diligence or regulatory advice. MoboGage and EVD System refer to offerings on evdsystem.com.*
