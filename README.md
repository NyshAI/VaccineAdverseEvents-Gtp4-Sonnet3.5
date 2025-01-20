# Analyzing Temporal and Associative Relationships of Vaccine Adverse Events for Hepatitis B vaccination

## Background and Goal:
Analyzing adverse events in the vaccine is essential for ensuring vaccine safety. With large datasets like Vaccine Adverse Events Reporting Systems (VAERS) capturing a wide range of reported vaccine adverse events, it becomes important to examine the temporal patterns and associations between them. In this project, the primary objective is to identify and uncover critical temporal relationships and associations of these adverse events with advanced natural language processing techniques.

### Essential Terminology:

#### Hepatitis B
Hepatitis B is a liver infection caused by the hepatitis B virus (HBV). It can range from a mild, short-term illness to a chronic, long-term condition. The virus primarily spreads through contact with infected body fluids, which may occur through blood transfusions, sharing needles, sexual contact, or from mother to child during childbirth.

#### Temporal Relationships
This involves studying when adverse events occur concerning when a vaccine was administered. By analyzing the timing, researchers can assess whether certain adverse events are more likely to happen immediately after vaccination, within a few days, weeks, or over a longer period. Understanding this timing helps determine if there’s a potential link between the vaccine and the event or if it’s coincidental.

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
The Vaccine Adverse Event Reporting System (VAERS)* is a national early warning system to detect possible safety problems in U.S.-licensed vaccines. VAERS is co-managed by the _Centers for Disease Control and Prevention (CDC)_ and the _U.S. Food and Drug Administration (FDA)_. VAERS accepts and analyzes reports of adverse events (possible side effects) after a person has received a vaccination.
<br>
* The data can be downloaded at [VAERS data source link](https://vaers.hhs.gov/data/datasets.html).
* The user guide to understand more about the data can be found in [VAERS data use guide](https://vaers.hhs.gov/docs/VAERSDataUseGuide_en_September2021.pdf).
* The data provided can be explored at [The LEAF VAERS Data Analysis System](http://vaers.leafnlp.org/data/vax_event_search_basic).

For each year there are three tables in the ***VAERS dataset***, including ***VAERS_DATA***, ***VAERS_Symptoms***, and ***VAERS_Vaccine***. <br>
For the Hepatitis B vaccine, data has been available from 1990 to now. This comprise  of ***106 tables***.<br><br>
To obtain the common columns in all three file types for each year, I have implemented an inner join using the column VAERS_ID containing VAERS identification numbers that are
common in all file types. The resultant file obtained for every year was joined to obtain the final file.<br><br>
The final file comprised ***73,793*** samples relevant to the Hepatitis B Vaccine, and these samples were used to implement this project.<br><br>
