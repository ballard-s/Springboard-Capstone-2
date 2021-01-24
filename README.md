# Springboard-Capstone-2

# Predicting Breast Cancer Survival and Identifying Biomarkers for Survival
To better understand a patient’s potential outcome after being diagnosed with a genetic disorder or disease, it is important to understand how specific features of the disease and aberrations in the individual's genetic make-up could be affecting their survival. The analyses performed here aimed to predict whether a breast cancer patient would survive based on disease and tumor characteristics, as well as gene expression levels. In addition, it aimeds to identify genes as biomarkers whose expression levels significantly differ between patients who survive and those who do not survive.

The [final report]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Final%20Report/Capstone_2_Final_Report.pdf) of these analyses expands on the summary below.

## Data
The original [data set](https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Data/NKI_breast_cancer.csv) was obtained from the Netherlands Cancer Institute (NKI).

## DataWrangling
[Data Wrangling Notebook]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Data-Wrangling/Capstone2_DW.ipynb)

* This data set had been previously cleaned, so minimal data wrangling was necessary. 
* The data set with nonessential features removed can be found [here]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Data/nki_bc_cleaned.csv). 
* Because the values in the columns have different magnitudes and because the data is both categorical and continuous in nature, the data was standardized. This [modified data set]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Data/nki_bc_for_model.csv) was used in training and testing the model.

## Exploratory Data Analysis
[EDA Notebook]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/EDA/Capstone_2_EDA.ipynb)

The 'eventdeath' feature was used to divide the data into 2 groups (those individuals who survived and those that did not survive). The patients that survived lived 4.7 years longer than those patients that did not survive.

![screenshot](https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Figures/Patient%20Survival%20time.png)

In addition, differences in the mean expression levels of the examined genes between the 2 groups reveals that they may be may be potential biomarkers for determining breast cancer survival.

![Gene Expression]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Figures/Gene%20pairplot.png)

## Modeling
[Modeling Notebook]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Modeling/Capstone_2_Modeling.ipynb)

Three different models were tested (Logistic Regression, Random Forest, and Cox Proportional Hazard Models), and the Logistic Regression Model was selected as the better performing model. The metrics of the model were:
![Logistic Regression metrics]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Figures/Logistic%20Regression%20metrics.png)

## Identifying features of interest to serve as biomarkers for patient survival 
Being able to identify specific genes that are affecting breast cancer patient survival may provide an avenue of scientific exploration for specific biomarkers of the disease as well as therapeutic targets.

The means for each feature were compared between the two groups using an independent samples t-test. The features that displayed a potentially significant difference (p-value <= 0.05) and a fold difference >=2 or <=-2 were then identified. The ten features with the most significant p-values were:

![top ten]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Figures/Ten%20Features%20with%20the%20Greatest%20p-values.png)

When compared to the 20 features comprised of the top ten positive and top ten negative coefficients from the Logistic Regression model, the following features overlapped:

![overlap]( https://github.com/ballard-s/Springboard-Capstone-2/blob/master/Figures/Significant%20Logistic%20Regression%20features%20table.png)

*Of note here, is that glutathione S-transferase theta-1 has previously been implicated in breast cancer development. This provides validation that features that influence breast cancer patients can be identified through these analyses.*

## Future Research and Recommendations

- expand the analyses
    - having additional data to add or use as a "test" set in the machine learning analysis
- Test more models, including:
    - support vector machine, neural networks, and extreme boost modelling
- include patients without breast cancer
    - examining gene expression analyses of non-affected individuals would provide insight onto biomarkers for breast cancer detection


## Who would benefit from these analyses?

* physician’s, researchers, and patients with recommended treatments, therapies, and pharmaceutical drugs to target aberrant gene expression
* academic or pharmaceutical researchers could test novel therapeutic targets for cancerous cells
