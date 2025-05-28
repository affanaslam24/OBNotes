AWS Glue retrieves data from sources and writes data to targets stored and transported in various data formats. AWS Glue supports using the Parquet format. This format is a performance-oriented, column-based data format You can use AWS Glue to read Parquet files from Amazon S3 and from streaming sources as well as write Parquet files to Amazon S3. You can read and write `bzip` and `gzip` archives containing Parquet files from S3.

When a crawler runs, it takes the following actions to interrogate a data store:

**Classifies data to determine the format, schema, and associated properties of the raw data** – You can configure the results of classification by creating a custom classifier.

**Groups data into tables or partitions** – Data is grouped based on crawler heuristics.

**Writes metadata to the Data Catalog** – You can configure how the crawler adds, updates, and deletes tables and partitions.

Hence, the correct answer is the option that says: ***Use AWS Glue crawler to automatically discover the raw data file in S3 as well as check its corresponding schema.* Create a scheduled ETL job in AWS Glue that will convert .csv files to Apache Parquet format and store the output of the processed files in the “`tutorialsdojo-data-transformed`" bucket.**


GLue and emr is used for etl purposes and different proccesses. Hadoop and spark comes to mind.
But whenever you see spark or apache, think of glue.



