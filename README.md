# Austin-Crime-Clearance-Rates
In this project, Leticia Rinaldini, Pender Fitz Gerald, and I decided to take a look at Austin's 2016 crime report, and try to find possible trends in crimes. The data was provided for us via Google Drive. It is made of all the crimes recorded by the Austin PD in 2016. The columns in the dataframe are:<br />
**GO Primary Key**: Made out of the year and incident number<br />
**Council District**: The district in which the crime was committed (map of districts)<br />
**GO Highest Offense Desc**: A text description of the offense using the APD description<br />
**Highest NIBRS/UCR Offense Description**: A text description using the FBI description <br />
**GO Report Date**: The date on which the crime was reported <br />
**GO Location**: Street adress where the crime happened<br />
**Clearance Status**: Whether or not the crime was "cleared" (i.e. the case was closed due to an arrest)<br />
**Clearance Date**: When the crime was cleared<br />
**GO District**: The District code (letter) where the crime was commited<br />
**GO Location Zip**: The zip code where the crime occurred<br />
**GO Census Tract**: The census tract where the crime happened (a subdivision of a county)<br />
**GO X Coordinate**: Geographical X Coordinate<br />
**GO Y Coordinate**: Geographical Y Coordinate<br />
<br />
We started by importing the data using pandas and looking up the NaN values. Out of 37,461 rows we found 6522 NaN values and decided to remove them. We then made 2 functions to clean our columns data types that changed all columns with decimal values into float64, integers into int64, and strings into object. The other function renamed the columns into more meaningful names by removing 'GO' from the begging of almost every column, replaced spaces with underscores, removed extra whitespaces, renamed 'Highest NIBRS/UCR Offense Description' into 'fbi_desc' and 'GO Highest Offense Desc' into 'apd_desc. The function also made all column names lowercase.
<br/>
We focused on factors such as location, time of the year and the type of crime to see if there is a correlation with the clearance rates or between the factors itself.
FBI description was made out of 7 different types of crime while the APD description had 54.The APD codes are more in detail and greater in number, so it will be easier to work with the FBI codes instead.here is what we found:<br/>
<br/>
-**Theft ended up as the most occuring crime with burgulary being a very distant second.<br/>
-The crime that occurs the least amount is Murder, with only 30 reported instances (0.09% of total crime) in our data.
<br/>
-Over 80% of crimes in Austin are not cleared.**<br/>
<br/>
  We decided to look more into why so many crimes were not cleared in 2016. After grouping the crimes by fbi descriptions, total counts, and clearance status we found that **Theft, Burglary, and Auto Theft are often not cleared, whereas Robbery and Agg Assault are cleared more often. Despite being the crime that occurs the least amount, Murder is cleared over 90% of the time**. Meaning of the 30 instances of Murder, 28 were cleared. Petty Theft, Burglary of a Vehicle, and Shoplifting are the crimes that occur the most in Austin according to the APD descriptions. These are crimes that are hard to clear because the victim usually doesn't know that the crime has occurred until it is too late. Thus, the police response is delayed making the case harder to solve.
  Another factor that could possibly play a big role in clearance rates was the time of the year crime has occured. Firstly, we needed to edit the date column by striping "-" from the date and making three seperate columns for day, month, and year. We then grouped the months, clearance status and crime types to find the total counts of crime in each month as well as their clearance rates. We found that the **top 5 months with the most crime were November, August, January, May, and December**. All of these are either summer or winter months, so the general assumption that that is when crime occurs the most would be correct for this dataset. **April was the month with the highest clearance rate of 17.72%**. The reason behind it, is the fact that the most occuring crime in April was Theft which we had noted earlier that is the type of crime getting cleared the most.
  Lastly, we searched for a connection between crime clearance and location. There were 46 different zip codes in the dataset. After grouping the data by zip codes and counts of crimes we found top 10 and bottom 10 zip codes for the total number of crimes occured in the zip code area.**The 5 ZIP Codes with most crime were: 78741, 78753, 78704, 78758, 78745. The 5 ZIP codes with least amount of crime were: 78732, 78737, 78728, 78712, 78652**. In order to make our plots, we created new columns in our dataframe that indicate whether or not the value in the location_zip column is in the top or bottom 10. Then, we used boolean indexing to sort out instances that occurred in the zip codes we're looking for, and plotted those. In alignment with our previous findings, most crimes in the top 10 zip codes have not been cleared. **The highest clearing zip code was 78753, which clears about 20% of crimes that occur**. ZIP codes with less crimes were located outside the city while the top 10 ZIP codes that had the most crime are located in the city center. The locations with less amounts of crime appear to struggle even more than locations with high amounts of crime in regards to clearing their cases.  <br/>
  After analyzing our data, we've made several observations and would like to recommend some changes that the Austin Police Department could make in order to better their clearance rates.

Theft occurs a staggering amount of times compared to other crimes. Coupled with the fact that it has a very low clearance rate makes it a real issue. Although most of these occurrences are petty crimes that the police could not take much action on, there are a few preventative measures that could be put in place. Preventative measures like increasing gate security at parking lots, encouraging residents to get security systems, and adding signage to high-theft areas are all things that could help lower the amount of occurrences, and increase clearance.

The Austin Police Department appears to be very efficient at solving murder cases, so no need to recommend any changes in that department.

Increased patrolling around the winter and summer months could help relieve some of the crime that occurs. This idea also applies to the zip codes with high amounts of crime. Having authorities in the area helps increase response time to crime scenes, which gives the crime a better chance of being cleared.
