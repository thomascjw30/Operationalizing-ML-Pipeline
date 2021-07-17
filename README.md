
# Operationizing Machine Learning Pipelines by Thomas Choong

This project is part of the Machine Learning Engineer with Azure Nanodegree program. This is project #2 and I am tasked to use Azure & Python SDK & Swagger to create a model (using AutoML), select best model, deploy best model via an endpoint, publish the endpoint and finally consume it via HTTP API.

## Architectural Diagram
1.) Authentication - Using Git Bash to login into Azure via 'az login' command
<br>2.) Auto ML Experiment - Upload the banking data and run AutoML to retrieve the best performing model
<br>3.) Deploying the Best Model - Using the results from AutoML, I've selected the best performing model (Accuracy) and deployed it 
<br>4.) Enable Logging - Before we consume the model we must activate logging insights via Git Bash, this allows us to see real-time stats of any errors or issues before & during consumption of the model
<br>5.) Swagger Documentation - Swagger is used to consume the model and enabling the API to have access to the end model. 
<br>6.) Consume Model Endpoints - After both model & endpoint has been deployed, I am able to use Git Bash to test some JSON data against the endpoint to retrieve results
<br>7.) Publish Pipeline - This workflow was automated by creating a pipeline with the Python SDK

## Key Steps
1.) Authentication - Used Udacity's Virtual Lab and utilized gitbash's 'az login' command to log into MS Azure

2.) Auto ML Experiment - I utilized MS Azure's AutoML library to run AutoML on the Bank Marketing data. The results of AutoML gave us VotingEnsemble as the best performing algoriitmn on this dataset, therefore this is the model I went with

Bank Marketing Dataset Avaiiability
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/dataset_avialable.PNG">

Best Performing Model After AutoML Run
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/automl-bestmodel.PNG">

3.) Deploying the Best Model -  I deployed the model above to an endpoint (using Azure Container Instance) while enabling Authentication

<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/automl-run.PNG">


<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/automl-run.PNG">

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
