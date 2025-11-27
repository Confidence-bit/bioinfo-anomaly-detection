# bioinfo-anomaly-detection
Bioinformatics Data Visualization and Anomaly Detection Project

**Project Overview**

This mini-project analyzes real gene expression data and applies cybersecurity-inspired anomaly detection techniques to identify unusual patterns that may indicate:

•	Data corruption

•	Pipeline or sequencing errors

•	Sample contamination

•	Intentional manipulation or unauthorized modification

It demonstrates the intersection of bioinformatics, data science, machine learning and cyberbiosecurity, showing how statistical and machine learning tools can help maintain the integrity and reliability of biological datasets.

**Introduction**

Modern bioinformatics workflows rely on large-scale sequencing and gene expression data. However, these datasets are vulnerable to:

•	Experimental noise

•	Pipeline errors

•	Software bugs

•	Malicious tampering

•	Data corruption during storage or transfer

This project demonstrates how cybersecurity anomaly-detection methods particularly Isolation Forest can be applied to biological data to detect unusual patterns that may signal corruption or intrusion.

Using a publicly available dataset, the project performs:

•	Data cleaning

•	Standardization

•	Unsupervised anomaly detection

•	PCA visualization

•	Heatmaps and hierarchical clustering

The goal is to bridge bioinformatics and cyberbiosecurity, illustrating how computational tools can protect the integrity of biological data.

**Objectives**

1. Load, clean, and preprocess a real gene expression dataset
   
2. Perform statistical and exploratory data analysis (EDA)
   
3. Apply Isolation Forest to detect abnormal patterns
   
4. Visualize structure and anomalies using:
   
•	Heatmaps

•	PCA plots

5. Interpret anomalies from a cyberbiosecurity perspective
   
6. Demonstrate how anomalies may indicate:
   
•	Pipeline errors

•	Sample contamination

•	Unauthorized manipulation

•	System compromise

**Project Structure**

bioinfo-anomaly-detection/
│
├── Bioinformatics_Data_Visualization_and_Anomaly_Detection.ipynb

├── GSE282062_Original_read_count.xlsx

└── README.md

**Dataset Overview**

**Source**: Public gene expression dataset

**Format**: Excel (.xlsx)

**Genes**: 58,884

**Columns**:

•	Geneid — Ensembl gene identifiers

•	pCDH — control

•	CDK6 — wild-type

•	CDK6_D224Y — mutant

**Notes**:

•	No missing values

•	Integer expression counts

•	Suitable for direct processing

**Methods and Results**

**1. Data Cleaning**

•	Set Geneid as index

•	Converted all expression columns to numeric

•	Checked for missing values (none found)

**Outcome:**

Dataset was clean and ready for statistical and machine learning analysis.

**2. Standardization**

Expression values were standardized using:

scaler = StandardScaler()

X_scaled = scaler.fit_transform(df.T).T

**Why?:**

Standardization ensures each gene contributes equally to the anomaly detection model.

**Outcome:**

All samples (pCDH, CDK6, CDK6_D224Y) were placed on a comparable scale.

**3. Anomaly Detection (Isolation Forest)**
   
Model:

iso = IsolationForest(contamination=0.03, random_state=42)

labels = iso.fit_predict(df_scaled.T)

**Anomaly scores:**
Anomaly Scores: [1 1 1]

**Interpretation**
•	1 = normal

•	–1 = anomaly

Since all three samples received 1, the model detected no anomalies.

**Why this happened:**

•	With only three samples, and

•	Each sample behaving consistently across most genes

The Isolation Forest algorithm had no statistical reason to isolate any sample as abnormal.

**Cyberbiosecurity meaning**

The absence of anomalies suggests:

•	No detectable signs of data corruption

•	No major deviations that resemble tampering

•	No pipeline irregularities detectable by this model

This is also valuable it demonstrates stability and integrity in the dataset.

**4. Visualization**

**PCA Plot**

PCA reduces the entire gene expression matrix into two principal components.

**Observed Result:**

•	All three samples clustered closely, with no strong outliers

•	This visually supports the anomaly score result

**Interpretation:**

The samples show a high degree of similarity in global expression structure.

**Heatmap and Clustering**

**Using:**

sns.clustermap(df_scaled.sample(300, replace=True))

**Observed Result:**

•	The heatmap showed gene clusters and natural patterns

•	No sample-specific cluster separated dramatically from others

•	No extreme expression shifts were visually observed

**Interpretation:**

The heatmap supports the PCA and Isolation Forest findings, the samples form a stable group with no visual anomalies.

**Summary of Findings**

**Method	Result**

**Isolation Forest:**	No anomalies detected

**PCA:** No outlier samples

**Heatmap:**	No visually abnormal clusters

**What this means**

The gene expression dataset appears:

•	Consistent

•	Stable

•	Free of detectable corruption or unexpected variation

**From a cyberbiosecurity perspective, this means:**

•	No signs of unauthorized data manipulation

•	No detectable pipeline errors

•	No suspicious deviations across samples


This project shows how combining bioinformatics + cybersecurity strengthens the protection of biological data, demonstrating how machine learning can be applied to verify data integrity.


**Technologies Used**

•	Python 3

•	Pandas

•	NumPy

•	Scikit-learn (IsolationForest, PCA)

•	Matplotlib, Seaborn

•	Plotly Express

•	Jupyter Notebook

**How to Run This Project**

1. Clone the repository
git clone https://github.com/Confidence-bit/bioinfo-anomaly-detection.git

2. Install required libraries
pip install pandas numpy seaborn matplotlib scikit-learn plotly

3. Open the Jupyter Notebook
jupyter notebook

4. Run all cells
This will reproduce all analyses, plots, and anomaly detection results.

**Author**

**Orji Confidence Ogechi**



