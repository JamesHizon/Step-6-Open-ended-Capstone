# Step 6 Open-ended Capstone

### Description
Within this Step, I used AWS S3 and EMR Notebook, where I developed a class called ```DataPipeline``` which has 4 main methods needed for extracting data, loading, copying and deleting, and removing files. I mainly have the first three up and running, and will make updates to the ```remove_all_files``` method as necessary to ensure I remove files outside of the desired file folder. Yet, since time is limited, I will mainly try to just deal with the first three. Ignore the other methods that I am still deciding if I should keep.

Data Pipeline Methods:
1. ```extract_load()``` - used to scrape data and automatically load files (apply array slicing to specify how many to download, i.e. 100 GBs or in our case, nearly 20-50 GBs of data).
2. ```spark_read_transform``` - with help of pyspark package, this is used to read and transform data as desired for the two different data streams and write to desired location using ".repartition(1)".
3. ```s3_copy_delete``` - used to copy file that has been repartitioned inside a temporary folder to the desired "Data_Stream_1" folder or "Data_Stream_2" folder, and then deleted the temporary folder.
4. ```remove_all_files``` - Used to delete all files with ".csv" and does not contain the folder name in the file path.

Previously, I had tried to scrape data and transform data using pandas for a few files. I then scaled my solution to use the ```PySpark API```. In order for me to interact with AWS S3 inside EMR Cluster, I needed to ensure I properly set my EMR Cluster configuration settings so I can interact with S3, and used the ```boto3``` Python package to gain access to S3 via S3 resource object.

### How to Install Packages inside EMR Notebook:
```
sc.install_pypi_package("boto3")
sc.install_pypi_package("pandas")
sc.install_pypi_package("requests")
sc.install_pypi_package("bs4")
```

### How to interact with AWS S3 via boto3:
You can first create an s3 object, followed by working with the available attributes and methods attached to the corresponding method.
For example, something simple we can do is observe which buckets are available inside your S3 bucket as follows.
```
s3 = boto3.resource("s3")
for bucket in s3.buckets.all():
  print(bucket)
```

### Uploaded Files
This repository will include the following 3 items:
1. Jupyter Notebook file that I used via EMR Notebook on AWS
2. Snapshot of AWS EMR Cluster creation
3. Snapshot of AWS EMR Notebook
4. Snapshot of AWS S3 Bucket used to store data

### Challenge:
There wasn't sufficient space on EMR Cluster to download all of first ~1000 files, so I tried to start a new cluster to begin trying to download the next 1000 files. Thus, there will be a gap in regards to dates, but the cool thing is that I can still try and get nearly 100 GBs of data uploaded as well as diversity of data ranging from first six months of 2021 and span to 6 months within the intersection of the end of 2019 and early 2020.

