# proj-food-inspections  

## Objective
In the past month, I saw the food inspection dataset from the City of Chicago Data Portal.  I felt like this dataset has potential to be interesting since it has a broad range of features and data that could be enhanced with additional data resources.  Since the data is specific to permitting, the business names, ids, and addresses would largely be accurate due to the nature of this information being needed by the general public.   

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


