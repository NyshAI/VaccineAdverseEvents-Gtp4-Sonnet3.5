# Analyzing Temporal and Associative Relationships of Vaccine Adverse Events for Hepatitis B vaccination

## Background and Goal:
Analyzing adverse events in the vaccine is essential for ensuring vaccine safety. With large datasets like Vaccine Adverse Events Reporting Systems (VAERS) capturing a wide range of reported vaccine adverse events, it becomes important to examine their temporal patterns and associations. In this project, the primary objective is to identify and uncover critical temporal relationships and associations of these adverse events with advanced natural language processing techniques.

### Essential Terminology:

#### Hepatitis B
Hepatitis B is a liver infection caused by the hepatitis B virus (HBV). It can range from a mild, short-term illness to a chronic, long-term condition. The virus primarily spreads through contact with infected body fluids, which may occur through blood transfusions, sharing needles, sexual contact, or from mother to child during childbirth.

#### Temporal Relationships
This involves studying when adverse events occur concerning when a vaccine was administered. By analyzing the timing, researchers can assess whether certain adverse events are more likely to happen immediately after vaccination, within a few days, weeks, or longer. Understanding this timing helps determine if there’s a potential link between the vaccine and the event or if it’s coincidental.

#### Associative Relationships:
This part examines possible correlations or associations between the vaccine and specific adverse events. By identifying patterns in data, researchers can see if certain side effects appear more frequently with specific vaccines, age groups, health conditions, or demographic factors.

#### Vaccine Adverse Events: 
These are any health issues or side effects reported after a person receives a vaccine, ranging from mild symptoms (like a sore arm) to more severe reactions.
<br><br>
In essence, the analysis aims to provide insights into when adverse events are likely to happen post-vaccination and whether these events are more common in specific contexts, ultimately helping in assessing Hepatitis B vaccine safety and improving patient outcomes.

## Problem Formulation:
The following are the main aspects of this project:
* **Data Procurement and Preprocessing**
* **Statistical Analysis of VAERS data for Hepatitis B Vaccine**
* **Temporal Relationship Analysis of Symptom**
* **Associative Relationship Analysis of Symptoms**
* **Insights and Conclusion**

## **Data Procurement and Preprocessing**
### Data source:
The Vaccine Adverse Event Reporting System (VAERS)* is a national early warning system that detects possible safety problems in U.S.-licensed vaccines. VAERS is co-managed by the _Centers for Disease Control and Prevention (CDC)_ and the _U.S. Food and Drug Administration (FDA)_. VAERS accepts and analyzes reports of adverse events (possible side effects) after a person has received a vaccination.
<br>
* The data can be downloaded at [VAERS data source link](https://vaers.hhs.gov/data/datasets.html).
* The user guide to understand more about the data can be found in [VAERS data use guide](https://vaers.hhs.gov/docs/VAERSDataUseGuide_en_September2021.pdf).
* The data provided can be explored at [The LEAF VAERS Data Analysis System](http://vaers.leafnlp.org/data/vax_event_search_basic).

For each year there are three tables in the ***VAERS dataset***, including ***VAERS_DATA***, ***VAERS_Symptoms***, and ***VAERS_Vaccine***. <br><br>
For the Hepatitis B vaccine, data has been available from 1990 to now. This comprise  of ***106 tables***.<br><br>
To obtain the common columns in all three file types for each year, I have implemented an inner join using the column VAERS_ID containing VAERS identification numbers that are
common in all file types. The resultant file obtained for every year was joined to obtain the final file.<br><br>
The final file comprised ***73,793*** samples relevant to the Hepatitis B Vaccine, which were used to implement this project.<br><br>

## Data Preprocessing:
A function was written in Python to perform the following preprocessing steps on the crude description present in the variable **SYMPTOM_TEXT** of patients who received vaccination:
* **Handled the missing values**
* **Converted text to lowercase**
* **Removed Characters**
* **Removed punctuation**
* **Performed Text Tokenization**
* **Removed Stop Words**
<div align="center">
<img width="578" alt="image" src="https://github.com/user-attachments/assets/958593de-4a62-4bdc-a5c2-416bd8e19f32" />
</div>

### Token summary in the processed texts:
#### Five-Point Summary comparison of token count:
<div align="center">
<img width="596" alt="image" src="https://github.com/user-attachments/assets/d302b00b-cfe7-455c-8872-33e3dc1495c3" />
</div>
<br>
We notice that there is a significant reduction in the number of tokens in processed text. Also, there is a significant difference between the 3rd quartile 75th percentile, and 100th percentile, indicating the presence of a large number of outliers. The nonrelevant outliers were removed.<br>

#### The boxplot of the token count after preprocessing:
<div align="center">
<img width="700" alt="image" src="https://github.com/user-attachments/assets/0698e5cb-fe14-446c-9606-85109d33d26b" />
</div>

## Statistical Analysis of VAERS data for Hepatitis B Vaccine
### Types of Hepatitis B Vaccines administered based on age
#### Histogram:
<div align="center">
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/95bbd3f8-ca4a-4383-9190-c921baf30773" />
</div>

#### Five-Point Summary:
<div align="center">
<img width="700" alt="image" src="https://github.com/user-attachments/assets/ea09b492-1a1a-45f0-b842-1c88219d9bf3" />
</div>

#### Insights:
* Engerix – B was the most administered Hepatitis B vaccine 
* It was administered mostly between the age groups of 0-9


### Types of Hepatitis B Vaccines administered based on Gender:
#### Histogram:
<div align = "center">
<img width="900" alt="image" src="https://github.com/user-attachments/assets/32ded4bc-8372-4728-a943-71cfb8983909" />
</div>

#### Count:
<div align="center">
<img width="500" alt="image" src="https://github.com/user-attachments/assets/299c2f86-f042-4f0d-ae55-3c5d998611fd" />
</div>

#### Insights:
* Engerix – B was the most administered Hepatitis B vaccine.
* It was administered mostly to females.

### Death count analysis of deaths that occurred due to Hepatitis-B vaccination.
#### Histogram:
<div align = "center">
<img width="900" alt="image" src="https://github.com/user-attachments/assets/5b1b563f-d584-4490-b6a4-e3957046651c" />
</div>

#### Count:
<div align = "center">
<img width="400" alt="image" src="https://github.com/user-attachments/assets/69bd8298-2671-4b7a-8f57-0611b6f1a1a4" />
</div>

#### Insight:
We notice that the ***Recombivax-HB*** vaccine has caused more deaths even though it was the second most administered vaccine. 
So, in comparison, the ***Engerix-B*** vaccine has performed better.


### Frequency of life-threatening events caused after Hepatitis B Vaccine Administration:
#### Histogram:
<div align = "center">
<img width="900" alt="image" src="https://github.com/user-attachments/assets/155d6597-ce51-4e1d-b148-c71f2ba0f610" />
</div>

#### Count:
<div align = "center">
<img width="400" alt="image" src="https://github.com/user-attachments/assets/69bd8298-2671-4b7a-8f57-0611b6f1a1a4" />
</div>

#### Insight:
We notice that although the ***Recombivax-HB*** vaccine has caused more deaths when compared to ***Engerix-B***, the ***Engerix-B*** causes more life-threatening diseases.

## Temporal Relationship Analysis of Symptoms:

