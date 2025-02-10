# Analyzing Temporal and Associative Relationships of Vaccine Adverse Events for Hepatitis B vaccination

## Background and Goal:
Analyzing adverse events in the vaccine is essential for ensuring vaccine safety. With large datasets like Vaccine Adverse Events Reporting Systems (VAERS) capturing a wide range of reported vaccine adverse events, it becomes important to examine their temporal patterns and associations. In this project, the primary objective is to identify and uncover critical temporal relationships and associations of these adverse events with advanced natural language processing techniques.

### Essential Terminology:

#### Hepatitis B
Hepatitis B is a liver infection caused by the hepatitis B virus (HBV). It can range from a mild, short-term illness to a chronic, long-term condition. The virus primarily spreads through contact with infected body fluids, which may occur through blood transfusions, sharing needles, sexual contact, or from mother to child during childbirth.

#### Temporal Relationships
This involves studying when adverse events occur concerning when a vaccine was administered. By analyzing the timing, researchers can assess whether certain adverse events are more likely to happen immediately after vaccination, within a few days, weeks, or longer. Understanding this timing helps determine if there’s a potential link between the vaccine and the event or if it’s coincidental.

#### Associative Relationships:
This part examines possible correlations or associations between the vaccine and specific adverse events. By identifying patterns in data, researchers can see if certain side effects appear more frequently with particular vaccines, age groups, health conditions, or demographic factors.

#### Vaccine Adverse Events: 
These are any health issues or side effects reported after receiving a vaccine, ranging from mild symptoms (like a sore arm) to more severe reactions.
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
Temporal relationships analysis explores connections between symptoms that occur over time as a consequence of the Hepatitis B vaccine being administered. The analysis of temporal relationships of symptoms is essential to understand the cause-and-effect relationships among them. As part of the analysis of temporal analysis of symptoms caused due to Hepatitis B vaccination we perform the following steps:
  1.  Use GPT4 via API call and design prompt to extract symptoms in the order in which they occur in the crude textual description present in the variable "SYMPTOM_TEXT".
  2.  Use Antropic's Cluade Sonnet 3.5 via API call and design prompt to extract symptoms in the order in which they occur in the crude textual description present in the variable "SYMPTOM_TEXT"
  3.  Create a set of unique symptoms generated by both LLMs. 
  4.  Both LLMs might extract the same symptom in different ways, so there can be multiple representations for the same symptom. For instance, similar symptom representations such as **{'felt nauseated', 'nauseated', 'nausea', 'cont sl nauseated', 'woke nauseated', 'nauseated throughout the day', 'became nauseated', 'nauseate', 'slightly nauseated'}** can only be represented by the symptom name **{'nauseated'}**.<br>
    To group similar representations of the same symptom we use a technique called **approximate string matching** which is also popularly known as **fuzzy string matching**, which is used to find strings that match a pattern approximately (rather than exactly). <br>
    <img width="1000" alt="image" src="https://github.com/user-attachments/assets/592b2ef5-0027-40d0-b85e-97def4782bbb" />
5.  Create a diction of symptoms that makes sense and their possible representations as key-value pairs.
6.  Replace the various symptom representations of a symptom with a unique representation (which is the key of the dictionary created above) in the lists of symptoms generated by both GPT4 and Claude 3.5 Sonnet LLMs. By doing this, we have a standard unique representation of symptoms in "GPT4_SYMPTOMS" and "Claude_SYMPTOMS"
7.  With the standardized list of symptoms generated by GPT4 and Sonnet  obtained above compute the following evaluation metrics and analyze the output:
    * **Kendall’s Tau ($\tau$) Rank Correlation Coefficient**
    * **Longest Common Subsequence (LCS)**
    * **Dynamic Time Warping (DTW)**

### GPT 4 Symptom extraction:
From the textual descriptions of symptoms that occurred as a consequence of vaccination, available in the **SYMPTOM_TEXT** variable, we need to extract a list of symptoms in the order they appear. The output should be structured as $[symptom_1,symptom_2,...,symptom_n]$, where $symptom_1,symptom_2,...,symptom_n$ are extracted sequentially as they appear in the **SYMPTOMS_TEXT** variable.<br>
To do this we implement the following steps:<br>
   1. Load the OpenAI key to make GPT calls securely stored in the environment as follows:<br>
      <img width="319" alt="image" src="https://github.com/user-attachments/assets/7d769e20-5cf9-40b8-87fe-22e4f38c79f5" /><br>
      where **OPENAI_API_KEY** should contain the actual value of the key in the environment.
   2.  **Token Limit Function**: Truncate input text to ensure it fits within GPT-4's token limit I have set it to a default of 3000.<br> 
       **Note:** This limit should be set carefully, considering the cost per token and the requirements of the task at hand.<br>
       <img width="500" alt="image" src="https://github.com/user-attachments/assets/360e4629-7afe-4536-8d1a-30a3fd76d90e" />
   3.  Function to extract a sequential list of symptoms using GPT4:<br>
      This function takes in one record of the SYMPTOM_TEXT variable as a parameter which is named 'text'. If the input provided is not text or is missing I return an empty 
       [].<br>
       I then go on to implement a try-and-catch block.<br>
       In the try block, I use the above-provided Token Limit Function to ensure that the number of tokens is below 3000, so that the costs are in check, in case the input 
       text is long. <br> I then call the GPT4 API using the Call **ChatCompletion.create** as follows:<br>
       <img width="1000" alt="image" src="https://github.com/user-attachments/assets/385e5c41-5c7b-4a19-a26b-ba0bf0102d59" /><br>
       I have designed the prompt as follows:<br>
       <img width="847" alt="image" src="https://github.com/user-attachments/assets/5780f5ab-f982-4cc7-8cae-6403a72c22b8" /><br>
       Explanation of parameter:<br>
       - **`model="gpt-4"`**: Specifies that we are using the GPT-4 model.
       - **Messages Format**:
         - **System Message**: Sets the assistant's behavior to focus on analyzing medical text and extracting symptoms.
         - **User Message**: Sends the formatted prompt containing the input text.
         - **`max_tokens=500`**: Limits the response length to **500 tokens**.
         - **temperature=0.2**: The **temperature** parameter will determine how controls the level of randomness and creativity in its responses:<br>
                - **0.0–0.4**: Low temperature, producing conservative and predictable responses.<br>
                - **0.5–0.7**: Medium temperature, producing a balance between creativity and accuracy.<br>
                - **0.8–1.0**: High temperature, producing highly creative and unpredictable responses.<br>
           Since I have wanted the responses to be more conservative I have set a lower value of temperature.<br>
           
  4. Then we parse the response to extract the symptom as follows:<br>
     <img width="500" alt="image" src="https://github.com/user-attachments/assets/4b12f678-e565-4373-8b01-9a0c78136dc4" />

  5. The **symptoms** extracted above is a string consisting of a list of symptoms of the format, *"[symptom_1,symptom_2,...,symptom_n]"*. This needs to be converted into a Python list comprising symptoms. This is implemented as follows:<br>
     <img width="858" alt="image" src="https://github.com/user-attachments/assets/1b049283-8671-45f9-8c7d-8da765c36334" /><br>
The above steps are implemented as the try block.
6. As part of the expect block we make sure that if an expectation is raised while extracting symptoms, an empty list **[]** is returned, and the execution continues to extract the symptoms from the next textual record of "SYMPTOM_TEXT".

### Symptom extraction using Antropic's Claude-Sonnet-3.5 model:
The process of extracting symptoms from the crude textual description of SYMPTOMS_TEXT using Sonet3.5 is similar to the process we used with Sonnet 3.5 models.<br> The Anthropic API key is stored in the working environment as follows:<br>
<img width="309" alt="image" src="https://github.com/user-attachments/assets/4014f7bb-d992-4b7d-80ae-fce35b945b8e" /><br>
I have written a function called **extract_symptoms_claude** which takes the textual descriptions as input available in SYMPTOMS_TEXT and performs the following steps.
1. If the input is not a text or empty an empty string [] is returned.
2. Then we implement a try-catch block. In the try block,
    - We use the truncate_text to make sure that the text is not too long.
    - 


        
                                                                                                                        
                                   
             


       
       

       

        
       


    
