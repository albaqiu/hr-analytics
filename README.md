# HR Analytics: Predicting Job Change of Data Scientists

Statistical modelling coursework (Assignment 2, December 2025) based on the Kaggle dataset [HR Analytics: Job Change of Data Scientists](https://www.kaggle.com/datasets/arashnic/hr-analytics-job-change-of-data-scientists). The goal is to predict whether a candidate is looking for a job change (`target`, binary) with **logistic regression**.

## What it covers

1. **Data preparation**: type conversion, duplicate and ID checks, removal of `city` and `enrollee_id`
2. **Variable analysis**: outliers and distributions of numeric variables (`city_development_index`, `training_hours`, `experience`); cleaning and regrouping of categorical variables (`gender`, `education_level`, `major_discipline`, `company_size`, ...)
3. **Missing data**: study of the missingness mechanism, removal of individuals with too many missing values, MICE imputation and validation
4. **Profiling and feature selection** against the target
5. **Train/test split**
6. **Modelling** with `glm(family = "binomial")`:
   - numeric predictors first, with polynomial terms and factor versions of `experience` and `training_hours`
   - then factor main effects and interactions (stepwise selection)
   - residual analysis and filtering of unusual and influential observations after each stage
7. **Goodness of fit and interpretation**: ROC curve and AUC, confusion matrix and model metrics

## Repository structure

| File | Purpose |
|---|---|
| `Assignment2elisa.Rmd` | Most complete version of the analysis (includes confusion matrix and final metrics; saves `dfpost.rds`) |
| `Assignment2.Rmd` | Alternative version of the same analysis |
| `aug_train.csv` | Training data read by both notebooks (identical to `data/aug_train.csv`) |
| `data/` | Original Kaggle files: `aug_train.csv`, `aug_test.csv`, `sample_submission.csv` |
| `dfpost.rds` | Cleaned and imputed dataset saved after preprocessing |
| `hr-analytics.Rproj` | RStudio project |

## Variables

`city_development_index`, `gender`, `relevent_experience`, `enrolled_university`, `education_level`, `major_discipline`, `experience`, `company_size`, `company_type`, `last_new_job`, `training_hours` and the target `target` (1 = looking for a job change).

## How to run

1. Open `hr-analytics.Rproj` in RStudio.
2. Install the packages:

   ```r
   install.packages(c("car", "MASS", "AER", "DescTools", "FactoMineR", "ModelMetrics",
                      "ResourceSelection", "cvAUC", "dplyr", "effects", "lmtest",
                      "mice", "statmod", "corrplot"))
   ```

3. Knit `Assignment2elisa.Rmd`. MICE imputation can take a few minutes.

## Authors

Laia Jané, Elisa Müller and Runxiao Qiu
