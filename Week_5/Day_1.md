# SQL Intro

## Topics
### Intro to RDBMS
### Relational Data Model (Tables, Columns, Rows)
### SELECT Statements
  * Filtering, ordering, limiting, etc.
  * Joining tables
  * Grouping records
  * Aggregate functions
  * Other advanced examples

[Notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w05d01)
[Lecture here](https://us02web.zoom.us/rec/play/bhuDvQ_5oNWZPwV9fqmxaBitospw--l_DeBcSrCayTMmOeaGgS8qE3Kns7votUha3Sy3sXq5hVxqNqd6.m_wqeWmZeAFgEOwW?startTime=1600100366000&_x_zm_rtaid=-3UHTfQRRn2kaKVBbi5KAQ.1600177987611.30d02265316c7987d486a9442bffcc79&_x_zm_rhtaid=196)

### 3 pillars of web development
* Web servers
* Client side
* Databases (data must be stored seperately from the server so that it persists)

### RDBMS
* Relational DataBase Management Server
* Collection of relational databases
* 'psql' connects to postgreSQL (open source database software) on the command line

### Relational Data Model
* Tabular data => columns and rows
* Columns === fields (adjectives [first_name, email, etc.])
* Rows === records
  * Table is a collection of records that are similar in some way and conform to the same structure
  * S === Structured (NOSQL is not structured)
  * All users must have the same data in their records
* Each table is related to one or more other tables in the database
  * Post gets connected to user, order gets connected to a customer, etc.

### SELECT Statements
* SELECT === give me back information (Think of a GET request)
* Primary Key === unique identifier
  * Integers work best for this
* SELECT * FROM users === Hello World of databases (select all data from the database)
**Look into NPM Faker**
* Capitalize all SQL keywords to make easier reading, lowercase our created words to distinguish
* Use COUNT(*) to count all records (be careful with using MAX because records can be deleted! This does not give a count of all records)
**Cannot use "" in SQL, must use ''**
  * Double quotes === table name or column name
**No intrinsic order to databases!! Must sort them if you need them in a particular order**
* ASC (ascending) is the default so don't need to include it, DESC will reverse the order (can also use -[value] instead of DESC but this may not work in other SQL servers)
* AND will not work in ORDER BY, we need to use a comma to seperate the sort order
  * Second sort (sub-sort) is only applied if there is a tie in the first sort value
* Built-in function NOW() will automatically generate today's date! So we can easily query previous dates or future dates
  * Can also query this in select to see what NOW() is coming back with
  * This will default to midnight on the date you are querying so ensure this works for the data you need to query (it will include today's date)
* Can include comments in SQL queries using --
* Use DISTINCT to ensure there are no repeats in the data (each will appear only once)
  * Only works on single column queries because if you add more than one value that will mean one needs to be repeated in order to show the other value distinctly
* FK === Foreign Key => stores the PK (Primary Key) of another record, this record is now linked to another table
  * Albums is connected to Songs table with a single crow-foot line meaning albums (single line) is one to many songs (crows foot)
* SQL does not work well with ambiguity! We need to be specific about how tables can be joined together (which column in first table === column in second table)
  * JOIN songs ON albums.id = album_id <-- Think of accessing an object! This allows us to be specific about which table we are referring to
* GROUP BY allows us to group related records together using a criteria
* Use AS to alias a field so that it makes sense (what is that field about)
* Keywords need to be listed in a specific order to fire in the correct order
* We cannot user where when referring to aggregate data (count, max, etc.)
  * Must use HAVING (a WHERE for GROUP BY) => Must occur after GROUP BY
* You can use GROUP BY and HAVING without including them in SELECT (our output) but we don't get that visual cue that the call worked
* INNER JOIN === default JOIN statement
  * Like the overlap in a Venn diagram, includes only the records that match, anything else gets excluded
  * Can use LEFT JOIN (from table, in this case albums) or RIGHT JOIN (to table, in this case songs)
    * LEFT === TableA + matches from TableB
    * RIGHT === TableB + matches from TableA
    * Can also use FULL OUTER JOIN which includes everything from all tables
    * Can also exclude things that do match using NULL (only include data that does not match)
* To ROUND to 2 decimal places generate average, * 100, then divide whole thing by 100
  * Better practice to return the whole value! We can always round with JS before showing value to the user (especially with financial queries the fractions matter)
* Use sub-query to calculate average within WHERE statement since we cannot use aggregate functions in WHERE, use another SELECT statement
  * Sub-queries can be added to initial SELECT statement as well so we can compare and ensure the query is working
* LIMIT will only load a subset of the records so you can get an idea of hte dataset without loading 20000 records, for example
  * This is the last thing to run
* Match LIMIT with OFFSET which says how many records to skip (this way you can see a specific chunk of data, for example LIMIT 10 OFFSET 10 will show records 11-20)
  * Think of pages in google (you can see 10 records on page one, then next 10 on page 2, etc. => OFFSET increments every page)
    * LIMIT pageAmount OFFSET (pagenumber - 1) * pageAmount
  * OFFSET is always a multiple of LIMIT