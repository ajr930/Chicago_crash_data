# Chicago Car Crash Analysis

![image](https://user-images.githubusercontent.com/83923459/133816914-d8fe9f74-3106-4082-86b9-d85d60e6ecc3.png)
<br>
## Overview
The city of Chicago is looking to mitigate future accidents and we will use this data set to see what the primary cause of these accidents are.
<br>
## Data
In order to use run this data you must download the data sets from the following 3 links and store them in the same folder as your notebook<br>
1.https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if
2.https://data.cityofchicago.org/Transportation/Traffic-Crashes-Vehicles/68nd-jvt3
3.https://data.cityofchicago.org/Transportation/Traffic-Crashes-People/u6pd-qa9d

![Screen Shot 2021-09-17 at 11 51 26 AM](https://user-images.githubusercontent.com/83923459/133817714-95649f44-28f1-4b00-9421-0147291dfca9.png)
<br>
Merging Data
![Screen Shot 2021-09-17 at 11 53 24 AM](https://user-images.githubusercontent.com/83923459/133817923-85ae5139-eb88-410c-b7b8-426ce116b47e.png)

## Cleaning Data
We then cleaned the data and trimmed the classification categories for the prime contributory causes to fit our models<br>
While cleaning data and finding the top contributory causes there were over 50% of that data did not have the primary contribtory causes<br>
We will then try and predict the cause to help understand accidents and use the data to reduce them in the future


## Top Eleven Contributory Causes of Accidents
![image](https://user-images.githubusercontent.com/83923459/133819234-0e027b25-c854-418c-b6a9-de7fee4b4356.png)
<br>We see that "Failing to Reduce Speed to Avoid Crash/Following too Closely" is the number one contributory cause with over 24% of all accidents<br>
We also see that "School Bus Related" accidents have the lowest amount of accidents 
<br>Suggesting to take notes and mimic school bus related laws/characterstics to reduce accidents in other categories

## Model
We did a Dummy Model as our baseline and got an accuracy of 26%

![Screen Shot 2021-09-17 at 12 09 31 PM](https://user-images.githubusercontent.com/83923459/133820043-7265f8a4-bea5-417b-9793-aa21f9ee141f.png)

### Logistic Regression Model
55% Accuracte with a 75% AUC
![Screen Shot 2021-09-17 at 12 11 34 PM](https://user-images.githubusercontent.com/83923459/133820375-14ecc461-77b0-434d-a130-4d8f15ff696c.png)

### KNN Model
Used the Elbow method to find the best n_neighbors
![image](https://user-images.githubusercontent.com/83923459/133820517-09ef9d33-3a4d-42eb-afb5-6d0d9501282d.png)
<br>This shows that we can use the n_neighbors parameter of 20
<br> Was not able to do better with this model
![Screen Shot 2021-09-17 at 12 15 27 PM](https://user-images.githubusercontent.com/83923459/133820768-e5b58643-03f0-4337-b1ea-2abdca04322f.png)

### XGBoost -Best Model
![Screen Shot 2021-09-17 at 12 28 56 PM](https://user-images.githubusercontent.com/83923459/133822527-6bbee025-c41c-4421-b398-dba195042ac9.png)
<br> We see from the confusion matrix that some classes aren't being represented because they are undersampled
![Screen Shot 2021-09-17 at 12 30 03 PM](https://user-images.githubusercontent.com/83923459/133822714-9dd2af93-65dc-4daf-a66e-0506f4a59057.png)

## SMOTE to bring up the samples
![Screen Shot 2021-09-17 at 12 31 56 PM](https://user-images.githubusercontent.com/83923459/133823027-725c1e55-a56b-4e5c-8f81-61e8a26ecd74.png)

### XGBoost with SMOTE
![Screen Shot 2021-09-17 at 12 32 08 PM](https://user-images.githubusercontent.com/83923459/133823641-955dae12-4801-4393-af18-43b25388009a.png)

### Confusion Matrix to make sure undersampled classes were represented
![Screen Shot 2021-09-17 at 12 32 21 PM](https://user-images.githubusercontent.com/83923459/133823148-57a7818e-64c8-432b-aa70-4b1823ccb117.png)



## Conclusion
<br> We were only able to predict 47% of the primary cause of the accident while representing all the classes. THe next suggestion would be to trim the calss categories into maybe 4 categories to get better predictions for missing data
<br>
<br> As for mitigating future accidents it would be helpful to look at how School Busses are able to not get into so many accidents, including making turning right on red illegal or maybe better training for drivers as school bus drivers need to take a course.


