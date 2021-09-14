# Udacity Project Model Optimization
# Summary
This was a comparison between AzureML Hyperdrive and AutoML model optimization to find the best model for predicting a Yes or a No in the banking dataset. 
## Data
Since there is no documentation about the data I had to google search to dataset to find that it is from a direct marketing campaign of a bank in Portugal and contains demographic, financial, and time related variables about the customer and when they were last contacted. The desired outcome of our model is to predict the 'y' column which is whether or not the client subscribed to a term loan (UCI Machine Learning Repository: Bank Marketing Data Set https://archive.ics.uci.edu/ml/datasets/bank+marketing).
## Conclusion
The model that performed the best was the VotingEnsemble from the AutoML optimization process with an accuracy of 92.25%.
![image](https://user-images.githubusercontent.com/28558135/133342080-dafe9011-9ce3-4afd-8251-84b16eb8b6c1.png)


# Scikit-learn Pipeline
The scikit-learn pipeline uses an environment yml file to define the python dependencies to run the model. It pulls the banking data into a TabularDataset object and then transforms that object into a Pandas Dataframe. The pipeline then cleans the data by dropping the nulls and one-hot encoding the categorical data and finally outputting the cleansed x and y dataframes. 
## Model and Termination Policy
Using a Logistic Regression classification model the random parameter sampler mixed and matched predetermined parameter values for the arguements C and max_iter to find the pair of hyperparameters that produced the highest accuracy. The Bandit early termination process was used to terminate any models that were being run that were not within a given amount of the best model that was run, this saved computing nodes from having to finish training models that were going to be sub-par.

# AutoML
The model produced from the AutoML with the best results was the VotingEnsemble classification model using hyperparameters that differed from the scikit-learn pipeline. The C regularization parameter used in this model was 1.76 and a max_iter of 100 to the scikit-learn pipelines .83 and 500 respectively.

# Comparison
AutoML was the easier architecture to setup and required less code to ultimately produce a better result in terms of accuracy. The difference that I can see here is that AutoML will try many different types of models to see which is the best for classifying the data presented, where scikit-learn will only try what you specify it should try and no more or less.

# Future Work
Feature engineering may help this model to be more accurate. Having domain knowledge of banking and how some of the variables may be used to create more features for the model to use would increase the accuracy.

# Proof of Cluster Clean Up
![image](https://user-images.githubusercontent.com/28558135/133321039-1027a188-bc97-47bb-b74b-b32a202f7ae5.png)
