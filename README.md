# Unearthed Explore Australia: Gold Deposit Prediction

## Flatiron School Capstone Project

### Author: Mark Subra
This project is the capstone project for the Data Science Immersive Bootcamp at Flatiron School. The project is based on the [Unearthed: Explorer Challenge](https://unearthed.solutions/u/challenge/generate-new-knowledge-predicting-all-australian-mineral-deposits). The scale of the challenge was too large to be able to complete in the timeframe given, so a binary classification of gold mines was eventually decided to be the goal.

![Unearthed](https://unearthed.solutions/u/sites/default/files/challenge-images/unnamed.jpg)

## Presentation
[Link to be added]

### Business Understanding and Background
Every year, each person in the United states uses [40,633 pounds of new minerals](https://mineralseducationcoalition.org/wp-content/uploads/2019-Mining-Cart-Per-Capita-color.pdf). Mining involves many challenges from exploration to environmental remediation. Ore-bearing, large-scale deposits are rare due to various geological processes taking place in combination over time. Predicting mineral deposits will lower exploration costs and unnecessary drilling and/or excavation which will also cause less harm to the environment.

### Data
The data are provided by OZ Minerals as a set of images including satellite imagery, geophysical, and geologic data. This particular project used the training dataset which contained over 30,000 images which was then divided into a 75%-25% train-test split designated by ID number and commodities present such as gold, copper, iron, platinum, etc.

![Images](https://github.com/jesserobertson/explore_australia/raw/master/resources/layer_examples.png?raw=true)

### Data Preparation - Statistical Models
The images were processed using the rasterio library which specializes in geospatial data, and the method can be seen in the [Image Processing](https://github.com/geomms/Unearthed_Explore_Australia_Flatiron_School_Capstone_Project/blob/master/Image%20Processing.ipynb) notebook. This was done with assistance from another [notebook](https://github.com/pedrojunqueira/ExploreSA/blob/master/MyNBs/First%20Exploration%20Trainset.ipynb) which was of great help in processing the images. A corresponding numerical value to the categroy of image was then input into a dataframe for every ID as well as the primary mineral.

### Data Preparation - VGG16 Convolutional Neural Network (CNN)
The second method in processing and classifying data was the VGG16 CNN whose notebook can be seen [here](https://github.com/geomms/Unearthed_Explore_Australia_Flatiron_School_Capstone_Project/blob/master/VGG16.ipynb). The images were split 75%-25% into training and test with 8 IDs for validation. This was created with assistance from a [kaggle notebook](https://www.kaggle.com/carloalbertobarbano/vgg16-transfer-learning-pytorch) demonstrating this method on images of retinal data.

![VGG](https://it.mathworks.com/content/mathworks/it/it/discovery/convolutional-neural-network/_jcr_content/mainParsys/image_copy.adapt.full.high.jpg/1523891801700.jpg)

### Modeling
Several models were used to classify the deposits with varying degrees of accuracy.
  - [Random Forest Multi Class Baseline](https://github.com/geomms/Unearthed_Explore_Australia_Flatiron_School_Capstone_Project/blob/master/Baseline%20Model%20Random%20Forest.ipynb): 
    - Accuracy: 
      - Train: 0.9826
      - Test: 0.5697
     - Balanced Accuracy:
      -
