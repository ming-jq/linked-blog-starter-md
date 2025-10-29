- Inputs and outputs
	- Input: 
		1. Set of promo-SKU-timeline
		2. All SKU-week combinations after filtered by given promos
	- Output: 
		- demand uplift in quantity or percentage for each given SKU-week, then joined onto promo data 
- prediction granularity - date vs week
	- Ideally week, but certain items have more than one type of promo/price within a week. 
	- A simplification would be take the average price point, and then have promo type as one hot encoded in the input data so a single SKU-week can have multiple?

## Potential Data Sources
- 
## Resources
- [Analysis piece on Argos - slides](https://jsainsbury-my.sharepoint.com/:p:/g/personal/chris_sheehan_sainsburys_co_uk/EWrRLSMqMB1KtpF56Aj6eK4BRvNROo_JK2hfcUTeYL4cqQ?wdOrigin=TEAMS-MAGLEV.p2p_ns.rwc&wdExp=TEAMS-TREATMENT&wdhostclicktime=1761433026986&web=1)
- [CDP data](https://sainsburys-tech.atlassian.net/wiki/spaces/CDPT/pages/449675344/1.+CDP+-+Argos+Customer+Data+Set)
	- [Joining CDP data with snowflake: entity_id - profile_id](https://sainsburys-tech.atlassian.net/wiki/spaces/CDPT/pages/688032787/Customer+Segmentation+for+One+ENTITY_ID+with+Many+PROFILE_ID+s)
	- 
