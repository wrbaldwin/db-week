## Data Design for Microservices

[Customer Spreadsheet](https://github.com/wrbaldwin/db-week/blob/master/docs/D04S07_Lab-Building-Scalable-Microservices.xlsx)

### Lab Prep
* Divide into groupsof 6-8 people
* Each group is a consulting company
* You have been hired to advise on Microservices

### About the Customer 
* Customer is a successful bricks-and-mortar retailer
* Old e-commerce system based on Oracle
* They want replace it with something modern
* They want something “Amazon-like”

### About the Spreadsheet
* Channel Affiliate
   * 3rd party company
   * Selling through the client’s e-commerce site
* Promotion
   * Various sales
   * Buy-one-get-one
   * Other commercial promotions
   * Each needs a start and stop time.
### Deliverables (at the next customer meeting ...)
* What will you ask the client?
* What will you present, if anything?

### Customer Provided ER diagram

Channels/affilates

CC_SITE_BASE	Base information for the site	
	SITE_NO	Identifier for Site
	SITE_NM	Name for Site
	ENTR_NO	Identifier for the affilates
	ENTRE_CONTR_NO	Contractor for the affilates
	BZ_TP_CD	Businss type code
	SHOP_COMP_GRP_CD	Shop composition group code
	SALE_SCT_CD	Sales category code
	TRADE_STRT_DTIME	Transaction start date time
	TRADE_END_DTIME	Transaction end date time
	BIZ_AEMP_ID	Sales person ID
	CARD_DSCNT_APLY_YN	To apply credit card discounts
	SKSC_USE_YN	To apply skyscrapper
	THM_URL_ADDR	Url for theme
	ID_PSWD_GD_URL_ADDR	Url for id/password guideline
	UTIL_GD_URL_ADDR	Url for usage info
	ADVT_BNR_URL_ADDR	Url for banner
	SYS_REG_DTIME	System registeration date time
	SYS_REGR_ID	Registered by
	SYS_MOD_DTIME	System modification date time
	SYS_MODR_ID	Modified by
	MNPR_APLY_YN	
	PRC_DSCNT_CD	
	MAST_SITE_NO	Master site number
	TMPL_TP_CD	Tmplate type code
