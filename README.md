# DATA606CapstoneProject
Repository for UMBC Data Science MPS Capstone Project 

By: Crista Barnes and Rami Knio

### Instructions for Running Project Notebooks 

1. Run Building_Dataset.ipynb
   

   *This notebook takes the data from Redfin (located in the Data folder) and combines/cleans the data, as well as performs some basic EDA*

   *Output of notebook: finalcsv.csv*
   
3. Run Enriching_the_Dataset_with_OSMNX.ipynb

   *The notebook takes finalcsv and adds data from the Open Street Map package https://wiki.openstreetmap.org/wiki/Main_Page. It cleans the OSM data and calculates distances from each house to each point attraction and the edge of each park. It also creates a feature for all the areas of every park under 0.5, 0.75, 1, 1.25, 1.5, 1.75, 2, 2.25, and 2.5 km from each house and a crosses highway variable to determine if one needs to cross a highway to get to the largest park in all the above listed thresholds*

   *Output of notebook: refined_data_sample_distancetesting.csv*

4. Run Exploring_Location_Options.ipynb

   *This notebooks takes finalcsv and adds a new feature that utilizes target encoding to combine information from the neighborhood and zip code columns to feed the model information about a house location. We target encoded on neighborhood when the neighborhood had at least 50 houses and on the zip code when the neighborhood had less than 50 houses*

    *Output of notebook: encoded_df.csv*

5. Run Final_Model_Run_and_Save.ipynb

   *This notebooks takes refined_data_sample_distancetesting.csv and adds a column from encoded_df.csv for target encoding. We then select our final features to use based on analysis in other notebooks and hyperparameter tune an XGBoost model. This notebook also saves data, models, and a target encoding dictionary required for deployment*

   *Output of notebook: 'location_to_price_dict.pkl', 'X_raw_final.csv' 'X_train_final.csv', 'xgb_model_final.pkl', 'y_train_final.pkl'*

7. Run Model_Deployment_Final.ipynb

   *This notebook demonstrates model deployment on data from redfin. The dataset used contains houses on the market in the area of interest but have note been sold yet. The data was downloaded manually from redfin and uploaded to the github. This notebook performs preproccessing seen in Building_Dataset.ipynb and Enriching_the_Dataset_with_OSMNX.ipynb, then generates predictions using the files from Final_Model_Run_and_Save.ipynb* 

#### Additional Notebooks

1. Base_Model.ipynb - this notebook provides the proccess and results for building models just using the base data from redfin, no OSMNMX enhancements
2. Base_Model_v2.ipynb - this notebook is similar to Base_model.ipynb. It also incorporates target encoding and demonstrates an improvement in model performance
3. Pipeline_Example.ipynb - this notebook demonstrates how to read in new dataframes from github, preprocess data, and build/evaluate models based on the new data.
4. Pipeline_Example_v2.ipynb - this notebook is similar to Pipeline_Example. It was created to handle the incorporation of the target encoded variable, and includes some other minor changes.
5. Saving_training_data,_model,_etc.ipynb - this notebook was created for saving data needed for model deployment in an earlier stage of the project. It outputs files needed for Model_Deployment_Example.ipynb
6. Model_Deployment_Example.ipynb - this notebook displays an example of an earlier version of the model executed on one house listed on redfin that had not been sold yet
7. Base_Model_v2.ipynb - this notebook provides the testing that determines targeting encoding on neighborhoods that have at least 50 houses provides a better performance than using any lower threshold
8. Large_Park_Exploration.ipynb - this notebook provides visualization of the park dataset to validate cleaning operations that are carried out in Enriching_the_Dataset_with_OSMNX
9. More_Threshold_Testing.ipynb - this notebook is a follow up to Exploring_Location_Options.ipynb, where we confirm that 50 was our best threshold for target encoding
10. Distance_Threshold_Testing.ipynb - this notebook was used to determine our best threshold for greenspace area and crosses_highway, which turned out to be 2.5 km
11. Parks_and_Highways.ipynb - this notebook provides visualization and foundation of the code to get the Crosses_Highway variable available in Enriching_the_Dataset_with_OSMNX
