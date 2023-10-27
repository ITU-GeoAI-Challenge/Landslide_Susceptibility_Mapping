
# GEO-AI Challenge for Landslide Susceptibility Mapping
This solution makes use of five files:
* 4 data files (all from the data provided as part of the competition):
  * 'Train.gpkg' which contains geometries classified as either susceptible or not.
  * 'geological_faults.gpkg' and 'land_use_land_cover.gpkg' for extracting
additional features about any specific land geometry that will aid in the
prediction of its susceptibility to landslides.
  * 'Test.gpkg' contains the data of locations for testing the performance of the
model

* A Jupyter notebook named 'GeoLandslide.ipynb' containing the code for handling
data, training model and predicting the landslide susceptibility of the test locations.
## The environment
The Jupyter notebook runs in a python environment. For a Google Colab CPU runtime type,
it lasts under 40 minutes.
No paid subscriptions or resources were used
## The Jupyter Notebook
* This notebook takes input of all 4 data files mentioned previously and outputs
'Submission.csv'.
* To run the notebook the 'data_path'' variable must contain the path to the directory
containing all the data files mentioned previously.
* The notebook contains python code and the whole code runs on Google colab lasting
for under 40 minutes.
* The General Overview of the Notebook is as follows:
1. Importing Relevant libraries
geopandas (0.13.2), pandas (1.5.3), numpy (1.23.5), scikit-learn (1.2.2),
imbalanced-learn (0.10.1)
2. Reading and Cleaning Data
3. Engineering Features
The features fed into the model are 38 and fall into 3 categories:
 - Features from the train and test geometries which include the area
('area') of the geometry under consideration
 - Features from the land-use-land-cover categories which make up the
geometry for which the susceptibility is being predicted.
This includes total area of each of the land-use-land-cover category
(eg: 'area_31' indicates the size of lands with land-use-land-cover
code of 31 ('cod_31') that fall within the geometry under consideration)
 - Features from geological fault lines that lie within the geometry for
which susceptibility is being predicted.
This includes the cumulative length ('SHAPE_LEN') of the fault lines
that falls within the geometry.
4. Developing Pipelines and training models
  * Pipeline involved scaling (standardScaler), selecting best features
(SelectKBest) and then fitting a RandomForestClassifier model
  * Prior to fitting the model to the training data, balance was introduced to the
number of landslide susceptible and landslide-proof observations by the help
of the SMOTE technique.
  * The model's hyperparameters were tuned using the RandomizedsearchCV
5. Predicting and preparing submission
  * Predictions are made on the data imported from 'Test.gpkg' which has been
transformed to include the same features as the train data.
  * The final predictions are exported to 'Submission.csv' in the same directory as
the jupyter notebook.
