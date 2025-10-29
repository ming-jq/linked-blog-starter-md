We're solving a problem of prediction demand uplift from promotions, on estate-week-SKU level

here are the data we have: 

- promo tags: SKU-day-promotag
- demand data: SKU-day
- sales data: SKU-day
- current forecast for flyered and deflyered demand: SKU-week level
- competitor price: SKU-competitor-day level

We face and issue of aggregating the data onto week level. In promo tag dataset, some items change price/promotion within a week. same with competitor price, for a single day the price may dip, of course it would take away lots of demand. 