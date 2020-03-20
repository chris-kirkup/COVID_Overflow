# COVID_Overflow

The purpose of this map is to illustrate the projected overflow rate (number of patients needing hospitalization versus number of available beds) 30 days from now for each hospital in the US. To calculate this overflow rate I used this model (https://github.com/pennsignals/chime) created by PennMed to project number of daily COIVD19 admissions and the daily COVID19 patient census for a hospital given: number of COVID19 patients currently in the hospital, number of infected individuals in region, and total population in region. The most difficult part of this calculation is determining the current number of COVID19 patients in a given hospital, for the purposes of this illustration I calculated this based on the total number of COVID19 infections in the county times hospitalization rate times the market share of each individual hospital (market share = number of beds in hosptial / number of beds in county). This is of course making the assumption that COVID19 patients are evenly distributed throughout the hospitals in a county, this is likely a faulty assumption - ideally in future we can come up with a better data source/method for extrapolating Hospital-level patient counts (e.g. scraping from new articles) to improve the vailidity of this model.

Issues - 
* Mapping between hospitals in datasets is sparse at this point (note lack of hospitals in California) - this should be able to be improved in the future, but I haven't had much time to improve the quality of this mapping just yet
* Getting a better estimation of hospital-level patient counts should vastly improve the accuracy and utility of this model however this comes with it's own issues including - 
    * Non-traditional treatment landscape - new and non-standard facilties are being added to the ranks of those preparing to take in patients by the day, for example Carney Hospital in Dorchester is being devoted entirely to COIVD19 treatment, USNS Comfort hosptial ship being depolyed to NYC, etc.
    * Non-standard language in articles refering to patient counts increases complexity of extratcing patient counts form text  - for example "Massachusetts General Hospital officials said the number of patients suspected to have COVID-19 in their emergency room or in beds had quadrupled to 53 between Monday and Tuesday, in addition to three other confirmed cases in intensive care and three in regular beds."
* County level counts are not being reported by some states - including Vermont, West Virgina, Rhode Island
* Right now the Overflow Risk is not factoring in the number of beds being taken up by non-COVID19 patients - I'll have to do some more research into the proportion of open beds versus total beds in a hospital at any given time to compensate for this in future

![Image of Map](https://github.com/chris-kirkup/COVID_Overflow/blob/master/Screen%20Shot%202020-03-20%20at%201.55.27%20PM.png)

Map : https://drive.google.com/open?id=1Z1LNNhKqQNftvuzhYAvAM8pH_JFKnpjA&usp=sharing


Sources - 

County-Level Case Counts:
https://www.livescience.com/coronavirus-updates-united-states.html

State-Level Case Counts:
https://github.com/CSSEGISandData/COVID-19

County Populations:
https://www.census.gov/data/datasets/time-series/demo/popest/2010s-counties-total.html

Hospitals:
https://hifld-geoplatform.opendata.arcgis.com/datasets/hospitals

ICU-Bed Counts Per Hospital:
https://www.cms.gov/Research-Statistics-Data-and-Systems/Downloadable-Public-Use-Files/Cost-Reports/Hospital-2010-form

CHIME Model:
https://github.com/pennsignals/chime


Hospital-Level patient counts are calculated based on number of patients in county times hospitalization rate times the market share of the hospital within the county (beds in hospital/beds in county)

CHIME Parameters:

    doubling_time = 6

    relative_contact_rate = 0 #percentage reduction in contact rate due to social distancing measures

    hosp_rate = 0.05 #percentage of COIVD19 patients needing hospitalization

    icu_use_rate = 0.02 #percentage of patients needing ICU bed

    vent_use_rate = 0.01 #percentage of patients needing ventilator

    hosp_los = 7 #average length of stay for hospitalized patient

    icu_los = 9 #average length of stay for ICU patient

    vent_los = 10 #average length of stay for ventilator patient

    market_share = 0.2 #beds in hospital / beds in county

    recovery_days = 14.0
