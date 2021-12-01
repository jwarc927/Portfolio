### Problem Statement

The goals of this project are twofold:

1) We try to use a linear regression model to provide some meaningful, actionable advice for home owners in Ames, Iowa to use in planning their future home rennovation projects.
2) Simultaneously, we try to fit a model which will provide the most predictive power in estimating the price of homes in our test set.

The first goal requires model interpretability.  The average home owner is not going to understand feature coefficients and regularization parameters.  So, we attempt to distil the results of our model into actionable things that a home owner could do.  For example we want to be able to say something along the lines of: "If you want to remodel your home, we recommend that you focus on X and spend approximately Y dollars on the project."

The second goal does not require interpretability and feature engineering, dummy variables, regularization will be used with the sole purpose of minimizng the Root Mean Square Error (RMSE) of the final predictions on the test set.  As we will see an, essentially uninterpretable feature will be constructed which nonetheless provides a great deal of predictive power.


### Data Used

The dataset we are using is obtained from the Kaggle website and presented as a competition to use the data to compute predictions that will minimize the RMSE.  This dataset contains 82 different features including two arbitary ID columns and 22 nominal, 23 ordinal, 13 discrete, and 20 continuous variables whcih may contain useful information for our model.  

The original data is from the Ames, Iowa Assessor’s Office and the data dictionary can be consulted here: [Ames Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)

### Conclusions

To answer the first aspect of our problem statement we can consult the following table:

|Feature|Coefficient|per Unit|Description|
|---|---|---|---|
|**bsmtfin_sf_1**|8935|per 461 sf|Increase price of home by 8,935 for every 461 sf of finished basement area| 
|**bsmt_qual**|3006|per 0.69 increment|Increase price of home by 3,006 for every 0.69 steps in appraiser's opinion of basement quality| 
|**kitchen_qual**|3982|per 0.67 increment|Increase price of home by 3,982 for every 0.67 steps in appraiser's opinion of kitchen quality| 
|**year_remod/add**|3661|per 21 years|Decrease price of home by 3,661 for every 21 years since last remodel| 
|**screen_porch**|3184|per 57 sf|Increase price of home by 3,184 for every 57 sf of screened in porch area| 
|**fireplaces**|2136|per 0.64 fireplaces|Increase price of home by 2,136 for every 0.64 fireplaces| 
|**exter_qual**|3545|per 0.59 increments|Increase price of home by 3,545 for every 0.59 steps in appraiser's opinion of exterior quality| 

This leads us to the recommendation that for a home owner to optimize the current value of their home they should finish as much of their basement as possible at a quality that exceeds the typical.  They should improove their kitchen as much as is possible within their budget.  They should add a screened porch as large as they have room and they should add a fireplace.  On top of all of this, the exterior quality of their home and grounds should be improved as much as possible.  

For the second aspect of the problem statement: we have generated a model which an RMSE of 19,777 on the training set.  This model incorporates elements that are not addressed in the first portion of the problem, but which, nonetheless, increase the predictive power of the model.