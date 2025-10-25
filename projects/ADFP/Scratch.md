- Inputs and outputs
	- Input: 
		1. Set of promo-SKU-timeline
		2. All SKU-week combinations after filtered by given promos
	- Output: 
		- demand uplift in quantity or percentage for each given SKU-week, then joined onto promo data 
- prediction granularity - date vs week
	- Ideally week, but certain items have more than one type of promo/price within a week. 
	- A simplification would be take the average price point, and then have promo type as one hot encoded in the input data so a single SKU-week can have multiple?