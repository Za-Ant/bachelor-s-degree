## Bachelor Project

This repository contains machine learning files based on a gaming dataset, which includes information about sessions, player actions, and their characteristics. The project uses a series of Jupyter notebooks for step-by-step data preparation, feature engineering, class balancing, as well as building and training neural networks using TensorFlow, Keras, and Dask libraries.

### File Map:
- `db_splitter.ipynb`: splits a large session attribute dataset into separate CSV files by category.
  - loads **meta_sessions_attributes.csv** and attribute definitions from **meta_sessions_attributes_definitions.csv**
  - partitions data accordingly
---  
- `ad.ipynb`: prepares an enriched dataset based on game sessions and additional data sources.
  - loads **meta_session_new.csv** and **gems_spent.csv**
  - aggregates extra features from all CSV files in the directory (excluding files in extra_files)
  - merges session data and computes cumulative statistics per user
  - creates the final dataset with accumulated features and the target player_metric
  - supports distributed data processing via Dask
---    
- `neural_net1.ipynb`: implements a neural network using TensorFlow/Keras for gameplay data analysis.
  - loads and preprocesses data
  - uses Dask for distributed processing (Client setup)
  - builds a correlation matrix to analyze feature relationships with the target metric player_metric
  - constructs a fully connected neural network using Keras
--- 
- `classification2.ipynb`: performs data preparation and feature extraction for classification tasks.
  - loads original datasets: **meta_sessions.csv**, **meta_sessions_attributes.csv**, and feature definitions
  - uses Dask for scalable data processing
  - extracts feature indices based on definitions
--- 
- `easy_dataset_maker.ipynb`: creates a simplified dataset by selecting the first n = 100 users.
  - filters relevant session data from **meta_sessions.csv** and **meta_sessions_attributes.csv**
  - saves the result as **ms_new.csv**
---     
- `neural_net2.ipynb`: loads and processes pre-filtered datasets for neural network training.
  - uses **ms_new.csv** and **new_ms_attr.csv**
  - reads feature definitions from **meta_sessions_attributes_definitions.csv**
  - prepares input features for classification
  - initializes neural network weights
--- 
- `smote_classification.ipynb`:performs classification with class balancing using SMOTE.
  - loads **ms_new.csv** and **new_ms_attr.csv** using Dask
  - applies feature definitions from **meta_sessions_attributes_definitions.csv**
  - prepares data and applies SMOTE to address class imbalance
  - trains a classifier on the balanced dataset
--- 
- model Weights (.h5 Files): saved weights of trained neural networks using Keras/TensorFlow.
  These files are used for: restoring trained models without retraining, running inference on new data, comparing different architectures or training configurations.
  
  - `model.weights.h5`: Baseline model
  - `model1.weights.h5`: First alternative architecture/feature set
  - `model2.weights.h5`: Improved model
  - `model3.weights.h5`: Final or optimized version
--- 
- `raw_data.zip`: includes sampled data for the first 100 users:
  - **ms_new.csv**: Filtered session metadata (e.g., by game_id)
  - **new_ms_attr.csv**: Corresponding session attributes

The full version of the original data is available via a Google Drive link: https://drive.google.com/drive/folders/1zuZmxSQDj5UCKyD3Uic9ObXEXkl8zeXc?usp=sharing 

