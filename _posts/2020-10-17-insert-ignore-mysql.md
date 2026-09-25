---
layout: post
title: "INSERT IGNORE MySQL"
date: 2020-10-17 18:03:54
categories: ["MySQL", "sql"]
---

The `INSERT` MySQL statement allows you to add multiple rows into a table but should an error occur, MySQL terminates and returns an error. This means no row is inserted into the table. When you need to ignore the error and allow insertion of valid data the `INSERT IGNORE` statement is one you can use. MySQL will throw a warning but the valid data will be inserted into the table.

We will create a table `members` with a unique `mobile` column, this will be our constraint ensuring we don't duplicate mobile numbers.

`CREATE TABLE members (INT PRIMARY KEY AUTO_INCREMENT, mobile VARCHAR(13) NOT NULL UNIQUE  
);`

Now we insert a new row:

`INSERT INTO members(mobile) VALUES('+254711111111');`

This works fine, now lets try inserting three rows into the table

`INSERT INTO members(mobile) VALUES('+254711111123'), ('+254711111112'), ('+254711111111');`





We get this error because we are entering a duplicate mobile number +254711111111 resulting into the other two records not getting inserting into the table

`ERROR 1062 (23000): Duplicate entry '+254711111111' for key 'members.mobile'`

For us to allow insertion without worrying about the constraint we will use in the INSERT IGNORE statement as follows;



`INSERT IGNORE members(mobile) VALUES('+254711111123'), ('+254711111112'), ('+254711111111');`



This statement returns;



`Query OK, 2 rows affected, 1 warning (0.01 sec) Records: 3 Duplicates: 1 Warnings: 1`



We can deduct that 2 rows were inserted and we have 1 duplicate from the 3 records we intended to insert. Lets look at the warning;



```
SHOW WARNINGS;  
  
+---------+------+----------------------------------------------------------+  
| Level | Code | Message |  
+---------+------+----------------------------------------------------------+  
| Warning | 1062 | Duplicate entry '+254711111111' for key 'members.mobile' |  
+---------+------+----------------------------------------------------------+  
1 row in set (0.01 sec)
```



**NOTE: INSERT INTO is a MySQL extension of SQL**