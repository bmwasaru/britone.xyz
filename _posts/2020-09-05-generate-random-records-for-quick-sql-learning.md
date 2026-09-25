---
layout: post
title: "Generate random records for quick SQL learning"
date: 2020-09-05 20:23:11
categories: ["sql"]
---

Here is a scenario; you want to run SQL queries on a large dataset but you do not this size of data in a database for you to be able to run your queries, the reason for wanting to do could be purely for learning something new or test on fake data. Luckily database systems have some form of random function to let us do this. The following SQL queries will help illustrate this:



First I will create a database called learnings and connect to this database



```
root=# CREATE DATABASE learnings; 
root=# \c learnings;
```



I will create the item table with name and price columns






```
learnings=# DROP TABLE IF EXISTS item CASCADE;
learnings=# CREATE TABLE item ( id serial PRIMARY KEY, name TEXT NOT NULL, price INT NOT NULL);
```



Now we need to generate random item names and prices and insert into our table



```
learnings=# INSERT INTO item (name, price) SELECT random()::text, (random() * 1000)::int FROM generate_series(0, 10000);
```



To confirm this we can run count the number of rows:



```
learnings=# SELECT COUNT(*) FROM item;
 count 
-------
 10001
(1 row)
```



This is how the records looks like



```
learnings=# SELECT * FROM item LIMIT 10;
 id |        name         | price 
----+---------------------+-------
  1 | 0.6466864528333005  |   617
  2 | 0.6869094458296274  |   274
  3 | 0.9281113108784851  |    82
  4 | 0.693868683310356   |   686
  5 | 0.42091712212046417 |   288
  6 | 0.840926035554844   |   819
  7 | 0.5463565203279828  |   497
  8 | 0.591873872733359   |   954
  9 | 0.33089428807260646 |   435
 10 | 0.23777077297054916 |   723
(10 rows)
```