# SageMakerStudioLab-starter

This project is to help you understand how to use the free AWS Service **Amazon SageMaker Studio Lab**.

It contains some Jupyter Notebooks that walk you through some features of this service, and how they compare with Amazon SageMaker itself.

Note that "Amazon SageMaker Studio Lab" is intended to be used as a standalone free service for building Machine Learning models. 
It is a free stand-alone AWS Service, that does not require an AWS Account. 
By default, notebooks in the Lab are not able to connect to any AWS Service (unless you provide a suitable key/secret key combination).

So many of the existing SageMaker Jupyter notebooks will not work in the 'Lab'.

To help this transition, I am collating some of the common notebooks I have used in SageMaker, and re-factoring them to work in 'Lab. This typically means using SKLearn algorithms, rather than SageMaker algorithms. It also means that model training is done on the notebook itself, rather than by remotely doing training in the cloud. 

NOTE: This Repo is currently "work in progress"

## Key differences between Amazon SageMaker and Amazon SageMaker Studio Lab

Amazon SageMaker Studio Lab ('SMSL') should be thought of as an independent service, compared with other AWS Services such as S3, SageMaker, EC2 etc. You do not need to have an AWS Account in order to use SMSL.

1. SMSL is a free service. It requires separate username (email address) and password. Users request approval for a new account, which is typically approved in a few days. 
2. SMSL enables each user to run a Jupyter Lab Notebook instance for up to 12 hours. These can be either CPU- or GPU- types. After 12 hours, you can shut down that instance and restart it. 
3. It is not directly possible to connect to AWS Services such as S3. (You can call all AWS services from within SMSL but you need to have a key and secret key combination in order to do so. These services are then chargeable. )
4. There are no separate APIs for Training or Deployment.
5. All training and inferencing is done directly on the Notebook instance (rather than making API calls to SageMaker).
6. All data should be stored directly on the hard drive of the Notebook instance. 
7. For these reasons, SMSL is more like the "traditional" way of doing machine learning - creating a notebook and doing all data processing, training and inferencing directly on that notebook instance. 

## SageMaker Studio Lab Environments 

When you launch Amazon SageMaker Studio Lab, you have a basic Python environment. Additional libraries such as numpy, pandas, sklearn etc. are not installed by default. 
So before you can make use of a Jupyter Notebook, you need to run `conda` to install the necessary components. You do this by loading a YML file into Jupyter Lab which contains the dependencies. Inside the Jupyter Lab file browser, you right-click on that YML file and choose "Build Conda Environment". This opens up a Terminal Session and installs the packages.


The following is an example of a YML file which creates an environment called `titanic-env`:
```
name: titanic-env
dependencies:
  - python=3.9
  - pip
  - pip:
    - pip
    - setuptools
    - wheel
    - pandas
    - scikit-learn
    - nltk
    - matplotlib
    - numpy
    - seaborn
    - ipykernel
    - jinja2
```

When you run a specific Jupyter Notebook, you choose the Kernel which you have just created (in this case, called `titanic-env`)


You can find out what kernels are available by entering the following command at a terminal: `conda env list`
You can also use `conda env remove -n titanic-env` to delete the kernel called `titanic-env`


It is recommended that you remove any conda environments that you are not currently needing. 


