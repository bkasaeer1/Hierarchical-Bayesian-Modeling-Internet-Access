# Project Overview and Findings
This project explores the relationship between county-level internet access and various socioeconomic parameters across different regions of the United States (South, Midwest, Northeast, and South). Leveraging the power of hierarchical Bayesian modeling, it examines the uncertainties surrounding model variables—an aspect where traditional frequentist Maximum Likelihood Estimation (MLE) often falls short. Hierarchical Bayesian modeling, with its ability to provide probabilistic inferences and robust uncertainty estimates, is revealed as an invaluable tool for understanding complex relationships. The project's findings indicate the significance of poverty in controlling the internet access rates and demonstrate how regional variations influence these dynamics.
# Input Datasets
Below provides the list of datasets used for this analysis.
| Field Name                   | Description                                                                                                          |
|------------------------------|----------------------------------------------------------------------------------------------------------------------|
| GEOID                        | Geographic identifier for the county.                                                                              |
| Region                       | The region of the United States to which the county belongs.                                                       |
| State                        | The state in which the county is located.                                                                         |
| County                       | The name of the county.                                                                                           |
| CensusPop2010                | The population of the county as per the 2010 US Census.                                                             |
| USDAPopEst2019               | The estimated population of the county in 2019 according to the USDA.                                            |
| ACSPctBelDiplom5yr2018       | Percentage of the population in the county with less than a high school diploma based on American Community Survey 2018 5-year estimates. |
| ACSPctSomCollegORAssociate5yr2018 | Percentage of the population in the county with some college or associate's degree based on American Community Survey 2018 5-year estimates. |
| ACSPctBSCorHigher5yr2018      | Percentage of the population in the county with a Bachelor's degree or higher based on American Community Survey 2018 5-year estimates.    |
| ACSPctBelPov                 | Percentage of the population below the poverty line in the county based on American Community Survey 2018 5-year Estimates. |
| ACSPctNoIntAcc               | Percentage of the population with no internet access in the county based on American Community Survey 2018 5-year Estimates.            |
| amin_CONDN                   | The minimum advertised download speed in the county based on FCC 477 Dec 2019 data.                                       |
| amin_CONUP                   | The minimum upload speed in the county based on FCC 477 Dec 2019 data.                                                    |
| amax_CONDN                   | The maximum advertised download speed in the county based on FCC 477 Dec 2019 data.                                       |
| amax_CONUP                   | The maximum upload speed in the county based on FCC 477 Dec 2019 data.                                                    |
| median_CONDN                 | The median advertised download speed in the county based on FCC 477 Dec 2019 data.                                        |
| median_CONUP                 | The median upload speed in the county based on FCC 477 Dec 2019 data.                                                      |
| 10th percentile_CONDN         | The 10th percentile advertised download speed in the county based on FCC 477 Dec 2019 data.                               |
| 10th percentile_CONUP         | The 10th percentile of upload speeds in the county based on FCC 477 Dec 2019 data.                                        |
| 90th percentile_CONDN         | The 90th percentile advertised download speed in the county based on FCC 477 Dec 2019 data.                               |
| 90th percentile_CONUP         | The 90th percentile of upload speeds in the county based on FCC 477 Dec 2019 data.                                        |
| BLSUnempRateAvg2019          | The average unemployment rate in the county in 2019 according to the Bureau of Labor Statistics.                   |
| DOCMedHHIncomeUSD2018        | The median household income in the county in 2018 based on the Department of Commerce's SAIPE program.           |
| DOCMedHHIncomePctofState2018 | The median household income as a percentage of the state's median income in 2018 based on the Department of Commerce's SAIPE program. |
| CensusNumPeopInPoverty2018   | The number of people in poverty in the county in 2018.                                                           |
| CensusPctPoverty2018         | The percentage of the population living in poverty in the county in 2018.                                       |
| CensusMedHHIncomUSD2018     | The median household income in the county in 2018 according to the US Census.                                        |

# Step Summaries

## Step 1: Data Preprocessing
This initial step involves collecting and cleaning county-level socioeconomic and broadband data from various sources. The goal is to create a consistent and clean dataset for further analysis.

## Step 2: Correlation Analysis
The project dives into exploring correlations by utilizing heatmap plots, emphasizing the relationships between internet access and socioeconomic parameters, and revealing substantial variations among different U.S. regions.

## Step 3: Bayesian Modeling - Unpooled Model
The project starts with building an "Unpooled Bayesian Model" that treats each county's data independently, considering the relationship between internet access and poverty.

## Step 4: Bayesian Modeling - Complete Pooling Model
Next, a "Complete Pooling Bayesian Model" considers all counties as a single group, providing an alternative perspective on the relationship.

## Step 5: Bayesian Modeling - Partially Pooled (Hierarchical) Model
In this section, the project builds a "Partially Pooled (Hierarchical) Bayesian Model" that captures variations at regional and state levels, enhancing the understanding of the relationship's complexity.

## Step 6: Model Evaluation - MAE and RMSE
Performance evaluation of the models using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE) reveals the strengths and weaknesses of each approach, highlighting the effectiveness of hierarchical modeling in this context.

## Step 7: Shrinkage Effect
Visualizing the impact of hierarchical modeling in shrinking the slope and intercept parameters provides a clearer picture of the model's robustness and reliability.

## Step 8: Model Validation - Posterior Predictive Check (PPC)
The process involves a "Posterior Predictive Check (PPC)" to assess the model's performance in capturing the data's distribution and validate its reliability.

## Step 9: Saving Posterior Traces - Unpooled Model
This code outlines the process of creating and saving posterior traces for a hierarchical model, allowing for efficient retrieval and utilization of the model's results without rerunning the time-consuming sampling process.

## Step 10: Traceplot Visualization - Pooled Model
The code plots the trace of parameters for a pooled model, providing insights into the distributions and behaviors of these variables.

## Step 11: Partial Pooling (Hierarchical) Model
In this hierarchical modeling approach, a global distribution is established, allowing model parameters to vary within each state.

## Step 12: Assessing Priors - Prior Predictive Checks
In the process of applying hierarchical modeling, a prior predictive check is performed to assess the adequacy of the specified priors for accurate parameter estimation before observing the actual data.

## Step 13: Saving Posterior Traces - Partial Pooling (Hierarchical) Model
The code outlines the process of creating and saving posterior traces for a hierarchical model, allowing for efficient retrieval and utilization of the model's results without rerunning the time-consuming sampling process.

## Step 14: Traceplot Visualization - Partial Pooling (Hierarchical) Model
This code generates traceplot visualizations for the parameters and hyperparameters of the hierarchical model, providing insights into the distributions and behaviors of these variables.

## Step 15: Baseline Linear Regression Model
A linear regression model is built to serve as a baseline for comparison with the hierarchical Bayesian model. The model aims to predict the percentage of the population in each county with no internet access based on the percentage of the population in each county with income below the poverty line using data from ACS 2018 5-year estimates.

## Step 16: Model Performance Evaluation
In this step, the performance of three different models—unpooled, pooled, and partially pooled (hierarchical models)—is evaluated by calculating their Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE) using posterior samples.

## Step 17: Comprehensive Model Evaluation
The evaluate function assesses the performance of various regression models using Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE) metrics, offering a comprehensive evaluation of regression models and serving as a valuable tool for model selection and comparison.

## Step 18: Shrinkage Effect - Visualizing Hierarchical Model
The following plot showcases how the hierarchical Bayesian model effectively shrinks the slope and intercept of the regression model by implementing partial pooling, improving model robustness.

## Step 19: Posterior Predictive Check (PPC) for Hierarchical Model
A posterior predictive check (PPC) is conducted for the hierarchical Bayesian model to assess its performance in capturing the data's distribution and validate its reliability.

## Step 20: Visualizing Predictive Relationship
This step visualizes the predicted relationship between the predictor (Poverty Rate) and the outcome (No Internet Access Rate) within the context of a hierarchical Bayesian model.

## Step 21: Visualizing Credible Intervals
Credible intervals for both unpooled and pooled predictions are depicted using two separate forest plots, emphasizing the accuracy and improved reliability achieved through the hierarchical approach.

## Step 22: Comparing Predictions
Visualizing and comparing predictions for each state's relationship between poverty rate and internet access reveals the superior performance of the hierarchical Bayesian model.

## Step 23: Final Model Coefficients
A detailed Pandas dataframe is created to store model coefficients for further analysis and reference, offering key insights into the relationship between poverty and internet access.
