# EDA on Life Expectancy Using WHO Data

This repository contains a Jupyter Notebook for an Exploratory Data Analysis (EDA) of the **Life Expectancy dataset**, which was collected by the WHO and the United Nations. The main goal of this project is to perform comprehensive data analysis and extract critical insights from the data to understand the factors influencing life expectancy.

### Data Source
The dataset is available on Kaggle.

### Dataset Information
The dataset includes the following variables:
* **Life expectancy:** The target variable, measured in years.
* **Country:** The country for which the data is recorded.
* **Year:** The year of the record.
* **Status:** The development status of the country (Developing or Developed).
* **Population:** The total population of the country.
* **Adult Mortality:** The number of deaths of adults per 1000 population.
* **Infant deaths:** The number of infant deaths per 1000 population.
* **Under-five deaths:** The number of under-five deaths per 1000 population.
* **GDP:** Gross Domestic Product per capita in USD.
* **Percentage expenditure:** The expenditure on health as a percentage of GDP per capita.
* **Total expenditure:** General government expenditure on health as a percentage of total government expenditure.
* **Income composition:** The Human Development Index in terms of income composition of resources.
* **Hepatitis B:** Immunization coverage of Hepatitis B (HepB) among one-year-olds.
* **Polio:** Polio (Pol3) immunization coverage among one-year-olds.
* **Diphtheria:** Diphtheria tetanus toxoid and pertussis (DTP3) immunization coverage among one-year-olds.
* **Measles:** The number of reported cases per 1000 population.
* **HIV/AIDS:** Deaths per 1000 live births from HIV/AIDS (ages 0-4).
* **Thinness 5-9:** Prevalence of thinness among children and adolescents aged 5 to 9.
* **Thinness 10-19:** Prevalence of thinness among children and adolescents aged 10 to 19.
* **BMI:** The average Body Mass Index of the entire population.
* **Alcohol:** Recorded per capita consumption of pure alcohol (in liters) for those aged 15+.
* **Schooling:** Number of years of schooling.

### Tools and Libraries
The analysis was performed using the Python libraries:
-   **Pandas** for data manipulation and analysis.
-   **Numpy** for numerical operations.
-   **Matplotlib.pyplot** and **Seaborn** for data visualization.
-   **Scikit-learn** for imputing missing values.

### Data Preprocessing
The notebook addressed several data quality issues to prepare the dataset for analysis.

#### Column Cleaning
Some column names contained leading/trailing spaces and were renamed for consistency and ease of use.
-   `Life expectancy ` was renamed to `Life expectancy`.
-   `percentage expenditure` was renamed to `percentage_expenditure`.
-   `Hepatitis B` was renamed to `Hepatitis_B`.
-   `Measles ` was renamed to `Measles`.
-   ` BMI ` was renamed to `BMI`.
-   `Income composition of resources` was renamed to `Income_composition_of_resources`.

The following columns were dropped from the dataset as they had many missing values and were redundant:
-   `Adult Mortality`
-   `infant deaths`
-   `under-five deaths `
-   `Polio`
-   `Diphtheria `
-   ` HIV/AIDS`

#### Handling Missing Values
The notebook identified columns with missing values, with the highest percentage being in `Hepatitis_B` at 18.89%.
-   Rows with missing values in the `Life expectancy` and `BMI` columns were removed.
-   Missing values in the `Alcohol` column were imputed using the median, as a boxplot showed the presence of outliers that would skew the mean.
-   Missing values in the `Hepatitis_B`, `Total expenditure`, `GDP`, `Population`, `Income_composition_of_resources`, and `Schooling` columns were imputed using the mean or median, depending on the distribution of the data.

### Exploratory Data Analysis (EDA)
The analysis included:
-   **Univariate Analysis:** The distributions of all numerical variables were visualized using boxplots and KDE plots. The counts of categorical variables (`Year` and `Status`) were also examined.
-   **Bivariate Analysis:** A heatmap of the correlation matrix was used to identify relationships between the numerical features. This helped in understanding which variables have a strong positive or negative correlation with life expectancy.
-   **Feature relationships:** The relationship between the target variable `Life expectancy` and key features such as `GDP`, `BMI`, `Schooling`, `Alcohol`, and `Income_composition_of_resources` were visualized using scatter plots. These plots provide visual insights into how each feature affects life expectancy.
-   **Categorical variable analysis:** The impact of the `Status` of a country on life expectancy was analyzed. The distribution of life expectancy for "Developed" and "Developing" countries was compared to highlight any significant differences.

This analysis interprets the coefficients from a Ridge regression model. It's important to remember that these coefficients represent the relationship between each feature and the target variable, assuming all other features are held constant. The values are based on **scaled** or **normalized** data, which is standard practice for Ridge regression.


### **Key Takeaways**
*   **Most Influential Features:** `Schooling` and `BMI` are the most significant positive drivers of the target variable. For every one-unit increase in their scaled values, the target is predicted to increase by `3.69` and `3.54` respectively.
*   **Strongest Negative Influencer:** The `Status_Developing` feature has the most substantial negative impact. A status of "Developing" is associated with a decrease of `3.03` in the target variable compared to the baseline (presumably "Developed").
*   **High-Impact Health & Economic Factors:** `Income_composition_of_resources` is another powerful positive predictor, indicating that improvements in human development are strongly linked to an increase in the target variable.
*   **Moderate Positive Influencers:** `GDP`, `Hepatitis_B`, and `Year` all have a moderate positive association with the outcome.
*   **Minimal Impact:** `Measles`, `percentage_expenditure`, and `Population` show a very small, almost negligible, relationship with the target variable in this model.

| Feature                             | Coefficient | Interpretation                                                                                                                              |
| ----------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Schooling**                       | 3.691       | **Very Strong Positive Impact.** A one-unit increase in schooling years is associated with a 3.69-unit increase in the target variable.          |
| **BMI**                             | 3.536       | **Very Strong Positive Impact.** A one-unit increase in BMI is associated with a 3.54-unit increase in the target variable.                     |
| **Income_composition_of_resources** | 3.113       | **Strong Positive Impact.** A one-unit increase in the Human Development Index is linked to a 3.11-unit increase in the target.                |
| **Hepatitis_B**                     | 0.297       | **Moderate Positive Impact.** Increased Hepatitis B immunization coverage is associated with a 0.30-unit increase in the target.                  |
| **GDP**                             | 0.207       | **Moderate Positive Impact.** A one-unit increase in GDP is linked to a 0.21-unit increase in the target variable.                             |
| **Year**                            | 0.168       | **Moderate Positive Impact.** Each passing year is associated with a 0.17-unit increase in the target, suggesting a positive time trend.       |
| **Total expenditure**               | 0.097       | **Slight Positive Impact.** Higher government expenditure on health corresponds to a small (0.10-unit) increase in the target.                  |
| **percentage_expenditure**          | 0.026       | **Minimal Positive Impact.** The percentage of total expenditure spent on health has a very small positive association.                          |
| **Population**                      | 0.017       | **Minimal Positive Impact.** Population size has a negligible positive effect on the target variable.                                       |
| **Measles**                         | -0.013      | **Minimal Negative Impact.** The number of measles cases has a negligible negative association with the target.                               |
| **Alcohol**                         | -0.749      | **Strong Negative Impact.** A one-unit increase in alcohol consumption is associated with a 0.75-unit decrease in the target variable.         |
| **Status_Developing**               | -3.028      | **Very Strong Negative Impact.** A country being in "Developing" status is linked to a 3.03-unit decrease in the target compared to the alternative status. |

1.  **Socio-Economic Factors are Dominant:** The most powerful predictors in your model are `Schooling`, `BMI`, `Income_composition_of_resources`, and `Status_Developing`. This suggests that the target variable (likely a measure of health or life expectancy) is heavily influenced by education, physical health, economic development, and overall country status.

2.  **Health Interventions Show Mixed Impact:** While `Hepatitis_B` immunization shows a moderate positive effect, factors like `Measles` cases and `Total expenditure` on health have a surprisingly small impact. This could imply that broad-based socio-economic improvements have a far greater effect than specific health spending, or it might be a result of multicollinearity that Ridge regression is managing.

3.  **Lifestyle Choices Matter:** The strong negative coefficient for `Alcohol` highlights its significant detrimental effect on the outcome.

4.  **Ridge Regression's Influence:** Since this is a Ridge model, the coefficients have been "shrunk" towards zero to handle potential multicollinearity. This means the true effects might be even larger, but these values represent a more stable and reliable estimate. The smaller coefficients (e.g., for `Population` and `Measles`) may have been shrunk more significantly if they were correlated with other, more predictive features.

