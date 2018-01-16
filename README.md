# Text-Classification-with-Spark-on-Amazon-EMR-Hadoop-Cluster
Classify customer reviews on automobiles into five classes using Spark MLLib on an Amazon EMR Hadoop cluster.

Data Extraction

Download the dataset from the link, and then save it into local disk. http://snap.stanford.edu/data/amazon/productGraph/categoryFiles/reviews_Automotive_5.json.gz

Run this data_extraction.py to extract the fiels of Overall and ReviewTexts, and then save them into a text file: reviews_Automotive.txt

Package the Scala Project with SBT

Download sbt.rar and unpack it into C:\project\

In the folder: C:\project\sbt, run: $ sbt assembly

Run the Spark Application on Amazon EMR Cluster

upload the Executable Jar file (CustomerReviewClassificationEMR-assembly-1.0.jar) located in the folder: C:\project\sbt\target\scala-2.11, to s3 bucket: s3://yifengspark

upload the dataset (reviews_Automotive.txt) to s3 bucket: s3://yifengsparkdata

sign in to Amazon AWS account, and create an EMR cluster (Spark 2.0.2 on Hadoop 2.7.3 YARN with Ganglia 3.7.2 and Zeppelin 0.6.2)

click "Add Step" to submit the Spark application: a) in the field of Spark-submit options, enter: --class CustomerReviewClassificationEMR --verbose; b) in the field of Application Location, enter: s3://yifengspark/CustomerReviewClassificationEMR-assembly-1.0.jar

run the Spark application, and check the output result from s3 bucket (if you have stored the result to s3 bucket in your Scala source code.)
