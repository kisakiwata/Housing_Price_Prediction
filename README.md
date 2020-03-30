### Introduction
We are a team of data scientists who explored the housing market of Ames, Iowa, between the years of 2006 and 2010 to understand the nuances of house pricing with the intention to build machine learning models that predict the prices and future sales in comparable markets. We build on the knowledge and experience of successful developers and real estate agents and are able to provide a more holistic and accurate approach to evaluation, with the ultimate goal of helping our clients make better informed investments of their time and money. 


### Methodology
We based our research on the Ames, Iowa data set available on Kaggle, which provides up to 79 data points for every house sold in Ames in a five year period. In order to eliminate redundancies and focus on the most important characteristics, we made hypotheses based on our business acumen and domain knowledge, and then pressure-tested our assumptions with rigorous statistical analysis. 

Some of our initial assumptions about feature importance included:

Square footage of the home
Neighborhood
Age of the house
Quality of the house
Year of the sale
Garage may be a more important asset depending on the location/type of the house
A front yard may be a less important asset depending on the location/type of the house
Some other features, such as masonry type, may provide important insight at the higher end of the market
These are some of the principles that guided our investigation. Some were ultimately confirmed, and others were found to be less significant than we imagined. 

We further verified our approach with machine learning methods which identified the most influential factors in determining the sale price of a house. As a major tool in our refinement and decision-making process, we used data visualization.

### Exploratory Data Analysis
 A major assumption of ours as we built our models was that a linear relationship existed between the sale price of houses and the various features of the houses. In order to confirm that a linear model is appropriate to estimate sale price, there are several conditions our data must satisfy. In its raw form, our data did not satisfy all of the conditions. We used data visualizations to help identify which conditions were being violated and to verify that they had been corrected after our manipulations. One example is the assumption that sale prices are normally distributed. The graphic below demonstrates that sale prices are skewed, and so do not adhere to the assumption of normality. When we take natural logarithm of the sale prices, we find the distribution becomes closer to normal. It also resolved another issue known as heteroskedasticity. This transformation allows us to be more confident in our statistical analyses and the predictions of our model.

Other issues were resolved with a combination of discarding redundant data points and combining others to create more informative features. One such example is the creation of the characteristic “Age at Sale” which wasn’t available in our original data frame but which we created from the information we did have. We suspected that the time since a house was last remodeled may have a greater impact on the sale price than the overall age of the house, and our analyses ultimately confirmed this suspicion. 

### Model Building

After proceeding with feature engineering, we separated our data into a training and testing dataset and fitted our first multi linear regression model using 18 features. As MLR models tend often to be over fitted, we decided next on using a regularized model such lasso to reduce the variance in our model. One other advantage of the lasso model is its features selection properties.

By tuning the hyper-parameter lambda, we were able to drop some of the coefficients of our existing features to 0, thus reducing our initial list of features to as small as 11.

We also explored AIC and random forests models, both of which were helpful in confirming the importance of the features we selected.  Looking past the percentage of variance explained by each model, we selected the model with lowest root mean square deviation (RMSE).

Our focus was to retain as much interpretability as possible without sacrificing accuracy, but we trained some complex models for comparison to understand how much accuracy we were potentially sacrificing. Below is a side by side comparison of the different models we trained and how well they performed. We can see our MLR was the most successful, which is unsurprising given the linear relationship of our data. 

### Conclusion
 
Ultimately, our hypothesis was confirmed that house prices follow, roughly, a linear relationship. Key drivers of price change from house to house include the overall quality of the house (aesthetics), house size (primarily interior), house age at the time of sale, as well as location (anyone surprised by this!?). 

While not our best predictor of price, Random Forest models helped us build intuition about feature importance, and they performed reasonably well on prediction vs. our simple linear regression model. However, because of their relatively low interpretability, compared with linear models, Random Forest are not recommended for driving external client conversations, i.e., informing a real estate agent on the relative significance of lot size on purchase price. 

Further research should pressure test these conclusions across various market types, considering that the training data strictly represented Ames, IA, a college town and suburb of Des Moines, and not other market types. For instance, the complexity of Manhattan’s residential real estate market may be better represented by another model type. Perhaps a more sophisticated, opaque model will be useful when trying to generalize a single model (or ensemble) to predict price across a wider variety of features and larger dataset (i.e., national or global housing prices). 
