
# Deep learning experiment tutorial: 

## Build a TensorFlow model using (Watson Machine Learning) to recognize handwritten numbers.



This tutorial guides you through using the MNIST computer vision data set to train a deep learning TensorFlow model 
to recognize handwritten digits.  In this tutorial, you will 
train, 
deploy, and 
test the model with experiment builder.

## Steps Overview
- This tutorial is heavily based on tutorial found in the "**IBM Cloud Pak for Data V2.5.0 Knowledge Center**", 
see [here](https://www.ibm.com/support/knowledgecenter/SSQNUZ_2.5.0/wsj/analyze-data/ml_local_tutorial_tensorflow_experiment-builder.html) for additional details.

- User access to **Watson Machine Learning Accelerator (WML)** with the same User ID you use for Watson Studio. 
Watson Machine Learning Accelerator is a component required to run experiments.

## Steps overview
Here are the basic steps for training a deep learning model with experiment builder in Watson Studio:

1. [Set up data files](#step1)
1. [Download sample code](#step2)
1. [Train the model](#step3)
1. [Monitor training progress and results](#step4)
1. [Deploy the trained model](#step5)
1. [Test the deployed model](#step6)


This tutorial does not demonstrate distributed deep learning, or using the Watson Machine Learning hyperparameter optimization feature.

---
<a id='Step1'></a>
## Step 1: Set up data files
Training a deep learning model using Watson Machine Learning relies on accessing training files stored 
in a local repository your system administrator sets up for Watson Machine Learning Accelerator, 
which is a required plug-in for running experiments.

- Create a new project or open an existing project.
- Download MNIST sample data files to your local computer from here: 
 [MNIST sample files](http://yann.lecun.com/exdb/mnist/)
  ```
  THe MNIST provides a good database for people who want to try learning techniques and 
  pattern recognition methods on real-world data while spending minimal efforts on preprocessing and formatting.
  currently there are four (4) files are available on this site
  
  Note: Some browsers automatically uncompress the sample data files, which causes errors later in this tutorial. 
  Follow instructions on the MNIST download page for verifying how your browser handled the files.
  ```
- Create a folder for the data files under where Watson Machine Learning Accelerator is installed.
- Copy or transfer the data files into the folder.

---
<a id='Step2'></a>
## Step 2: Download sample code
Download sample TensorFlow model-building Python code from here: 
[tf-model.zip file](https://github.com/pmservice/wml-sample-models/blob/master/tensorflow/v4_samples/tf-model-local.zip)

The **tf-model.zip** contains two files:
- **convolutional_network.py** - Model-building Python code
- **input_data.py** - A "helper" file for reading the MNIST data files

---
<a id='Step3'></a>
## Step 3: Train the model
This tutorial demonstrates training the model using experiment builder in Watson Studio.

1. Open a project.
1. Click **Add** to project and choose **Experiments**.
1. Specify a name for the experiment and an optional description.
1. Specify the path where the training data is stored relative to the mount point for Watson Machine Learning Accelerator. 
   For example, if you saved your files to **wmla-nfs/wmla-data/mnist-tutorial**, and you know that 
   **Watson Machine Learning Accelerator** is installed to **wmla-nfs**, 
   - enter **/wmla-data/mnist-tutorial** as the path for the data.
1. Click **Add training definition** to create the training definition you will use to run the experiment.
   1. Click the New training definition tab.
   1. Give the training definition a name.
   1. Upload the sample code, tf-model-local.zip, where prompted.
   1. Specify the framework that is used in the model-building code: **tensorflow 1.13-py3 or higher.**
   1. In the Execution command box, specify this command for running the model-building code:
   ```
    convolutional_network.py --trainImagesFile train-images-idx3-ubyte.gz --trainLabelsFile train-labels-idx1-ubyte.gz --testImagesFile t10k-images-idx3-ubyte.gz --testLabelsFile t10k-labels-idx1-ubyte.gz --learningRate 0.001 --trainingIters 6000
   ```
1. Select **“1 x NVIDIA Tesla V100(1GPU)”** for the compute plan.
1. Click **Create and run**.

---
<a id='Step4'></a>
## Step 4: Monitor training progress and results
You can monitor the progress of a training run in the Training Runs tab of experiment builder.

When the training run is complete, click on the training definition to view details of its training results, 
including logs and other output.

---
<a id='Step5'></a>
## Step 5: Deploy the trained model
You can use your trained model to classify new images only after the model has been deployed.

1. In the Training Runs tab of experiment builder, select **Save model** from the action menu. 
   Give the model a name and click **Save**. This stores the model in the Watson Machine Learning repository and saves it to the project.
2. In the project’s **Asset tab** you can now see the saved model. 
   - To deploy the model, you must first promote it to a deployment space. 
   - Choose **Promote** from the action menu for the model. 
   - You will be prompted to associate a deployment space with your project if you haven’t done so yet.
3. A prompt is shown to navigate to your Deployment Space after promoting the model. Alternatively the Deployment Space can be accessed via the Overview tab in the project under the Associated deployment space heading.
4. After navigating to the deployment space click on the model name.
5. Click **Deploy**.
6. Choose **Online** and enter a name for the deployment.

---
<a id='Step6'></a>
## Step 6: Test the deployed model
You can quickly test your deployed model from the deployment details page.

1. On your local computer, download this sample payload JSON file with input data corresponding to the handwritten digits "5" and "4": 
[MNIST_sample_payload_V4.json](https://github.com/pmservice/wml-sample-models/blob/master/MNIST_sample_payload_V4.json) 

2. In the **Test area** of the deployment details page in **Watson Studio**, paste the value of the payload field from 
**tf-mnist-test-payload.json**. Then click **Predict**.

---
## Sample output:

```
{
  "values": [
    7,
    4
  ]
}
```

This output shows the 
- first input data was correctly classified as belonging to the class "7", and 
- second input data was correctly classified as belonging to the class "4".
