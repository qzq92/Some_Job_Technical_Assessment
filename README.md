# Simple technical interview assessment on mock Company site access data and US Arrest data using Python Programming.


## Note:

Please note the analysis is made using simple assumptions without much complex interpretation due to time constraints. Making too much assumptions and creating complex relationship makes analysis difficult and hard to justify on the rationale and would require more effort.

## Section 1

The *data* folder contains an 'Access_data' subfolder which includes 22 datasets in .csv format and 1 data dictionary in .docx format. The datasets are sample of the mock-data on individuals accessing two office sites of Company ABC, consisting of:

1. When: Time of entry by the individual

2. Profile: Type of access card
    -	0 - Staff Pass
    -	1 - Temp Pass
    -	2 - Visitor Pass

3. Dept: Department of the individual

4. CardNum: Card unique identifier. The length of the card number cannot be less than 8 characters. Currently, if CardNum starts with a/multiple ‘0’, the data captured in system will exclude/remove the “0”.

You can **assume that the total number of staff in the company is 2000 and the data is extracted from the company’s building access system. An individual can tap in and out several times within the same day. When the individual first clock in, that would be the earliest time slot and the only record you will base off the analysis.** (You can also state your other assumptions if need be.)

### Question 1.1

Write code preferably in **R or Python** to process and organise the raw data (*Access_data.zip*) to make it suitable for analysis. **Identify and resolve the data quality issues** in the raw data, if any. (The created code should **allow user to efficiently and easily run it to ingest additional datasets of different period, beyond the given sample.**)

Key data issues identified with resolution:
1. Malformed Card ID information. Resolution: Comparison with other known ID based on card type and department information as part of correction. Only 2 cases 
2. Lots of #REF! and #VALUE! artefact in excel file for Card ID due to referencing or invalid formatting required which is not handled. Resolution: #REF! treated as system glitch causing duplciates, entries are removed. #VALUE! could indicate some form of malformed information not known. A simple imputation with "NewCard" is used to distinguish the card from other known card information.
3. Incorrect column header identified for some csv files due to additional space or 's' (plural form). Resolution: Retain only the first four alphanumeric characters after stripping leading/trailing spaces.
4. Varying value representation for *Profile* and *Department* features, where "2" or 2 or "Visitor Pass" is used to represent the same profile. Similarly for *Department* where 'Dept  1' and 'Dept 1' were encountered. Resolution: Standardised representation using suitable mapping and processing.
5. Duplicated row entries. Resolution: Removed upon implementing resolution #2 and combining all data.

## Section 2

The *data* folder contains a 'US_Arrest_Data' subfolder which includes 8 datasets in .csv format and 3 data dictionaries in .docx format. You may or may not use all the datasets during this assessment.

### Question 2.1

Categorise / group the states based on their characteristics.

Categorisation of states is done by applying AgglomerativeClustering based identified assigned number of clusters from Dendrogram interpretation of optimal cluster based on following features from dataset:
- Population
- Income
- Illiteracy
- Life Exp
- Murder Manslaughter Rate 
- HS Grad
- Area
- Murder Arrest Rate
- Assault Arrest Rate
- UrbanPop
- Rape Arrest Rate

### Question 2.2

What factors are statistically significant in predicting Assault rates?

Dataset: USArrest.csv (main). You may wish to use the other datasets to enhance your study.

In view of predicting Assault rates, we can use ordinary least square regression with 4 identified features and predict assault arrest (as a proxy feature) to actual assault rate.

We can use a regression model assault rates (dependent factor) as a function of other features (predictor factors) based on the following:
- Illiteracy rate (Illteracy)
- Income
- UrbanPop (Urban population)

where we need to have a standardised regression coefficient for fair comparison due to the use of common scale. Other arrest related features would not be included as the high correlation may be due to confounding effects (recalcitrant culprit) maybe involved in both assault/rape/murder crimes during same period. Non-arrest related features with moderate/strong correlation (more than 0.5 in absolute correlations) are excluded from regression modelling to avoid complexities in the algorithm and increasing risks of error and for simpicity purposes.

Assumptions: We assume that any arrest can only be categorised into either arrest cases of Murder, Assault or Rape since they are crimes of different severity. Based on the high positive correlation between murder arrest and murder/manslaughter rate features, I suppose similar correlation would apply for assault case if assault rate information is known, and that all crimes are treated equally by authorities. It would be illogical to include life expectancy as predictor feature to assault rates and does not indicate some form of vulnerability for crimes to occur.
