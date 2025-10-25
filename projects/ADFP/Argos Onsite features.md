- When applying aggregation, need to do a distinct by tealium id/customer -> avoid being inflated by the same customer seeing the same promo
    - In a session you may have one-to-many customer to item mapping ->
- [ ] Click reason is also available - could be from carousel/google/etc. -> **find out which column this is - possibly `page_type`**
	- e.g.  page_type=pdp_google. (pdp means product display page)
- also have information when add to cart whether a promo is applied  
- `tealium_event` and `event` columns are good columns to check 
- `page_path` - full information including sku
- one timestamp column is faster to filter - need to see which


To understand and make use of table [FLF_ARGOS_WEB_ONLINE_EVENT](https://sainsburys.eu.alationcloud.com/app/table/138597), I need to: 
- [ ] Have an initial feature wishlist
- [ ] Look at key columns `event_action`, `page_type` to understand what options there are and what concerns us from like 1-day sample
- [ ] Write query to extract some or all of those features
- [ ] Brainstorm with team what features could be useful.

