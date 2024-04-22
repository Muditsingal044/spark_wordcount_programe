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

conf = SparkConf().setAppName("WordCount")
sc = SparkContext(conf=conf)


lines = sc.textFile("input.txt")


words = lines.flatMap(lambda line: line.split())


word_counts = words.map(lambda word: (word, 1))


word_counts = word_counts.reduceByKey(lambda x, y: x + y)


word_counts_list = word_counts.collect()
for word, count in word_counts_list:
    print(f"{word}: {count}")


sc.stop()

.......................................................................


## 4. add line in input.txt -> 

i am mudit 
i am human

.............................................

## CMD ->

5. spark-submit wordcount.py












