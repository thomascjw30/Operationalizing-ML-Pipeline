
# Operationalizing Machine Learning Pipelines by Thomas Choong

## Overview
This project is part of the Machine Learning Engineer with Azure Nanodegree program. This is project #2 and I am tasked to use Azure & Python SDK & Swagger to create a model (using AutoML), select best model, deploy best model via an endpoint, publish the endpoint and finally consume it via HTTP API.

I am utilizing bank marketing data (provided by Udacity) to create a classification model. Ultimate goal, is to have this model predict whether a customer will subscribe to a banking product. Lastly, this is done through creating, consuming and publishing an ML Pipeline.

## Architectural Diagram
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/Untitled.png">

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
As you can see the status of the endpoint is active and in Healthy status, additionally, you can see I chose the name 'demo-model-deploy' which will align with the logs.py file in the next step
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/model_deployment_status.PNG">

4.) Enable Logging - Logging was enabled via Git Bash, however, I needed to first download the config.json file into my main directory, from there I utilized Git Bash to turn on logging and insights by executing the logs.py file (command: 'python logs.py' in Git Bash). I did not make any changes to the logs.py file because the endpoint name was set to 'demo-model-deploy' (if I had chosen a different endpoint name, I would have had to adjust that in the logs.py file)

<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/model_deployment_insights_activated.PNG">
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/logs.py%20screenshot%202.png">
Insights Page
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/insights_page.PNG">

5.) Swagger - After logging has been successfully turned on, a swagger URI should be available to download, I downloaded this file into my Swagger folder.
Before executing the swagger.sh executable on Git Bash, I had to change the port # to 9001 as the port in the original swagger.sh executable, 8000, was in use.
After changing the port #'s, I executed the swagger.sh (command: 'bash swagger.sh')
Lastly, I also executed serve.py in git bash (command: 'python serve.py')

This gave me the following status on Swagger and also the ability to ping against my endpoint via Swagger URL (Note: even though I set port to 9001, the Swagger URL I inputed into Swagger's browser was still 8000 as that was what was executed when executing serve.py file)

<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/swagger_1.PNG">
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/swagger_2.PNG">

6.) Consume Endpoints - With everything in place, I was able to test out and consume the endpoint by executing the endpoint.py (however, before executing I had to change up the orders of the JSON file because it gave a 502 error) (Command: 'python endpoint.py')

<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/endpoint_success.PNG">

7.) Publish the Pipeline - I used the aml-pipelines-with-automated-machine-learning-step provided by Udacity to create a pipeline
After successfully running the Udacity notebook, I was able to create a pipeline which I later published

Successfully running the jupyter notebook
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/completed_jnotebook_run.PNG">

Available Pipelines After Jupyter Notebook execution
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/pipeline.PNG">

Final Pipeline Active Status
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/pipeline_status_active.PNG">
<img src="https://github.com/thomascjw30/operationalizing-ml-pipeline/blob/main/Screenshots/active_endpoint.png">




## Screen Recording
<a href="https://youtu.be/m30BxWEmqU8">Here</a> is a screen recording of a quick walk through of the consumption of this ml pipeline

## Futre Improvements
- Data imbalance - given the dataset is highly skewed, it may improve the model to either undersample or oversample to make the feature variables more evenly distributed
- Use pipelines to automate the whole workflow from data prep, to ML tasks and deployment
- Adjust the exit criterion time from 1 to a few hours to see if accuracy rates/models improve (at the cost of more processing resource/longer processing time)

