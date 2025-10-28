## First look
- Predict the weekly uplifts in demand from promotions
- Merchandising team is in charge of setting promotions - they tell forecast team how much, when, how long, and what's the expected uplift from the promotion. Then forecasting team would use that information and do demand forecast which feed into BoD
	- _So we are producing an intermediate outputs that help the forecasting team? Do they use similar inputs as us?_ - Yes
- our output will be evaluated on sales that come out of **demcalc**, which is a model that answers the following question: what's the 'would-have-been' sales if we had unlimited stock in all stores? which would be higher than the real sales (as the latter is constrained by stock)
- inputs:
	- weekly sales
	- weekly demand forecast excluding promotion activities
- output:
	- uplift in demand in units/percentage from promotions per SKU per week

- Viability:
	- low baseline
	- good support from stakeholders, internal users only who's keen on the product, can get initial feedback from a poc

- POC till end of December

## Questions
- Currently if uplift predictions are not intuitive (e.g. super high/low or negative, are there any manual adjustment to it?) This is important because if stakeholders override the model frequently, our actual business impact shrinks regardless of model accuracy. Also uncovers systematic bias.
- What additional data does demcalc have that we don't? Actual sales, store stock, any other information? - good for understanding accuracy ceiling
- How in advance are we aiming our prediction to be - at the beginning of the week, or more than that?
- Do we only care about uplift caused by the promotions immediately? What about the decrease at later weeks?
- Predict pct uplift vs qty uplift? demand on how promotion effect scales with baseline demand. We would know from data right?
- ---
- When does our model run - start of the week? Do we only predict given promotion tag on certain SKUs from the merchandise team?
## Material and notes
- [Intro to demand forecast](https://jsainsbury.sharepoint.com/teams/commercial_academy/_layouts/15/stream.aspx?id=%2Fteams%2Fcommercial%5Facademy%2FShared%20Documents%2F4%2E%20Process%2C%20Systems%20and%20Tools%2FProcess%2FForecasting%2FIntro%20to%20Demand%20Forecasting%2D20230106%5F031944%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2Ec419e571%2D3624%2D4695%2Da2a0%2D9430225b17d3&isSPOFile=1&xsdata=MDV8MDJ8fDQzYzVhYzk5NTkwMzRjZWRmZWJkMDhkZTBjOGZjNDQ5fGUxMWZkNjM0MjZiNTQ3ZjQ4YjhjOTA4ZTQ2NmU5YmRmfDB8MHw2Mzg5NjIwMDg3NDYyMzM2OTJ8VW5rbm93bnxWR1ZoYlhOVFpXTjFjbWwwZVZObGNuWnBZMlY4ZXlKRFFTSTZJbFJsWVcxelgwRlVVRk5sY25acFkyVmZVMUJQVEU5R0lpd2lWaUk2SWpBdU1DNHdNREF3SWl3aVVDSTZJbGRwYmpNeUlpd2lRVTRpT2lKUGRHaGxjaUlzSWxkVUlqb3hNWDA9fDF8TDJOb1lYUnpMekU1T20xbFpYUnBibWRmVGxkTk5FNXFTbXRhYlUxMFQwZE5OVnBETURCWmFrRXhURlJzYlU1VVozUk9WMFY1VFVkUk0wNVVSbXRPVkUxNFFIUm9jbVZoWkM1Mk1pOXRaWE56WVdkbGN5OHhOell3TmpBME1EYzBNekV6fDIyMTYwODc5OWY5ODQ3NDI2MWU5MDhkZTBjOGZjNDQ5fDgwMTk2YTIyYTFjMTQwYjdhNjEzYWFhODk4NjhkNTE2&sdata=ZmNHanV1UGFlVkptVi8wQkIwUkFIRzFxRkhPOVNhK3FUN0lWRXhERXZBVT0%3D&ovuser=e11fd634%2D26b5%2D47f4%2D8b8c%2D908e466e9bdf%2Cchris%2Esheehan%40sainsburys%2Eco%2Euk&web=1&OR=Teams%2DHL&CT=1761041841242&clickparams=eyJBcHBOYW1lIjoiVGVhbXMtRGVza3RvcCIsIkFwcFZlcnNpb24iOiI1MC8yNTA5MTExNjAxOCJ9)
	- Demand = Actual Sales + Missed Sales
		- Missed Sales are what we could have sold if there were unlimited stock in all locations.
		- We forecast demand instead of sales to separate out concerns of stock - which is something BoD would look to optimise
	- How is demand used:
		- Look back: how much demand is realised into sales - measure for stock effectiveness.
		- Future plan: crucial for planning small item replen and large item intake. Availability for small item availability KPIs.
- Merchandise team manage demand forecast.
- Forecasting systems
	- Small items:
		- Past customer sales (online+instore) -> feed into demcalc and output past demand -> **demand planner (store-week level)** -> FDT splits outputs into store-day level -> BoD plans stock in stores -> AIP store plan system
		- **we are trying to improve demand planner - flyered forecast, which is the demand forecast with promotion activities**
	- Large item:
		- Past customer sales (online+instore) -> feed into demcalc and output past demand -> demand planner (store-week level) -> JDA planning system -> forecast used for intake prioritisation

- What is demcalc
	- for small items only
	- inputs: original sku/store forecast, actual sales (online/instore), store stock levels
	- outputs: actual demand (a.k.a. adjusted demand)
- Current **Demand Planner (DP)**
	- Inputs - deflyered forecast, sales uplift, product profile (aggregated by similar SKUs)
	- output: forecast at SKU/warehouse/week level
	- Runs weekly on a Sunday

- **Forecast disaggregation tool (FDT)** - break down DP outputs from store-sku-week level to store-sku-day level
- ForAgg - helps implementing BoD decisions
- AIP store plan - load foragg and bod decisions to store



