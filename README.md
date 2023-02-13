## Question and Data

During the COVID pandemic, the Centers for Disease and Control and Prevention (CDC) published an article showing that the obese population was more likely to die or have further complications due to the virus.  There are countless other similar studies that indicate the severity of the health problem that is obesity.

The United States is known for being a land of great opportunity, wealth and freedom. Along with that, however, it is associated with a sedentary lifestyle, fast food restaurants, and obesity. This stereotype doesn't come from nowhere; the United States has an obesity rate of 36.5%, making the country the most obese among developed countries. Within the limits of the conclusions that the field of data science can make, we decided to answer: Is the availability of fast food restaurants in the USA correlated with higher obesity rates? We will also attempt to discover other variables that could be associated with obesity rates and determine how correlated they seem to be with it. 

## Data
We used data from the Food Environment Atlas by the U.S Department of Agriculture collected in years ranging from 2013 to 2015. They use the Behavioral Risk Factor Surveillance System (BRFSS), the U.S. Census, and the USDA's Economic Research Service as their sources and they organize their data at the county level. Therefore, we have used each county as one data point. We believe that the fact the data is from different years may cause a slight alteration in the results of our model. This should be negligible since they're only at most two years apart.

We picked a few variables that we thought could be relevant in determining obesity rates:

obesrate = rate of obesity in each county in the US, 2013\
fasfoo = fast-food restaurants per 1000 people in each county in the US, 2014\
medinc = median household income, 2015\
diab = rate of diabetes in each county in the US, 2013\
fitplace = recreation & fitness facilities per 1000 people in each county in the US, 2014\
loaccgro = percent of access to grocery stores in each county in the US, 2015.


https://www.ers.usda.gov/data-products/food-environment-atlas/data-access-and-documentation-downloads/
# Methods
To answer our question, we chose to use a two step process. For the first step, we decided to split the initial data set by clustering using k-means. This would allow our models in the second step of the process to make better predictions. Plus, separating our data to create different models will prevent over-fitting. Clustering may also offer additional insights in our data. For example, we can use visualizations to identify new patterns by location.  

We clustered on the variables mentioned above (fasfoo, medinc, diab, fitplace, loaccgro), excluding obesity rate as this is our target variable.

Based on the elbow chart we created using k-means, 4 centers looked like the most adequate. We analyzed each of the clusters separately. For each cluster, we trained a random forest (RF) regression model, evaluating them using mean-squared error (MSE). RF also grants us the ability to see variable importance, helping us answer our question of which features are the best predictors of obesity rate. RF's benefits of bagging and boosting to mitigate under-fitting and over-fitting also made it an appealing option.
