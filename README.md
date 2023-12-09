# Simple technical interview assessment on mock Company site access data and US Arrest data using Python Programming.

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

## Section 2

The *data* folder contains a 'US_Arrest_Data' subfolder which includes 8 datasets in .csv format and 3 data dictionaries in .docx format. You may or may not use all the datasets during this assessment.

### Question 2.1

Categorise / group the states based on their characteristics.

### Question 2.2

What factors are statistically significant in predicting Assault rates?

Dataset: USArrest.csv (main). You may wish to use the other datasets to enhance your study.