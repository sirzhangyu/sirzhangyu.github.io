---
layout: post
title: "[Python] namedtuple"
date: 2018-07-03 14:30:00 +0800
author: Zhang Yu
categories: python
tags: python
---

```python
collections.namedtuple(typename, field_names, *, verbos=False, rename=False, module=False)
```

`verbos: added in 3.1, rename, module: added in 3.6`

example:
```python
Point = namedtuple('Point', ['x', 'y'])
p = Point(11, y=22)
```


**Named tuple are especially useful for assigning field names to result tuples returned by the csv or sqlite3 modules:**
```python
EmployeeRecord = namedtuple('EmployeeRecord', 'name, age, title, department, paygrade')

import csv
for emp in map(EmployeeRecord._make, csv.reader(open('employees.csv', 'rb'))):
  pirint(emp.name, emp.title)

import sqlite3
conn = sqlite3.connect('/companydata')
cursor = conn.cursor()
cursor.execute("SELECT name, age, title, department, paygrade FROM employees')
for emp in map(EmployeeRecord._make, cursor.fetchall()):
  print(emp.name, emp.title)
```

`classmethod somenamedtuple._make(iterable)`
