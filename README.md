# data-512-a2

## Goal
This project is for Homework [A2](https://docs.google.com/document/d/11eswL84T-H6bli8aX_-XndCN6tAZ4bIb9Z2ywiIf2fE/edit#) of the DATA-512 Human Centered Data Science class at the University of Washington. 

The project seeks to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from a variety of countries. I  will combine a dataset of Wikipedia articles with a dataset of country populations, and use a machine learning service called ORES to estimate the quality of each article.

## Data Source
Two original data sources are used - 
- The Wikipedia politicians by country dataset can be found on [Figshare](https://figshare.com/articles/dataset/Untitled_Item/5513449). More specifically, I will use *page_data.csv* for this assignment.
- The population data is available in CSV format as [*WPDS_2020_data.csv*](https://docs.google.com/spreadsheets/d/1CFJO2zna2No5KqNm9rPK5PCACoXKzb-nycJFhV689Iw/edit#gid=283125346). This dataset is drawn from the [world population data sheet](https://www.prb.org/international/indicator/population/table/) published by the Population Reference Bureau.


## Cleaned Data Schema
Here is the data schema for wp_wpds_politicians_by_country.csv in the data_cleaned folder.
|Column|Description|Mapping from the API calls|
|-|-|-|
|country|The country where the politician is from.|From both WPDS and page_data.|
|article_name|The article name of the politician|From page_data.|
|revision_id|The identifier of the Wikipedia article.|From page_data.|
|article_quality_est.| The quality estimate from the ML model|ORES API|
|population|The population of the country.|From WPDS.|


## Reflections and Implications

From the results of my analysis, I found that the top countries by article coverage and quality are very small countries and some of them unheard of prior to this assignment. This is largely caused by the fact that the extremes are more likely to appear when we have a smaller sample size (in this case, small population). It is also interesting to see that North America scores somewhere near average for both coverage and quality articles. It might make sense that it lags behind European countries, considering their longer history and multiple-party political system. However, the fact that it lag behind Carribean on per person adjusted basis is intriguing, considering that we are talking about the English Wikipedia pages.

Another interesting takeaway is that China politicians have the lowest number of quality article per population. Given that US and China are experiencing a Thucydides Trap and news on China and Chinese politicians is seen on a daily basis, it is quite surprising to see if that not many Chinese politicians have good quality articles (only 40). I also wonder if we are only counting politicians from modern China and if emperors from various dynasties count as well.

Here are the three questions I will address - 

### What biases did you expect to find in the data (before you started working with it), and why?

First of all, we are using the English Wikipedia pages for our analysis, so politicians from English speaking countries have an advantage on coverage and popularity. The results would be very different if we measure politicians in other languages.

Second of all, no models are perfect, and when we utilized a machine learning model to measure politicians' coverage, it wouldn't produce as accurate data as we retrieve the rating directly from the pages. Without much further research into the ML model used, I wouldn't be able to tell specifically which way it is biased but it would be surprising if the model is not at all biased towards any group.


### What might your results suggest about (English) Wikipedia as a data source?

From regions' rankings in bothe the good article and all article coverage, Oceania, Europe and America rank higher than Africa and Asia. It is not surprising that is the case as Oceania, Europe, and America have predominantly Anglo_Saxon culture, whereas Africa and Asian have distinct culture, whether in the root of their language and the current lifestyle. More importantly, most people in Africa or Asia cannot speak/write English fluently. This creates a bias in a less population available to write articles about their politicians on Wikipedia in English.


### Can you think of a realistic data science research situation where using these data (to train a model, perform a hypothesis-driven research, or make business decisions) might create biased or misleading results, due to the inherent gaps and limitations of the data?

Most of the crime research use race as a variable. However, the data and research has significant endogenity concerns. Black people are targeted by the police and therefore would have higher rate. The bias here needs further research and understand, and can NEVER be used in causal inference.

## API License

