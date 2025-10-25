- [ ] Have joined current forecast with item table, but now blocked - need to ask 1. where the demcalc forecast data is to calculate current error, and 2. (optionally) have the week-level aggregated promo dataset from Stefano
---
**Goal:** 
- Want to look for headlines like 70% of promo sales come from furniture, 30% of inaccuracies came from mobile phones, 40% of SKUs whose uplift are underestimated come from lego
- i.e. category, time of year and type of promo that has the highest room for improvement

**How:**
- Compare current model forecast with demcalc demand estimates. Then join with Stefano's base data
	- base and total forecast in either 'input_data/Historic-Forecast-Extract20250827-edit.csv', which has the latest forecast for each week, or 'input_data/Forecast-Lead-Time-Extract-20251001.csv', which has forecasts up to 8 weeks before (bit more useful but bigger)

**Misc notes**
- Argos SKUs in dim item table might have leading '10000' in SKU code. Use column `op_co_item_cd` for matching instead

