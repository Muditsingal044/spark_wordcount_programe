# spark_wordcount_programe

..................................................................................

# wordcount programe
************************************************

## CMD ->
1. mkdir wordcount.py  

2. mkdir input.txt 

............................................................

## 3. add this programe in wordcount.py  ->

from pyspark import SparkContext, SparkConf

# Create a SparkContext
conf = SparkConf().setAppName("WordCount")
sc = SparkContext(conf=conf)

# Load the input data from a text file
lines = sc.textFile("input.txt")

# Split each line into words
words = lines.flatMap(lambda line: line.split())

# Map each word to a tuple of (word, 1)
word_counts = words.map(lambda word: (word, 1))

# Reduce by key to count occurrences of each word
word_counts = word_counts.reduceByKey(lambda x, y: x + y)

# Collect the result locally and print it
word_counts_list = word_counts.collect()
for word, count in word_counts_list:
    print(f"{word}: {count}")

# Stop the SparkContext
sc.stop()

.......................................................................


## 4. add line in input.txt -> 

i am mudit 
i am human

.............................................

## CMD ->

5. spark-submit wordcount.py












