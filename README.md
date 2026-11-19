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

Link to data: [rendered PDF](data_management.pdf)

## 5. EDA

_The techniques and functions you plan to use to import, wrangle, visualize, and explore the data, and why each is needed._


## 6. Modeling

_The models you plan to use, your response and predictor variables, and why the models fit your research question._


## 7. Communicate

Results will be displayed on poster.

## 8. LLM disclaimer

We expect to use ChatGPT for debugging original code, with the purpose of returning optimal model visualizations and results. Raw data will not be shared with any LLMs.

