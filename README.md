# spark-examples
Contains spark examples in **Scala**

* ## Difference between **map** and **flatMap** transformations

Both **map** and **flatMap** are transformations on [**R**esilient **D**istributed **D**atasets](https://spark.apache.org/docs/latest/rdd-programming-guide.html#resilient-distributed-datasets-rdds), that return another RDD.

```scala

def tokenize(s: String) : Array[String] = s => s.split(" ")

```

```spark
val rdd = sc.parallelize(List("coffee panda", "happy panda", "happiest panda party"))

val mappedRDD = rdd.map(x => tokenize(x))
mappedRDD.collect() // prints Array(Array(coffee, panda), Array(happy, panda), Array(happiest, panda, party))

val flatMappedRDD = rdd.flatMap(x => tokenize(x))
flatMappedRDD.collect() // prints Array(coffee, panda, happy, panda, happiest, panda, party)
```
