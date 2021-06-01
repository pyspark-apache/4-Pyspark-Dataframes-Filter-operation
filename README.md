# 4 Pyspark Dataframes Filter operation
1. [ Filter operations ](#schema1)
2. [& and](#schema2)
3. [| or](#schema3)
4. [~ not](#schema4)

<hr>

<a name="schema1"></a>

# 1. Filter operations
~~~python
### Salary of the people less than or equal 2000
df_pyspark.filter("Salary<=20000").show()
+-------+---+----------+------+
|   Name|age|Experience|Salary|
+-------+---+----------+------+
|  Sunny| 29|         4| 20000|
|   Paul| 24|         3| 20000|
| Harsha| 21|         1| 15000|
|Shubham| 23|         2| 18000|
+-------+---+----------+------+
df_pyspark.filter("Salary<=20000").select(["Name","age"]).show()
+-------+---+
|   Name|age|
+-------+---+
|  Sunny| 29|
|   Paul| 24|
| Harsha| 21|
|Shubham| 23|
+-------+---+
~~~

<hr>

<a name="schema2"></a>

# 2. & and
~~~python
df_pyspark.filter((df_pyspark["Salary"]<=20000)& (df_pyspark["Salary"]>=15000)).show()
+-------+---+----------+------+
|   Name|age|Experience|Salary|
+-------+---+----------+------+
|  Sunny| 29|         4| 20000|
|   Paul| 24|         3| 20000|
| Harsha| 21|         1| 15000|
|Shubham| 23|         2| 18000|
+-------+---+----------+------+

~~~
<hr>

<a name="schema3"></a>

# 3. | or
~~~python
df_pyspark.filter((df_pyspark["Salary"]<=20000)| (df_pyspark["Salary"]>=15000)).show()
+---------+---+----------+------+
|     Name|age|Experience|Salary|
+---------+---+----------+------+
|    Krish| 31|        10| 30000|
|Sudhanshu| 30|         8| 25000|
|    Sunny| 29|         4| 20000|
|     Paul| 24|         3| 20000|
|   Harsha| 21|         1| 15000|
|  Shubham| 23|         2| 18000|
+---------+---+----------+------+

~~~
<hr>

<a name="schema4"></a>

# 4. ~ not
~~~python
df_pyspark.filter(~(df_pyspark['Salary']<=20000)).show()
+---------+---+----------+------+
|     Name|age|Experience|Salary|
+---------+---+----------+------+
|    Krish| 31|        10| 30000|
|Sudhanshu| 30|         8| 25000|
+---------+---+----------+------+
~~~