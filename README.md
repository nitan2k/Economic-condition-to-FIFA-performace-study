# How does a country's economic status impact it's football performance in the international stage?
### By Nitan Singh, Vladamir Rife, Ehaab Basil

## SETUP AND DATA WRANGLING
Football (soccer) is the most popular sport on Earth, and as such, many countries at many different economic levels compete to be the best. However, some countries are obviously better than others in the sport. This project aims to see if the economy and stability of a country correlates signifigantly with the performance of their national team.

Our hypothesis is that countries with a greater economic performance tend to have better national teams than those that do not. In order to test this, we will use machine learning to analyze each nation's GDP (Gross Domestic Product), GDP-per-captia, and PPP (Purchasing Power Parity), compared to their total FIFA points as the dependent variable. We will only be analyzing this for the year of 2016, as that is the latest year across all of the datasets.


## Data Collection and Curation

The datasets we will use for this project include one table with each country's GDP, a second table with each country's population, a third table with each country's PPP, and a fourth table with each country's fragility index all acting as independent varaibles. and a final table holding each country's FIFA rankings and total points as our dependent variable. The links to each data source are provided below:

GDP: https://github.com/datasets/gdp/blob/master/data/gdp.csv

Population: https://github.com/datasets/population/blob/master/data/population.csv

PPP: https://github.com/datasets/ppp/blob/master/data/ppp-gdp.csv

FIFA ranking: https://github.com/cnc8/fifa-world-ranking/blob/master/fifa_ranking-2020-12-10.csv

## Why FIFA Total Points?

We chose the total points listed in the FIFA rankings database to be our measure of each country's performance in football since it is the most widely used metric for ranking national teams in men's soccer. The basic algorithm for computing the total points that produce these rankings is as follows:

The country's total points = (Their previous 12 month averaged match points + Their 36 month averaged match points before that)

Furthermore, the point system for each match is as follows:

Points from a single match = M x I x T x C

M = 3, 1, 0, 1, or 2 depending on if the country won, drew, lost, lost on penalties, or won on penalties respectively

I = 1, 2.5, 3, or 4 depending on if the match was a friendly, world-cup/confederation-level qualifier, confederation-level final, or world cup final game respectively

T = (200 - the opposing team's FIFA rank)

C = 1, 0.99, or 0.85 depending on if the opposing team is in the CONMEBOL, UEFA, or AFC/CAF/OFC/CONCACAF confederations respectively

More information about this algorithm exists at: https://www.goal.com/en-us/news/fifa-world-ranking-how-it-is-calculated-what-it-is-used-for/16w60sntgv7x61a6q08b7ooi0p

## Why GDP?

We chose GDP (Gross Domestic Product) as a metric for a country's wealth since it is a direct measurement of a country's monetary productivity and consumption. The basic algorithm for computing GDP is as follows:

The country's GDP = C + G + I + NX

C = total domestic consumer spending or private consumption expenditure

G = total government consumption expenditure and gross investment carried out under the government’s name

I = all capital expenditures or private domestic investments

NX = (country's total export costs - country's total import costs)

More information about this algorithm exists at: https://www.analyticssteps.com/blogs/introduction-gross-domestic-product-gdp

## Why GDP Per Capita?

We chose GDP per capita as a metric for a country's wealth since it is a measurement of a country's monetary productivity and consumption as opposed to its population. The basic algorithm for computing GDP per capita is as follows:

The country's GDP Per Capita = (The country's GDP / The country's population)

## Why PPP?

PPP (Purchasing Power Parity) is the measure of how accessible and affordable goods are in a country with one standard unit of their currency (Ex: USD, Euro, Russian Ruble, etc). We chose this as a metric for a country's wealth since it is a good measure of how financially comfortable it is for citizens to exist in their country of origin. PPP can be calculated using the following formula:

The country's PPP = Cost of goods in the country / Cost of goods in another country (usually the US)

More information about this algorithm exists at: https://www.ig.com/en/trading-strategies/what-is-purchasing-power-parity--ppp---191106

Read the data from each of the github tables into a dataframe. We are only interested in the rows concerning individual countries, so we will delete any row with information about a country grouping (Ex: "Arab World"). We also need to drop any unecessary columns or rename any columns that might conflict with the other tables we will merge that table with.

## Conclusions
### Takeaways:

- PPP (Purchasing Power Parity) is not a signifigant indicator of a country's national team performances at any level (global or regional).
- The GDP (Gross Domestic Product) and GDP per capita of a country are possitively correlated with their men's national team performances at a global level, but inconsistent at a regional level.
- The fragility index of a country is a signifigant indicator of a negative correlation between a country's instability and their men's national team's performance (and conversely, a possitive correlation between a country's stability and performance) for all confederations other than CONMEBOL.
- The Brain Drain of a country is comparatively the most signifigant indicator of a negative correlation between itself and the performance of that country's national team across all confederations aside from the outlier OFC confederation.
- 
## Future Possibilities

The analytic method we used to quantify the signficance of an indicator was rather simple; Isolate the variable to its own column, compare the variable against the potential dependent variable via a linear regression, and check the significance with p-value. We were consistent with our methodolgy, which limits the extent of unnecassary skews due to a change in analytic approach. And even though we didnt find a definitive set of indicators that could correlate to a country's football performance, we havent analyzed everything. There are many other factors, from climate conditions to government spending breakdowns that could be attributed to football performance. Additionally, there are many other models that could yield better predictions than a linear regression, such as a polynomial regression, SVM, or even a neural network. As a final takeaway, this tutorial is a mere stepping stone to the wide range of analytical approaches one could take to explain what aspects of a country most influences its professional football performace.

