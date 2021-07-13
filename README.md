# Surfs_Up

#### *Analyzing weather data on Python from an SQLite Database using SQLAlchemy and a Flask App*

## Overview
This project consisted on analyzing weather data from Oahu, Hawaii to support a Surf and Ice-cream shop investment proposal. The analysis consisted on determining whether the seasons could affect the surf and ice-cream business. The final product was a full report and a flask application that read the data from a SQLite Database for other users to access it. 

## Resources
- Data resources: 
  - hawaii.sqlite

- Software used: 
  - Python
  - SQLAlchemy
  - SQLite
  - Flask

## Results
Statistical results of the precipitation and temperature of the two most active and important months across the years as follows:

![Final_stats](https://user-images.githubusercontent.com/83378141/125126996-eb8f0880-e0c9-11eb-9e05-897e35e1ff2a.png)

- As it can be seen, the average temperature for both June and December are considered good weather suitable for ice-cream (71°F and 74.0°F).
- None of the two seasons of the year show to have considerably high average precipitation. The precipitation distribution for both June and December happens to be skewed to the right meaning that it is not normally raining. 1st Quartile and median have 0mm, and the 3rd Quartile has 0.1mm which is minimum precipitation. 
- It must be taken into consideration that the month of december happens to have a max precipitation of 6.4mm which is considered heavy rain. On the other hand, the max precipitation for June happens to be 4.4mm which is considered medium-high. Overall, the distribution shows that precipitation might not be enough reason to close our shop out-of-business due to weather conditions. 
- Taking all this into account, June happens to be the most profitable time of the year as the distribution of the weather is more suitable for surfing and ice-cream sales. 

## Summary

The results were found by querying the SQLite database from the Jupyter notebook to then use the `describe()` function to get the statistical analysis. 

The extra precipitation results were created by querying from our SQLite database as follows: 
```
# For June
prcp_june = []
prcp_june = session.query(Measurement.prcp).filter(extract('month', Measurement.date) == 6).all()
Precip_june = pd.DataFrame(prcp_june, columns=['June Precipitation'])
stats_prcp_june = Precip_june.describe()
stats_prcp_june

# For December 
prcp_dec = []
prcp_dec = session.query(Measurement.prcp).filter(extract('month', Measurement.date) == 12).all()
Precip_dec = pd.DataFrame(prcp_dec, columns=['December Precipitation'])
stats_prcp_dec = Precip_dec.describe()
stats_prcp_dec
```

For more detail on the Python script and libraries used refer to the [Surf's Up Jupyter Notebook](https://github.com/nicoserrano/Surfs_Up/blob/main/SurfsUp_Challenge.ipynb)
