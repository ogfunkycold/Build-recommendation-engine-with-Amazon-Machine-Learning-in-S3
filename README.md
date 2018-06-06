Build recommendation engine with Amazon Machine Learning in S3
================================================================

## Introduction
#### Overview
In this lab, you will build a smart solution using Amazon Redshift and Amazon Machine Learning that predict rental bikes for Capital bikeshare system.
The dataset contains daily amount of rental bikes between years 2011 and 2012 in Capital bikeshare system with the corresponding weather and seasonal information.
You will learn how to use Redshift and predict using Machine Learning to create a model that will predict the rental bikes.

#### Topics covered

By the end of this lab, you will be able to:

* Create a Redshift cluster, build Redshift table and load data from Amazon S3.
* Create a Machine Learning Model
* Train the Machine Learning Model, using historic data about rental bikes.
* Predict the rental amount for the future sharebike system with Redshift and Amazon Machine Learning

## About this lab
#### Scenario

The dataset contains daily amount of rental bikes between years 2011 and 2012 in Capital bikeshare system with the corresponding weather and seasonal information.
All we want to know is how much bikes we should prepare for the next week. To avoid the situation when the supply could not meet the demand.

#### Architecture Diagram
We upload data into S3. Then, we used Amazon Machine Learning for training model and prediction. All of the output will be stored into S3.

![1.jpg](/images/1.jpg)


## Prerequisites

>Make sure your are in US East (N. Virginia), which short name is us-east-1.


## Lab tutorial
#### Upload file to S3

1. 	On the service menu, click ‘S3’, Click ‘Create Bucket’.

2. 	For Bucket Name, type **‘Unique Name’**.

3. 	For Region, choose ‘US East (N. Virginia)’, Click ‘Create’.

4. 	Select the bucket which you created before, Click ‘Upload’, Click ‘Add files’.

5. 	Select the **day_part_two.csv** file which in the share folder, then choose Click ‘Start Upload’.


#### Working with Amazon Machine Learning

##### Create Model via Amazon Machine Learning

1. 	On the service menu, click ‘Machine Learning’.

2. 	Click ‘Get Started’ and ‘Launch’.

3. 	For ‘where is your data’, choose ‘S3’.

4. 	For **S3 location**, choose the s3 bucket location/file which you created.

5. 	For Datasource name, type ‘aml‐ver2’, Click ‘Verify’.

6. 	For S3 permissions, click ‘yes’ about Amazon ML needs read permission for this Amazon S3 location. Do you want to grant permission?

> Note: You will see ‘The validation is successful. To go to the next step, choose Continue’

7. 	Click ‘Continue’.

8. 	In Schema part:

* About first line in the column name, click **yes** when you see the question: Does the first line in your CSV contain the column names?
* For	Datatype,	choose	season/mnth/weekday/workingday/weathersit	as **Catagorical**
* For Datatype, choose cnt as **Numetric**
* Click ‘Continue’

9. 	In Target part:

* For target, choose ‘cnt’ as target for prediction
* Click ‘Continue’

10. 	In Row ID part:

* Click ‘Review’

11. 	In Review part:

* Click ‘Finish’

12. 	In ML model settings part:

* Click ‘Review’

13. 	In Review part:

* Click ‘Create ML Model’
* For this moment, you will see the message said ‘ status: Pending’, you can test this machine learning until the status go to ‘completed’

##### Testing with Amazon Machine Learning

14. 	For Dashboard, click ‘ML‐model’ which AML created. 

15. 	For the left panel, click ‘Try real-time predictions’

* For season, you can type 1 to 4
* For mnth, you can type 1 to 12
* For weekday, you can type 1 to 7
* For workingday, you can type 1 to 2
* For weathersit, you can type 1 to 4

16. Then, click ‘create prediction’, you will see the predict value in the right panel. 	


## End your lab

##### Delete S3

* On the service menu, click ‘S3’.
* Select the bucket which you created before.
* Select Action, then click ‘Delete Bucket’.
* Confirm the action, then delete the bucket.

##### Delete Amazon Machine Learning

* On the service menu, click ‘Machine Learning’.
* Select the items which you created before.
* Select ‘Actions’, then click ‘Delete’.
* Click ‘click’.
