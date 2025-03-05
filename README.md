# Analyzing Temporal and Associative Relationships of Vaccine Adverse Events for Hepatitis B vaccination

## Background and Goal:
Analyzing adverse events in the vaccine is essential for ensuring vaccine safety. With large datasets like Vaccine Adverse Events Reporting Systems (VAERS) capturing a wide range of reported vaccine adverse events, examining their temporal patterns and associations becomes important. In this project, the primary objective is to identify and uncover critical temporal relationships and associations of these adverse events with advanced natural language processing techniques.

### Essential Terminology:

#### Hepatitis B
Hepatitis B is a liver infection caused by the hepatitis B virus (HBV). It can range from a mild, short-term illness to a chronic, long-term condition. The virus primarily spreads through contact with infected body fluids, which may occur through blood transfusions, sharing needles, sexual contact, or from mother to child during childbirth.

#### Temporal Relationships
This involves studying when adverse events occur, concerning when a vaccine was administered. By analyzing the timing, researchers can assess whether certain adverse events are more likely to happen immediately after vaccination, within a few days, weeks, or longer. Understanding this timing helps determine if there’s a potential link between the vaccine and the event or if it’s coincidental.

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
  4.  Stranderdize the representation of symptoms in the symptoms lists extracted by both GPT4 and Claude Sonnet 3.5 using **approximate string matching** also popularly known as **fuzzy string matching**.
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
7. We apply the above "extract_symptoms_gpt4" to each textual record of "SYMPTOM_TEXT" and store the extracted list of symptoms in a variable called "extract_symptoms_gpt4".<br>
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/d6e967da-cb41-4930-9772-d1b94050e44c" />

   
### Symptom extraction using Antropic's Claude-Sonnet-3.5 model:
The process of extracting symptoms from the crude textual description of SYMPTOMS_TEXT using Sonet3.5 is similar to the process we used with Sonnet 3.5 models.<br> The Anthropic API key is stored in the working environment as follows:<br>
<img width="500" alt="image" src="https://github.com/user-attachments/assets/4014f7bb-d992-4b7d-80ae-fce35b945b8e" /><br>
I have written a function called **extract_symptoms_claude** which takes the textual descriptions as input available in SYMPTOMS_TEXT and performs the following steps.
1. If the input is not a text or empty, an empty string [] is returned.
2. Then we implement a try-catch block. In the try block,
    - We use the truncate_text to make sure that the text is not too long.
    - We send the API request to  Claude Messages as follows:
      <img width="600" alt="image" src="https://github.com/user-attachments/assets/0850b612-79f4-44dc-980e-a2cbccdfd129" />
    - The parameter * 'content' * is provided with a prompt which is designed as follows:
      <img width="1000" alt="image" src="https://github.com/user-attachments/assets/3788c64f-c126-4305-a328-1ddac627268c" />
3. The raw response provided by the Claude Sonnet 3.5 LLM is of the form:<br>
   <img width="919" alt="image" src="https://github.com/user-attachments/assets/537f92c7-fcee-46da-9652-96158ef4a892" />
4. The list of symptoms is extracted as follows:<br>
   <img width="600" alt="image" src="https://github.com/user-attachments/assets/acbbbcbb-9616-4786-b4f5-45d82a22fdc9" /><br>
   <img width="800" alt="image" src="https://github.com/user-attachments/assets/b2d6522c-d330-4b4e-bcf8-ff870909499a" /><br>
   The function returns the above-extracted list of symptoms.
5. The above-defined **extract_symptoms_claude** function is applied to each textual description record of **SYMPTOM_TEXT** as input and the lists of symptoms extracted are saved in the **Claude_SYMPTOMS** variable as follows:<br>
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/309e14fd-d970-47aa-bd15-6a22cbe9b506" />

#### Comparison of List of Symptoms Extracted by GPT4 and Claude Sonnet 3.5:
<div align = "center">
<img width="1082" alt="image" src="https://github.com/user-attachments/assets/dca95b38-ad24-453e-964d-5edf20943bed" />
</div>

### Standardization of representation of extracted symptoms:
Both LLMs might extract the same symptom in different ways, so there can be multiple representations for the same symptom. For instance, similar symptom representations such as **{'felt nauseated', 'nauseated', 'nausea', 'cont sl nauseated', 'woke nauseated', 'nauseated throughout the day', 'became nauseated', 'nauseate', 'slightly nauseated'}** can only be represented by the symptom name **{'nauseated'}**.<br>
    To group similar representations of the same symptom we use a technique called **approximate string matching** which is also popularly known as **fuzzy string matching**, which is used to find strings that match a pattern approximately (rather than exactly). <br>
<div align = "center">
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/592b2ef5-0027-40d0-b85e-97def4782bbb" />
</div> 
<div align = "center">
<img width="400" alt="image" src="https://github.com/user-attachments/assets/7846d181-67d3-445f-90e0-8ff774b1a05f" />
</div> 
A function named group_similar_symptoms is defined as follows, to group similar representations of the same symptoms by implementing fuzzy string matching with a similarity threshold of 90%.
<div align = "center">
<img width="800" alt="image" src="https://github.com/user-attachments/assets/7077700a-358e-4eea-8d44-5624ca883375" />
</div> 
<div align = "center">
<img width="800" alt="image" src="https://github.com/user-attachments/assets/23c2ab7e-34ed-44f8-9bed-2cec51d06ee8" />
</div> <br>

**Creating a common dictionary from grouped_symptoms_gpt4 and grouped_symptoms_Claude3**
<div align = "center">
<img width="1004" alt="image" src="https://github.com/user-attachments/assets/f99dc5d4-367b-4362-bff3-6911b79d4948" />
<img width="1004" alt="image" src="https://github.com/user-attachments/assets/22b74ea9-89b4-4f8a-8f0a-e85cf773bd4b" />
</div><br>

**This dictionary is manually modified to ensure that various representations of a symptom are correctly mapped to a unified key, accurately representing the symptom and maintaining consistency across different variations. This unified key of a symptom will replace the various representations of a symptom in the list of symptoms generated by GPT4 and Calude Sonnet 3.5 latest LLM.**

**Top 10 Frequently Occurring Symptoms extracted by Chat GPT 4:**
<div align = "center">
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/0af021cf-8354-4fa0-adbf-fc4d2bb4598e" />
</div>

**Top 10 Frequently Occurring Symptoms extracted by  Anthropic Claude 3.5 Sonnet Latest:**
<div align = "center">
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/f758e57e-ae7f-4cd3-ac6c-4aabe6cade8d" />
</div>   
The top 10 symptoms generated by GPT-4 and Claude Sonnet 3.5 are extremely similar.

**Top 10 Frequently Sequence of symptoms that occur due to Hepatitis-B vaccination:**
<div align = "center">     
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/76114974-1a8c-4f5f-8ad0-2e860e5f69a5" />
</div>                                                                                                                     

### Comparison of Post-HepatitisB Vaccination Symptom Sequences generated by GPT-4 & Claude 3.5 Using Kendall’s $\tau$ Coefficient:
Kendall’s Tau ($\tau$) assesses how well the relationship between two variables can be described by a monotonic function. It considers pairs of observations and calculates the proportion of concordant (consistent ranking between two variables) and discordant (opposite ranking) pairs.      

#### **Formula:**
$$
\tau = \frac{C - D}{\frac{1}{2} n (n - 1)}
$$

##### **Where:**
- **C**: The number of **concordant pairs**, i.e., pairs of observations that have the same rank order in both variables.
- **D**: The number of **discordant pairs**, i.e., pairs of observations with opposite rank orders in the variables.
- **n**: The total number of observations.

---

#### **Interpretation of Kendall’s Tau:**
- $\tau = +1$: Perfect agreement between the rankings of the two variables (all pairs are concordant).
- $\tau = -1$: Perfect disagreement between the rankings (all discordant pairs).
- $\tau = 0$: No association between the rankings of the two variables.

---

#### **Kendall Tau Rank Correlation Coefficient Results and Analysis**
##### **Output Sample:**
<div align = "center">  
<img width="800" alt="image" src="https://github.com/user-attachments/assets/310f1c42-27c2-4d90-b865-f482b966fbd3" />
</div>   

##### **Kendall $\tau$ Five Point Summary:**
<div align = "center">  
<img width="500" alt="image" src="https://github.com/user-attachments/assets/106c2fb1-5763-4a7a-bdb8-57f172e602cc" />
</div>   

##### **Kendall $\tau$ Box Plot:**
<div align = "center">  
<img width="600" alt="image" src="https://github.com/user-attachments/assets/4d934791-7617-4bbc-b407-e0494c4d1129" />
</div>

#### Analysis of the Box Plot for Kendall Tau Coefficient

##### Key Observations:
* **Median (Q2)**: The thick orange line inside the box represents the median, which appears to be close to 0.9.
* **Interquartile Range (IQR)**: The box spans approximately from **0.75** to **1.0**, *indicating that 50% of the data falls within this range*.

##### Whiskers:
* The **right whisker** extends slightly beyond **1.0**, suggesting a *high concentration of values near the upper range*.
* The **left whisker** extends toward **0.5-0.6**, showing some *variability in lower values*.

##### Outliers:
* Numerous **outliers** are present on the **left side** (values between **0.0** and **0.5**).
* These **outliers indicate cases where Kendall Tau values deviate significantly**, suggesting a weaker correlation in some instances.

##### **Interpretation:**
- The **distribution is right-skewed**, meaning most Kendall Tau coefficients are **highly positive** (close to 1), indicating **strong agreement in rankings**.
- The **presence of outliers** below **0.5** suggests some cases with **weaker correlations**, possibly due to **variability in extracted symptom sequences**.
- A **high median (close to 0.9)** indicates that, in most cases, the ranking sequences generated by **GPT-4 and Claude 3.5 Sonnet** are **highly correlated**.

#### **Insights:**
- The **high agreement** (upper quartile near 1.0) suggests that **GPT-4 and Claude 3.5 Sonnet** often provide **similar orderings**.
- The **outliers at the lower end** may indicate scenarios where **rankings diverged significantly**, possibly due to **ambiguous symptoms, model biases, or dataset inconsistencies**.


### Longest Common Subsequence (LCS) in Post-Hepatitis B Vaccination Symptom Sequences from GPT-4 & Claude 3.5:
**Longest Common Subsequence (LCS)** is a classic problem in computer science used to find the longest sequence that appears in the same relative order within two given sequences. Unlike substrings, subsequences are not required to occupy consecutive positions within the original sequences.

#### Definition:
Given two sequences, $X$ and $Y$ of the length $n$, the Longest Common Subsequence is the longest sequence that can be derived from both $X$ and $Y$ by deleting some or none of their characters without rearranging the remaining characters.<br>

**Example**:<br>
For sequences $X$ = $”ABCBDAB”$ and $Y$ = $”BDCAB”$, the LCS is:<br>**"BCAB"** or **"BDAB"**, each of length **4**.

#### Formula and Approach:
Let two sequences be defined as follows:  
$X = (x_1 x_2 \cdots x_m)$ and $Y = (y_1 y_2 \cdots y_n)$.  
The prefixes of $X$ are $X_0, X_1, X_2, \dots, X_m$;  
the prefixes of $Y$ are $Y_0, Y_1, Y_2, \dots, Y_n$.  

Let $LCS(X_i, Y_j)$ represent the set of longest common subsequences of prefixes $X_i$ and $Y_j$.  
This set of sequences is given by the following:

$$
LCS(X_i, Y_j) =
\begin{cases} 
\epsilon & \text{if } i = 0 \text{ or } j = 0 \\ 
LCS(X_{i-1}, Y_{j-1}) \mathbin{\hat{}} x_i & \text{if } i, j > 0 \text{ and } x_i = y_j \\ 
\max \{ LCS(X_i, Y_{j-1}), LCS(X_{i-1}, Y_j) \} & \text{if } i, j > 0 \text{ and } x_i \neq y_j 
\end{cases}
$$

To find the **LCS** of $X_i$ and $Y_j$, compare $x_i$ and $y_j$:
- If they are **equal**, then the sequence $LCS(X_{i-1}, Y_{j-1})$ is extended by that element, $x_i$.
- If they are **not equal**, then the longest among the two sequences, $LCS(X_i, Y_{j-1})$ and $LCS(X_{i-1}, Y_j)$, is retained.
- *(If they are the same length but not identical, then both are retained.)*

The **base case**, when either $X_i$ or $Y_i$ is **empty**, is the **empty string**, $\epsilon$.

#### **Output Sample:**
<div align = "center">  
<img width="800" alt="image" src="https://github.com/user-attachments/assets/600228df-f52d-4eda-85bb-e54f99aece18" />
</div>   

##### **Definition: Longest Common Subsequence (LCS) Ratio**

The **Longest Common Subsequence Ratio (LCS Ratio)** is a **normalized similarity measure** that quantifies the similarity between two sequences based on their **Longest Common Subsequence (LCS)**.

It is defined as:

$$
\text{LCS Ratio} = \frac{|LCS(X, Y)|}{\max(|X|, |Y|)}
$$

where:
- \( |LCS(X, Y)| \) is the length of the **Longest Common Subsequence** between sequences \(X\) and \(Y\).
- \( |X| \) and \( |Y| \) are the lengths of the original sequences.
- \( \max(|X|, |Y|) \) ensures the ratio is **normalized** between **0 and 1**.

##### **Interpretation:**
- **LCS Ratio = 1** → The sequences are **identical**.
- **LCS Ratio = 0** → The sequences have **no common subsequence**.
- **Higher LCS Ratio** → Greater similarity between the sequences.

##### **LCS Ratio Five Point Summary:**
<div align = "center">  
<img width="400" alt="image" src="https://github.com/user-attachments/assets/9ec8a518-ebd7-4acb-9fa1-6550a68e0d65"/>
</div>  

##### **LCS Ratio Box Plot:**
<div align = "center">  
<img width="600" alt="image" src="https://github.com/user-attachments/assets/538828f3-d938-463f-a9ae-ff244a3bcf3b" />
</div>

##### **Interpretation of the Box Plot for LCS Ratio**  

###### **1. Distribution Characteristics**  
- The **box plot represents the distribution of Longest Common Subsequence (LCS) Ratios** across different sequences.
- The **x-axis** represents the **LCS Ratio**, ranging from **0 to 1**.

###### **2. Key Observations**  
- **Median (Q2)**:  
  - The **orange line inside the box** represents the **median** (50th percentile), which is around **0.90**.
  - This suggests that for **half of the cases, the LCS Ratio is at least 0.90**, indicating strong similarity in many cases.

- **Interquartile Range (IQR)**:  
  - The **box extends approximately from 0.81 to 1.0**, meaning **50% of the LCS Ratios fall within this range**.
  - This shows that the majority of sequences exhibit a **high degree of similarity**.

- **Whiskers**:  
  - The **right whisker extends to 1.0**, suggesting that several cases achieve a **perfect LCS Ratio**.
  - The **left whisker extends to around 0.5**, indicating some lower-similarity cases.

- **Outliers**:  
  - Several **outliers** are present below **0.5**, with extreme values even **below 0.0814**.
  - These outliers indicate cases where the **LCS Ratio is significantly lower**, meaning **the sequences have minimal commonality**.

##### **3. Interpretation & Insights**  
- The **high median (0.90) and upper quartile near 1.0** suggest that in most cases, the sequences **share a significant portion of common elements**.
- The **presence of outliers** below **0.5** suggests that **some sequences have weak similarity**, possibly due to:
  - Variability in extracted sequences.
  - Model inconsistencies (GPT-4 vs. Claude 3.5).
  - Noise or differences in text preprocessing.
- The **right-skewed distribution** indicates **high similarity in most cases** but with some cases where similarity is low.

### **Dynamic Time Wrapping (DTW) in Post-Hepatitis B Vaccination Symptom Sequences from GPT-4 & Claude 3.5:**
DTW measures the similarity between two sequences that may vary in time or speed. It finds an optimal alignment between the sequences by allowing for stretching and compressing of time (or order in this case). This metric is often used when the exact matching of order is not as important as the overall alignment of patterns between sequences.<br>

#### **Definition:**
Dynamic Time Warping finds an optimal alignment between two sequences by allowing non-linear mapping along the time dimension. In other words, it stretches or compresses
sections of the time series to find the best match between them. The goal of DTW is to minimize the distance between the two sequences, even if they differ in speed or duration.

#### **Mathematical Formulation**

Given two sequences $A = \lbrace a_1, a_2, \dots, a_n \rbrace$ and $B = \lbrace b_1, b_2, \dots, b_m \rbrace$, where $a_i$ and $b_j$ are elements of the sequences $A$ and $B$ respectively, DTW computes the minimum cumulative distance between them.

##### **1. Cost Matrix**
Define a cost matrix $C$ of size $n \times m$,<br>
where $C(i, j)$ represents the cost (or distance) of aligning $a_i$ with $b_j$.<br>
The cost is typically calculated using a distance metric, such as the Euclidean distance:

$$
C(i, j) = \text{distance}(a_i, b_j) = |a_i - b_j|
$$

##### **2. Accumulated Cost Matrix**
Construct an accumulated cost matrix $D$ where each element $D(i, j)$ represents the minimum cumulative cost to align the first $i$ elements of $A$ with the first $j$ elements of $B$:

$$
D(i, j) = C(i, j) + \min 
\begin{cases} 
D(i-1, j) \\ 
D(i, j-1) \\ 
D(i-1, j-1) 
\end{cases}
$$

- Here,
  - $D(i-1, j)$ corresponds to an **insertion**.
  - $D(i, j-1)$ corresponds to a **deletion**.
  - $D(i-1, j-1)$ corresponds to a **match (or diagonal move).**

##### **3. Boundary Conditions**
The boundary conditions are initialized as follows:

$$
D(1,1) = C(1,1)
$$

$$
D(i,1) = D(i-1,1) + C(i,1) \quad \text{for } i = 2, \dots, n
$$

$$
D(1,j) = D(1,j-1) + C(1,j) \quad \text{for } j = 2, \dots, m
$$

##### **4. Optimal Warping Path**
The optimal warping path \( W \) is defined as:

$$
W = \{(i_1, j_1), (i_2, j_2), \dots, (i_L, j_L)\}
$$

where \( W \) is a sequence of matrix indices that minimizes the cumulative distance.  
This path is found by **backtracking** from \( D(n, m) \) to \( D(1,1) \) by following the minimum cost direction at each step.

The overall **DTW distance** is given by:

$$
DTW(A, B) = D(n, m)
$$

#### **Output Sample:**
<div align = "center">  
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/462605a7-77a0-41aa-b58f-3f9d6bd5afc2" />
</div>

#### **DTW Five Point Summary:**
<div align = "center">  
<img width="400" alt="image" src="https://github.com/user-attachments/assets/3633e71a-4949-42de-816a-c255fa623655" />
</div>  

- **Minimum (0.0):** The lowest DTW distance observed in the dataset is **0**, indicating perfect alignment in some cases.

- **1st Quartile (Q1 = 0.0):** 25% of the DTW distances are **0**, meaning a significant proportion of sequences have nearly perfect alignment.

- **Median (Q2 = 0.0):** The **50th percentile (median) is also 0**, indicating that **at least half** of the dataset contains sequences that are **identical or very similar**.

- **3rd Quartile (Q3 = 0.0):** 75% of the DTW distances are **0**, meaning most of the comparisons show little to no difference.

- **Maximum (282.0):** The highest DTW distance recorded is **282**, showing that some sequences have **significant misalignment**.

#### **DTW Five Box Plot:**
<div align = "center">  
<img width="600" alt="image" src="https://github.com/user-attachments/assets/be947137-51bb-4246-9a26-7d4974f3adcb" />
</div>

#### **Box Plot Analysis:**
- Tightly clustered box at 0: Since **Q1**, **Q2**, and **Q3** are all **0**, the **entire interquartile range (IQR) is compressed**, meaning the **majority of DTW values are 0.**

- Presence of Outliers:
  - The **dots extending to the right (above 0)** represent **outliers**, which indicate sequences with **high DTW distances**.
  - These outliers extend **from low values (10-50) to very high values (200+)**, suggesting that a small subset of sequences has **poor alignment**.

- Extreme Outliers:
  - The **maximum value (282)** is far away from the rest of the distribution, indicating that a few sequences exhibit **significant deviations** in structure.

#### **Interpretation & Insights:**

- **Most sequences are highly similar** (as shown by the **median and quartiles being 0**).

- **Some sequences show significant misalignment**, with **DTW distances reaching as high as 282**.

- **Outliers suggest variability in the dataset**, possibly due to:
  - **Differences in sequence length**.
  - **Model inconsistencies**.

 ## **Associative Relationship Analysis of Symptoms:**
We perform an association analysis based on the input, which is the list of symptoms in the available 10,000 records. This allows us to analyze the patterns or relationships of different symptoms that frequently occur together or share similar characteristics. The output will be a list of rules identified based on the data. The symptoms in each rule indicate that the probability of their co-occurrence is high.<br>
The association analysis is performed using **Apriori Algorithm**.

### **Apriori Algorithm**:
The Apriori algorithm is an _association rule mining algorithm_ used primarily to identify frequent itemsets in a large dataset and to derive association rules. It is commonly used in _market basket analysis_ to find product combinations that frequently appear together in transactions. The algorithm is based on the Apriori principle, which states that if an itemset is frequent, all of its subsets must also be frequent.<br>

#### Apriori Algorithm Steps:

##### (a) **Support**: Generate Frequent Symptom Sets:
- Identify all symptom sets in the dataset that have support above a minimum threshold (called frequent symptom sets).
- Use the **Apriori property** to prune symptom sets. If a subset of a symptom set is not frequent, then the symptom set itself cannot be frequent.

##### (b) **Generate Association Rules**:
From the frequent symptom sets, generate association rules that have confidence above a minimum threshold.

##### **Association Rule Formula**:
For a rule $\( A \to B \)$:

---

##### **Support**:
Measures the occurrence of transactions \( A \) and \( B \) together:

$$
Support(A \to B) = \frac{Transactions\ containing\ (A \cup B)}{Total\ transactions}
$$

---

##### **Confidence**:
Measures how often \( B \) occurs in transactions that contain \( A \):

$$
Confidence(A \to B) = \frac{Transactions\ containing\ (A \cup B)}{Transactions\ containing\ A}
$$

---

##### **Lift**:
Compares the confidence of a rule with the expected confidence if \( A \) and \( B \) were independent:

$$
Lift(A \to B) = \frac{Support(A \cup B)}{Support(A) \times Support(B)}
$$

In practice, the Apriori algorithm iteratively increases the size of symptom sets (startingfrom single symptoms). It applies the Apriori property to keep only frequent symptom sets, reducing computation time and complexity.
#### **Key Metrics of Apriori Algorithm**:
##### **Support:**
This metric measures how frequently a symptom appears in the dataset relative to the total number of transactions. A higher support indicates a more significant presence of the symptom in the dataset. Support tells us how often a particular symptom or combination of symptoms appears in all the transactions.<br>
Measure of symptoms A and B occurring together is given by:<br>
<div align="center">

  $$
  S(I_A) = \frac{Occ(I_A)}{TotalTransactions}
  $$
  
  where \( S($I_A$) \) represents the **support of item A**,  
  \( $I_A$ \) is the **item A**, and  
  \( Occ($I_A$) \) is the **number of occurrences** of item \( A \).

</div>

**Top 15 antecedence(A symptoms) and consequents(B symptoms) occuring together sorted by support in descending:**
<div align = "center"> 
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/dd79b27d-202a-417f-a140-defa455ee121" />
</div>
<br>
Interpretation:<br>
From the output obtained below we find that individual syptoms such as "nauseated", "lightheadedness", "chilling joint pains" occur most frequently and symptom sequences such as "chilling joint pains, coughing", "low grade, chilling joint pains" and "low grade, coughing, chilling joint pains, upper respiratory congestion, lightheadedness" occur most frequently.
<div align = "center"> 
<img width="800" alt="image" src="https://github.com/user-attachments/assets/cebdf079-7b09-4929-b3d8-579ac048c3b2" />
</div>

#### **Confidence:**
The confidence metric identifies the probability of symptoms or sets of symptoms occurring in the itemsets together. For example, if there are two symtoms in a record, the existence of one symptom is assumed to lead to the other. The first item or itemset is the **antecedent**, and the second is the **consequent**. *The confidence is thus defined as the ratio of the number of transactions having both the antecedent and the consequent, to the number of transactions only having the antecedent*. This scenario is represented as:
<div align="center">

   $$
   C(A, B) = \frac{Occ(A \cap B)}{Occ(A)}
   $$

   where \( C(A,B) \) is the **confidence** that \( A \) leads to \( B \),<br>
   \( B \) is the **consequent**, and <br>
   \( A \) is the **antecedent**.

</div>

**Top 15 antecedence(A symptoms) and consequents(B symptoms) occuring together sorted by confidence in descending:**
<div align = "center"> 
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/35b66dd0-5b99-4c1c-a6b9-cddfd40eb5dd" />
</div>
<br>
Interpretation:<br>
From the output obtained above, we notice that, the confience amongst them is 1.0, so there is a 100% change that the antecedence symptoms will certainly lead to consequents. That is, say for instance, if the set of symptoms "muscle weakness, nauseated, nv diarrhea" occured then it is certain that the symptoms "vomit, severe dizziness" has also occured.

#### **Lift:**
Lift is the factor with which the likelihood of symptom or list of symptoms A leading to symptom or list of symptoms B is higher than the likelihood of A. This metric quantifies the strength of association between A and B. It can help indicate whether there is a real relationship between the symptoms or lists of symptoms in a recordt or are they being grouped together by coincidence.
<br>
<div align="center">

   $$
   L(A, B) = \frac{C(A, B)}{S(B)}
   $$

   where \( L(A,B) \) is the **lift** for item \( A \) leading to item \( B \),  
   \( C(A,B) \) is the **confidence** that item \( A \) leads to item \( B \),  
   \( S(B) \) is the **support** for item \( B \).

</div>

**Top 15 antecedence(A symptoms) and consequents(B symptoms) occuring together sorted by confidence in descending:**
<div align = "center"> 
<img width="1200" alt="image" src="https://github.com/user-attachments/assets/db414e09-0cb1-4f86-8bab-daceed94d7d5" />
</div>
<br>
Interpretation:<br>
From the output obtained above, we notice that, the lift for antecedence(A symptoms) and consequents(B symptoms) pairs are significantly high.<br> For instance, consider the pair of sets of symptoms "severe dizziness, nv diarrhea" and "vomit, muscle weakness, nauseated" which have the highest lift of 19.285714, indicate that the probility of these sets of symptoms occuring together is 19.29 times more than them occuring individually.


#### Exploring the relationships amongst Support, Confidence and Lift:

<div align = "center"> 
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/7a4b7725-4169-4f18-b7d9-b4ff3527f139" />
</div>

##### **Interpretation of the Scatter Plot**

The scatter plot visualizes the association rules generated using the **Apriori algorithm** on symptoms **post Hepatitis B vaccination** based on three key measures:  
- **Support (X-axis)**: Frequency of the symptom combinations occuring together.
- **Confidence (Y-axis)**: How likely a symptom (consequent) appears given another symptom (antecedent).  
- **Lift (Color Intensity)**: How much more likely symptoms co-occur together compared to random chance.

###### **Key Observations:**

1. Most rules have low support (< 0.1)
  - This suggests that most symptom combinations are relatively rare in the dataset.  
  - A few high-support rules (~0.18) indicate some **common symptom associations** after Hepatitis B vaccination.

2. Higher Confidence for Low-Support Rules
  - Many rules with low support have **high confidence (~1.0)**, meaning that when these symptoms occur, they are highly predictive of each other.
  - However, high confidence **alone does not mean strong association** (e.g., a rare symptom may always co-occur with another, inflating confidence).

3. Lift Highlights Strong Associations
  - The **color gradient (Lift value)** shows stronger associations:  
    - **Darker (low lift ~2.5)**: Weak correlations (symptoms occur at expected random rates).  
    - **Brighter (high lift ~18.0)**: Strongly associated symptoms that occur **far more frequently** together than expected.
  - The **high-lift rules (yellow-green dots)** often appear at low support, suggesting **rare but highly dependent symptoms**.

###### Implications for Hepatitis B Vaccination Symptoms
  - The high **Lift** (green/yellow points) suggests **some symptoms are significantly co-occurring**, which might indicate **side effects clusters** that require medical attention.
  - **Rules with high confidence & low support** could indicate **rare but strong symptom dependencies**.
  - **High-support & high-lift** rules suggest **common symptom pairs** that are much more frequent than chance, which could be useful for **clinical assessments**.

###### **Conclusion**
  - This analysis helps identify **strong symptom associations** that may need further investigation.
  - High **lift rules** could be **clinically relevant** for recognizing **frequent symptom clusters post-vaccination**.
  - **Low-support, high-lift** rules might indicate **rare but significant side effects** that warrant additional research.

<br>

## **Association Rules Network Graph for Post Hepatitis B Vaccination Symptoms**:
The **Association Rules Network Graph** visualizes the relationships between symptoms experienced after the **Hepatitis B vaccination**, based on association rule mining. Each **node** represents a symptom or a group of symptoms, and the **edges (arrows)** represent association rules between them.<br>

# **Association Rules Network Graph for Post Hepatitis B Vaccination Symptoms**
The **Association Rules Network Graph** visualizes the relationships between symptoms experienced after the **Hepatitis B vaccination**, based on association rule mining. Each **node** represents a symptom or a group of symptoms, and the **edges (arrows)** represent association rules between them.

# **Association Rules Network Graph for Post Hepatitis B Vaccination Symptoms**

The **Association Rules Network Graph** visualizes the relationships between symptoms experienced after the **Hepatitis B vaccination**, based on association rule mining. Each **node** represents a symptom or a group of symptoms, and the **edges (arrows)** represent association rules between them.

## 🔍 **Click the Image to View in Full Size**
# **Association Rules Network Graph for Post Hepatitis B Vaccination Symptoms**

The **Association Rules Network Graph** visualizes the relationships between symptoms experienced after the **Hepatitis B vaccination**, based on association rule mining. Each **node** represents a symptom or a group of symptoms, and the **edges (arrows)** represent association rules between them.

## 🔍 **Click the Image to View in Full Size**
[![Association Rules Network Graph](https://raw.githubusercontent.com/your-username/your-repo/main/path/to/image.png)](https://raw.githubusercontent.com/your-username/your-repo/main/path/to/image.png)

