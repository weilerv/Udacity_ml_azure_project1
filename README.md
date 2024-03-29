# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Useful Resources
- [ScriptRunConfig Class](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.scriptrunconfig?view=azure-ml-py)
- [Configure and submit training runs](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-set-up-training-targets)
- [HyperDriveConfig Class](https://docs.microsoft.com/en-us/python/api/azureml-train-core/azureml.train.hyperdrive.hyperdriveconfig?view=azure-ml-py)
- [How to tune hyperparamters](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-tune-hyperparameters)


## Summary
**In 1-2 sentences, explain the problem statement: e.g "This dataset contains data about... we seek to predict..."**
This dataset contains data about bank costumers and  we seek to predict if a client will subscribe to a bank deposit or not.
**In 1-2 sentences, explain the solution: e.g. "The best performing model was a ..."**
The best performing model was created by autoML and its Voting Ensemble with XGboost classifier which resulted 0.9159 accuracy.
## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**
Tabular data was loaded and cleaned, then the two parameters of logistic regression were set to random choice, which mans that they will be chosen randomly. the inverse of regularization strength was set to 0.1,0.5,1,5 (since 1 is the default) and max iter was set to 50,100,500 since 100 is the default.
For classification algorithm logistic regression was used with the above given parameters. 
**What are the benefits of the parameter sampler you chose?**
It covers both hyperparameters we can set and it has no too much options so don't use much capacity.
**What are the benefits of the early stopping policy you chose?**
I chose the Bandit policy because it terminates a run when the evaluation metric doesn' fall into a given interval (factor or amount) with respect to the best performing model.
## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML.**
The best model generated by autoML was Voting Ensemble model with XGBoost classifier with the following parameters:
"booster": "gbtree",
        "colsample_bytree": 1,
        "eta": 0.05,
        "gamma": 0,
        "max_depth": 6,
        "max_leaves": 0,
        "n_estimators": 200,
        "objective": "reg:logistic",
        "reg_alpha": 0.625,
        "reg_lambda": 0.8333333333333334,
        "subsample": 0.8,
        "tree_method": "auto"
## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**
Scikit-learn pipeline: accuracy: 0.9135
AutoML pipeline: accuracy: 0.9159
The difference between the two accuracy is not much, autoML's is a bit better. Our pipeline uses logistic regression model with different parameters, while autoML uses many type of models. Data cleaning is same for both.
## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**
Try out more models not only logistic regression, for autoML let the time out be higher, maybe it finds an even better model. (Of course it costs more compute resource so more money. 

