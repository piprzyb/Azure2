# Operationalizing Machine Learning

This project uses Azure Machine Learning to configure a cloud-based machine learning production model, deploy it, and consume it. Pipeline is also created using SDK, published and consumed.

Steps that are followed:

* Authentication
* Automated ML Experiment  
* Deploy the best model
* Enable logging  
* Swagger Documentation
* Consume model endpoints  
* Create and publish a pipeline  
* Documentation


## Architectural Diagram
![alt text](pics/architecture.png)

## Key Steps
### Step 1: Authentication
In this step, service principal ml-auth was to be created, but since the project was executed in Udacity Azure Workspace, the authentication step was already part of the setup.
### Step 2: Automated ML Experiment
At first, dataset used in this project was uploaded to Azure workspace. Dataset contains data about marketing campaigns in banking institution and objective was to predict if marketing campaign was successful, meaning if contacted customer subscribed to product ('yes') or not ('no').
![alt text](pics/data_upload.png)
After dataset registration, AutoML experiment was created with task type - Classification. 
![alt text](pics/best_model1.png)
Best model was VotingEnsemble classifier with accuracy of 92%.
![alt text](pics/best_model2.png)
### Step 3: Deploy the best model
In this step best model was deployed. Deployment allows to interact with the HTTP API service and interact with the model by sending data over POST requests.
![alt text](pics/deploy.png)
### Step 4: Enable logging
After the deployment, Application Insights service was enabled and logs retrived. At first config.json was downloaded from the Azure Workspace. Then logs.py script was updated with the details of the deployement, and attribute enable_app_insights was set to True. After those steps python script was run:
![alt text](pics/logs_py.png)
Applications Insights enabled:
![alt text](pics/app_ins.png)
### Step 5: Swagger Documentation
In this step, deployed model was consumed using Swagger. Azure provides a Swagger JSON file for deployed models. Swagger is then run locally using swagger.sh and serve.py script is executed to interact with Swagger instance and send request using HTTP POST method. 
![alt text](pics/sw.png)
### Step 6: Consume model endpoints
After the deployment we can interact with trained model and send data for scoring. Using endpoint.py file sample features are sent via POST method and result is returned.
![alt text](pics/resp.png)
Also as optional step we can benchmark the endpoint using Apache Benchmark and runing benchmark script.
![alt text](pics/benchmark.png)
### Step 7: Create and publish a pipeline
In this step Azure SDK is used to create, publish and consume a pipeline.

Pipeline created:
![alt text](pics/pipeline_created.png)

Pipeline endpoint:
![alt text](pics/pipeline_endpoint.png)

Bankmarketing with AutoML module:
![alt text](pics/bankmkt_automl.png)

Published pipeline overview:
![alt text](pics/overview_active.png)

RunDetail widget:
![alt text](pics/widget.png)

Scheduled run:
![alt text](pics/sched_run.png)

## Screen Recording
https://www.youtube.com/watch?v=onmwoeLrca0


