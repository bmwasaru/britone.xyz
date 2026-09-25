---
layout: post
title: "Heroku Database Credentials"
date: 2020-12-10 14:48:47
categories: ["heroku", "python"]
---

When deploying to Heroku and use a database it creates the DATABASE\_URL environment variable for you that you can connect your application with.



With python you can access this using the `os` module as follow:



`os.environ.get('DATABASE_URL')`



Though you might need to access the different details like; database name, user and password. Here is how I get to access this details, in this example I am using ClearDB, MySQL host provider.



```
import os


if os.environ.get('CLEARDB_DATABASE_URL'):
    db_url = os.environ['CLEARDB_DATABASE_URL']
    mysql_database = db_url.split('/')[3]
    mysql_user = db_url.split('//')[1].split(':')[0]
    mysql_password = db_url.split('@')[0].split(':')[2]
    mysql_host = db_url.split('@')[1].split('/')[0]
else:
    mysql_database = ""
    mysql_user = ""
    mysql_password = ""
    mysql_host = "localhost"
```



Follow me on twitter here <https://twitter.com/bmwasaru>