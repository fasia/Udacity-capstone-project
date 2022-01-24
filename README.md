
# Inventory Monitoring 
Keeping the right number of parts and products in a packaging customer orders, is one of the challenges that distribution centers and warehouses face. Inventory monitoring is a process to check the number of products in inventories as well as the number of ordered items in packages. Distribution centers use robots to move items as a part of their operations. Items are carried in “bins” which can contain multiple items. Due to the massive amount of bins that should be delivered every day, computer vision is an excellent automation choice to verify the number of items in each bin before packaging and delivery. 

In this project, I use a public dataset from Amazon Bin Image Dataset, which contains more than 500,000 bin images. I use Amazon Sagemaker for pre-processing a part of dataset and store them in a S3 bucket. Moreover, I use pre-trained machine learning model to speed up the training process. 

## Project Requirements
What is required for replicate this project.

- An 'AWS' account.
- An 'S3' bucket to upload the project's data.
- A 'SageMaker Notebook Instance,' a machine learning (ML) compute instance running the 'Jupyter Notebook' App.
- Clone to git repository "https://github.com/udacity/nd009t-capstone-starter.git"
- open the starter folder and follow the instructions in `sagemaker.ipynb` 
- The neccessary files to run the projects are available in repository. 
- Kernel to use is `conda_pytorch_latest_p36` or similar 
- At the end of the project stop the kernel.

## Dataset
The dataset can be found in "https://registry.opendata.aws/amazon-bin-imagery/"

### Overview
The dataset containes images od bins with the items inside them. The project goal is to create a machine learning system which can count the number of items in given images of bins. 

### Access
To copy a single bin-image from AWS we can run `!aws s3 cp s3://aft-vbi-pds/bin-images/XXXX.jpg XXXX.jpg --no-sign-request` 
To copy the metadata of a single bin-image from AWS: `!aws s3 cp s3://aft-vbi-pds/metadata/XXXX.json XXXX.json --no-sign-request`

## Model Training
The model that is used for the training is ResNet50. We use a hpo range for hyperparameter tuning to find the best hyperparameters for our model. We use this model because is strong model for image detection and recognition. The hyperparameters that we are using for this project are `learning_rate` and `batch_size`. 
The evaluation metric that we use in the project is `Cross Entropy Loss`.

## Pipeline
The project pipeline is as follow:

- Upload training data to an S3 bucket.
- Model training script to train a model on the dataset.
- Train the train model in SageMaker
- Evaluate the model by creating a benchmark model and comparing its Testing Loss and Testing Accuracy with our model's.

## Standout Suggestions
(Optional) 
- Debugging and Profiling the model
- Deploy an endpoint which gets an image and responses an array of predictions.

