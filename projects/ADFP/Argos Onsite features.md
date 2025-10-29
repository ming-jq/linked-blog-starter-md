- **Tips**
	- When applying aggregation, need to do a distinct by tealium id/customer -> avoid being inflated by the same customer seeing the same promo
		- In a session you may have one-to-many customer to item mapping
	- [x] Click reason is also available - could be from carousel/google/etc. -> **find out which column this is - possibly `page_type`**  - yes it is page_type. ✅ 2025-10-25
		- e.g.  page_type=pdp_google. (pdp means product display page)
	- also have information when add to cart whether a promo is applied  
	- `tealium_event` and `event` columns are good columns to check 
	- `page_path` - full information including sku
	- one timestamp column is faster to filter - need to see which
	**Additional Qns to ask Calum:**
	- Where does Argos App interactions data live in?
	
To understand and make use of table [FLF_ARGOS_WEB_ONLINE_EVENT](https://sainsburys.eu.alationcloud.com/app/table/138597), I need to: 
- [x] Have an initial feature wishlist - [[Feature Wishlist]] ✅ 2025-10-27
- [/] Look at key columns `event_action`, `page_type` to understand what options there are and what concerns us from a 1-day sample
	- `event_action=slp_displayLocalisationPrompt and page_path like '/list/save-%'` - event page
	- `event-action=prepayConfirmation_initialLoad` - order confirmed
- [ ] Write query to extract some or all of those features
	- [/] Naive query to record weekly view count for promoted items - `analysis/analytics/sql/promo_item_weekly_view_counts.sql`, need to do SKU-date match when joining onto interactions tables
	- [x] Brainstorm with team what features could be useful. ✅ 2025-10-27 [[Feature list plan]]
---

- [x] I should understand where promotions appear in user journeys more - study Argos website and brainstorm where I may see a promotion. Find a user journey example for each. ✅ 2025-10-27
	- User journey: https://miro.com/app/board/uXjVJ2sXFOA=/?moveToWidget=3458764645722190351&cot=14

- need to see how to match promo code with event page
- number of sessions that goes through event page rather than search as an indicator of importance being put on home page
