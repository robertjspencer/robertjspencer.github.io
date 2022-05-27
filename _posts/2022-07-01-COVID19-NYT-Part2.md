# SQL Project #1b. A deeper look

In my [previous post](https://robertjspencer.github.io/2022/05/21/COVID19-NYT.html), I looked at COVID-19 data provided by The New York Times. If you haven't read it, I highly recommend reading it before continuing any further.

For my last question for that post, I asked, 'What are the top 10 states by deaths:population ratio and is their governor a Democrat or Republican?' and the results were surprising. Here were the results:

![image](https://user-images.githubusercontent.com/105367716/170274486-64b0e227-ec20-4c59-99ad-1b6e2d3df5c7.png)

As seen above, 9 out of the top 10 states by death:population ratio were Democrat governed sates. 

This was surprising due to how Republicans have questionably handled the pandemic since it began including the promotion of misinformation [[1]](https://www.nytimes.com/2020/09/30/us/politics/trump-coronavirus-misinformation.html)[[2]](https://www.theatlantic.com/politics/archive/2020/11/trumps-lies-about-coronavirus/608647/)[[3]](https://abcnews.go.com/Health/wireStory/gop-state-lawmakers-spread-covid-19-misinformation-76166298)[[4]](https://www.washingtonpost.com/politics/2021/09/14/florida-desantis-vaccine-misinformation-rna/), purposeful ignorance of health and medical professionals [[5]](https://www.nature.com/articles/d41586-020-03035-4)[[6]](https://www.washingtonpost.com/national/coronavirus-ravaged-florida-as-ron-desantis-sidelined-scientists-and-followed-trump/2020/07/25/0b8008da-c648-11ea-b037-f9711f89ee46_story.html), disregard for and sometimes outright banning public health measures [[7]](https://www.texastribune.org/2021/08/06/texas-greg-abbott-covid-restrictions/)[[8]](https://www.cbsnews.com/news/georgia-governor-brian-kemp-bans-city-face-mask-orders-coronavirus-pandemic/)[[9]](https://www.reuters.com/world/us/appeals-court-rules-favor-florida-governor-reinstates-ban-mask-mandates-florida-2021-09-10/), and the prioritizement of the economy over peoples wellbeing [[10]](https://www.sciencedirect.com/science/article/pii/S0191886921002658). So this leaves one to ask, if who's in charge doesn't affect a state's deaths:population ratio, what might?

## After some thought as to what might factors might signifanctly affect the deaths:population ratio, I've decided to ask these questions:
1. Does a state's population density correlate with its deaths:population ratio?
2. Does a state's education level correlate with its deaths:population ratio?
3. Does a state's income inequality correlate with its deaths:population ratio?
4. Overall what are my thoughts?

In order to answer the questions above, using the query below, I queried every state's deaths:population ratio and exported the results into an .csv file also containing each states population density (Population/km^2), education ranking and income inequality [(Gini coefficient)](https://data.oecd.org/inequality/income-inequality.htm).
```
SELECT  state_info.state,
        MAX(deaths) AS total_deaths,
        population AS est_population_2021,
        (MAX(deaths) * 1.0 / population) AS deaths_population_ratio,
        governor,
        political_party
FROM state_info
INNER JOIN us_counties_2022
ON state_info.state = us_counties_2022.state
GROUP BY state_info.state
ORDER BY state;
```

The result:

### Question 1 answer - Does a state's population density correlate with its deaths:population ratio?

EXPORT state and deaths_population_ratio into an excel sheet. Using excel calculate r value for all of these.
