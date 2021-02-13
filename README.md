# Diabetes Diagnosis Prediction with Azure AutoML
In this project, we train a classification model that predicts diabetes diagnoses. After this we deploy the model and make an endpoint available for other applications to consume.

## Dataset
The data set is provided by Microsoft at https://aka.ms/diabetes-data. It contains 10 columns and 100,009 rows containing metrics of different patients such as pregnancy information, body mass index, plasma glucose, age, and so on. 

![Creating the data set in Azure ML Studio](https://github.com/obinnaonyema/automl_predict_diabetes/blob/main/create_dataset.PNG)

## Run AutoML Experiment
An AutoML experiment was set up with AUC_Weighted as primary metric. 

<ul>To calculate this metric, the training process will use some of the data to trail the model, then apply cross-validation to iteratively test the model with data it wasn't trained with and compare the predicted value with the actual known value. From these comparisons a confusion matrix of true positives, false positives, true negatives and false negatives is tabulated and additional classification metrics are calculated including a Receiving Operator Curve (ROC) that compares the true positive and false positive rates. The area under this curve (AUC) is used to evaluate performance of the model.
 </ul>

Exit criterion: the job was set to run for 0.25 hours and metric score threshold set to 90%.

After the experiment completed, the best model was a combination of MaxAbsScaler and XGboostClassifier with an AUC_Weighted score of 0.98877

![Best Model](https://github.com/obinnaonyema/automl_predict_diabetes/blob/main/best_model.PNG)

## Deploy and Test Model

The best model was deployed and then tested with sample data. View sample data in the notebook in this repo.

![Deploy Model](https://github.com/obinnaonyema/automl_predict_diabetes/blob/main/deploy_model.PNG)
