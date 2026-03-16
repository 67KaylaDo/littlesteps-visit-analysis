# LittleSteps Healthcare Visit Analysis

## 1. Project Overview

This project analyzes nurse visit operations for **LittleSteps**, an at-home healthcare provider.  
The objective of this analysis is to identify patterns in **patient visit durations and nurse travel times** in order to improve operational efficiency.

The analysis focuses on:

- Understanding visit duration across service types
- Investigating geographic variation in visit times
- Estimating travel time between visits
- Extracting insights from nurse notes
- Identifying potential operational improvements

The analysis was conducted using **Python, statistical testing, and data visualization techniques**.

---

## 2. Analytical Approach

The project follows a structured data analytics workflow.

### Data Preparation

The dataset was first cleaned and standardized to ensure reliable analysis.

Key steps included:

- Loading and exploring the dataset
- Handling missing values
- Removing duplicate records
- Standardizing categorical variables
- Converting timestamp fields
- Extracting information from nurse notes

### Feature Engineering

Two key operational metrics were created:

**visit_duration_minutes**

Calculated as the difference between visit start and end times.

**travel_duration_minutes**

Estimated as the time gap between consecutive visits performed by the same nurse.

To improve accuracy:

- Negative travel durations were removed
- Travel durations were restricted to visits occurring on the same day

### Statistical Analysis

The analysis evaluates operational patterns using:

- Descriptive statistics
- Group comparisons
- Statistical hypothesis testing

Statistical tests used:

- **Shapiro-Wilk test** to check normality
- **Kruskal-Wallis test** to compare visit duration across locations
- **Dunn post-hoc test** for pairwise comparisons

### Data Visualization

Visualizations created include:

- Histograms of visit duration
- Bar charts for service type comparison
- Boxplots for location comparison
- Nurse travel time comparisons
- Nurse note category analysis

---

## 3. Repository Structure

littlesteps-visit-analysis/

data/  
    visits.csv  

notebooks/  
    littlesteps_analysis.ipynb  

requirements.txt  
README.md  

---

## 4. Environment Setup

### Clone the repository

git clone https://github.com/67KaylaDo/littlesteps-visit-analysis.git  
cd littlesteps-visit-analysis

### Install dependencies

pip install -r requirements.txt

### Run the notebook

jupyter notebook notebooks/littlesteps_analysis.ipynb

---

## 5. Key Findings

### Service Type Differences

Visit duration varies significantly across service types.

- **Wound Care** visits require the longest time (~101 minutes)
- **Medication Administration** visits average ~90 minutes
- **Physical Therapy and General Check-ups** require shorter durations (~74–76 minutes)

### Geographic Variation

Visit duration differs across locations.

- **North region** shows the longest average visit duration (~108 minutes)
- **South region** follows (~91 minutes)
- **East and West regions** show shorter visit durations (~72 minutes)

Statistical testing confirmed that visit duration distributions differ across locations.

### Nurse Travel Patterns

Travel time between visits varies significantly across nurses.

This suggests potential opportunities to improve:

- geographic clustering of patient visits
- nurse routing efficiency
- scheduling balance

### Nurse Notes Insights

Clinical context extracted from nurse notes reveals that:

- wound care related visits are associated with longer visit durations
- routine monitoring visits are shorter

These insights could be used to improve scheduling predictions.

---

## 6. Operational Recommendations

Based on the analysis, several improvements could increase operational efficiency.

**Optimize Nurse Routing**

Cluster patient visits geographically to reduce travel time.

**Adjust Scheduling Based on Service Complexity**

Allocate longer time slots for complex services such as wound care.

**Use Clinical Signals for Scheduling**

Information extracted from nurse notes may help predict visit complexity.

**Monitor Extreme Visit Durations**

Extremely long visits should be reviewed to identify operational inefficiencies.

---

## 7. Assumptions and Challenges

Several assumptions were required due to dataset limitations.

### Travel Duration Estimation

Travel time was not directly recorded in the dataset.  
It was approximated using the time gap between consecutive visits for the same nurse.

This value may include:

- travel time
- scheduling gaps
- administrative activities

### Non-Normal Data Distribution

Visit duration data was skewed with extreme outliers, therefore **non-parametric statistical tests** were used instead of ANOVA.

### Limited Contextual Variables

Information such as patient severity, geographic distance, or detailed scheduling data was not available.

---

## 8. Technologies Used

Python  
Pandas  
NumPy  
Matplotlib  
Seaborn  
SciPy  
scikit-posthocs  
Jupyter Notebook

---

## Author

Tuệ Minh Đỗ  
LittleSteps Healthcare Visit Analysis Project
