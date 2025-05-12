# Capstone
Public Health Spatial Modeling (MedSat Dataset)
Hi! Thanks for checking out this project. The goal here is to explore how environmental, geographic, and sociodemographic factors impact public health outcomes across England. We used data from the MedSat dataset (2019 and 2020) and applied a combination of interpretable machine learning and spatial models to understand patterns in seven key health outcomes: anxiety, depression, asthma, diabetes, hypertension, opioid use, and overall prescription rates.

 **How to Run the Project (in order)**
To keep things smooth, please follow the notebooks in this order:

**1. Feature_Engineering.ipynb**

This is the first notebook and handles all the initial setup:

It merges the 2019 and 2020 data,

Cleans the dataset (removing duplicates, renaming columns),

Handles missing values using appropriate imputation,

And performs exploratory data analysis (EDA), like summary stats and heatmaps.

You'll end up with a clean dataset ready for modeling.

**2. Feature_selection.ipynb**
This notebook does the heavy lifting on feature importance:

It runs knockoff filtering to cut down the number of features,

Tunes XGBoost with cross-validation,

Builds a "Rashomon set" of strong models,

Applies SHAP, LOCO, Permutation, and CMR to rank feature importance,

And implements GAM (Generalized Additive Models) for capturing global non-linear effects.

After this, you'll have the top predictors selected for each health outcome.

**3. MGWR_Code.ipynb**
Now we go local. This notebook uses MGWR (Multiscale Geographically Weighted Regression) to show how the influence of predictors varies across different regions:

We work at the Local Authority District (LAD) level,

Fit the MGWR model using top predictors and LAD centroids,

And store the region-specific coefficients.

This gives us a much deeper look at how location affects health predictors.

**4. lad-clustering.ipynb**
This is the final piece, where we group areas with similar health profiles:

We cluster LADs based on MGWR output,

The result is a set of spatially coherent “health risk zones”.

Great for policymakers or public health planners to see where targeted action might help most.

**Tools & Libraries Used**
Make sure you’ve got these Python libraries installed:

pandas, numpy, geopandas, shap, xgboost, scikit-learn

mgwr, statsmodels, matplotlib, seaborn
