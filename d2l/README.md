# How to setup and run the 'Dive into Deep Learning' course in Amazon SageMaker Studio Lab

To run the D2L course, you need to upload these files into your Amazon SageMaker Studio Lab 'Project' (aka Jupyter Lab):

- d2l-env.yml
- Setup.ipynb

## Instructions 

Login to Amazon SageMaker Studio Lab and create a new project. For D2L, this will need to be a GPU project, since we are doing Deep Learning which requires access to a Graphics Card in the later chapters of the course. 

'Open Project'

This will start Jupyter Lab.

Navigate to the /d2l/ folder in Jupyter Lab.

Right click on the `d2l-env.yml` file and choose 'Build Conda Environment'. This will start a Terminal Session and run Conda commands to install the necessary libraries for running D2L.

Double-click on the `Setup.ipynb` file to open it, and run through all the cells. This will download and unpack the ZIP file containing all the 'Dive into Deep Learning' artifacts.

