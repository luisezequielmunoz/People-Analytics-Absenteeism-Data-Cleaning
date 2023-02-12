# People Analytics Absenteeism - Data cleaning

![Screenshot 2023-02-12 at 19 52 13](https://user-images.githubusercontent.com/66885480/218330930-a41c420f-1e7f-4f58-a387-03fadeea00f2.jpg)


## General info

The goal of this project is to apply certain data cleaning techniques to prepare the dataset, which will be further used by the Data Science team for ML models development. 

Pandas and NumPy are the main libraries used in this project.

## Dataset

The dataset **_Absenteeism-data.csv_** allows for several new combinations of attributes and attribute exclusions, or the modification of the attribute type (categorical, integer, or real) depending on the purpose of the research. 

1. Individual identification (ID)
2. Reason for absence (ICD).
Absences attested by the International Code of Diseases (ICD) stratified into 28 categories (I to XXVIII) as follows:


    - I Certain infectious and parasitic diseases
    - II Neoplasms
    - III Diseases of the blood and blood-forming organs and certain disorders involving the immune mechanism
    - IV Endocrine, nutritional and metabolic diseases
    - V Mental and behavioural disorders
    - VI Diseases of the nervous system
    - VII Diseases of the eye and adnexa
    - VIII Diseases of the ear and mastoid process
    - IX Diseases of the circulatory system
    - X Diseases of the respiratory system
    - XI Diseases of the digestive system
    - XII Diseases of the skin and subcutaneous tissue
    - XIII Diseases of the musculoskeletal system and connective tissue
    - XIV Diseases of the genitourinary system
    - XV Pregnancy, childbirth and the puerperium
    - XVI Certain conditions originating in the perinatal period
    - XVII Congenital malformations, deformations and chromosomal abnormalities
    - XVIII Symptoms, signs and abnormal clinical and laboratory findings, not elsewhere classified
    - XIX Injury, poisoning and certain other consequences of external causes
    - XX  NaN
    - XXI Factors influencing health status and contact with health services.
    - XXII patient follow-up
    - XXIII medical consultation
    - XXIV blood donation
    - XXV laboratory examination 
    - XXVI unjustified absence 
    - XXVII physiotherapy 
    - XXVIII dental consultation 


3. Date (dd-mm-yyyy)
4. Transportation expense
5. Distance from Residence to Work (kilometers)
6. Age
7. Work load Average/day
8. Education (high school (1), graduate (2), postgraduate (3), master and doctor (4))
9. Children (number of children)
10. Pets (number of pet)
11. Body mass index
12. Absenteeism time in hours (target)



## Approach

**ID:** Dropping the ID Column because it will not help to the analysis (do not carry numeric information)

**Absence reason:** Min value 0, max value 28, len 28. That would be 29 numbers reasons, we only have 28, there is one number missing: number 20. This column is categorical nominal (read dataset info). Adding dummies related to the absence's reason, checking if all absences have, at least, one reason. Group reasons based on certain business definition (group dummies) as follows:

 - GROUP 1 (1 to 14): Disease group
 - GROUP 2 (15 to 17): Pregnancy
 - GROUP 3 (18 to 21): Poisoning
 - GROUP 4 (22 to 28): Light reason for absence (medical consultation, dental appointment, etc).
 
**Dates:** Extracting month and day of the week for analysis (prob. employees are taking Mondays and Fridays off). 

**Education:** Considering Education 2, 3, 4 vs Education 1, then it makes no sense to separate 2-3-4 individually, but rather create two dummies (highschool vs higher degree).


## Outcome

Cleaned dataset available: **_df_cleaned.csv_** 
