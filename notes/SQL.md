Structured Query Language

Relational Database Management System

# Syntax

- SQL keywords are NOT case sensitive
- Semicolon is the standard way to separate each SQL statement in database systems that allow more than one SQL statement to be executed in the same call to the server.
- Database contains tables that are comprised of **columns** and **records**.
- comment: --single line /* */ multiple lines
- keywords for different system is different, followings are for SQL Server

# 增删改查

**Select**

```sql
-- 1
SELECT column1, column2, ... FROM table_name;

-- 2
SELECT * FROM table_name;

-- 3 distinct
SELECT DISTINCT column1, column2, ...FROM table_name;
--The SELECT DISTINCT statement is used to return only distinct (different) values.

-- 4 order by, sort the result-set in ascending or descending order.
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC(default)|DESC;

-- 5 use top limit... keywords to select the first n rows

-- 6 as
SELECT CustomerName AS Customer, ContactName AS [Contact Person]
FROM Customers;

SELECT CustomerName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
FROM Customers;

SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName='Around the Horn' AND c.CustomerID=o.CustomerID;

-- INTO
SELECT *
INTO newtable [IN externaldb]
FROM oldtable
WHERE condition;
```

```sql
-- 7 The `GROUP BY` statement is often used with aggregate functions (`COUNT()`, `MAX()`, `MIN()`, `SUM()`, `AVG()`) to group the result-set by one or more columns.
-- The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions.

SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);

SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country;

SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5;
```



**Where (condition)**

where can be used to select insert delete update,,,

```sql
-- extract only those records that fulfill a specified condition.
SELECT column1, column2, ...
FROM table_name
WHERE condition;

SELECT * FROM Customers
WHERE Country='Mexico';

-- operator for condition:
-- =,>,<,!=,>=,<=,BETWEEN 50 AND 60,IN ('Paris','London'),LIKE 's%',

-- combine condition with AND OR NOT
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;

SELECT * FROM Customers
WHERE City='Berlin' OR City='München';

SELECT * FROM Customers
WHERE NOT Country='Germany';
```



**Insert**

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

INSERT INTO table_name
VALUES (value1, value2, value3, ...); -- adding values for all the columns of the table

INSERT INTO table2 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;
```



**Update**

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

**Delete**

```sql
DELETE FROM table_name WHERE condition;
```



# Operator

MIN(), MAX(), COUNT(), AVG(), SUM()

```sql
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```

**LIKE pattern**

Wildcards are often used in conjunction with the `LIKE` operator:

| %    | Represents zero or more characters                         | bl% finds bl, black, blue, and blob     |
| ---- | ---------------------------------------------------------- | --------------------------------------- |
| _    | Represents a single character                              | h_t finds hot, hat, and hit             |
| []   | Represents any single character within the brackets        | h[oa]t finds hot and hat, but not hit   |
| ^    | Represents any character not in the brackets               | h[ ^oa]t finds hit, but not hot and hat |
| -    | Represents any single character within the specified range | c[a-b]t finds cat and cbt               |

```
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;

```

**In**

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);

SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```

**Union and Union ALL**

- combine the result-set of two or more `SELECT` statements.

- Every `SELECT` statement within `UNION` must have the same number of columns
- The columns must also have similar data types
- The columns in every `SELECT` statement must also be in the same order

```
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City;

SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION ALL
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
```

**EXISTS**

The `EXISTS` operator is used to test for the existence of any record in a subquery.

The `EXISTS` operator returns TRUE if the subquery returns one or more records.

```sql
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);

SELECT SupplierName
FROM Suppliers
WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND Price < 20);
```

**ANY and ALL**

```
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY/ALL
  (SELECT column_name
  FROM table_name
  WHERE condition);
  
SELECT ProductName
FROM Products
WHERE ProductID = ANY
  (SELECT ProductID
  FROM OrderDetails
  WHERE Quantity = 10);
```



# Join

- `(INNER) JOIN`: Returns records that have matching values in both tables
- `LEFT (OUTER) JOIN`: Returns all records from the left table, and the matched records from the right table
- `RIGHT (OUTER) JOIN`: Returns all records from the right table, and the matched records from the left table
- `FULL (OUTER) JOIN`: Returns all records when there is a match in either left or right table

```sql
SELECT column_name(s)
FROM table1
INNER JOIN/LEFT JOIN/RIGHT JOIN/FULL JOIN table2
ON table1.column_name = table2.column_name;
```

**self join**

```
SELECT column_name(s)
FROM table1 T1, table1 T2
WHERE condition;

SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City
FROM Customers A, Customers B
WHERE A.CustomerID <> B.CustomerID
AND A.City = B.City
ORDER BY A.City;
```

# Database

**database**

```sql
CREATE DATABASE databasename; -- create db

DROP DATABASE databasename; -- drop db

BACKUP DATABASE databasename
TO DISK = 'filepath';
-- back up db

BACKUP DATABASE databasename
TO DISK = 'filepath'
WITH DIFFERENTIAL;
-- only backs up the parts of the database that have changed since the last full database backup.
```

**table**

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);

CREATE TABLE new_table_name AS
    SELECT column1, column2,...
    FROM existing_table_name
    WHERE ....;
    
DROP TABLE table_name;

-- add column
ALTER TABLE table_name
ADD column_name datatype;
-- drop column
ALTER TABLE table_name
DROP COLUMN column_name;
-- change data type or constraint
ALTER TABLE table_name
ALTER COLUMN column_name datatype;
```

datatype: https://www.w3schools.com/sql/sql_datatypes.asp

**Constraint**

specify rules for the data in a table.

The following constraints are commonly used in SQL:

- `NOT NULL` - Ensures that a column *cannot have a NULL value*
- `UNIQUE` - Ensures that all values in a column are **different**
- `PRIMARY KEY` - A combination of a `NOT NULL` and `UNIQUE`. Uniquely identifies each row in a table,only **one** `PRIMARY KEY` constraint per table.
- `FOREIGN KEY` - Prevents actions that would destroy **links** between tables
- `CHECK` - Ensures that the values in a column satisfies a specific condition
- `DEFAULT` - Sets a default value for a column if no value is specified
- `CREATE INDEX` - Used to create and retrieve data from the database very quickly

```sql
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    column3 datatype constraint,
    ....
);

CREATE TABLE Persons (
    ID int NOT NULL UNIQUE PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int CHECK (Age>=18),
    PersonID int FOREIGN KEY REFERENCES Persons(PersonID),
    City varchar(255) DEFAULT 'Sandnes'
);
```

**Index**

Indexes are used to retrieve data from the database more quickly than otherwise. ??

```
CREATE INDEX index_name
ON table_name (column1, column2, ...);

DROP INDEX table_name.index_name;
```

# SQL Injection

```
uName = getRequestString("username");
uPass = getRequestString("userpassword");

sql = 'SELECT * FROM Users WHERE Name ="' + uName + '" AND Pass ="' + uPass + '"'
```

if hacker enter " or ""=" for name and password, then the sql turns to:

```
sql = 'SELECT * FROM Users WHERE Name =" " or ""="" AND Pass ="" or ""=""'
```

Its always right.

So use **parameters** to protect. SQL parameters are values that are added to an SQL query at execution time, in a controlled manner.

```
txtNam = getRequestString("CustomerName");
txtAdd = getRequestString("Address");
txtCit = getRequestString("City");
txtSQL = "INSERT INTO Customers (CustomerName,Address,City) Values(@0,@1,@2)";
db.Execute(txtSQL,txtNam,txtAdd,txtCit);
```

The SQL engine checks each parameter to ensure that it is correct for its column and are treated literally, and not as part of the SQL to be executed.