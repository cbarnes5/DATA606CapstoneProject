# DATA606CapstoneProject
Repository for UMBC Data Science MPS Capstone Project 

By: Crista Barnes and Rami Knio

### Instructions for Running Project Notebooks 

1. Run Building_Dataset.ipynb
   

   *This notebook takes the data from Redfin (located in the Data folder) and combines/cleans the data, as well as performs some basic EDA*

   *Output of notebook: finalcsv.csv*
   
3. Run Enriching_the_Dataset_with_OSMNX.ipynb

   *The notebook takes finalcsv and adds data from the Open Street Map package https://wiki.openstreetmap.org/wiki/Main_Page. It cleans the OSM data and calculates distances from each house to each point attraction and the edge of each park. It also creates a feature that adds all the areas of every park under 1km from each house*

   *Output of notebook: refined_data_sample.csv*

4. Run Exploring_Location_Options.ipynb

   *This notebooks takes finalcsv and adds a new feature that utilizes target encoding to combine information from the neighborhood and zip code columns to feed the model information about a house location. We target encoded on neighborhood when the neighborhood had at least 50 houses and on the zip code when the neighborhood had less than 50 houses*

   *Output of notebook: encoded_df.csv*

5. Run Pipeline_Example_v2.ipynb

   *This notebook combines refined_data_sample and encoded_df and runs a training dataset through a Linear Regression Model, an XGBoost Model and a Random Forest Model. The notebook selects the best performer and runs the testing dataset through the model to provide accuracy results*

#### Additional Notebooks

1. Base_Model_v2.ipynb - this notebook provides the testing that determines targeting encoding on neighborhoods that have at least 50 houses provides a better performance than using any lower threshold
2. Large_Park_Exploration.ipynb - this notebook provides visualization of the park dataset to validate cleaning operations that are carried out in Enriching_the_Dataset_with_OSMNX
3. More_Threshold_Testing.ipynb - this notebook proves targeting encoding on neighborhoods that have at least 50 houses is better than targeting encoding on only zip codes
