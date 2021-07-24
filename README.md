# Step 6 Open-ended Capstone

### Description
Within this Step, I used AWS S3 and EMR Notebook, where I developed a class called ```DataPipeline``` which has 4 main methods needed for extracting data, loading, copying and deleting, and removing files. I mainly have the first three up and running, and will make updates to the ```remove_all_files``` method as necessary to ensure I remove files outside of the desired file folder. Yet, since time is limited, I will mainly try to just deal with the first three. Ignore the other methods that I am still deciding if I should keep.

Data Pipeline Methods:
1. ```extract_load()``` - used to scrape data and automatically load files (apply array slicing to specify how many to download, i.e. 100 GBs or in our case, nearly 20-50 GBs of data).
2. ```spark_read_transform``` - with help of pyspark package, this is used to read and transform data as desired for the two different data streams and write to desired location using ".repartition(1)".
3. ```s3_copy_delete``` - used to copy file that has been repartitioned inside a temporary folder to the desired "Data_Stream_1" folder or "Data_Stream_2" folder, and then deleted the temporary folder.
4. ```remove_all_files``` - Used to delete all files with ".csv" and does not contain the folder name in the file path.

### Uploaded Files
This repository will include the following 3 items:
1. Jupyter Notebook file that I used via EMR Notebook on AWS.
2. Snapshot of AWS EMR Cluster creation
3. Snapshot of AWS S3 Bucket used to store data.

