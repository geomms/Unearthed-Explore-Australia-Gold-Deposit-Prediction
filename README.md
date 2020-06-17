# Unearthed Explore Australia: Gold Deposit Prediction

## Flatiron School Capstone Project

### Author: Mark Subra
This project is the capstone project for the Data Science Immersive Bootcamp at Flatiron School. The project is based on the [Unearthed: Explorer Challenge](https://unearthed.solutions/u/challenge/generate-new-knowledge-predicting-all-australian-mineral-deposits). The scale of the challenge was too large to be able to complete in the timeframe given, so a binary classification of gold mines was eventually decided to be the goal.

![Unearthed](https://unearthed.solutions/u/sites/default/files/challenge-images/unnamed.jpg)

## Presentation
![Link to be added](https://www.youtube.com/watch?v=r1W00fVjhk8&feature=youtu.be)

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

### Modeling - Statistical
Several models were used to classify the deposits with varying degrees of accuracy.
  - [Random Forest Multi Class Baseline](https://github.com/geomms/Unearthed_Explore_Australia_Flatiron_School_Capstone_Project/blob/master/Baseline%20Model%20Random%20Forest.ipynb): 
    - Accuracy: 
      - Train: 0.9826
      - Test: 0.5697
    - Balanced Accuracy:
      - Train: 0.9619
      - Test: 0.3080
  - [Binary Classification](https://github.com/geomms/Unearthed_Explore_Australia_Flatiron_School_Capstone_Project/blob/master/Binary%20Classification.ipynb) - Random Forest:
    - Accuracy:
      - Train: 0.8372
      - Test: 0.8250
    - Balanced Accuracy:
      - Train: 0.6451
      - Test: 0.6174
  - LGBM Classifier:
    - Accuracy:
      - Train: 1.0
      - Test: 0.8416
    - Balanced Accuracy:
      - Train: 1.0
      - Test: 0.6947
  - XGBoost:
    - Accuracy:
      - Train: 1.0
      - Test: 0.8274
    - Balanced Accuracy:
      - Train: 1.0
      - Test: 0.6778
  - Logistic Regression:
    - Accuracy:
      - Train: 0.7788
      - Test: 0.7565
    - Balanced Accuracy:
      - Train: 0.7501
      - Test: 0.6870
### Modeling - VGG16 CNN Transfer Learning
The model was trained using only a sample of 14 IDs of training data which trained for 2 and 4 epochs. It was then applied to the entire test set of 455 IDs. Notebook can be seen [here](https://github.com/geomms/Unearthed_Explore_Australia_Flatiron_School_Capstone_Project/blob/master/VGG16%20Test.ipynb)
  - Two epoch model:
     - Training completed in 17m 45s
        - Best accuracy: 0.6974
     - Evaluation completed in 100m 36s
        - Avg loss (test): 0.0834
        - Avg accuracy (test): 0.6709
  - Four epoch model:
     - Training completed in 28m 47s
        - Best accuracy: 0.7500
     - Evaluation completed in 76m 22s
        - Avg loss (test): 0.0712
        - Avg accuracy (test): 0.7463
### Conclusion and Further Work
The initial statistical models had certain perks, however the better method overall was the CNN with transfer learning since it only required a small training set to produce a good accuracy score. The neural network can be improved with training on the whole set or a larger training set as well as training for more epochs. The statistical models can also be improved with better feature engineering and integration with other types of data such as drill hole, seismic, geochemical, and other geologic data.

For exploration purposes, the random forest model would work the best. It did miss some gold deposits, however, of the gold deposits predicted, only 5 of 28 were false positives. This means that if an miners were scouting these 28 potential sites, 23 would be successful targets. In other words it is better to be sure of the deposits that are predicted than to simply increase accuracy.
