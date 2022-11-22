# Kickstarting with Excel

## Overview of Project
[Kickstarter](https://www.kickstarter.com/?ref=ksr-redirect-kickstarter_today) is a crowdfunding platform that has been used to raise over $6 billion and successfully fund more than 230,000 creative projects. Within the theater category, over $49 million has been raised with a success rate of approximately 60%. This project uses Kickstarter data to analyze trends in successful and unsuccessful theater campaigns.

### Purpose
The purpose of this project was to analyze Kickstarter data and gain insights to plan a fundraising campaign for a play. The goal was to analyze the factors that contribute to a successful campaign. More specifically, we were interested in how funding goals and launch date are related to campaign outcomes.

## Analysis and Challenges
The Kickstarter data contains information for campaigns between 2009 and 2017. Some of the fields used in the dataset to describe the campaigns include: 
* parent category
* subcategory
* goal amount
* pledged amount
* launch date
* outcomes

The dataset and analysis can be viewed in the Kickstarter_Challenge.xlsx file.

### Analysis of Outcomes Based on Launch Date
To start the analysis, "Years" was added to the dataset using the formula `=YEAR(@R:R)`. Next, a pivot table was created with "Years" and "Parent Category" as filters, "outcomes" in columns, "Date Created Conversion" in rows, and "Count of Outcomes" in values. Two fields, "Years2" and "Quarters", were automatically created when adding "Date Created Conversion" to rows. These two fields were deleted from rows to collapse the pivot table to only show the months of the year.

The resulting table was then filtered by "Parent Category" to show only "theater" campaigns. The column labels were sorted in descending order and filtered to exclude "live" and "blank" campaign outcomes (see below).

| ![Pivot Table](/Resources/PivotTable.png) | 
|:--:| 
| *Pivot Table of Outcomes Based on Launch Date* |

### Analysis of Outcomes Based on Goals
To show outcomes based on goals, a table was created which showed the total number and percentage of successful, failed, and canceled campaigns for each goal range. There were 12 goal ranges from "Less than $1,000" to "More than $50,000" in $5,000 increments. To calculate the number of campaigns, `COUNTIFS` was used which filtered on campaign outcome, goal range, and subcategory. See the example below:

`=COUNTIFS(Kickstarter!$F:$F, "successful",Kickstarter!$D:$D,">=1000",Kickstarter!$D:$D,"<=4999",Kickstarter!$O:$O,"plays")`. 

The total number of projects for each goal range and the percentage of successful, failed, and canceled projects for each goal range was also calculated. To find the total number of projects, the `SUM()` function was used. For the percentages, the number successful, failed, and canceled were each divided by the total number of projects in the specified goal range.

| ![Table](/Resources/Table.png) | 
|:--:| 
| *Table of Outcomes Based on Goals* |

### Challenges and Difficulties Encountered
There were few difficulties in conducting this analysis. The only task that required a little bit of extra research was determining how to include multiple conditions in the `COUNTIFS()` function. To learn more about the function, I consulted [W3schools](https://www.w3schools.com/excel/excel_countifs.php).

For individuals with little experience in Excel, I could also see where creating the Outcomes Based on Goals chart would initially be challenging. Instead of highlighting the entire table, you need to highlight the first column, hold `command`, and highlight the last three columns in the table.


## Results

### Compaign Outcomes by Launch Date Conclusions
The month with the greatest number of campaign launches was May, followed by June, July, and August. Based on this analysis, the summer months are the most popular time to launch a fundraising campaign and May is the month with the highest proportion of successful campaigns. Following the trends in the data, the campaign should be launched in May.

December is the worst month to launch a campaign. Almost 50% of campaigns failed during this month. Launching a campaign in this month should be avoided.

| ![Outcomes by Launch Date](/Resources/Theater_Outcomes_vs_Launch.png) | 
|:--:| 
| *Line Chart of Outcomes Based on Launch Date* |

### Campaign Outcomes by Goal Conclusion
The majority of campaigns, 889 in total, have a funding goal of less than $10,000. Within this subset, the lower the funding goal, the greater the percentage of successful campaigns. Once the funding goal increases to $15,000 or more, the percentage of failed campaigns is more likely to be greater than the percentage of successful campaigns. 

| ![Outcomes by Goal](/Resources/Outcomes_vs_Goals.png) | 
|:--:| 
| *Line Chart of Outcomes By Goal* |

### Limitations
The dataset only includes projects from 2009-2017. This data may not accurately reflect trends that are present in more current data, particularly within the last three years. Making decisions on the basis of outdated information carries risks.

The dataset is also relatively small. This is especially evident when looking at campaigns by goal amount. There are very few campaigns with goals greater than $20,000 which makes comparing the success of larger campaigns with smaller campaigns unreliable. 

Additionally, the number of backers is included in the dataset, but there are no demographic variables about the backers. Without knowing more about the donors who contributed to successful campaigns, the campaign cannot be targeted to those most likely to contribute.

### Additional Tables and Graphs
Since the fund raising campaign is seeking $10,000, it may be useful to create more granular tables or graphs that focus on funding under $15,000. More specifically, for the Outcomes Based on Goals analysis, creating a chart with dollar ranges for every $1,000 instead of $5,000. This would help identify the best fundraising goal. 

It would also be interesting to compare plays to other subcategories of campaigns. For instance, comparing plays to somewhat similar art forms like musicals may strengthen the above conclusions or show different trends entirely.
