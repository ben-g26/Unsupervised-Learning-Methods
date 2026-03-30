<a id="readme-top"></a>

<!-- PROJECT LOGO --> 
<br /> 
<div align="center"> 
 <a href="https://github.com/ben-g26/Unsupervised-Learning-Methods"> <img src="Logo.png" alt="Logo" width="558" height="435"> 
 </a> 
<h3 align="center">Unsupervised Classification of Sea Ice and Leads</h3> 
 <p align="center"> 
 <strong>AI for Earth Observation (GEOL0069) - Week 4 | UCL Earth Sciences</strong> 
  <br /> 
 Sea ice vs lead classification using K-Means, GMM, and AWI-based radar alignment 
 <br/> 
  <a href="https://github.com/eemeleems/GEOL0069_W4_unsupervised"><strong>Explore the docs »</strong></a> 
  <br /> 
  <br /> 
 </p> 
</div> 
<!-- TABLE OF CONTENTS --> 
<details> 
 <summary>Table of Contents</summary> 
 <ol> 
  <li> 
   <a href="#project-summary">Project Summary</a> 
   <ul> 
    <li><a href="#sentinel-2-and-sentinel-3-data">Sentinel-2 & Sentinel-3 Data</a></li> 
    <li><a href="#unsupervised-learning-models">Unsupervised Learning Models</a></li> 
    <li><a href="#k-means-clustering">K-Means Clustering</a></li> 
    <li><a href="#gaussian-mixture-models">Gaussian Mixture Models (GMM)</a></li> 
    <li><a href="#avi-alignment">AVI Alignment</a></li> 
   </ul> 
  </li> 
  <li> 
   <a href="#getting-started">Getting Started</a> 
   <ul> 
    <li><a href="#prerequisites-installation">Prerequisites & Installation</a></li> 
   </ul> 
  </li> 
  <li><a href="#contact">Contact</a></li> 
  <li><a href="#acknowledgments">Acknowledgments</a></li> 
 </ol> 
</details> 
<!-- ABOUT THE PROJECT -->
Project Summary

Monitoring sea ice and leads in polar regions is essential for understanding ocean–atmosphere heat exchange and ensuring safe navigation. This project applies unsupervised machine learning to classify these features from satellite imagery.

Two clustering approaches are implemented using Sentinel-2 optical (MSI) and Sentinel-3 altimetry (SRAL) data. Model outputs are evaluated against European Space Agency (ESA) reference data.

<p align="right">(<a href="#readme-top">back to top</a>)</p>
Sentinel-2 and Sentinel-3 Data

Sentinel-2 and Sentinel-3 are part of the ESA Copernicus programme. This project combines optical imagery with radar altimetry to improve classification robustness, particularly under conditions where optical data is limited (e.g., cloud cover).

Read more about the missions here: Sentinel-2
 & Sentinel-3

Further instrument details: Sentinel-2 MSI
 & Sentinel-3 Altimetry Data Guide
.

<br/>
Unsupervised Learning Models

Unsupervised learning identifies structure in unlabeled datasets by grouping similar observations and extracting latent patterns. It is particularly suited to large, high-dimensional datasets.

This project focuses on:

K-Means Clustering (hard clustering)
Gaussian Mixture Models (GMM) (probabilistic clustering)
<br/>
K-Means Clustering

K-means partitions data into k clusters by minimising within-cluster variance (inertia). Cluster centroids are iteratively updated until convergence.

<br/>

Key characteristics:

Requires pre-defined number of clusters (k)
Uses Euclidean distance for assignment
Iterative optimisation (assignment → update)
<br/>

Advantages:

Computationally efficient
Easy to interpret and implement
<p align="right">(<a href="#readme-top">back to top</a>)</p>
Gaussian Mixture Models (GMM)

GMMs model data as a weighted combination of Gaussian distributions, enabling probabilistic (soft) clustering. Each component is defined by its mean and covariance.

<br/>

Key characteristics:

Provides cluster membership probabilities
Supports flexible cluster shapes via covariance structure
Fitted using the Expectation-Maximization (EM) algorithm
<br/>

EM workflow:

E-step: Estimate cluster membership probabilities
M-step: Update model parameters to maximise likelihood
<br/>

Advantages:

Captures uncertainty in assignments
Handles non-spherical cluster distributions
<p align="right">(<a href="#readme-top">back to top</a>)</p>
AWI Alignment

Radar altimetry signals are sensitive to orbital errors and Mean Sea Surface (MSS) variability. To improve feature extraction, sub-pixel waveform alignment based on the Alfred Wegener Institute (AWI) method is applied.

FFT (Fast Fourier Transform) oversampling is used to align waveforms to a common reference, reducing noise in Peakiness and SSD metrics and improving cluster separability.

<p align="right">(<a href="#readme-top">back to top</a>)</p> <!-- GETTING STARTED -->
Getting Started

The project is designed for execution in Google Colab, which provides the computational resources required for large NetCDF and raster datasets, along with seamless Google Drive integration.

Local execution is also supported; however, file paths must be adapted accordingly to access Copernicus Sentinel data. The notebook can be launched via the Colab link in the repository’s .ipynb file.

<p align="right">(<a href="#readme-top">back to top</a>)</p>
Prerequisites & Installation

Installation commands are included in the notebook.

Required Packages:

!pip install rasterio
!pip install netCDF4
<br/>

Python & Machine Learning Libraries:

import rasterio
import numpy as np
import matplotlib.pyplot as plt
from netCDF4 import Dataset
from scipy.interpolate import interp1d
from scipy.optimize import curve_fit

from sklearn.cluster import KMeans
from sklearn.mixture import GaussianMixture
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay, classification_report
from numpy import asarray as ar, exp
<br/>

Sentinel-2 and Sentinel-3 datasets were obtained via the Copernicus Data Store
. Access requires account authentication within your workflow.

Before running the notebook, ensure datasets are extracted and colocated as described here: Colocating Sentinel Data
.

Dataset folder names:

Sentinel-2 (MSI) data : S2A_MSIL1C_20190301T235611_N0207_R116_T01WCU_20190302T014622.SAFE
Sentinel-3 (SRAL) data : S3B_SR_2_LAN_SI_20190301T231304_20190301T233006_20230405T162425_1021_022_301______LN3_R_NT_005.SEN3
<p align="right">(<a href="#readme-top">back to top</a>)</p> <!-- CONTACT -->
Contact

Benjamin Guillaud-Leblanc - LinkedIn
 - ben.guillaud-leblanc.22@ucl.ac.uk

Project Link: https://github.com/ben-g26/Unsupervised-Learning-Methods

<p align="right">(<a href="#readme-top">back to top</a>)</p> <!-- ACKNOWLEDGMENTS -->
Acknowledgments
Week 4 assignment for GEOL0069 Artificial Intelligence for Earth Observation (2025/26), University College London.
Prof. Michel Tsamados
 and Weibin Chen
 for the original notebook and instruction.
ESA/Copernicus
 for Sentinel data access.
AWI (Alfred Wegner Institute)
 for radar re-tracking methodology.
<p align="right">(<a href="#readme-top">back to top</a>)</p>


