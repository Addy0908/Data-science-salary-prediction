# Data Science Salary Prediction : Project Overview 
Repo for Data science salary prediction (glassdor)


![wordclod](https://user-images.githubusercontent.com/67167223/227974312-62d9cd6a-e34e-4c40-9177-4f181cd14669.png)



* Developed a tool to help data scientists negotiate their pay when they land a job that estimates data science salary **(MAE $ 11K).**
* Utilizing Python and Selenium, I scraped over a thousand job descriptions from Glassdoor.
*  **Python**, **Excel**, **AWS**, and **Spark** were engineered features from the language of each job description to measure their value to businesses.
* GridsearchCV was used to enhance the **Linear**, **Lasso**, and **Random Forest Regressors** in order to get the optimal model.


## Code and Resources Used 
**Python Version:** 3.10  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, selenium, pickle   
**Scraper Github:** https://github.com/arapfaik/scraping-glassdoor-selenium  
**Scraper Article:** https://towardsdatascience.com/selenium-tutorial-scraping-glassdoor-com-in-10-minutes-3d0915c6d905  


## Web Scraping
I modified the github repository for the web scraper (above) to scrape 1000 job listings from glassdoor.com. We obtained the following for each job:
*	Job title
*	Salary Estimate
*	Job Description
*	Rating
*	Company 
*	Location
*	Company Headquarters 
*	Company Size
*	Company Founded Date
*	Type of Ownership 
*	Industry
*	Sector
*	Revenue
*	Competitors 

## Data Cleaning
I had to clean up the data once I scraped it in order to make it acceptable for our model. The following modifications were made:

*	Separated numeric data out of salary. 
*	Created columns for the salary and hourly pay provided by the employer. 
*	Removed rows without salary. 
*	Parsed rating out of company text. 
*	Created a new column for company state.
*	Added a column to indicate whether the position was located at corporate headquarters.
*	Incorporated the founding date into the company's age.
*	If the job description included a list of various talents, columns were made for them:
    * Python  
    * R  
    * Excel  
    * AWS  
    * Spark 
*	Column for simplified job title and Seniority. 
*	Column for description length. 

## EDA
I examined the data distributions and value counts for the different categorical variables. The pivot tables' highlights are listed below.

![avg_salary](https://user-images.githubusercontent.com/67167223/227979013-6177b852-8eb6-430f-a2c5-a55725e65ee5.jpg)
![barplot](https://user-images.githubusercontent.com/67167223/227979042-5d71534c-1194-4ba5-ba2a-14065c4d5628.jpg)
![heatmap](https://user-images.githubusercontent.com/67167223/227979078-87a5158c-25b0-4d4c-add8-922f35ba059e.jpg)
![industry](https://user-images.githubusercontent.com/67167223/227979105-e1fe8365-5f7e-4846-8754-c96e184700ee.jpg)
![observations](https://user-images.githubusercontent.com/67167223/227979148-38c4d2fd-11fd-4fe9-b621-2e62cb88f4e0.jpg)
![observ-details](https://user-images.githubusercontent.com/67167223/227979164-2796c461-089f-4c67-a964-7bd1fd1711b1.jpg)
![sector](https://user-images.githubusercontent.com/67167223/227979192-cf1b786c-58f1-4a80-8017-360ee544b584.jpg)

## Insights:

The project analyzed various parameters on **glassdoor Data Science Salary Data**  and the following insights have been found upon drilling the above parameters:

1. The **Annual Compensation** of a Data Scientist in the United States is around **$117,564**.

2. In the United States, the **Average Yearly Income** for any employment using data (including Machine Learning, Data Analytics, and Data Engineering) is approximately **$107,488**.

3. The **top 5 states** that provides highest Data Scientists Salaries are **California, Massachusetts, New York, Virginia, and Illinois**.

4. **Python** proficiency raises your verage yearly earnings from **87 to 112 dollars**.

5. Data Scientist (37.6%) is the most prevalent job title in fields involving data.

6. **Senior Machine Learning developers** make, on average, **142$ per year** more than all other seniors in any data-related sector.

7. **Junior data scientists** make, on average, **106.5 dollars per year**, the most of any junior in any other data-related area.

8. Organizations with four or more competitors tend to charge less than enterprises with fewer competitors.

9. The **top 4 paying sectors** for data scientists are **Biotech , IT , Business Services and Insurance**.

10. Among all data scientists, those employed in Lendings earn the lowest average wage.

11. All fields involving data require excellent mathematics abilities (mentioned in all job descriptions).

12. The **top employers** of data scientists are **Private Enterprises**.

## Model Building 

I started by creating dummy variables out of the categorical variables. Using a test size of 20% & also divided the data into train and test sets.

I experimented with three alternative models and used **Mean Absolute Error** to compare them. I have selected MAE because it is generally simple to comprehend and outliers aren't too problematic for this kind of model.   

The three different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Lasso Regression** – I believed a normalised regression like lasso would be successful due to the sparse data from the numerous categorical variables.
*	**Random Forest** – Again, I believed that this would fit well given the sparsity of the data.

## Model performance
The **Random Forest model** far outperformed the other approaches on the test and validation sets. 
*	**Random Forest** : MAE = 10.81
*	**Linear Regression**: MAE = 18.86
*	**Lasso Regression**: MAE = 19.67
