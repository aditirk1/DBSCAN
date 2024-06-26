# DBSCAN
Implementation of an ML algorithm, DBSCAN, on metabolome abundance data in treatment naive GBM patients.

Description of the data:
Proteogenomic and metabolomic characterization of human glioblastoma. Whole genome or whole exome sequencing of 99 samples. Generated by CPTAC. 

As seen in "Proteogenomic and metabolomic characterization of human glioblastoma. Cancer cell" by Wang LB, Karpova A, Gritsenko MA, et al. (doi:https://doi.org/10.1016/j.ccell.2021.01.006),
Metabolite identifications and data processing were conducted as previously detailed (Webb-Robertson et al., 2014). GC-MS raw data files were processed using Metabolite Detector software v2.0.6 beta (Hiller et al., 2009). Retention indices (RI) of detected metabolites were calculated based on the analysis of the FAMEs mixture, followed by their chromatographic alignment across all analyses after deconvolution. Metabolites were identified by matching experimental spectra to an augmented version of the Agilent Fiehn Metabolomics Retention Time Locked (RTL) Library (Kind et al., 2009), containing spectra and validated retention indices. All metabolite identifications were manually validated. The NIST 08 GC-MS library was also used to cross validate the spectral matching scores obtained using the Agilent library and to provide identifications for metabolites that were initially unidentified. The three most abundant fragment ions in the spectra of each identified metabolite were automatically determined by Metabolite Detector, and their summed abundances were integrated across the GC elution profile. A matrix of identified metabolites, unidentified metabolite features, and their corresponding abundances for each sample in the batch were exported for statistics. 

# Executive Summary
The project aimed to perform metabolomic characterisation and analysis of Glioblastoma. Glioblastoma is a highly aggressive brain tumor with complex metabolic dysregulation, making it crucial to understand the underlying metabolomic patterns to gain prospective therapeutic insights. 

High dimensional metabolic data was preprocessed, and clustered using the DBSCAN algorithm to describe metabolic abnormalities. Through principal component analysis (PCA) and differential expression analysis, we aimed to uncover subtypes and compare the data obtained from 99 GBM patients' whole genome generated by CPTAC.

Cancer cells often exhibit altered metabolic pathways to support rapid growth and proliferation. The analysis was performed on various attributes:
- Comparison of lactic acid, pyruvate, glucose levels
- Comparison of homocysteine and creatinine levels 
- Comparison of galactitol and glucose levels 
- Clustering based on age and BMI
 

The project utilized Python libraries such as pandas, NumPy, and matplotlib to preprocess and visualize metabolomic data. The knee point concept was used to determine the optimal value of the epsilon parameter. 

Visualizations such as heatmaps and pathway maps elucidated disrupted metabolic pathways in GBM, providing critical insights into potential targets and biomarkers. This project highlights Python as a powerful tool for bioinformatics and metabolomics research, enabling comprehensive exploration and comparison of metabolite expression patterns in Glioblastoma.


# Introduction
Density-Based Spatial Clustering of Applications with Noise (DBSCAN) is a machine learning 
algorithm for density-based clustering, first introduced in 1996 by Martin Ester and Hans Peter. 
It is a widely used unsupervised learning method for model construction and machine learning 
algorithms in various fields encompassing biological data analysis. DBSCAN is useful in 
identifying high-density clusters within data, separating them from low-density regions, and is 
suitable for arbitrarily shaped clusters.
DBSCAN is found to be more advantageous than k-means clustering as it does not require
the number of clusters to be specified beforehand, and it efficiently handles and identifies noise 
points. This makes it well-suited for very large datasets. DBSCAN's versatility has led to its 
application across various domains, including image processing, geospatial data analysis, data 
mining, astronomy, and anomaly detection.
Glioblastoma (GBM) is an exceptionally aggressive and malignant type of brain tumor. It is a 
grade 4 glioma brain tumor arising from brain cells called glial cells. A brain tumor's grade 
refers to how likely the tumor is to grow and spread. Grade 4 is the most aggressive and serious 
type of tumor. Symptoms of GBM include headaches, seizures, changes in behavior, and motor 
weakness. Understanding the metabolic alterations in treatment-naive GBM is crucial for 
developing targeted therapies and increased progression-free survival.

## 1.1 About the Domain

DBSCAN is an unsupervised machine learning algorithm that uses two parameters: epsilon (ε), 
the maximum radius of the neighborhood around a point, and MinPts, the minimum number of 
points required to form a dense region or cluster. Its applications are far-reaching.

1. Geospatial Data Analysis: Identifying densely populated areas, urban growth patterns, 
and hotspots for infrastructure development; detecting clusters of pollution, wildlife 
populations, or natural resources.
2. Image Processing: Segmenting images based on pixel density to identify objects or 
regions of interest; analyzing clusters in MRI or CT scans to detect anomalies such as 
tumors or lesions.
3. Market Research: Grouping customers based on purchasing behavior, preferences, or 
demographic information for targeted marketing; identifying trends and patterns in sales 
data to optimize product placement and inventory management.

## 1.2 Scope and Objectives 
### The Problem
GBM is an aggressive brain tumor with a high degree of metabolic dysregulation. Traditional 
clustering algorithms, such as k-means, are not optimal for this type of data due to their 
requirement for predefined cluster numbers and sensitivity to noise. There is a need for advanced 
clustering methods that can handle the complexity and high dimensionality of metabolomic data 
from GBM patients.
### Objectives
The primary objective of this study is to utilize DBSCAN for clustering based on the density of 
data points, identifying noise and outliers, and filtering out abnormalities in the dataset. This 
approach helps in understanding and analyzing the patterns and structures present in the data.
- Implement DBSCAN with optimized parameters using the knee point method for 
clustering.
- Analyze GBM metabolomic profiles using PCA and identify subclasses based on
visualized patterns.
- Conduct analyses on various attributes, including:
     - Clustering based on the abundance of lactic acid, pyruvate, and glucose.
     - Clustering based on the abundance of homocysteine and creatinine.
     - Clustering based on the abundance of galactitol and glucose.
     - Clustering based on age and BMI.
### Attributes
GBM cells, like most cancer cells, exhibit the Warburg effect, producing energy through 
glycolysis followed by lactic acid fermentation, even in the presence of oxygen. This metabolic 
shift can distinguish cancer patients from healthy individuals by analyzing their metabolic 
profiles. The selected attributes are vital in energy-producing metabolic pathways.
- Lactic Acid and Pyruvate Levels: Comparing these levels provides an understating 
about the shift towards glycolysis.
- Homocysteine Levels: As an intermediate in methionine metabolism, homocysteine is 
associated with oxidative stress.
- Creatinine Levels: Perturbations in creatinine levels offer insights into overall 
metabolic health.
- Galactitol Levels: Accumulation of galactitol indicates dysregulation in galactose 
metabolism.
- Age and BMI: Age can influence GBM progression, and clustering based on age can 
help identify age-specific metabolic patterns. BMI may also correlate with metabolic 
changes in GBM.


# Detailed Design and Architecture
## 2.1 Proposed System Architecture
The proposed system architecture is designed to detect unique metabolic subgroups in Glioblastoma Multiforme (GBM) patients (treatment-naive) by grouping metabolite abundance profiles using the DBSCAN algorithm. The system is intended to take high-dimensional metabolomic data, preprocess it, and perform clustering to identify underlying metabolic abnormalities and possible subgroups in GBM. The system architecture's main components include data collection, preprocessing, clustering algorithm application, visualization and analysis.
![Screenshot 2024-06-14 225247](https://github.com/aditirk1/DBSCAN/assets/132145522/f62f8f91-255a-471b-9b48-bae51725e8d9)


## 2.2 Design Architecture

Python is a multi-paradigm language that supports various programming approaches, including object-oriented, procedural, and functional styles. It is an interpreted language, meaning that the code is executed directly without being compiled into machine code first. This interpreted nature makes Python highly interactive, allowing developers to test and experiment with code in real-time. In this code, the architecture follows a modular approach.
The Data Input Module encapsulates functionality to handle input data files, ensuring compatibility across various formats and detecting potential errors or inconsistencies during file validation. It transforms input data into a structured format, typically a pandas DataFrame, to facilitate seamless processing. The Exploratory Data Analysis Module provides tools for computing descriptive statistics, generating correlation matrices, and visualizing data through heatmaps and scatter plots. This allows in uncovering underlying patterns and potential clusters within the metabolomic data. The Data Normalization and Scaling Module is used in preprocessing by standardizing feature scales using techniques like Min-Max scaling or standardization, ensuring uniformity across all features. The Dimensionality Reduction Module employs algorithms such as Principal Component Analysis (PCA) to reduce the dimensionality of high-dimensional data while preserving variance, thus enhancing visualization and facilitating effective clustering. The Clustering Module implements the DBSCAN algorithm for identifying clusters based on optimized parameters, determined using techniques like the KneeLocator algorithm for epsilon selection. Lastly, the Visualization enables the visualization of clustering results, creating scatter plots to highlight different clusters and distinguish between noise and cluster points, thus providing a visual aid for identifying subgroups.

## 2.3 Methodology

1. __Data Acquisition and Preprocessing__

The first step was to load the metabolomic data from a CSV file using pandas for efficient data handling and manipulation. Data integrity and completeness must be maintained by handling missing values through mean imputation. Finally, the dataset was transposed to align metabolite features as columns and patient samples as rows, optimizing the data structure for subsequent analysis.

2. __Merging necessary files__

Clinical patient data consisting of various categorical and numeric data (which were the features used in the analysis) was merged with metabolome abundance data based on the column “Patient_ID”. This ensured that both data were retained, with missing data being depicted as “NaN”. This step was performed for other analysis apart from the PCA derived data.

3. __Exploratory Data Analysis (EDA)__

Following the loading of required data, descriptive statistics using pandas to summarize the distribution of metabolite abundances across samples, including metrics such as mean, standard deviation, and quartiles, was performed. Utilized seaborn and matplotlib for generating correlation matrices and visualizing interrelationships among metabolites using heatmaps and scatter plots. These visualizations can determine potential metabolic patterns and outliers.

4. __Data Normalization and Scaling__
   
Normalization of metabolite abundances using MinMaxScaler from scikit-learn was performed to standardize data across a uniform range, preparing it for downstream analysis. This step ensures that all features contribute equally to algorithms and prevents biases due to varying scales.

5. __Dimensionality Reduction__
    
Implementation of Principal Component Analysis (PCA) from scikit-learn was done to reduce the dimensionality of the dataset while retaining essential variance. For the rest of the analysis, PCA was not performed as there were two dimensions only, when comparing two features in the data. Project the data into a lower-dimensional space using PCA, facilitating efficient visualization and clustering. This simplifies the interpretation of complex metabolomic profiles.

6. __Clustering Analysis__
    
Utilized the Density-Based Spatial Clustering of Applications with Noise (DBSCAN) algorithm from scikit-learn for clustering analysis. Optimized parameters such as epsilon and minimum samples using techniques like KneeLocator for enhanced clustering accuracy. Distinct metabolic subgroups within the data based on clustering results were identified, distinguishing noise from cluster points for comprehensive analysis.

7. __Visualization and Interpretation__
    
Visualized clustering outcomes using matplotlib and seaborn to create scatter plots and color-coded clusters. This visualization approach helps in effectively interpreting metabolic subgroups and highlighting important differences between clusters. 

# Implementation

## 3.1 About the code
DBSCAN was implemented using Python3 on the Jupyter Notebook. The code structure is as 
follows.
__Load Data file and Read the data__
Data was downloaded from cBioPortal for Cancer Genomics. The file consisted of various data 
including protein expression, mRNA expression, methylation, copy number variations and so 
on. We stuck to metabolome abundance data. The file was converted from .txt to .csv and loaded 
into python using the pandas library’s read_csv function as a dataframe.
```ruby
import pandas as pd
data = pd.read_csv('metabolome.csv', index_col=0)
```
__Dataset Structure__
The data consists of metabolite abundance data of 75 patients affected with glioblastoma 
multiforme (GBM) before any treatment regimes. There are a total of 134 metabolites, with 
some of them being labeled as “Unknown” by the authors. Columns are patient IDs and rows 
are metabolite names. The dataset was transposed using python by the code ```data.T``` in order to 
perform further deductions and conversions (scaling and dimensional reduction).

__Data Visualization__
* Utilized seaborn (```import seaborn as sns```) and matplotlib (```import matplotlib.pyplot as plt```) 
for data visualization.
* Created a heatmap using ```sns.heatmap()``` to visualize correlations between expression of 
metabolites.

__Data Scaling and Dimensionality Reduction__
* Employed ```StandardScaler()``` and ```MinMaxScaler()``` from scikit-learn for data scaling.
* Performed Principal Component Analysis (PCA) using ```PCA()``` from scikit-learn.
* Created a new DataFrame df with dimensionality-reduced data, with labels ‘X’ and ‘Y’.
  
__Optimal Epsilon Determination__
* Iterated over a range of k values using ```range()```.
* Fitted ```NearestNeighbors()``` from scikit-learn to compute distances and indices.
* Calculated mean distances and sorted them using NumPy operations.
* Employed ```KneeLocator()``` from the kneed library to find the optimal epsilon value.
* Plots the k-distance graph using ```plt.plot(), plt.axvline(), plt.xlabel(), plt.ylabel(), 
plt.title(), plt.legend()```.
* 2-dimensional data requires the use of DBSCAN’s default value of minpts = 4 (Ester et 
al., 1996)
* If the data has more than two dimension, minpts = dimensions*2, or minpts >= dimensions+1

__Clustering with DBSCAN__
* Applies DBSCAN clustering using ```DBSCAN()``` from scikit-learn.
* Stores cluster assignments in the DataFrame using ```.labels_```.
* Separated clusters and noise points based on cluster labels.
* Visualized clusters using ```sns.scatterplot()``` and ```plt.scatter()```.

__Further Data Processing and Clustering__
* Merged data from ‘clincial.csv’ and ‘metabolites.csv’ CSV files using ```pd.merge()```.
* Metabolites.csv is different from metabolome.csv in that the index_col name is 
Patient_ID in order to merge the two files on the column Patient_ID.
* Selected a subset of features for clustering analysis.
* Repeated the process of optimal epsilon determination and DBSCAN clustering on the 
subset.
* Created scatter plots using ```plt.subplots()``` and ```sns.scatterplot()``` to visualize clustering 
results for different feature combinations relevant to GBM.
    - Lactic acid, pyruvic acid, glucose
  - Age, BMI
  -  Galactitol, glucose
  -  Homocysteine, creatinine

## 3.2 Functions and Tools used
1. Numpy: A fundamental package for scientific computing with Python. It provides 
support for arrays, matrices, and many mathematical functions.
2. Pandas: A data manipulation and analysis library offering data structures like 
DataFrame.
3. DBSCAN: A clustering algorithm that groups points closely packed together while 
marking outliers as noise.
4. StandardScaler: Standardizes features by removing the mean and scaling to unit 
variance.
5. PCA (Principal Component Analysis): A dimensionality reduction technique that 
reduces the number of variables in a dataset, retaining maximum information possible.
6. Matplotlib: A library intended to create interactive visualizations by creating plots and 
graphs. 
7. NearestNeighbors: It is a sci-kit module that performs unsupervised nearest neighbor 
learning. 
8. KneeLocator (from kneed library): A method to automatically identify the "knee" or 
elbow point in a plotted curve, used to determine the optimal epsilon value for 
DBSCAN.
9. Seaborn: A data visualization library based on matplotlib, providing a high-level 
interface for creating attractive and informative statistical graphics.
10. MinMaxScaler: A scikit-learn preprocessor that scales features to a given range, in this 
case, scaling the data to the range [0, 1].


# Results
We compared levels of key metabolites such as lactic acid, pyruvate, glucose, homocysteine, 
creatinine, and galactitol, which resulted in notable differences that highlight the unique 
metabolic reprogramming in Glioblastoma Multiforme. To add to the interpretation, clustering 
based on demographic factors like age and BMI provided further context, showing how these 
variables might influence or correlate with metabolic changes in the tumor environment. 
```ruby
data.head()
```
![image](https://github.com/aditirk1/DBSCAN/assets/132145522/4db8d656-a237-42f7-b07e-52df6bbf70b6)

After transposing the data,
```ruby
data.info()
```
![image](https://github.com/aditirk1/DBSCAN/assets/132145522/2de70150-c534-4ece-b0e5-9d872287749e)

```ruby
data.corr()
```
![image](https://github.com/aditirk1/DBSCAN/assets/132145522/bf182c57-b038-4bfc-aceb-9db518e73a9d)
![image](https://github.com/aditirk1/DBSCAN/assets/132145522/b4e33497-ab60-4c98-90cb-c6082ba175d9)

Elbow plots based on k nearest neighbor were highly resourceful in identifying the best epsilon 
value for the dimensionally reduced or only scaled data. The minpts (minimum number of 
samples to consider as a cluster in DBSCAN) value was determined by the appropriate k value 
(as k = minpts). In this case, optimum eps value was determined to be 0.2767554389483952 at 
k = 4. 
![output_15_0](https://github.com/aditirk1/DBSCAN/assets/132145522/9058543a-a563-498d-83a0-f0b82201275e)
![output_17_0](https://github.com/aditirk1/DBSCAN/assets/132145522/8859e5ab-6910-4bc5-9e1f-34be70fde5e8)

The results of the clustering showed 4 major clusters that could indicate different metabolic subgroups within the GBM patient cohort. These subgroups may reflect variations in metabolite abundances and metabolic pathways across different patients. They may have clinical implications, such as guiding personalized treatment strategies based on metabolic profiles. The obtained subgroups need further validation with rigorous testing and additional data analysis.

Next, the three metabolites that are most implicated in GBM due to the Warburg effect - an increase in the rate of glucose uptake and preferential production of lactate, even in the presence of oxygen – pyruvate, lactate, and glucose, where considered for clustering. 
![output_23_0](https://github.com/aditirk1/DBSCAN/assets/132145522/914a7827-37c8-4b6f-b27c-748f2ea91fff)

![output_25_0](https://github.com/aditirk1/DBSCAN/assets/132145522/5880740a-913e-4d28-93a5-4ff83ac1a389)


The results were pretty significant for 2 plots out of 3. There were two subgroups for glucose and lactic acid abundance, where there is an indication that one group has a higher lactic acid abundance compared to the other, for the same glucose levels. Another interesting finding was pyruvate vs. lactic acid – again, two subgroups that were clearly separated and clustered well using DBSCAN. The figure is suggestive of the trend that for similar lactic acid levels, there is one sub group expressing pyruvate at a higher level than the other. The implications and potential outcomes of the variation between these subgroups must be investigated further. 

Age and BMI of the patient cohort were also clustered and visualized to see the spread of 
population in the given cohort. 3 clusters were obtained, and by visual interpretation, the cohort 
seems to consist of patients aged 60-70 primarily, with BMI varying between ~18 to 33, whereas 
the second cluster of middle aged people between 40-53 have BMI in the higher range ~24-33. 
The final cluster is a small sample of ages 50-54 with BMI well within 25 and above 20.

![output_27_0](https://github.com/aditirk1/DBSCAN/assets/132145522/c868fe04-24d0-4d91-8bde-c08efd1614d0)
![output_28_1](https://github.com/aditirk1/DBSCAN/assets/132145522/b6357ca0-815b-4c18-8094-f32787e451d4)

Creatinine is a breakdown product of creatine phosphate from muscle and protein metabolism. 
It is commonly used as a marker of kidney function. Its levels can vary in different physiological 
states and diseases, including cancers. Glioblastoma (GBM) is a malignancy dominated by the 
infiltration of tumor-associated myeloid cells (TAMCs). Examination of TAMC metabolic phenotypes in mouse models and patients with GBM identified the de novo creatine metabolic 
pathway as a hallmark of TAMCs. Homocysteine is an amino acid that is involved in methionine 
metabolism and elevated levels are associated with cardiovascular disease and potentially with 
certain cancers. Homocysteine has a detrimental influence on human neurons as seen in recent 
studies. The proneural-like subtype of GBM shows significantly increased levels of creatinine 
and homocysteine compared to other subtypes.

![output_29_0](https://github.com/aditirk1/DBSCAN/assets/132145522/bc8332a1-102b-4a3f-b8c6-ac51eb7e9552)
![output_30_1](https://github.com/aditirk1/DBSCAN/assets/132145522/b3fa91d6-ed7b-421c-8ee0-09273936a937)

Three clusters were identified, but the significance of clustering can only be determined after 
investigating the possible overlapping biological pathways and molecular basis for the 
upregulation of the metabolites, as well as whether the correlation holds valid by performing 
laboratory experiments.

The final plot was to cluster expression of galactitol and glucose. Galactitol is a glucose epimer produced from aldose reductase, the first enzyme of the polyol pathway [9]. Physiologically, 
this pathway converts excess glucose into fructose through the sequential activity of two 
enzymes: aldose reductase and sorbitol dehydrogenase. To check if there is any evidence of 
clustering, a scatter plot was plotted to visualize raw data:

![output_31_0](https://github.com/aditirk1/DBSCAN/assets/132145522/04480af3-d0be-4aa1-a257-c86d84a31673)

Since the plot suggested some form of clustering and variance in expression, the same procedure 
was followed as above to generate clusters using DBSCAN for these two metabolites. An elbow 
plot was plotted once again to check for the optimal k and epsilon value. The value was found 
to be k = 4 and eps = 0.8010010322532317. Clustering results were distinct, with a total of 7 
clusters! This possibly suggests that for different subgroups of GBM, the expression of glucose 
varies from ~ 20 to 26. 

![output_32_0](https://github.com/aditirk1/DBSCAN/assets/132145522/e70379c3-6a81-47fd-851e-a67cb8ef111c)
![output_33_1](https://github.com/aditirk1/DBSCAN/assets/132145522/6ce688af-20b6-447a-b74c-653086586ff6)

For the various levels of glucose expression, galactitol shows a markedly different pattern of 
expression in each subgroup, suggesting the possibility that the glycolysis pathways may be 
diverted in some patients to the polyol pathway to make up for excess glucose. 

# Conclusion and Future Enhancement
The clustering results obtained from the DBSCAN analysis on the metabolomic data represent 
only the first step of many in finding potential metabolic subtypes and patterns in glioblastoma 
multiforme (GBM) patients. These initial clusters require much more in-depth analysis and 
interpretation to fully understand their biological significance and clinical implications.
A key step is to look at the exact metabolic pathways and activities connected with each cluster. 
This can be accomplished by doing pathway enrichment analysis, which is basically mapping 
the metabolites in each cluster to known metabolic pathways and detecting those that are highly 
enriched or dysregulated. Understanding the underlying metabolic pathways provides an idea 
about fundamental biological mechanisms that drive the observed metabolic subtypes, as well 
as their possible role in tumor growth, therapy response, and patient outcomes.

It is important to note that DBSCAN is just the initial step in a multi-faceted analysis pipeline. 
The obtained clusters can serve as a starting point for further exploration and validation using 
additional statistical methods such as the t-test, ANOVA, machine learning techniques, or in 
vitro and in vivo experiments. These subsequent analyses can help refine the clustering results, 
identify potential drivers of GBM, and ultimately translate the findings into clinical applications, 
such as developing novel diagnostics, prognostic markers, or therapeutic strategies tailored to 
specific metabolic subtypes of GBM.

One challenge that may arise in the analysis of metabolomic data is the curse of dimensionality. 
As the number of features (metabolites) increases, the computational complexity and 
computational resources required for clustering algorithms like DBSCAN can increase 
exponentially. High-dimensional data can lead to sparse data distributions, making it difficult 
to identify meaningful clusters and patterns. To address this challenge, dimensionality reduction 
techniques like Principal Component Analysis (PCA), UMAP or t-SNE can be employed to 
project the high-dimensional data into a lower-dimensional space while preserving the most 
relevant information. Although PCA was used to reduce the dimensionality of the data, analysis 
of the clusters and meaningful interpretations can only be performed with thorough domain 
knowledge.

The future of DBSCAN and its applications in metabolomics and other omics fields holds great 
promise. Continuous improvements in user-friendliness, computational efficiency, and 
versatility will enhance the ability to analyze and interpret complex biological data. Enhancing 
parallel processing methods for multi-core and GPU-based systems and integrating DBSCAN 
into distributed computing frameworks such as Apache Spark are two ways to boost scalability. 
This algorithm has huge potential for improvement in the field of biological data science, and 
is widely being used to this day in high-dimensional data analysis in biology.

# References
1. Rashidi A, Billingham LK, Zolp A, et al. Myeloid cell-derived creatine in the hypoxic 
niche promotes glioblastoma growth. Cell metabolism. 2024;36(1):62-77.e8. 
doi:https://doi.org/10.1016/j.cmet.2023.11.013
2. Agapito G, Milano M, Cannataro M. A Python Clustering Analysis Protocol of Genes 
Expression Data Sets. Genes. 2022;13(10):1839-1839. 
doi:https://doi.org/10.3390/genes13101839
3. Wang LB, Karpova A, Gritsenko MA, et al. Proteogenomic and metabolomic 
characterization of human glioblastoma. Cancer cell. 2021;39(4):509-528.e20. 
doi:https://doi.org/10.1016/j.ccell.2021.01.006
4. https://www.kdnuggets.com/2022/08/implementing-dbscan-python.html (code snippet)
5. https://www.cbioportal.org/
6. https://www.reneshbedre.com/blog/dbscan-python (code snippet)
7. https://matplotlib.org/stable/users/explain/colors/colormaps.html
8. Mullin T. DBSCAN Parameter Estimation Using Python - Tara Mullin - Medium. 
Medium. Published July 10, 2020. https://medium.com/@tarammullin/dbscan￾parameter-estimation-ff8330e3a3bd

