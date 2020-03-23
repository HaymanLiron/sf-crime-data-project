# sf-crime-data-project
Project 2 of the Udacity Data Engineering ND

# Answers to questions in step 3

How did changing values on the SparkSession property parameters affect the throughput and latency of the data?


What were the 2-3 most efficient SparkSession property key/value pairs? Through testing multiple variations on values, how can you tell these were the most optimal?

1. How did changing values on the SparkSession property parameters affect the throughput and latency of the data?

Throughput and latency is best measured by the processedRowsPerSecond parameter in the Progress Reporter. If I use default settings, this stands at approx. 12 rows a second. 

By using these parameters: 
    spark.conf.set("spark.executor.memory", '8g')
    spark.conf.set('spark.executor.cores', '3')
    spark.conf.set('spark.cores.max', '3')
    spark.conf.set("spark.driver.memory", '8g')
it increased rapidly to 89 rows a second.

2. What were the 2-3 most efficient SparkSession property key/value pairs? Through testing multiple variations on values, how can you tell these were the most optimal? 

As I increase the driver and executor memory, the number of rows that can be processed increases. If I increase it to 16g each, it increases to 105 rows/second. So these settings are pretty significant.  

I can get to 118 rows a second if I increase the number of cores from 3 to 6. 

Becasuse I was running on local mode, I couldn't really take advantage of other settings related to parallelism. 
