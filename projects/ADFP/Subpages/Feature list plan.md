### Core
- promo_type, depth, was_price_displayed
- planned_placement, is_linked_from_homepage, average_traffic_by_promo_type: for example, average page load for save £x promotion
- promo frequency: Number of times/weeks SKU has been on promo in past 12 months 
### Important
- Non-promo periods: 
	- SKU-level historical CTR, page views and conversion. Percentage page views and conversion within category
	- Percentage PDP load from google - indicates predictive power of competitor price
- From past 'similar' promotions (*need a definition of promo similarity, e.g. by price reduction & valid period*):
	- Promo CTR, page views and conversion from past similar promotions
	- % demand uplift from past similar promotions
### Good to have
- Customer exploration depth: Avg number of same-category PDP loads per session before purchasing this SKU
- Session intent: % of historical sessions for this SKU that were "direct intent" (landed on PDP directly/<5 pages viewed/short tealium session length + purchased)
- For each SKU, correlation between page view delta and sale delta, i.e. how sensitive is this SKU to visibility changes
- Customer segment:
	- Nectar customer proportion visiting category page 
	- Nectar customer proportion for a certain SKU's sales
### Future build (high efforts needed, medium to low impact)
- Substitute items effect: Entropy of sales distribution within the same subcat
- Complementary items effect - need to 1. identify complementary products, and 2. analyse historical campaigns effects on those
- External marketing type: TV/social/paid search campaigns running alongside promo - requires external data



likely category specific

|Feature|Source|Engineering Effort|Why Include|Caveat|
|---|---|---|---|---|
|**Historical CTR for this SKU on category page** (past 12 weeks avg)|Adobe Analytics|Medium|Proxy for "attractiveness" - popular items get more clicks even without promo|Assumes category page structure is stable|
|**Historical page views for this SKU** (past 12 weeks avg)|Adobe Analytics|Medium|Proxy for baseline interest|Need to exclude promo weeks|
|**SKU's typical cart-add rate** (past 12 weeks, non-promo)|Adobe Analytics|Medium|Conversion propensity|Filter to non-promo periods|
|**Category page position/rank** (current state)|Adobe Analytics or promo tags|Medium|Higher position = more visibility|If not in promo tags, use current ranking as proxy|
|**Historical promo performance for this SKU** (avg uplift from past promos)|Your base demand + promo history|Medium|Best predictor if SKU has promo history|Cold-start problem for new SKUs|

**Goal:** Add behavioral proxies that predict which SKUs will benefit most from visibility.

---

### **Tier 3: Advanced/Experimental (Weeks 4-6, if time permits)**

_Higher complexity, uncertain ROI_

|Feature|Source|Engineering Effort|Why Deprioritize|
|---|---|---|---|
|**Nectar customer segment visiting category page** (% high-value customers)|Adobe Analytics + Nectar data|High|Requires joining user-level data, complex aggregation. May not generalize if segment mix changes|
|**Complement product basket co-occurrence** (what % of customers who buy X also buy Y)|Transaction data|High|Interesting for cross-sell, but not clear how to use pre-promo (you don't know who will visit during promo)|
|**External competitive pricing** (is our promo price lowest vs competitors)|External data|Very High|No existing pipeline - would need web scraping or paid data. Park for future|
|**Forecasted page views during promo week** (separate ML problem)|Adobe Analytics|Very High|Chicken-and-egg: promos drive traffic, traffic drives sales. Too circular for POC|

**Decision:** Only pursue if Tier 1-2 model shows promise and you have time.

---

### **Features to EXCLUDE (Red sticky note warnings)**

| Feature                                                | Why Exclude                                                     |
| ------------------------------------------------------ | --------------------------------------------------------------- |
| **Sessions that "see" the promo**                      | Only knowable during/after promo runs - not available pre-promo |
| **Actual CTR during promo**                            | Only knowable after promo runs                                  |
| **Items in cart/basket during promo**                  | Only knowable after promo runs                                  |
| **Page view variation during promo**                   | Only knowable after promo runs                                  |
| **"Frequently bought together" sections during promo** | Dynamic content - changes based on real-time behavior           |