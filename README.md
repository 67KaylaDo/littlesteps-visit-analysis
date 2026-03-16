# LittleSteps Healthcare Visit Analysis

## 1. Project Overview

This project analyzes nurse visit operations for **LittleSteps**, an at-home healthcare provider. The objective is to identify patterns in **patient visit duration and nurse travel time** to uncover opportunities for operational improvement.

The analysis explores how visit duration varies across **service types, geographic locations, and clinical contexts** extracted from nurse notes.

Key goals include:

- Understanding visit duration patterns across services
- Investigating geographic variation in visit times
- Estimating travel time between consecutive nurse visits
- Extracting insights from nurse notes using NLP classification
- Identifying potential operational improvements for scheduling and routing

The analysis was conducted using **Python, statistical analysis, and data visualization techniques**.

---

## 2. Analytical Approach

The project follows a structured **data analytics workflow** including data cleaning, feature engineering, statistical analysis, and visualization.

### Data Preparation

The dataset was cleaned and standardized to ensure reliable analysis.

Key preprocessing steps included:

- Loading and exploring the dataset
- Handling missing values
- Removing duplicate records
- Converting timestamp variables to datetime format
- Standardizing categorical variables
- Preparing nurse notes for NLP classification

### Feature Engineering

Two operational metrics were created to support analysis.

#### Visit Duration

`visit_duration_minutes` was calculated as the difference between visit start and visit end timestamps.

#### Travel Duration

`travel_duration_minutes` was estimated as the time gap between **consecutive visits performed by the same nurse**.

To improve accuracy:

- Negative travel durations were removed
- Travel durations were restricted to visits occurring **on the same day**

---

### Nurse Notes Classification

Nurse notes were analyzed using **zero-shot text classification** with the Hugging Face model:

`facebook/bart-large-mnli`

The classifier assigns one or more clinical labels to each note, including:

- follow-up needed
- review required
- wound care
- medication administration
- monitoring or assessment
- mobility or rehabilitation
- urgent or critical care
- vital signs check
- pain management
- stable condition
- patient condition update

This allows visit durations to be analyzed in relation to **clinical context**.

---

### Statistical Analysis

Operational patterns were evaluated using:

- descriptive statistics
- group comparisons
- non-parametric hypothesis testing

Because visit duration distributions were **skewed and non-normal**, non-parametric tests were used.

Statistical tests included:

- **Shapiro-Wilk test** to assess normality
- **Kruskal-Wallis test** to compare visit durations across locations
- **Dunn post-hoc test** for pairwise comparisons between locations

---

### Data Visualization

Several visualizations were used to explore patterns in the data, including:

- Histograms of visit duration
- Bar charts comparing service types
- Boxplots showing geographic variation
- Nurse travel time comparisons
- Nurse note category analysis

These visualizations help highlight operational patterns and potential inefficiencies.

---

## 3. Repository Structure

\`\`\`
littlesteps-visit-analysis/

data/
    visits.csv

notebooks/
    littlesteps_analysis.ipynb

requirements.txt
README.md
\`\`\`

---

## 4. Environment Setup

### Clone the Repository

\`\`\`bash
git clone https://github.com/67KaylaDo/littlesteps-visit-analysis.git
cd littlesteps-visit-analysis
\`\`\`

### Install Dependencies

\`\`\`bash
pip install -r requirements.txt
\`\`\`

### Run the Notebook

\`\`\`bash
jupyter notebook notebooks/littlesteps_analysis.ipynb
\`\`\`

---

## 5. Key Findings

### Service Type Differences

Visit duration varies significantly across service types.

- **Wound care visits** have the longest average duration (~101 minutes)
- **Medication administration visits** average approximately 90 minutes
- **Physical therapy and general check-ups** have shorter durations (~74–76 minutes)

These findings suggest that service complexity plays a major role in visit duration.

---

### Geographic Variation

Visit duration differs across geographic service areas.

- **North region** shows the longest average visit duration (~108 minutes)
- **South region** follows (~91 minutes)
- **East and West regions** show shorter average visit durations (~72 minutes)

Statistical testing confirmed that **visit duration distributions differ significantly across locations**.

Further analysis (such as post-hoc pairwise comparisons) helps identify **which specific locations differ from each other**.

---

### Nurse Travel Patterns

Estimated travel time between visits varies across nurses.

This suggests potential opportunities to improve:

- geographic clustering of patient visits
- nurse routing efficiency
- workload balancing

---

### Insights from Nurse Notes

Clinical information extracted from nurse notes reveals that:

- **Wound care related visits** tend to have longer durations
- **Routine monitoring visits** are typically shorter
- **Follow-up and review related visits** show moderate durations

These insights demonstrate that **clinical context is an important predictor of visit length**.

---

## 6. Operational Recommendations

Based on the analysis, several improvements could increase operational efficiency.

### Optimize Nurse Routing

Cluster patient visits geographically to reduce travel time and improve scheduling efficiency.

### Adjust Scheduling Based on Service Complexity

Allocate longer time slots for services such as wound care or complex treatments.

### Use Clinical Signals for Scheduling

Information extracted from nurse notes could help **predict visit duration more accurately**.

### Monitor Extreme Visit Durations

Outlier visits should be reviewed to identify:

- documentation errors
- operational delays
- unusually complex cases

---

## 7. Assumptions and Challenges

Several assumptions were required due to dataset limitations.

### Travel Duration Estimation

Travel time was not directly recorded.  
It was approximated using the **time gap between consecutive visits for the same nurse**.

This estimate may include:

- travel time
- scheduling gaps
- administrative work

---

### Non-Normal Data Distribution

Visit duration data was **skewed and contained extreme values**, therefore **non-parametric statistical tests** were used instead of ANOVA.

---

### Limited Contextual Variables

Additional information such as:

- patient severity
- exact travel distance
- nurse scheduling constraints

was not available in the dataset.

Including these variables could improve future analysis.

---

## 8. Technologies Used

Python  
Pandas  
NumPy  
Matplotlib  
Seaborn  
SciPy  
scikit-posthocs  
Hugging Face Transformers  
Jupyter Notebook

---

## Author

**Minh Do (Kayla)**

LittleSteps Healthcare Visit Analysis Project

