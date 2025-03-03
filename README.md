# End-to-End-Data-Engineering Project (SNOWFLAKE)

## Refer -  01_DB Schema Creation
Step 1: Create Dev_DB (Create 4 schemas under DEV_DB)
  1. Stage_SCH
  2. Clean_SCH
  3. Consumption_SCH
  4. Publish_SCH
     
Step 2: Create Warehouse 
  1. Load_WH : Load data to Stage_SCH (small/medium)
  2. Transform_WH : Tranform Data use Clean_SCH & Consumption_SCH (moderate/big warehouse depending on the size of data) 
  3. Stremalit_WH : Publish_SCH
  4. Adhoc_WH 

## Refer - 02_RAW_stg file 
Step 3: Create Internal Stage (RAW_stg) & File Format (JSON)

Step 4: Manulaly load json files into RAW_stg 

Step 5: Create a raw table to store air quality data

Step 6: Run COPY command to laod the data from json file to RAW_aqi table & create a TASK (that will load data evey hour) & will be created under Stage_SCH

## Refer -  03_CleanLayer   
Step 7: Flatten & De-duplicate 
  1. The record columns are stored within an array inside teh JSOn file format. In order to fetch these attributes we will have to faltten the JSON file using Lateral Flatten function & .notation to fetch exact         attributes. 
  2. We uploaded additional duplicate files. And then modified the SQL script to fetch only the oldest files accrording to the Timestamp column & discard the latest file. In our case we are considering the latest file to be a duplicate.
  3. Create Dynamic table so as to refresh the data with target_lag='downstream'


