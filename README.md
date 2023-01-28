# Modelling Global Temperature Anomaly: An Application of Granger Causality Analysis and Partial Least Squares Regression


## Overview 
This project examines a subset of variables known to contribute to climate change and attempts to quantify their influence on global temperature, using various analytical methods. 

This code has been written using Python version 3.7, through an ipynb file using Jupyter notebook. The project notebook is included in this repository and is called ‘Modelling Global Temperature Rise Code.ipynb’. This will show the fully executed version of all the code used in our project. The repository also includes the data file ‘all_data.csv’ needed to run the notebook and a report ‘Paper.pdf’ detailing the findings of the project. 

You will also see an additional folder called 'Data Filtering'. This contains the notebook 'Data Filtering.ipynb' which filters the original raw data sets and compiles them into a single csv called 'all_data.csv'. It then produces a pairs plot of the data at the end. 'all_data.csv' is already provided for you. Therefore, executing the 'Data Filtering.ipynb' notebook is not required before running ‘Modelling Global Temperature Rise Code.ipynb’. It is only included to illustrate how 'all_data.csv' was created


## Table of Contents
<a href="#installation">Installation</a>   
<a href="#packages">Packages</a>   
<a href="#notebook-structure">Notebook Structure</a>   
<a href="#code-contributors">Code Contributors</a>   



## Installation
You can download the repository by clicking the green ‘Code’ button and selecting ‘Download ZIP’ as seen below. 

<a href="https://ibb.co/K5hVKB4"><img src="https://i.ibb.co/Prj1DJX/download.png" alt="download" border="0"></a>

This will download the relevant Jupyter notebook file ‘Modelling Global Temperature Rise Code.ipynb’ along with the data needed to execute it (all_data.csv). 

In order to use Jupyter Noteboooks, you must have Anaconda downloaded. This can be downloaded from the <a href="https://www.anaconda.com/products/distribution">Anaconda website</a>. For further instruction on downloading Anaconda, please follow <a href="https://www.geeksforgeeks.org/how-to-install-anaconda-on-windows/">this link</a>. 

To open the code, you must first open Jupyter Notebooks. This can be done through Anaconda Navigator, by clicking Launch on Jupyter Notebook as seen below. 

<a href="https://ibb.co/f9GJ1yX"><img src="https://i.ibb.co/Qkj0bTJ/launch.png" alt="launch" border="0"></a>

Once in Jupyter Notebooks, go to the folder where you have saved the file and click to open the file. You will need to extract the zipped folder before opening it in Jupyter. 

## Packages

The necessary packages to run all of the code are found at the top of the Python notebook. 

These include:
- `pandas`
- `matplotlib`
- `statsmodels`
- `numpy`
- `scikit-learn`

These can be installed by executing the following command in Anaconda Prompt.

`conda install pandas matplotlib statsmodels numpy scikit-learn`

Additionally, if you wish to execute 'Data Filtering.ipynb', you must also install the following packages.

- `xarrray`
- `seaborn`

This can be done through the following command.

`conda install xarray seaborn`

## Notebook Structure
The notebook is divided into 3 sections. The entire notebook can be executed at once by pressing Cells > Run All or by typing `Ctrl + A` followed by `Shift + Enter`. Individual cells can be executed with `Shift + Enter`.   

A description of each section and the functions defined in it are given below.

### Granger Causality
This section generates time series plots of the data and examines if the data are stationary. The data is transformed by differentiation to make it stationary.
An appropriate lag length for Granger causality testing is determined using Akaike Information Criterion. Granger tests are then performed on the transformed data.


<table>
<thead>
  <tr>
    <th>Function</th>
    <th>Use</th>
    <th>Example</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>plot_df()</code></td>
    <td>Creates time series plot of variables</td>
    <td><code>plot_df(all_data, x=all_data.index, y=all_data.co2, title='CO2')</code></td>
  </tr>
  <tr>
    <td><code>Augmented_Dickey_Fuller()</code></td>
    <td>Prints test statistics of augmented Dickey Fuller test and whether data is stationary or not</td>
    <td><code>Augmented_Dickey_Fuller(adfuller(all_data['avg_temp']))</code><br></td>
  </tr>
</tbody>
</table>
  
### Principal component analysis
In this section, a principal component model of the data is constructed with all components retained. The eigenvectors of the data covariance matrix are printed along with the variance explained by each component. A score plot of the first two components is generated colour coded by temperature anomaly. 

No functions are defined.

  
### Partial least squares regression
This section implements a partial least squares model of the data. The mean squared error is estimated with 10 fold cross-validation and plotted against the number of components. Using this plot as a guide, an optimal number of components is selected. A model with 2 components is fitted to the data and the model parameters are printed.

<table>
<thead>
  <tr>
    <th>Function</th>
    <th>Use</th>
    <th>Example</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>PLS()</code></td>
    <td>Calculates mean squared error for partial least squares model with n components</td>
    <td><code>PLS(x, y, n)</code></td>
  </tr>
</tbody>
</table>
