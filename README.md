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

### Key Insights and Conclusion
The EDA of the Life Expectancy dataset revealed several key insights:
-   There is a strong positive correlation between `Life expectancy` and variables such as `GDP`, `Schooling`, and `Income_composition_of_resources`. This suggests that higher economic prosperity and better educational opportunities are linked to longer life expectancy.
-   The analysis of categorical data confirmed that developed countries generally have a higher life expectancy compared to developing countries.
-   The notebook successfully performed data cleaning and a detailed EDA, laying a solid foundation for further analysis, such as building a predictive model for life expectancy.
