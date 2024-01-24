---
title: "Python Knowledge"
tags: [python]
---

# Python Knowledge

## Reading & Writing Files
- [Python Official Docs - Reading & Writing files](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)

Search: `site:docs.python.org (TOPIC)`

```
f = open('data.txt', 'w', encoding="utf-8")
```

```
with open('data.txt', encoding="utf-8") as f:
    read_data = f.read()
```


For reading lines from a file, you can loop over the file object. 
```
for line in f:
    print(line, end='')
```
    This is the first line of the file.
    Second line of the file


## Replacing text

```
# References keyword argument 'name'
"My quest is {name}"              
```


## Strings
- https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str

### Quotes
    Single quotes: 'allows embedded "double" quotes'

    Double quotes: "allows embedded 'single' quotes"

    Triple quoted: '''Three single quotes''', """Three double quotes"""

Triple quoted strings may span multiple lines - all associated whitespace will be included in the string literal.

### Count occurances
https://docs.python.org/3/library/stdtypes.html#str.count
```
str.count
```

### Ends with
https://docs.python.org/3/library/stdtypes.html#str.endswith
```
str.endswith
```

### Combine text
https://docs.python.org/3/library/stdtypes.html#str.join
```
str.join
```

### Remove Prefix
https://docs.python.org/3/library/stdtypes.html#str.removeprefix
```
 str.removeprefix()
```

### Remove Suffix
https://docs.python.org/3/library/stdtypes.html#str.removesuffix

### Partition
https://docs.python.org/3/library/stdtypes.html#str.partition
```
 str.removeprefix()
```

### Replace text
https://docs.python.org/3/library/stdtypes.html#str.replace

### Split text
https://docs.python.org/3/library/stdtypes.html#str.split
```
'1,2,3'.split(',')
['1', '2', '3']
```

### Split lines
https://docs.python.org/3/library/stdtypes.html#str.splitlines

### Text starts with
https://docs.python.org/3/library/stdtypes.html#str.startswith

### Strip leading / training space
https://docs.python.org/3/library/stdtypes.html#str.strip

## Dictionary
https://docs.python.org/3/library/stdtypes.html#mapping-types-dict
```
 {'jack': 4098, 'sjoerd': 4127} or {4098: 'jack', 4127: 'sjoerd'}
```


`list(d)` - Return a list of all the keys used in the dictionary d.


`len(d)`  - Return the number of items in the dictionary d.


## Python & SQLite database
- https://docs.python.org/3/library/sqlite3.html



### Connect to database
```
import sqlite3
database_connection = sqlite3.connect("example.db")
```
https://docs.python.org/3/library/sqlite3.html#sqlite3.Connection

In order to execute SQL statements and fetch results from SQL queries, we need to use a database cursor.
```

database_cursor = database_connection.cursor()
```

### Create tables
Run database commands
```
# Create table
database_cursor.execute("CREATE TABLE movie(title, year, score)")
```

List database tables
```
query_result = database_cursor.execute("SELECT name FROM sqlite_master")
query_result.fetchall()
```


### Add data
Insert data into database
```
database_cursor.execute("""
    INSERT INTO movie VALUES
        ('Monty Python and the Holy Grail', 1975, 8.2),
        ('And Now for Something Completely Different', 1971, 7.5)
""")
```

Insert multiple data
```
data = [
    ("Monty Python Live at the Hollywood Bowl", 1982, 7.9),
    ("Monty Python's The Meaning of Life", 1983, 7.5),
    ("Monty Python's Life of Brian", 1979, 8.0),
]
database_cursor.executemany("INSERT INTO movie VALUES(?, ?, ?)", data)
# Remember to commit the transaction after executing INSERT.
database_connection.commit()  
```

Notice that `?` placeholders are used to bind data to the query. Always use placeholders instead of string formatting to bind Python values to SQL statements, to avoid SQL injection attacks (see How to use placeholders to bind values in SQL queries for more details).


### Save change to database
`database_connection.commit()`

### Search database
```
query_result = database_cursor.execute("SELECT score FROM movie")
query_result.fetchall()
```

The result is a list of tuples, one per row



Loop over a query:
```
for row in database_cursor.execute("SELECT year, title FROM movie ORDER BY year"):
    print(row)
```


Verify that the database has been written to disk by calling `datbase_connection.close()` to close the existing connection

```
database_connection.close()
```

### Backup database
- https://docs.python.org/3/library/sqlite3.html#sqlite3.Connection.backup

### Database cursors
- https://docs.python.org/3/library/sqlite3.html#cursor-objects

### Execute many statements
- https://docs.python.org/3/library/sqlite3.html#sqlite3.Cursor.executemany

### Fetch Many (to List)
- https://docs.python.org/3/library/sqlite3.html#sqlite3.Cursor.fetchmany

### Fetch all
- https://docs.python.org/3/library/sqlite3.html#sqlite3.Cursor.fetchall

### Database Errors
- https://docs.python.org/3/library/sqlite3.html#exceptions
https://sqlite.org/rescode.html

### Database / Python Data types
- https://docs.python.org/3/library/sqlite3.html#sqlite-and-python-types

### SQLite Command line interface (CLI)
- https://docs.python.org/3/library/sqlite3.html#command-line-interface

### Adding Data using Placeholders
Use placeholders to bind values in SQL queries
- https://docs.python.org/3/library/sqlite3.html#how-to-use-placeholders-to-bind-values-in-sql-queries

To insert a variable into a query string, use a placeholder in the string, and substitute the actual values into the query by providing them as a tuple of values to the second argument of the cursor’s execute() method.

```
con = sqlite3.connect(":memory:")
cur = con.execute("CREATE TABLE lang(name, first_appeared)")

# This is the named style used with executemany():
data = (
    {"name": "C", "year": 1972},
    {"name": "Fortran", "year": 1957},
    {"name": "Python", "year": 1991},
    {"name": "Go", "year": 2009},
)
cur.executemany("INSERT INTO lang VALUES(:name, :year)", data)
```

## Classes, attributes

```
class Point:
    def __init__(self, x, y):
        self.x, self.y = x, y
```

## Lists
- https://docs.python.org/3/library/stdtypes.html#lists

## Tuples
- https://docs.python.org/3/library/stdtypes.html#tuple

## Date & time
```
def adapt_date_iso(val):
    """Adapt datetime.date to ISO 8601 date."""
    return val.isoformat()

def convert_date(val):
    """Convert ISO 8601 date to datetime.date object."""
    return datetime.date.fromisoformat(val.decode())

def convert_datetime(val):
    """Convert ISO 8601 datetime to datetime.datetime object."""
    return datetime.datetime.fromisoformat(val.decode())

def convert_timestamp(val):
    """Convert Unix epoch timestamp to datetime.datetime object."""
    return datetime.datetime.fromtimestamp(int(val))

```

```
import datetime

d = datetime.datetime(2010, 7, 4, 12, 15, 58)

'{:%Y-%m-%d %H:%M:%S}'.format(d)
'2010-07-04 12:15:58'
```

### Database files

Store database in memory
```
con = sqlite3.connect(":memory:")
```
