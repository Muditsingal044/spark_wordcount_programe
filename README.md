# spark_wordcount_programe

..................................................................................

# wordcount programe
************************************************

## CMD ->

0. spark-shell
1. cat >> input.txt
   i am mudit , i am human

2. hadoop fs -put input.txt /tmp

3. val text = sc.textFile("hdfs://hmaster:9000/tmp/input.txt")

4. text.collect;

5. var counts = text.flatMap(line => line.split(" "))

6. counts.collect

7. val mapf = counts.map(word => (word,1))

8. mapf.collect

9. val red=mapf.reduceByKey(_+_)

10. red.collect
