
# Exploring Cancer Mortality Factors
## Background:
The scale of cancer burden in the United States is huge with millions of new cancer cases a year. Susceptibility to cancer has been organized into modifiable and non-modifiable factors. Modifiable factors include body mass index (BMI) and cigarette use while non-modifiable factors include age, sex, and race/ethnicity. Modifiable cancers are responsible for a huge fraction of all cancer cases and cancer prevention interventions that target modifiable risk factors have been shown to be effective in reducing cancer cases and deaths. By using data science to map out cancer risk prediction models this could help pinpoint those at greatest risk for cancer. To do this a cancer risk prediction model much include both modifiable and non-modifiable risk factors. We started by analyzing data from the Third National Health and Nutrition Examination Survey (NHANES III) and the National Death Index (NDI) Public-Use Linked Mortality Files. The goal of our analysis was to examine the NHANES III data and identify variables useful for prediction of mortality risk in python. 
## Methods:
The Third National Health and Nutrition Examination Survey (NHANES III) consisted of interview, medical examination, and laboratory data sets. This data was collected from 1988 to 1994 in the United States. NHANES III was linked with mortality data from the NDI death records by the National Center for Health Statistics. 

The exclusion factors included participants who: 
1. were under 18 years of age, 
2. had a self-reported cancer at baseline, and 
3. had missing values for variables related for the study.

In this study, the model used to relate the time that passed (before cancer death occurred) to risk factors was the Cox proportional hazard model. Specifically, the follow-up time variable (XXX) and cancer death were used as the survival outcome in the regression analysis. 

Using Python's **pandas**, we: 
1. Read the csv datasets into dataframes (i.e., adult, lab, exam, mort).
2. Removed all participant identifiers (SEQN) with missing causes of death (UCOD_LEADING) or missing follow-up time from interview (PERMTH_INT). 
3. Created a cancer mortality variable based on whether "Malignant neoplasms" (C00-C97) was recorded as the cause of death. 
4. Merged all datasets using the participant identifier variables (SEQN).
5. Removed baseline cancer cases using the HAC1N and HAC10 variables.
6. Removed participants with missing relevant variables (SDDPSU6, SDSTRA6, and WtPFQX6) and variables with a time outside the date of interview (i.e., PERMTH_EXM).

Using Python's **Scikit-Learn**, we:
1. Removed highly correlated variables (r≥0.9).
2. Chose the 25 most correlated predictor variables (i.e., the predictor variables with the highest r^2 values).  

Using Python's **Lifelines**, we applied the Cox Proportional Hazards Model to the 25 predictor variables mentioned above. 
> In addition to the 25 selected predictor variables the model also included:
1. A "survival object" created from the "cancer mortality" event and follow-up time variables.
2. A "design object" created from the "primary sampling unit" (SDDPSU6), "Stratification" (SDSTRA6), and "Weight" (WTPFQX6) variables. 

Using Python's **Plotly**, the Cox Proportional Hazard model was represented in the form of a volcano plot. 

## Results:
## Discussion:
## Conclusion: 
## References: 
