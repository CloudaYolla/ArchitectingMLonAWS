# Architecting Machine Learning on AWS
Architecting Machine Learning on AWS: A Practitioner’s Guide to Production-Grade ML on AWS Cloud with SageMaker

`(Revision History:
PA1, 2020-04-14, @akirmak: Initial version
`

*Welcome to the Architecting Machine Learning on AWS with SageMaker workshop.*

## Overview

The objective of this workshop is to provide a practitioner's guide to challenges of real-world ML problems, and demonstrate examples of how to tackle them on AWS Cloud. Aread covered: 

- **Data Engineering:** You will explore various examples of  Data Exploration, Feature Engineering & Data Cleaning using popular frameworks on python using a Jupyter Notebook (pandas, numPy, SeaBorn etc.). Since these frameworks are suitable for small-datasets (KB's, to single digit GBs, or to double digit GBs in extreme cases with very strong instances), they are suitable for working on a subset of the actual datasets. You will also experiment with big data analytics services can be used for data engineering, explorary data analytics; and how data is carried over from the data lake storage to compute clusters using S3. Services covered are: Amazon Athena - a Presto/HIVE based service for Ad-HoC analytics, Glue for Data Catalog Management and S3 for Data Lake Storage.  
    
- **ML Training**: You will train various supervised learning algorithms for regression & classification (For Regression: Decision Trees, For Classification: Logistic Regression & Artificial Neural Networks based Image Classification). You will observe how to do parallel ML training in the cloud on clusters to achieve scale.  

- **Evaluating ML Models:** The key to evaluating performance of an ML model is to be able to generate various metrics (depending on the type of algorithm), and to be able to persist measurements in the ML Project Life Cycle. You will see how model metrics, and metrics related to the compute cluster are persisted in Amazon S3 and AWS CloudWatch.  

- **Optimizing ML Models**: ML Optimization is a stochastic process. You will experiment with Automated Hyperparameter Tuning using Bayesian Search strategy to find the best performing hyperparameters. 

- **Framing the ML Problem:**  Infrastructure Requirements & Business Context

## Prerequisites

### Workshops
This workshop is part of a series. Make sure you've attended the first workshop.

  1. Machine Learning Theory (2 Hour Workshop). Webinar Link [TBD]


### Audience

- **Python** – you don't need to be an expert python programmer, but you do need to know the basics. If you don't, the official [Python tutorial](https://docs.python.org/3/tutorial/) is a good place to start.
- **Scientific Python** – We will be using a few popular python libraries, in particular NumPy, matplotlib and pandas. If you are not familiar with these libraries, you should probably start by going through the tutorials in the Tools section (especially NumPy).
- **Statistics** – We will also use some notions of Linear Statistics and Probability theory. You should be able to follow along if you learned these in the past as it won't be very advanced, but if you don't know about these topics or you need a refresher.

### Implicit Info & Level 300
This material is not a self-service document (yet). A lot of the key messages, that will be given in the session are not reflected in the document yet and will be articulated by the AWS presenter. Later revisions will improve.

This material is a Level 300 document. It assumes basic experince on AWS (S3, IAM, SageMaker). (e.g. screenshots of SageMaker console).  

### Tools, Services
- **AWS Account**: Bring your own AWS Account (with admin access to S3, SageMaker, IAM, ECR, Comprehend, Athena)
- **SageMaker Notebook ** – These notebooks are based on SageMaker Notebook running Jupyter. If you just plan to read without running any code, there's really nothing more to know, just keep reading!

### Preparing for the Labs
#### Create an ML Notebook 

As described here: https://docs.aws.amazon.com/sagemaker/latest/dg/gs-setup-working-env.html While specifying notebook, select 

    - `Instance Type` as `m5.xlarge`
    - `Additional Configuration -> Volume Size in GB` and enter 5GB
    - Add following IAM policies to the IAM role attached to the SageMaker Notebook:
       - `AmazonSageMakerFullAccess`
       - `AmazonS3FullAccess` 
       - `AmazonEC2ContainerRegistryReadOnly`
       - `AmazonEC2ContainerRegistryFullAccess`
       - `AmazonEC2ContainerServiceforEC2Role`
       - `AmazonAthenaFullAccess`
       - `ComprehendFullAccess`
       
#### Open Jupyter Terminal (In SageMaker)

    - Open `vi ~/.bashrc`
    - Append following
    `
        export PS1="\[$(tput setaf 6)\]\u@\h:\w $ \[$(tput sgr0)\]"
        export CLICOLOR=1
        export LSCOLORS=ExFxCxDxBxegedabagacad

        alias ll='ls -lah'
        export EDITOR=vim
    `
    - Do `source ~/.bashrc`
    - Do `sudo yum install htop -y`

#### Download Lab Guides & SageMaker Sample Notebooks (in SageMaker)

    - Open SageMaker Terminal
    - Do `cd SageMaker`
    - Clone Lab Guides `git clone https://github.com/CloudaYolla/ArchitectingMLonAWS.git`
    - Clone SageMaker examples `git clone https://github.com/awslabs/amazon-sagemaker-examples.git`
    

## Outline

1. [Module 1 AWS ML Outline](Module1_AWSML_Outline.ipynb) 
1. [Module 2 Local Data Engineering on Bike Sharing Dataset](Module2_Local_Data_Engineering_Bike_Sharing.ipynb)
1. [Module 3 Local Modeling Supervised Learning Regression on Bike Sharing Dataset](Module3_Local_Modeling_SL_Regression_Bike_Sharing.ipynb) 
1. [Module4 Big Data Engineering Amazon on Reviews Dataset](Module4_Big_Data_Engineering_Amazon_Reviews.ipynb) 
1. [Module5 ML Modeling SL Binary Classification on Bank Direct Marketing Dataset](Module5_ML_Modeling_SL_BinClassfcn_Bank_Direct_Marketing.ipynb) 
1. [Module6.1 ML Model Optimization Bank Direct_Marketing Bayesian](Module6_1_ML_Model_Optimization_Bank_Direct_Marketing_Bayesian.ipynb) 
1. [Module6.2 ML Model Optimization Analyze HyperParameter Tuning](Module6_2_ML_Model_Optimization_Analyze_HyperParamTuning.ipynb) 
1. [Module 7 ML Model Deployment into Production for Batch & Real-Time Predictions](architectingMLonAWS/mod7-deploy-scikit-byom/scikit_bring_your_own.ipynb) 



### Concepts Matrix
| Module | ML Project Stage | Open Dataset | ML Domain | Algorithm | Concepts | Services |
| ---| ---| ---| --- | --- | --- | --- | 
| Module 2 | ML Data Engineering | Kaggle Bike Sharing | | | Descriptive Statistics | SageMaker| 
| Module 3 | ML Modeling on Local Notebook | Kaggle Bike Sharing | Supervised Learning | Linear Regression & Decision Trees | Challenges of ML development on notebooks | SageMaker|  
| Module 4 | ML Data Engineering | Amazon.com Customer Reviews | | | Bridging the gap with big data & ML with Presto, Hue, HIVE, (Spark) | S3, Athena, Glue, Comprehend| 
| Module 5 | ML Modeling on Cloud | Bank - Direct Marketing | Supervised Learning |Binary Classification with Logistic Regression | Benefits of Training in the Cloud| SageMaker|  
| Module 6 - P I | ML Optimization | Bank - Direct Marketing |  | | ML Metrics for Classification | SageMaker|  
| Module 6 - P II| ML Optimization with Hyper Parameter Tuning|  |  | | Bayesian Search HPO Strategy | SageMaker|  
| Module 7 | ML Model Deployment |  |  | | Model hosting for Real-time vs. Batch Predictions, A/B testing, multi-model endpoints, Auto Scaling | SageMaker|  



