# Project 02 Proposal: <your project title>

**Team members:** <Emily Lupercio and Johanna Alvarado>

See the [Project 02 instructions](https://data385.github.io/project/proj02_wholegame.html) for what goes in each section. Bullet points are great. Put any images in an `img/` folder.

## 1. Problem statement

The FBI describes a hate crime to be a crime against a person, multiple people, or an organization based on their race, religion, sexual orientation, gender identity or due to a disability. It turns out, just about anyone in America is at risk of becoming a hate crime victim. 

We want to reveal patterns within the data. What groups are targeted most? Does it change every year? We expect to find a change in frequencies over the years. To see a sudden increase in the number of hate crimes. Our goal is to try to explain these trends.   

Finding a direct cause of hate crimes is not possible, but we can find correlations to explain sudden triggers.Then acknowledge them for preventative measures.  

## 2. Research question

Does the most frequently targeted group change at the time of presidential elections when it comes to San Francisco based hate crimes? 

## 3. Data acquisition

* The FBI Crime explorer data sets is a collection of crime reported by agencies. Official webpage provides download options per year for public access.  

* The Police Department Investigated Hate Crimes data set (PDIHC) is a collection of hate crime reports from the San Francisco Police Department. Data is not restricted and ranges from year 2000 to 2026

### a. Confirm viability

* Agencies such as county police offices and university campuses report hate crime incidents to the the FBI Crime explorer data sets for public access.
  * Documentation: https://www.fbi.gov/how-we-can-help-you/more-fbi-services-and-information/ucr 
  
* The San Francisco hate crimes data set is open for public download on the government's data web page.
  * documentation link: https://data.sf.gov/Public-Safety/Police-Department-Investigated-Hate-Crimes/huqr-9p9x/about_data

### b. Variables of interest

* From FBI data:
  * From Table 11 “total offences” per state, per year.  
  * From table 1 “incidents” per bias type, per year. 
  
* From PDIHC: 
  * Year and date of reported hate crime as categorical “occurence_month”  
  *Specific victim group as categorical “most_serious_bias” 
  *The motivation behind crime “most_serious_bias_type” 


## 4. Data example  

Link to data: https://github.com/jkalvarado/proj02/blob/main/data_management.pdf

## 5. EDA

We are using alternatives to scraping, which is downloading the csv of hate crime incidents and the FBI's 2025 Hate Crime Statistics 
(15 Excel tables).

Import: `read_csv()` for the incident CSV and `read_excel()` for the FBI tables, since they come as .xlsx files.

Wrangle: The FBI tables are made to look nice, not to be used in R (titles, footnotes, stacked headers), so we'll use `clean_names()` to fix column names, `filter()` to drop the extra rows, and `pivot_longer()` to make the tables tidy so they're easy to graph. We'll use `mutate()` with 
`as.Date()` to turn the incident months into real dates so we can look at trends.

Explore: `glimpse()`, `summary()`, and `count()` to check data types, missing values, and categories. `group_by()` + `summarize()` to break things down by bias type, crime type, and location. `left_join()` to match each state's numbers with its population so bigger states don't look
worse just because they have more people.

Visualize: ggplot2: bar charts (`geom_col()`) to compare groups and line graphs (`geom_line()`) to show changes over time.

## 6. Modeling

We're using the San Francisco PDIHC data for modeling since each row is one hate crime with a date and bias, which is what we need to answer our RQ. We'll make an election period variable (`election_period`) that marks incidents from 3 months before to 3 months after each presidential 
election (2000, 2004, ... 2024) as "yes" and everything else as "no".

Multiple linear regression: we'll count incidents per month for each bias type and use the monthly count as our response. Our predictors are `election_period`, bias type (`most_serious_bias_type`), and year. We'll add an interaction between `election_period` and bias type to see if some 
groups go up more than others during elections, which tells us if the most targeted group changes. We include year so we don't confuse a long-term trend with an election effect.

Logistic regression: to check the groups that come up most in our EDA one at a time. Our response is whether an incident targeted that group or not (yes/no from `most_serious_bias`), and our predictor is `election_period`. We picked logistic regression because the response only has two 
outcomes, and it'll show if an incident is more likely to target that group during an election period.

The FBI 2025 tables will be used for EDA and to compare San Francisco to the rest of California and the U.S.

## 7. Communicate

Results will be displayed on poster.

## 8. LLM disclaimer

We expect to use ChatGPT and Claude for debugging original code, with the purpose of returning optimal model visualizations and results. Raw data will not be shared with any LLMs, along with any identifiable data 

