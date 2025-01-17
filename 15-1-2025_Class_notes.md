# Class notes for 15/1/2025

Announcement: A small written exam on things we read on unit 1 on next week Tuesday i.e. 21/01/2024 

Start with an example -

If we are tying to make a cake we need to do some steps before starting the process like -

- bringing in the ingredients
- Check if any ingredient is unusable or not
- Check if the equipments like the oven and the baking pots are okay to use

Similarly before working on data we need to prepare the data for analysis. This task is known as data pre processing

Name          Age    Grade   Height    Test_Score
John Doe      16     10th    5'8"      85
Will Smith    15     NULL    1.72m     92.5
Tom H         17             5'10"     88
Loki          16     10th    168cm     ABSENT

So there are A lot of problems with this data -

1. height is recorded in different units (Inconsistent data); So convert all these data to one unit let's say we go with cm and convert all the data to cm .. The data will then look like below -

Name          Age    Grade   Height              Test_Score
John Doe      16     10th    5'8" -> 172 cm      85
Jane Smith    15     NULL    1.72m -> 172 cm     92.5
Tom H         17             5'10" -> 178 cm     88
Loki          16     10th    168cm -> 168 cm     ABSENT

Next we have missing missing values in forms of empty value for Grade for Tom H, .and a completely different type of data in Test_Score for Loki being `ABSENT`


Common data pre processing steps:

1. Data Cleaning 
 - Remove duplicates
 - Handle missing values
 - Fix structural errors
2. Data Transformation
 - Scaling - Scaling bigger data to smaller data like if we have values like 15,000,000 we can just write them as 15M (scaling to Million)
 - Normalization - Scaling the data to a range of 0 to 1 
 - Feature encoding - Here we convert one feature to another 
	 - Label Encoding - Good for binary data
	 - One hot encoding - Good for nominal data (Let's say we have a table with studnets and their highest degree obtained, then the possibilities are - high school, bachelor's, master's and PhD we can encode them from 1 to 4)
3. Data Reduction
- Feature selection - not all features of the data is important for our work. 
- Dimensionality reduction - 

Time for our own exercise -

Product    Price    Rating   Reviews
Laptop     1200$    4.5      Good!!
Phone      NULL     3,8      Average
Tablet     599      4.2      NULL

### Few after thought questions

- Why is data preprocessing important?
- What are three common data quality issues?
- How would you handle missing values in a dataset?
- What's the difference between normalization and standardization?
