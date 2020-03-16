# DevOps working with Cloud Pak for Data

## Getting Started with CP4D
The Getting started with IBM Cloud Pak for Data learning path is designed for anyone who is interested in a quick introduction to Cloud Pak for Data. To get started, see https://developer.ibm.com/series/cloud-pak-for-data-learning-path/

The learning path consists of step-by-step tutorials and patterns that explain the process of working with data on the platform:

- Virtualize Db2® Warehouse data using Data Virtualization (tutorial)
- Visualize data with Data Refinery (tutorial)
- Use Jupyter notebooks to analyze data and build and deploy models with Watson™ Machine Learning (code pattern)
- Monitor models with Watson OpenScale (code pattern)


## Deploying assets (Watson Machine Learning)
The last stage of the model development work flow is to deploy a model. This means you put the model into an environment so you can pass data to the model and get a score, or prediction back. 

In this way,you can evaluate the effectiveness of your model and start to use it to make business decisions.

Once the model is deployed ou can also access the model endpoint, which you will need to make the model available for wider use in applications.

## Supported Frameworks
Depending on what tools are configured, Watson Machine Learning provides the tools you need to deploy an asset, such as 
- an SPSS modeler flow, 
- a machine learning model, or 
- a Decision Optimization solution.

To deploy an asset, you must have a **deployment space** associated with the **Watson Studio project** that contains the asset. 

![Deployment Space](../images/ml-deployment-space.png)

```
A deployment space is where you will save the model, create the deployment, and find the information you need to score the model and get a prediction back, or embed the deployment in an app so you can interact with it programmatically.
```


Once a model or function is saved to a space, you can create and manage deployments. You can also create a deployment programmatically, in the model or function code, and view the deployment in the space.




For more information check out: https://www.ibm.com/support/knowledgecenter/SSQNUZ_2.5.0/wsj/wmls/wmls-deploy-overview.html

https://www.ibm.com/support/knowledgecenter/SSQNUZ_2.5.0/wsj/analyze-data/pm_service_supported_frameworks.html

## Supported frameworks (Watson Machine Learning)
To deploy a machine learning model that uses a framework that is not listed as supported, you can create a custom deployment. See the techniques used in this notebook for details.   

You can use popular tools, libraries, and frameworks to build machine learning models using IBM Watson Machine Learning. This topic lists supported versions and features.

Specifying a model type and runtime (Watson Machine Learning)


| Framework	| Versions |   Online |	Batch	| Virtual |
| --------- |--------- | --------- | --------- | -------- |
| Spark	    | 2.2 <br> 2.3	| Yes	| Yes Inline payload only |	No
| PMML | 	3.0 to 4.3 |	Yes	| Programmatic only <br>Inline payload only |	No |
| Hybrid/AutoML	 |	Yes	| No |	No |
| SPSS	| 17.1 <br>18.1 <br>18.2 |	Yes	| Yes |	No |
| Decision Optimization	| 12.9 |	No |	Yes |	No |
| Python function |	0.1	| yes | Programmatic only <br> Inline payload only |	no |
| Scikit-learn & XGBoost |	Scikit-learn-0.20 <br> XGBoost 0.82	| Yes |	Yes |	Yes |
| Tensorflow |	1.13 <br> Training not supported	| Yes	| Yes |	No
| Tensorflow |	1.14 <br> Training requires Watson Machine <br> Learning Accelerator <br>1.2.1 |	Yes	 | Yes |	No
| Keras	| 2.1.6 <br>Training not supported	| Yes | 	Yes | 	No |
| Keras	| 2.2.4 <br> Training requires Watson Machine <br> Learning Accelerator <br> 1.2.1 |	Yes	 | Yes |	No
| Keras	 |2.2.4-tf <br> Training requires Watson Machine <br> Learning Accelerator <br> 1.2.1	|Yes |	Yes	| No
| Caffe	 | 1.0	| Yes	| Yes	| No
| PyTorch | 1.0 <br> Training not supported |	Yes	| Yes |	No
| PyTorch | 1.1 <br> Training requires Watson <br> Machine Learning Accelerator | 1.2.1	| Yes | 	Yes	| No

