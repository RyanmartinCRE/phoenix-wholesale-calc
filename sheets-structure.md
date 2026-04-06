# Phoenix Wholesale Offer Calculator - Google Sheets Structure

## Sheet 1: DEAL CALCULATOR (Main Tab)

### INPUT SECTION (Yellow Highlighted Cells)
| Cell | Label | Default/Example |
|------|-------|-----------------|
| B3 | Property Address | "123 Main St, Phoenix, AZ" |
| B4 | Square Footage | 1,500 |
| B5 | After Repair Value (ARV) | $400,000 |
| B6 | Rehab Level | Dropdown: Light/Medium/Heavy |
| B7 | ARV Discount % | 70% |
| B8 | Assignment Fee Target | $10,000 |
| B9 | Contingency % | 15% |

### OUTPUT SECTION (Auto-Calculated)
| Cell | Label | Formula |
|------|-------|---------|
| B12 | Estimated Rehab Cost | =IF(B6="Light",B4*32.5,IF(B6="Medium",B4*62.5,B4*112.5)) |
| B13 | Rehab + Contingency | =B12*(1+B9) |
| B14 | MAO (Maximum Allowable Offer) | =(B5*B7)-B13-B8 |
| B15 | Suggested Initial Offer | =B14*0.85 |
| B16 | Suggested Max Offer | =B14*0.95 |
| B17 | Total Assignment Profit | =B8 |
| B18 | Buyer All-In Cost | =B14+B8+B13 |
| B19 | Buyer Potential Profit | =B5-B18 |

### DEAL GRADE
| Cell | Grade | Logic |
|------|-------|-------|
| B22 | Deal Grade | =IF(B14/B5>=0.5,"A",IF(B14/B5>=0.4,"B",IF(B14/B5>=0.3,"C","D"))) |

### GRADE LEGEND
- A = Excellent (50%+ margin) - Make offer immediately
- B = Good (40-50% margin) - Strong deal
- C = Fair (30-40% margin) - Negotiate hard
- D = Poor (<30% margin) - Pass or lowball

---

## Sheet 2: REHAB REFERENCE

### Per Square Foot Costs (Phoenix 2026)
| Level | Low | High | Avg | Scope |
|-------|-----|------|-----|-------|
| Light | $25 | $40 | $32.50 | Paint, flooring, fixtures, landscaping |
| Medium | $50 | $75 | $62.50 | + Kitchen, baths, windows, minor systems |
| Heavy | $90 | $135 | $112.50 | Full gut, studs, all systems, structural |

### Line Item Estimates
| Item | Low | High |
|------|-----|------|
| New Roof | $8,000 | $15,000 |
| HVAC Replacement | $7,500 | $12,000 |
| Kitchen Remodel | $15,000 | $30,000 |
| Full Bath Remodel | $6,000 | $12,000 |
| Flooring (LVP) | $4.50/sqft | $7/sqft |
| Interior Paint | $2.50/sqft | $4/sqft |
| Electrical Panel | $2,000 | $4,000 |
| Water Heater | $1,200 | $2,500 |

---

## Sheet 3: PHOENIX COMPS SOURCES

### Free Resources
| Source | URL | Use For |
|--------|-----|---------|
| Redfin Phoenix | redfin.com/city/14240/AZ/Phoenix | Sold comps, price trends |
| Zillow Phoenix | zillow.com/phoenix-az | Zestimates, sold data |
| Maricopa Assessor | mcassessor.maricopa.gov | Public records, tax info |
| AZ MLS (via agent) | arizona.realtor | Accurate sold data |

### Paid Resources
| Source | Cost | Best For |
|--------|------|----------|
| PropStream | $99/mo | Investor comps, skip tracing |
| BatchLeads | $59/mo | List stacking, motivated sellers |
| REsimpli | $99/mo | All-in-one investor CRM |

---

## Sheet 4: MAO FORMULA GUIDE

### Standard Wholesale Formula
```
MAO = (ARV × Discount %) - Repair Costs - Assignment Fee
```

### Example Deal Walkthrough
**Property:** 3BR/2BA, 1,400 sqft, Phoenix
- ARV: $350,000
- Rehab Level: Medium
- Assignment Fee: $8,000

**Calculation:**
1. ARV × 70% = $245,000
2. Repair Cost (1,400 × $62.50) = $87,500
3. Repairs + 15% Contingency = $100,625
4. MAO = $245,000 - $100,625 - $8,000 = **$136,375**
5. Suggested Offer (85% of MAO) = **$115,919**

---

## Sheet 5: BUYER NETWORK

### Wholesale Buyer Tracking
| Name | Phone | Email | Buy Box | Notes |
|------|-------|-------|---------|-------|
| Sample Buyer | (555) 123-4567 | buyer@email.com | $100K-$200K, C class | Cash buyer, closes fast |

### Phoenix Investor Groups
- AZREIA (Arizona Real Estate Investors Association)
- Phoenix Real Estate Investors Meetup
- Tucson Real Estate Investors Facebook Group
