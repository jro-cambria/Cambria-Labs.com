---
title: "SQLite database Knowledge"
tags: [databases]
---
# SQLite database Knowledge

## SQLite command line interface (CLI)
- https://sqlite.org/cli.html

### SQLite commands
```
.help - usage hints.
.dbinfo ?DB?             Show status information about the database
.dump ?OBJECTS?          Render database content as SQL
.excel                   Display the output of next command in spreadsheet
.import FILE TABLE       Import data from FILE into TABLE
.indexes ?TABLE?         Show names of indexes
.lint OPTIONS            Report potential schema issues.
.output ?FILE?           Send output to FILE or stdout if FILE is omitted
.read FILE               Read input from FILE or command output
.recover                 Recover as much data as possible from corrupt db.
.save ?OPTIONS? FILE     Write database to FILE (an alias for .backup ...)
.tables ?TABLE?          List names of tables matching LIKE pattern TABLE
.timer on|off            Turn SQL timer on or off
```

### Create table
```

$ sqlite3 example_database
SQLite version 3.36.0 2021-06-18 18:36:39

sqlite> create table tbl1(one text, two int);
sqlite> insert into tbl1 values('hello!',10);
sqlite> insert into tbl1 values('goodbye', 20);
sqlite> select * from tbl1;
hello!|10
goodbye|20
sqlite>

```

### SQL statements
Terminated by either a ';' character at the end of an input line


### Output formats
The sqlite3 program is able to show the results of a query in different output formats.
    csv
    column
    html
    insert
    json
    list
    markdown
    table
    tabs
Use the ".mode" dot command to switch between these output formats. The default output mode is "list". 


### Read SQL from a file
```
sqlite> .read myscript.sql
```


### Export to CSV
```
sqlite> .headers on
sqlite> .mode csv
```


### Archive Database
```
$ sqlite3 example_database .dump | gzip -c > example_database.archive.gz

```