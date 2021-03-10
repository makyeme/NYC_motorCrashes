# NYC Motor Vehicle Collisions: Accident-prone Streets


## Table of contents
- [GeneralInformation](#generalinformation)
- [Technologies](#technologies)
- [Setup](#setup)
- [Conclusion](#conclusion)



## 1. General Information

NYC is home to more than 8 million people and sees roughly 50 million tourists every year. Being one of the world’s major commercial hubs, there is a lot of traffic on both the roads and subways, the two most popular means of commuting, for most parts of the day. As a result of continuously intensifying interactions as population increases , more frequent accidents on the roads are expected. NYC Open Data provides easy access to a lot of data pertaining to motor vehicle accidents on the streets of New York. 

The aim of this project is to generate  a cleaned out and comprehensive dataset from the source dataset. This dataset will be used to develop a machine learning alogarithm, capable of predicting the most accident-prone streets of New York. The resulting information will provide deeper insights and enable the mayor of New York, Bill de Blasio to make better inferences regarding the most dangerous streets within the city.

Some of the questions I tried to explore through the data are outlined below:

- What is the target/dependant variable(s) to assess level of accident proneness?
- What to do with missing values?
- What predictor/independent variables to keep for future model development?
- what depth of data cleaning should be applied?



## 2. Technology

This project was created with:

- Anaconda virtual environment version: 4.9.2
- anaconda-navigator version: 1.10.0
- Python version: 3.8.5
- Jupyter notebook version: 6.2.0
- Numpy library version: 1.19.2
- Matplotlib library version: 3.3.4
- Pandas library version: 1.2.1
- Seaborn library version 0.11.0 



## Setup

The entire data cleaning processes and generation of a CSV file was excuted through 5 functions as detailed below:
NYC_crashes.ipynb file contains all the codes for the above stated fucntions, 
It is available at [Github/makyeme](https://github.com/makyeme/NYC_motorCrashes/blob/main/NYC_crashes.ipynb)

### i. getData() Function

This function when called is able to 
- pull the dataFrame 
- strip whitespace from cells that have a string-like object in them

Libraries used: pandas

 
 ### ii. exploreData() Function 
 
when called, returns exploratory information on the dataFrame, information such as:
- number of observations
- variable names of dataFrame
- sum of missing values per variable
- data types of variables

Libraries used: pandas
 
 ### iii. getMissing() Function
 
when called, returns a dataframe with missing data percentage per variable and plots it
The NYC moto collison dataset obtained contains a significant amount of missing values. Missing values per variable/column are shown below.


![Optional Text](https://github.com/makyeme/NYC_motorCrashes/blob/main/Missing_data.PNG)

NYC_crashes.ipynb includes all the code that finds the percentage of missing data and plots the graph above.

Libraries used: Matplotlib, Seaborn, Pandas

### iv. cleanData() Function

when called, returns a fairly cleaned out dataFrame for further data analysis.

While looking at the dataset, I wanted to see how messy and complete it was. In order to obtain meaningful statistics about variables and   assess their relevance  in predicting the most accident-prone streets in New York, it is necessary to get a sense of the distribution of missingness. This is also used in determining the useful variables. 

While there are several imputation techniques, if a variable has about 80-90% of missing data, it is probably not meaningful to impute the missing data since it is likely that I obtain false values. From the graph generated by the getMissing() function, I understood that the following variables were pretty much useless in the future analysis: “Vehicle Type Code 5”, “Contributing Factor Vehicle 5”, “Vehicle Type Code 4”, “Contributing Factor Vehicle 4”, “Vehicle Type Code 3”, “Contributing Factor Vehicle 3” and “Off Street Name”. 

I specifically set a threshold of 40 % missingness, all variables above the threshold were thrown out of the cleaned dataset.
The 40 % was motivated by the fact that I wanted to retain the variables: borough and zip_code. The two stated factors had a missingness of about 35 %. The two are very crucial in providing additional/deeper insights on the locality of motor accidents within New York city.
Furthermore, several other variables rendered redundant in predicting accident hotspots were thrown out. All retained varriables can be accessed via the csv file. For my minimum viable product(csv file), I chose to drop all rows with at least one missing value. The final csv file is void of missing values.

Libraries used: Pandas

### v. createCsv() Function 

when called Saves cleaned out dataframe to csv formart

libraries used: pandas



## 3. Conclusion

The project was an in-depth exercise to explore and clean data in the NYC motor vehicle collision dataset, in anticipation for developing a prediction model for accident-prone streets in New York city. Through the course of the project, I deepened my expertise in several data: exploration, cleaning, engineering and visualization techniques

### Limitations:

The output csv file captures a limited number of observations largely owing to missing values. This might impose gross negative impacts on the predictive abilities of the developed model. Furthermore, the dataset has several variables that could be explored in greater depth such as factors contributing to accidents, time of accident, vehicle types involved and a deeper analysis of socio-geographic elements.

### Future directions:

The next step in the data cleaning process is to try to retrieve missing data through several avenues, this will be crucial in limiting the amount of excluded data. Furthermore, It would  be optimal to include more variables in the dataFrame as long as they contain valuable information towards model development.
