---
layout: post
title: "Migrating multiple CharFields to null=False"
date: 2020-04-10 10:50:19
categories: ["Django"]
tags: ["code", "python"]
---

I am working on a simple project built on top of Django web framework. I have a user profile model that had 3 char fields that needed to be update from `null=True` to `null=False`
When I run `python manage.py migrate` on the django app I get the following error `django.db.utils.OperationalError: cannot ALTER TABLE "accounts_profile" because it has pending trigger events` To fix this I run the PostgreSQL shell (`psql`) to update and set the changed fields.
The SQL command for the fix is:
`db=# update accounts_profile set non_nullable_field = '' where non_nullable_field is null;`
I run the same command for the other two different fields.
Follow me on twitter [@bmwasaru](https://twitter.com/bmwasaru)