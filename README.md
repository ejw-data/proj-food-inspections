# proj-food-inspections  

Author:  Erin James Wills - ejw.data@gmail.com  

![](./images/inspection-banner.png)  

<br>

```
This project is in development.  Key parts have been finished but ongoing tasks have been planned.  
```

## Overview 
In the past month (Aug 2023), I saw the food inspection dataset from the City of Chicago Data Portal.  I felt like this dataset has potential to be interesting since it has a broad range of features and data that could be enhanced with additional data resources.  Since the data is specific to permitting, the business names, ids, and addresses would largely be accurate due to the nature of this information being needed by the general public.   

The initial goal of this project is to determine the following:
* Are there any unusual ways that restaurants are identified  
    - Does a restaurant receive one business license per address or does it change with renewals?
    - Over time do the restaurants retain their business license or do changes occur over time?
    - How do large organizations with food courts documented?
    - And many more questions related to the issuance of permits...
* Is there a particular feature that influences inspection pass rate more than other features?
    - Are there specific violations that result in failures?
    - Do certain restaurant types fail more often than others?
    - Do certain restaurant locations fail more than others?
    - Do some locations have more inspections than others?
* Do derived features influence inspection pass rates? 
    - As businesses gain operational experience (age of business), do they pass more frequently?
    - Do restaurants that have multiple locations (restaurant chains) have a higher pass rate?
    - Does the past inspection history influence failure rate?


This topic has potential to use multiple data sources:  
* City of Chicago Food Inspections (initial dataset)  
* City of Chicago Business License Inventory 
* Geoapify business directory lookup
* Yelp and other food service reviews
* Census data  

Additional outcomes of this project could include:
*  A multi-table database  
*  An ETL pipeline to add new data to the database
*  A machine learning model that identifies high failure rate restaurants based on business features
*  Recommendations about how food services can aid to reduce food inspection failures, how risk assessment could be modified to achieve better food risk metrics, and whether bias are built into the inspection systems.  



## Tasks
- [x] Create readme template with initial objectives  
- [x] Since datasets are too large to store on github, create a script that downloads files to the data folder
- [x] Create script that organizes the data into consistent features
- [x] Create script that summarizes data for each restaurant as new features  
- [x] Reduce the number of queries needed to find Chicago businesses to stay within Geoapify API query limits
- [ ] Use the geoapify api to find additional business information
- [x] Test classification models to determine key features for pass/fail inspection metric  
- [x] Evaluate model with classification report and other methods
- [x] Create preprocessing pipeline using `ColumnTranformer` or a custom transformer
- [ ] Perform NLP model like a sentiment analysis to incorporate city complaint and website reviews as a feature in the model  
- [ ] Currently no Regression modeling plans have been made but re-evaluate this later in the project as well as Clustering applications


## Current Results  
* Combining the two datasets is complete.  The original food inspection dataset had 258,000 rows of data and after cleaning had over 150,000 rows of data.  It also contained 26 features.  After merging the two datasets and doing some additional cleaning, a total of 148,000 rows of data existed with 47 features.  
*  The quality of the final dataset seems to be very good with only small numbers of NaN in some less important features.  
*  The dataset is moderately unbalanced with 60% of the data being pass inspection data and 20% of the data beging Passed with Conditions and Failed. Initial evaluation of the models did not indicate significant bias associated with the target balance.  
*  Each business and address was given a unique alias since there were inconsistencies with how license numbers were assigned.  
*  The business activity feature might be able to be improved by grouping similar categories together.  Including cuisine type may also improve predictive ability of the mdoel.  These tasks have been added to the to-do list.  
*  For analysis, percent failed was used as the main metric becasue it was more consistent over time as compared to the number of failed inspections.  There is a large variation with the number of inspections performed from year-to-year.  
*  Only a small amount of cyclic trends appear in the target variable.  The most significant trend is that there are fewer inspections in the winter and early spring than in the summer but the overall difference between the seasons is pretty moderate.  Accounting for this variation might be added to a future model.  
*  The risk type of the business did not seem to be influence the failure rate.  
*  Most of the other factors did not show siginficant importance relative to the target variable.  
The model did help identify these feautures as the most signficant:  
    *  Number of Violations Identified
    *  Number of Citations Issued  
    The other slightly important features included:
    *  Inspection type
    *  Business age  
    *  Number of Chains  
*  The model also revealed that Ward 42, 41, 13, and 34 have a minor significance but a much larger significance than the other wards.  Investigating these features could be interesting - is it a bias?
*  The model has reasonable predictions but did not predict well - it was 65% of the time correct in its prediction a failed inspection and 
it was able to identify correctly 42% of all the failed inspections.   
*  **More evaluation will be provided after the next set of updates.**  
*  The initial phases of creating a preprocessing pipeline are done.  Additional steps need to be added and it would be nice to include a nice ETL pipeline that brings in new data.  
*  An initial setup for using the geoapify api has been created and a grid system has been created to build a database of existing Chicago restaurants.  Comparing the results to Google's gmaps might be necessary.  Initial quality of geoapify api was highly questionable.  Further investigation is needed.  


## Future Work  
I am really interested in building in more data sources and organizing the content into a database.  The next steps will be to continue improving the model by trying different algorithms and adding a couple features.   

Once the model has more predictive power then I will consider developing the project into an full cycle project that will include some data engineering in the automated data extraction phase at the beginning, the entire data science workflow in the middle, and complete with more data engineering/ML engineering in deploying an api or app that includes monitoring capabilities.  I think this might be a nice professional development project that will keep my skills up-to-date.    


## Technologies  

* Python
* API  


## Data Source  

City of Chicago Data Portal:
* [City Limits Shapefile](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-City/ewy2-6yfk)  
* [Food Inspections](https://data.cityofchicago.org/Health-Human-Services/Food-Inspections/4ijn-s7e5)
* [Business Licenses - Current Active](https://data.cityofchicago.org/Community-Economic-Development/Business-Licenses-Current-Active/uupf-x98q)  
* [Business Licenses - All](https://data.cityofchicago.org/Community-Economic-Development/Business-Licenses/r5kz-chrr)  


## Setup and Installation  

1.  Clone the repo to your local machine
1.  Activate an environment that has these packages:
    *  Python
    *  Numpy
    *  Matplotlib
    *  Seaborn
    *  Scikit-learn
1.  The data files are too large to keep in the repo so first run `dataset_import.ipynb` found in `./data/original/`.  
1.  To create the cleaned data set run `feature_extraction.ipynb` found in the root directory.  
1.  Other interesting files to look at are `feature_analysis.ipynb` and `model_development.ipynb`.  