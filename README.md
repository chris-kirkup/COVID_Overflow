# COVID_Overflow


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


Hospital-Level patient counts are calculated based on number of patients in county times the market share of the hospital within the county (beds in hospital/beds in county)

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
