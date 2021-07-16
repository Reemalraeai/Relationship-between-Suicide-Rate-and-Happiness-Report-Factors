# Relationship-between-Suicide-Rate-and-Happiness-Report-Factors/indicators
Project Steps:
-	Define the purpose/ problem
-	Search for the data
-	Download the data
-	Explore the data
-	Clean & prepare the data for analysis
-	Analyze & interpret the data 
-	Visualize the data

Project Purpose:
Identify the relationship between a crude suicide rate & the happiness measures, which are the next seven  factors:happiness score, economic production (GPD per capita), social support, life expectancy, freedom, absence of corruption, and generosity of a country. These seven factors could be found in the World Happiness Report.

Data Source:

GDP per Capita and Suicide rates
https://www.kaggle.com/harshav05/gdp-per-capita-and-suicide-rates 
World Happiness Report
https://www.kaggle.com/unsdsn/world-happiness?select=2016.csv 

Suicide Rate Dataset

Importing & Exploring:
-	import suicide rates dataset
-	explore the dataset

o	see the first 5 rows (head())

o	see the number of columns & rows (shape)

o	see details about the columns (info())

o	see if there is missing value(isnull().sum())

Data Cleaning:
-	remove the unnecessary columns 
-	make the country name columns the index so we can join the datasets after
-	split this dataset to two datasets, one for 2015, and the other for 2016

Descriptive Analysis:
-	apply descriptive analysis on suicide rates for 2015 & 2016 to haver bigger idea about the data
-	apply boxplot to the dataset to explore the min, max, median, & outliers for each of the datasets
-	explore what are the top 5 countries for each year 

The Results of the descriptive analysis:

2015:
-	the boxplot shows that the top 5 countries are outliers, which means that the top 5 countries have suicide rate that differ so much from the rest of the world
-	interesting that 4 of the top 5 countries are in Europe (Kazakhstan locates in Eurasia)

![](/images/Suicide_rate_2015_boxplot.png)

![](/images/Suicide_rate_2015_top5.PNG)

2016:
-	there was a slight decline in the number of outliers (from 5 to 4), in the max rates (in 2015 the max rate was almost 35 & in 2016 the max rate was almost 32)
-	Suriname took the 5th place, and as a result, there were 3 countries from Europe, and 2 from South America

![](/images/Suicide_rate_2016_boxplot.png)

![](/images/Suicide_rate_2016_top5.PNG)


World Happiness Report Dataset

Importing & Exploring:
-	import world happiness report 2015 dataset
-	explore the dataset

o	see the first 5 rows (head())

o	see the number of columns & rows (shape)

o	see details about the columns (info())

o	see if there is missing value(isnull().sum())

*This process run twice, first to import & explore world happiness report dataset for 2015 and the second to import & explore world happiness report dataset for 2016

Data Cleaning:
-	remove the unnecessary columns 
-	make the country name columns the index so we can join the datasets after

*This process run twice, first to clean happiness report dataset for 2015 and the second to clean world happiness report dataset for 2016

-	merge the world happiness report for 2015 dataset with suicide rate for 2015 dataset in one dataset called “suiciderate_happiness_report_2015”
-	merge the world happiness report for 2016 dataset with suicide rate for 2016 dataset in one dataset called “suiciderate_happiness_report_2016”
-	there are two datasets prepared for analysis, suicide rates & happiness report for 2015 dataset & suicide rates & happiness report for 2016 dataset

Data Analysis & Visualization:
-	see the correlation between the variables in the suicide rate & happiness report for 2015 dataset using corr() function 
-	create a correlation matrix using heat map
-	create a function that will return a scatter plot with a regression line, the Pearson Correlation Coefficient, the p-value & returns if there is a correlation, if the correlation is negative or positive, if it is weak, moderate, strong, or very strong and if it is significant or not

The function:

def correlation(x, y, t):

    sns.regplot(x, y)
    
    plt.title('Correlation between suicide rate &' + ' ' + t)
    
    pearson_coef, p_value = stats.pearsonr(x, y)
    
    print('The Pearson Correlation Coefficient is', pearson_coef, 'with a P-value of P =', p_value)
    
    if 0 <= pearson_coef <= 0.19:
    
        print('There is NO correlation')
        
    elif 0.20 <= pearson_coef <= 0.40:
    
        print('Weak positive correlation')
        
    elif 0.40 <= pearson_coef <= 0.59:
    
        print('Moderate positive correlation')
        
    elif 0.60 <= pearson_coef <= 0.79:
    
        print('Strong positive correlation')
        
    elif 0.80 <= pearson_coef <= 1:
    
        print('Very stong positive correlation')
        
    elif -0.19 <= pearson_coef <= -0.01:
    
        print('There is NO correlation')
        
    elif -0.39 <= pearson_coef <= -0.20:
    
        print('Weak negative correlation')
        
    elif -0.59 <= pearson_coef <= -0.40:
    
        print('Moderate negative correlation')
        
    elif -0.79 <= pearson_coef <= -0.60:
    
        print('Strong negative correlation')
        
    elif -0.80 >= pearson_coef >= -1:
    
        print('Very stong negative correlation')
        
    if p_value <= 0.05 and 0.20 <= pearson_coef <= 1:
    
        print('This positive correlation is significant')
        
    elif p_value <= 0.05 and -0.20 >= pearson_coef >= -1:
    
        print('This negative correlation is significant')
        
    elif p_value > 0.05 and 0.20 <= pearson_coef <= 1:
    
        print('This positive correlation is NOT significant')
        
    elif p_value > 0.05 and -0.20 >= pearson_coef >= -1:
    
        print('This negative correlation is NOT significant') 
        

-	create y2015 variable that presents suicide rate for 2015
-	find the correlation between suicide rate for 2015 & each indicator of happiness report for 2015 (7 factors/indicators) correlation between suicide rate & Happiness Score 2015 using the correlation function we’ve created 
-	see the correlation between the variables in the suicide rate & happiness report for 2015 dataset using corr() function 
-	create a correlation matrix using heat map
-	create y2016 variable that presents suicide rate for 2016
-	find the correlation between suicide rate for 2015 & each indicator of happiness report for 2016 (7 factors/indicators) correlation between suicide rate & Happiness Score 2016 using the correlation function 

Results:

2015:
-	There are weak positive correlations between suicide rate (dependent variable/ target) and Happiness Score, Economy (GDP per Capita), Family and Health (Life Expectancy) for 2015 (independent variables/ predictors) and these correlations are significant


![](/images/suicide_rate_happinesss_indicators_correlation_matrix_2015.png)

![](/images/correlation_suiciderate_happinessscore_2015.PNG)

![](/images/correlation_suiciderate_GDP_2015.PNG)

![](/images/correlation_suiciderate_family_2015.PNG)

![](/images/correlation_suiciderate_health_2015.PNG)


2016:
-	as in the previous analysis, there are weak positive correlations between suicide rate (dependent variable/ target) and Happiness Score, Economy (GDP per Capita), Family and Health (Life Expectancy) for 2016 (independent variables/ predictors) and these correlations are significant


![](/images/suicide_rate_happinesss_indicators_correlation_matrix_2016.png)

![](/images/correlation_suiciderate_happinessscore_2016.PNG)

![](/images/correlation_suiciderate_GDP_2016.PNG)

![](/images/correlation_suiciderate_family_2016.PNG)

![](/images/correlation_suiciderate_health_2016.PNG)

Main Result:
-	according to these analyses, we can state that a country that has a higher happiness score, higher GDP, higher family (social support), or higher Health (Life Expectancy), tends to have a higher suicide rate.
-	As a result, we can state that the developed countries tend to have higher suicide rates
