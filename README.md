# Operationalizing Machine Learning

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, a cloud-based machine learning production model is created, deployed it in Azure container instance, and consumed it using REST API.

## Summary
This dataset contains data about [Bank Marketing](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-	data/bankmarketing_train.csv"). The details about each applicant is available along with historical transactional data to predict whether the applicant will subscribe for long term deposit or not. 
A classification algorithm is used to train model using AUTO ML and the best model that provides better accuracy is selected and deployed in Azure container instance(ACI). The deployed model provides end point to send request to REST API and also Swagger URI. Document is generated using swagger and models are consumed using end point.
AutoML pipeline is created using Axure SDK in notebook and pipeline is delpoyed.

The Architecture:

![imag](./images/1_Arch.png)



# Project main steps
In this project, the following steps are executed :

* ### Automated ML Experiment:
  * **`Dataset`**:
  Bank marketing data set is registered. A classification algorithm is selected and an experiment is created and executed on a standard_ds12_v2 cluster.
 
	![BankMarketing Data](./images/2_BankMarketingData.PNG)
 
	![imag](./images/3_BikeExperimentCompleted.PNG)
 
	The best model choosen is VotingEnsemble that haa resulted in 91.9% Accuracy. 
	![imag](./images/4_VotingEnsemble-2.PNG)
	
  * **Metrics**:	
	![imag](./images/7_Metric_precision_Recall.PNG)
	![imag](./images/10_2_2%20Metrics.PNG)
	
 
 
* ### **`Deploy the best model`**:

	The model(deploy-automl) is deployed using Azure Container instance(ACI). 
	REST API is generated and URI for Swagger is also generated. 
	Applications insights is set to false.
	
	![imag](./images/5_AutoMLDeployed.PNG)
    
* ### **`Enable logging`**:

	Logs.py is loaded and applications insights is set to 'True'.
	
	![imag](./images/7_InsightsEnabled.PNG)
	
	![imag](./images/8_LogsScript.PNG)
	
	
	![imag](./images/5_Logs%20Executed.PNG)
	
	     	
     
* ### **`Swagger Documentation`**:

    Swagger.json file is downloaded and port number is changed 9000 as default one is used. 
    Swagger API is tested and Serve.py is executed to enable Swagger 'Get' and 'POST' API from local host

    
	![imag](./images/9_SwaggerOnLocalhost.PNG)
    
* ### **`Consume model using endpoint`**:

    Endpoint is modified with required suitable URI and key. This will generate data.json. 
    
    
    ![imag](./images/8_3_Endpoint.PNG)

    ![imag](./images/endpoint.PNG)
    
    
    The benchmark file is executed.	
    ![imag](./images/10_benchmarkRunning.PNG)
 
###  `Create Pipeline and publish` 
* ### **`Create and publish a pipeline`**:

   	In the notepad, the bank marketing data is loaded .
   	![imag](./images/11_Notepad-Experiment.PNG)
   
* 'The pipeline' is created for BankMarketing_experiment and it is published.
   	![imag](./images/12_Notepad-CreateMLPipeline.PNG)
   	![imag](./images/13_Notepad-CreateMLPipeline%20(2).PNG)
	
   **Pipeline Created in ML Studio**:
	![imag](./images/11_pipelineRunOverview.PNG)
   
* **The rest 'endpoint' is created and published**
   	![imag](./images/15_Notepad-PublishEndpoint.PNG)
	
	![imag](./images/14_Notepad-PublishEndPoint.PNG)
   
* **The pipeline run is dispayed in ML studio**
   	![imag](./images/17_Notepad-PipelineRunFromStudio.PNG)
	![imag](./images/15_2_PipelineRunDetails.PNG)
    
* **The endpoints are consumed as shown in ML studio**  
  	![imag](./images/18_Notepad-EndPointConsuption.PNG)
	![imag](./images/16_PipelineRuns.PNG)
	
	![imag](./images/18_PipilineEndpointsActive.PNG)
	![imag](./images/endpoint%20completed.PNG)
     
* ### **Documentation**

  	The video is created to explain entire process of AUTO ML studio
  
  [Operationalizing Machine Learning from Azure](https://www.youtube.com/watch?v=_QTYBboZXrg)
  
##  The steps to improve the project
	* The model performance can be increased by analyzing the the Bank Marketing data and ensuring that it is balanced properly.
	  Either oversampling or undersampling methods can be used
	
	* We can check train and test set split methods like stratefied split and holdout based validation to check if that results in better accuracy
	  We can fine tune all hyper parameters and check if it can enhance performance of the model.
	
	* The present model achieved accuracy of 91.5% which is considered as good accuracy. 
	  Further more deep learning models can be used to further enhance model accuracy
	  Deep learning can be enabled through AUTO ML config by setting enable_dnn parameter to TRUE
	
	
	
