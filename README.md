# A binary classification model to predict commercial flight cancellations.
---
### Goals
Create a binary classification model to predict cancellations of commercial flights leaving Heathrow

### Prior model builds on flights  
https://srcole.github.io/assets/flight_delay/report.pdf - study which used classification for >15 mins late

### Reasons why flights get cancelled  
https://www.claimcompass.eu/blog/why-is-my-flight-cancelled/ 

### Format of this repository  
 - This repo has been divided into the separate stages undertaken when developing this project.
 - Please run each script in numerical order to reproduce results shown.  You will need API keys for the flight aware API
 - All datasets are saved to and loaded from the datasets folder. Each dataset's number pertains to which script __created__ that dataset
---
__Folders and scripts__  

0. - define environment  

1. 1- API_scrape_dataset_build:  
__1.1- Base_dataset_with_outcome.ipynb__
    - Flight aware API - not included in final model
    - Aviation edge API - base of our dataset

2. 2- Preprocessing:  
__2- preprocessing.ipynb__
    - clean headers
    - NaN values
    - Time formats
    - create a data dictionary
    - set outcome variable

3. 3- Exploratory_data_analysis:  
__3-EDA-ml-flights.ipynb__
    - 1. Date range
    - Missingness
    - Filters to add to data before modelling
        non-commercial carriers
        'empty' carrier
    - Distribution of outcome variable
        alone  
        by terminal  
        by carrier  
4. 4- Feature Engineering:  

    - __4- Feature engineering.ipynb__ (Basic level)
        - Encoding airlines - % of Heathrow flights - rank from 1-5. 124 unique carriers
        - turn time_of_day into 4 segments redeye, morning, afternoon, evening
        - one hot cat variables  

    - __4.1 Covid UK data.ipynb__  

    - __4.2 WorldBank_airPassengersDepartures_API.ipynb__  
    World bank API to get month by month totals of passenger departures globally  

    - __4.3 Webscrape_IATA_codes.ipynb__
    Scrape a table from Wikipedia to get IATA codes and airline country and other misc info

5. Modelling:  
    -  Binary Classifier chosen was XGBoost (speed and accuracy)
         A Random Serach Cross Validation was used to improve the model performance


### Feature Ideas (* Denotes included - others to be done if time is sufficient)

1. Airline recode *
    1. size of airlines # flights out of heathrow *  
    2. size of airlines company size  
    3. size of airlines profitability  
    
    
2. Covid *
    1. new cases in london by day
    2. new cases in the UK by day * (maybe different decision making bases on one and not the other?)  
    3. If we can get carrier country - we can using 1.2 Webscrape_IATA_codes.ipynb then we can get daily covid cases at destination too.
​
​
​
3. Worker strikes
    1. web crawler on the airline union websites - matches of the word 'strike' in the last 2 week period (time needed for organisation)   
    2. other industrial actions  
​
​
4. Twitter
    1. Sentiment analysis on Tweets __from__ heathrow leadership accounts  
    2. Sentiment analysis on Tweets __about__ heathrow leadership using hastags  
    3. aviation authority - bag of keywords  
​
​
5. Weather
    1. daily api hit for forecasts on flight day __(careful not to include future information)__ - score forecast events on a scale of 'disruptiveness' 
​
​
6. Polical/civil/security issues
    1. webscrape of news headlines. Either looking for keywords 'airport' OR sentiment score or both.  
​
​
7. technical faults/disruptions
    1. public airport information - websites  
    2. Boeing/Airbus announcments - faults  
​
​
8. World Bank - airline passengers API *
    1. Passengers from PREVIOUS month increase/decrease % - will a recent decrease of passengers result in more cancellations?


