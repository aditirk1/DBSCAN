# DBSCAN
Implementation of an ML algorithm, DBSCAN, on metabolome abundance data in treatment naive GBM patients.

Description of the data:
Proteogenomic and metabolomic characterization of human glioblastoma. Whole genome or whole exome sequencing of 99 samples. Generated by CPTAC. 

As seen in "Proteogenomic and metabolomic characterization of human glioblastoma. Cancer cell" by Wang LB, Karpova A, Gritsenko MA, et al. (doi:https://doi.org/10.1016/j.ccell.2021.01.006),
Metabolite identifications and data processing were conducted as previously detailed (Webb-Robertson et al., 2014). GC-MS raw data files were processed using Metabolite Detector software v2.0.6 beta (Hiller et al., 2009). Retention indices (RI) of detected metabolites were calculated based on the analysis of the FAMEs mixture, followed by their chromatographic alignment across all analyses after deconvolution. Metabolites were identified by matching experimental spectra to an augmented version of the Agilent Fiehn Metabolomics Retention Time Locked (RTL) Library (Kind et al., 2009), containing spectra and validated retention indices. All metabolite identifications were manually validated. The NIST 08 GC-MS library was also used to cross validate the spectral matching scores obtained using the Agilent library and to provide identifications for metabolites that were initially unidentified. The three most abundant fragment ions in the spectra of each identified metabolite were automatically determined by Metabolite Detector, and their summed abundances were integrated across the GC elution profile. A matrix of identified metabolites, unidentified metabolite features, and their corresponding abundances for each sample in the batch were exported for statistics. 

# EXECUTIVE SUMMARY
The project aimed to perform metabolomic characterisation and analysis of Glioblastoma. Glioblastoma is a highly aggressive brain tumor with complex metabolic dysregulation, making it crucial to understand the underlying metabolomic patterns to gain prospective therapeutic insights. 

High dimensional metabolic data was preprocessed, and clustered using the DBSCAN algorithm to describe metabolic abnormalities. Through principal component analysis (PCA) and differential expression analysis, we aimed to uncover subtypes and compare the data obtained from 99 GBM patients.

Cancer cells often exhibit altered metabolic pathways to support rapid growth and proliferation. The analysis was performed on various attributes:
- comparison of lactic acid, pyruvate, glucose levels
- comparison of homocysteine and creatinine levels 
- comparison of galactitol and glucose levels 
- clustering based on age and BMI
 

The project utilized Python libraries such as pandas, NumPy, and matplotlib to preprocess and visualize metabolomic data. The knee point concept was used to determine the optimal value of the epsilon parameter. 

Visualizations such as heatmaps and pathway maps elucidated disrupted metabolic pathways in GBM, providing critical insights into potential targets and biomarkers. This project highlights Python as a powerful tool for bioinformatics and metabolomics research, enabling comprehensive exploration and comparison of metabolite expression patterns in Glioblastoma.


# INTRODUCTION
Density-Based Spatial Clustering of Applications with Noise (DBSCAN) is a base algorithm for density-based clustering. It is a popular unsupervised learning method used for model construction and machine learning algorithms. It is a clustering method utilized for separating high-density clusters from low-density clusters with data containing outliers and noise. It is very useful in defining arbitrarily shaped clusters. It classifies points as core, border, or noise based on two parameters: Eps (the radius defining a point's neighborhood) MinPts (the minimum number of points required within this radius for a point to be considered a core point)


# OBJECTIVE
-Implement DBSCAN with optimized parameters using the knee point method for clustering
-Analyze GBM metabolomic profiles and identify subclasses based on the patterns visualized. 






# RESULTS
GBM cells, like most cancer cells, exhibit the Warburg effect, where they produce energy through glycolysis followed by lactic acid fermentation even in the presence of Oxygen. This allows us to distinguish between cancer patients and healthy people, by analyzing their metabolic profiles. 
The chosen attributes are crucial in energy producing metabolic pathways. Comparison of lactic acid, pyruvate levels between the patients gives an understanding about shift towards glycolysis. 
Homocysteine is an intermediate in the methionine metabolism and is associated with oxidative stress. Creatinine level perturbations can give an insight into the overall metabolic health. Galactitol accumulation can be indicative of a dysregulation of galactose metabolism.
Age can affect the progression of GBM. Clustering based on age can help in identification of age- specific metabolic patterns.

