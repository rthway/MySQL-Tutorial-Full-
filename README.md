# MySQL-Tutorial (Full) / MySQL Full Tutorial with example 
## MySQL intro + installation
### Windows installation

 - Download the MySQL Workbench installer for Windows from the official
   website (https://dev.mysql.com/downloads/workbench/) Once the
   download is complete, double-click on the installer file to start the
   installation process.  
  - Click on the "Next" button to proceed with the installation. Select the components that you want to install and
   - click "Next" Choose the location where you want to install MySQL
   Workbench and click "Next" Select the type of setup you want to use
   and click "Next" Enter your MySQL root password and click "Next"
   Review the settings and click "Install" Wait for the installation to
   complete and click "Finish" Launch MySQL Workbench from the start
   menu or the desktop shortcut. Connect to your MySQL server by
   entering the necessary connection details, such as the server
   address, username, and password. 
   Congratulations! You have   successfully installed MySQL Workbench on your Windows machine.

## DATABASES
**Creating Database:**

    Create database <db_name>
    create database employees

**use database :**

    use database <db_name>
    use employees;

**delete database:**

    drop database employees

## TABLES

Tables are the basic structure in a MySQL database that stores data in rows and columns. Each table has a unique name, and each column in the table has a name and data type.

**Creating a Table:**
Type the command "CREATE TABLE [table name] (column1_name data_type(size), column2_name data_type(size), ...);" and press enter.

Here's an example of the command to create a table called "employees":

    CREATE TABLE employees (id INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY, first_name VARCHAR(50) NOT NULL, last_name VARCHAR(50) NOT NULL, email VARCHAR(100) NOT NULL);

You can also create a table with foreign key constraints:

    CREATE TABLE orders (order_id INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY, customer_id INT(11) NOT NULL, order_date DATE NOT NULL, FOREIGN KEY (customer_id) REFERENCES customers(customer_id));

**Modifying a Table:**
Here's an example of the command to add a column in the table "employees":

    ALTER TABLE employees ADD address VARCHAR(200);

**Deleting a Table:**
command "DROP TABLE [table name];" and press enter.

    drop database employees;

## INSERT ROWS
command "INSERT INTO [table name] ([column1], [column2], [column3], ...) VALUES ([value1], [value2], [value3], ...);"

Here's an example of the command to insert a new row into a table called "employees":

    INSERT INTO employees (first_name, last_name, email) VALUES ('John', 'Doe', 'johndoe@example.com');

You can also use the command to insert multiple rows at once:

    INSERT INTO employees (first_name, last_name, email) VALUES ('Jane', 'Doe', 'janedoe@example.com'), ('Bob', 'Smith', 'bobsmith@example.com');

You can also use SELECT statement to insert data from another table:

    INSERT INTO employees (first_name, last_name, email) SELECT first_name, last_name, email FROM temp_employees;

## SELECT
The SELECT statement is used to retrieve data from a MySQL database. Here are the basic steps to use the SELECT statement:
command "SELECT [column1], [column2], ... FROM [table name];" and press enter.

Here's an example of the command to select all columns from the "employees" table:

    SELECT * FROM employees;

You can also select specific columns:

    SELECT first_name, last_name, email FROM employees;

You can filter the results using WHERE clause:

    SELECT first_name, last_name, email FROM employees WHERE last_name='Doe';

You can also use ORDER BY clause to sort the results:

    SELECT first_name, last_name, email FROM employees ORDER BY last_name;

You can use LIMIT clause to limit the number of rows returned:

    SELECT first_name, last_name, email FROM employees LIMIT 5;

You can join multiple tables to retrieve data from them:

    SELECT employees.first_name, employees.last_name, orders.order_date FROM employees JOIN orders ON employees.id = orders.employee_id;

You can also use aggregate functions like COUNT, SUM, AVG, MAX, MIN, etc to retrieve summarized data:

    SELECT COUNT(employee_id) FROM orders;

The SELECT statement is one of the most commonly used SQL commands and is essential for retrieving data from a MySQL database. You can use various clauses like WHERE, ORDER BY, LIMIT, JOIN, etc to filter, sort and retrieve specific data.

## UPDATE & DELETE
The UPDATE and DELETE statements are used to modify and delete data in a MySQL table.
**Updating Data:**
Here's an example of the command to update the email of an employee with an ID of 1 in the "employees" table:

    UPDATE employees SET email = 'johndoe@gmail.com' WHERE id = 1;

**Deleting Data:**
Here's an example of the command to delete the employee with an ID of 2 in the "employees" table:

    DELETE FROM employees WHERE id = 2;

Please note that both UPDATE and DELETE statements are powerful commands that can modify or delete large amounts of data. So, it is important to be very careful when using them and always include a WHERE clause to specify the condition for the operation. Also, it's always a good practice to make a backup of the data before making any changes.

In summary, the UPDATE and DELETE statements are used to modify and delete data in a MySQL table, respectively. Both statements require the use of a WHERE clause to specify the condition for the operation. It's important to be very careful when using these commands and always make a backup of the data before making any changes.



## AUTOCOMMIT, COMMIT, ROLLBACK
In MySQL, AUTOCOMMIT, COMMIT, and ROLLBACK are used to control the transaction management of the database.

**AUTOCOMMIT:**
By default, MySQL runs in AUTOCOMMIT mode, which means that every SQL statement is treated as a separate transaction and is immediately committed to the database. This means that any changes made to the data are permanent and cannot be undone.

**COMMIT:**
The COMMIT command is used to save all changes made in a transaction to the database. A transaction is a series of SQL statements that are executed together as a single unit of work. When the COMMIT command is executed, all changes made during the transaction are permanently committed to the database and cannot be undone.

**ROLLBACK:**
The ROLLBACK command is used to undo all changes made in a transaction. When the ROLLBACK command is executed, all changes made during the transaction are rolled back, and the data is restored to its state before the transaction began.

You can use the following commands to control the transaction management:

    START TRANSACTION;
    -- Execute SQL statements
    COMMIT;

In case you need to undo the transaction, you can use:

    START TRANSACTION;
    -- Execute SQL statements
    ROLLBACK;

Please note that if you are using AUTOCOMMIT mode, you don't have to use the COMMIT command explicitly because every SQL statement is committed immediately. You also can't use the ROLLBACK command in AUTOCOMMIT mode because there is no transaction to rollback.

In summary, AUTOCOMMIT, COMMIT, and ROLLBACK are used to control the transaction management of the database. AUTOCOMMIT mode commits every SQL statement immediately, while COMMIT and ROLLBACK commands are used to save or undo changes made in a transaction respectively. It's important to understand the use of these commands to ensure data integrity and consistency in the database.

## CURRENT_DATE() & CURRENT_TIME()
In MySQL, you can use the CURRENT_DATE() and CURRENT_TIME() functions to return the current date and time, respectively.

The CURRENT_DATE() function returns the current date in the format 'YYYY-MM-DD'.

The CURRENT_TIME() function returns the current time in the format 'HH:MM:SS'.

You can use these functions in a SQL query like this:

    SELECT CURRENT_DATE();
    SELECT CURRENT_TIME();

You can also use them in a query to insert the current date and time into a table like this:

    INSERT INTO table_name (date_column, time_column) VALUES (CURRENT_DATE(), CURRENT_TIME());

You can also use the NOW() function that return the current date and time together in the format 'YYYY-MM-DD HH:MM:SS'

    SELECT NOW();


## UNIQUE
In MySQL, the UNIQUE constraint is used to ensure that the values in a specific column or a set of columns are unique across the entire table or a group of tables. This means that no two rows in the table can have the same value in the specified column(s).

You can create a UNIQUE constraint on a single column or a set of columns in a table using the following syntax:

    CREATE TABLE table_name (
        column1 data_type UNIQUE,
        column2 data_type,
        ...
    );

    ALTER TABLE table_name
    ADD UNIQUE (column1, column2);

For Example:

    CREATE TABLE Employee (
        EmployeeID INT UNIQUE,
        EmployeeName VARCHAR(255) NOT NULL,
        ...
    );

    ALTER TABLE Employee
    ADD UNIQUE (EmployeeName);

You can also create a UNIQUE constraint on an existing table using the ALTER TABLE statement with the ADD CONSTRAINT clause.

    ALTER TABLE table_name
    ADD CONSTRAINT constraint_name UNIQUE (column1, column2);

It's important to keep in mind that the UNIQUE constraint does not allow null values in the specified column(s). If you want to allow null values and still ensure uniqueness, you can use the UNIQUE INDEX instead.

You can also use the SHOW INDEX command to list all indexes (including unique) on a table:

    SHOW INDEX FROM table_name;

You can also use the SHOW CREATE TABLE command to see the unique keys of a table:

    SHOW CREATE TABLE table_name;


##NOT NULL
In MySQL, the NOT NULL constraint is used to ensure that a column cannot have a NULL value. This means that when a new row is inserted into a table, a value must be provided for that column. If an attempt is made to insert a NULL value into a column with the NOT NULL constraint, an error will be returned and the insert will fail.
You can use NOT NULL constraint in CREATE and ALTER table statement.
Example:

    CREATE TABLE students (
        id INT NOT NULL,
        name VARCHAR(255) NOT NULL,
        age INT NOT NULL
    );

Here, id, name and age columns cannot have a null value.


## CHECK

In MySQL, the CHECK constraint is used to ensure that the values in a column meet a specific condition. This constraint can be used to validate data that is inserted or updated in a table.
The CHECK constraint is specified as part of the column definition in a CREATE TABLE or ALTER TABLE statement.
For example, you can use the CHECK constraint to ensure that the value in a "age" column is greater than 18:

    CREATE TABLE students (
        id INT NOT NULL,
        name VARCHAR(255) NOT NULL,
        age INT CHECK (age > 18)
    );

Here, the CHECK constraint ensures that the age column cannot have value less than 18.
Note that MySQL before version 8.0.16 doesn't support CHECK constraint in the CREATE and ALTER table statement. However, you can use the triggers to implement the functionality of the check constraint.


## DEFAULT

In MySQL, the DEFAULT constraint is used to set a default value for a column. This value will be used when a new row is inserted into a table and no value is specified for that column.
The DEFAULT constraint can be specified as part of the column definition in a CREATE TABLE or ALTER TABLE statement.
For example, you can use the DEFAULT constraint to set a default value of "unemployed" for a "status" column:

    CREATE TABLE employees (
        id INT NOT NULL,
        name VARCHAR(255) NOT NULL,
        status VARCHAR(255) DEFAULT 'unemployed'
    );

Here, when a new row is inserted into the "employees" table and no value is specified for the "status" column, the default value of "unemployed" will be used.
In the case of inserting a new row without providing a value for the status column, status column will have 'unemployed' value.

It's also worth noting that default value can be a function as well, like DEFAULT CURRENT_TIMESTAMP which sets the current timestamp as default value.

## PRIMARY KEYS / 

In MySQL, a primary key is a column or set of columns that uniquely identifies each row in a table. The primary key is used to enforce the integrity of the data in the table and to create relationships with other tables in the database.

A primary key is defined by using the PRIMARY KEY constraint when creating or altering a table. A table can have only one primary key, but it can consist of one or more columns.

For example, you can create a "customers" table with a primary key on the "id" column:

    CREATE TABLE customers (
        id INT NOT NULL PRIMARY KEY,
        name VARCHAR(255) NOT NULL,
        address VARCHAR(255)
    );

In this example, the "id" column is the primary key for the "customers" table. It means that the value of id column must be unique and not null.

In addition, It's also possible to have a primary key that consist of multiple columns called as composite primary key, for example:


    CREATE TABLE Sales (
        ProductID INT NOT NULL,
        StoreID INT NOT NULL,
        SaleDate DATE NOT NULL,
        Quantity INT NOT NULL,
        PRIMARY KEY (ProductID, StoreID, SaleDate)
    );

Here, the primary key is a combination of ProductID, StoreID and SaleDate.

It's worth noting that, the primary key is used to create relationship between tables, this relationship can be one-to-one, one-to-many and many-to-many.

## AUTO_INCREMENT

In MySQL, the AUTO_INCREMENT attribute is used to automatically generate a unique value for a column when a new row is inserted into a table. This is commonly used for columns that act as the primary key for a table, such as an "id" column.

The AUTO_INCREMENT attribute is specified as part of the column definition in a CREATE TABLE or ALTER TABLE statement.

For example, you can create a "employees" table with an "id" column that is set as the primary key and has the AUTO_INCREMENT attribute:

    CREATE TABLE employees (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(255) NOT NULL,
        salary FLOAT
    );

When a new row is inserted into the "employees" table and no value is specified for the "id" column, MySQL will automatically generate a unique value for that column. The first row inserted will have id = 1, the second row inserted will have id = 2 and so on.

It's also worth noting that, you can set the initial value of the AUTO_INCREMENT by using the START WITH clause. For example, AUTO_INCREMENT=1000 to set the initial value as 1000.

You can also reset the next auto-increment value using ALTER TABLE statement and the AUTO_INCREMENT keyword.

ALTER TABLE employees AUTO_INCREMENT = 1;
This statement will reset the next auto-increment value to 1 for the table employees.


## FOREIGN KEYS
In MySQL, a foreign key is a column or set of columns in a table that is used to establish a link between the data in two tables. The foreign key is used to enforce referential integrity and to create relationships between tables.

A foreign key is defined by using the FOREIGN KEY constraint when creating or altering a table. A table can have multiple foreign keys, and a foreign key can reference a primary key or unique key in another table.

For example, you can create a "orders" table with a foreign key on the "customer_id" column that references the "id" column in a "customers" table:


    CREATE TABLE customers (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        name VARCHAR(255) NOT NULL,
        address VARCHAR(255)
    );
    
    CREATE TABLE orders (
        id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
        customer_id INT NOT NULL,
        order_date DATE NOT NULL,
        FOREIGN KEY (customer_id) REFERENCES customers(id)
    );

In this example, the "customer_id" column in the "orders" table is a foreign key that references the "id" column in the "customers" table. This creates a relationship between the two tables where each order is associated with a customer.

When a foreign key is defined, the database engine enforces referential integrity, which means that it checks that the values in the foreign key match the values in the primary key of the referenced table. For example, it will not allow to insert a customer_id in orders table that doesn't exist in customers table.

It's also worth noting that, you can use the ON DELETE and ON UPDATE options of the FOREIGN KEY constraint to specify the action to be taken when the referenced row in the parent table is deleted or updated. The actions can be RESTRICT, CASCADE, SET NULL, and SET DEFAULT.

## JOINS
In MySQL, a JOIN is a way to combine data from two or more tables based on a related column between them. JOINs are used to retrieve data from multiple tables as if the data were coming from one table.

There are several types of JOINs in MySQL:

INNER JOIN: This type of JOIN only returns rows from both tables where the join condition is met. It is the most common type of JOIN and is the default if no specific JOIN type is specified.
LEFT JOIN (or LEFT OUTER JOIN): This type of JOIN returns all rows from the left table (i.e. the first table in the JOIN clause), and any matching rows from the right table. If there is no match, NULL values will be returned for right table's columns.
RIGHT JOIN (or RIGHT OUTER JOIN): This type of JOIN returns all rows from the right table (i.e. the second table in the JOIN clause), and any matching rows from the left table. If there is no match, NULL values will be returned for left table's columns.
FULL JOIN (or FULL OUTER JOIN): This type of JOIN returns all rows from both tables. If there is no match, NULL values will be returned for the non-matching columns.
For example, you can use the INNER JOIN to retrieve the data of customers and their orders:

    SELECT customers.name, orders.order_date
    FROM customers
    INNER JOIN orders ON customers.id = orders.customer_id;

This query will return the name and order date of customers who have placed an order.

It's worth noting that, you can join multiple tables together, and also use different types of JOINs in the same query. Additionally, you can use aliases to make your query more readable and to avoid naming conflicts between columns from different tables.

Here are some of the most common types of joins, along with an example of each:

INNER JOIN: An inner join returns only the rows that have matching values in both tables.

    SELECT *
    FROM customers
    INNER JOIN orders
    ON customers.id = orders.customer_id;

This query returns all rows from the "customers" table where there is a matching "id" in the "orders" table, and only the columns from both tables.

LEFT JOIN: A left join returns all rows from the left table (the first table in the query) and any matching rows from the right table. If there is no match, the right table's columns will contain NULL values.

    SELECT *
    FROM customers
    LEFT JOIN orders
    ON customers.id = orders.customer_id;

This query returns all rows from the "customers" table and any matching rows from the "orders" table. If there is no match, the columns from the "orders" table will contain NULL values.

RIGHT JOIN: A right join returns all rows from the right table (the second table in the query) and any matching rows from the left table. If there is no match, the left table's columns will contain NULL values.

    SELECT *
    FROM customers
    RIGHT JOIN orders
    ON customers.id = orders.customer_id;

This query returns all rows from the "orders" table and any matching rows from the "customers" table. If there is no match, the columns from the "customers" table will contain NULL values.

FULL OUTER JOIN: A full outer join returns all rows from both tables, and any matching rows. If there is no match, the columns from the non-matching table will contain NULL values.

    SELECT *
    FROM customers
    FULL OUTER JOIN orders
    ON customers.id = orders.customer_id;

This query returns all rows from both the "customers" and "orders" tables, and any matching rows. If there is no match, the columns from the non-matching table will contain NULL values.

CROSS JOIN: A cross join returns the Cartesian product of the two tables, i.e., it returns all possible combinations of rows from the two tables.

    SELECT *
    FROM customers
    CROSS JOIN orders;

This query returns all possible combinations of rows from the "customers" and "orders" tables.

It's worth noting that, the join condition can be any valid expression that compares two columns, not only the equality. Also, the join condition can be combined with other conditions using the WHERE clause.

## FUNCTIONS
In MySQL, a function is a predefined and reusable set of instructions that perform a specific task. Functions are used to perform operations on data in a table, such as calculating values, manipulating strings, or converting data types.

MySQL provides a wide range of built-in functions for various purposes, including:

Aggregate functions: These functions perform calculations on multiple rows of data and return a single value, such as COUNT(), SUM(), AVG(), MIN(), and MAX().

    SELECT COUNT(*) FROM employees;

This query returns the number of rows in the "employees" table.

Date and time functions: These functions work with date and time data and can be used to extract parts of a date or time, add or subtract time, or format dates and times. Examples include NOW(), CURDATE(), DAY(), MONTH(), YEAR(), and DATE_FORMAT().

    SELECT NOW();

This query returns the current date and time.

String functions: These functions perform operations on strings, such as concatenating, extracting, or replacing substrings. Examples include CONCAT(), SUBSTR(), LENGTH(), UPPER() and LOWER().

    SELECT CONCAT(first_name, ' ', last_name) FROM employees;

This query concatenates the "first_name" and "last_name" columns and returns a single column with the full name of each employee.

Conversion functions: These functions convert data from one type to another, such as converting a number to a string or a date to a timestamp. Examples include CAST(), CONVERT() and UNIX_TIMESTAMP().

    SELECT CAST(price AS DECIMAL(10,2)) FROM products;

This query converts the "price" column to a decimal with 2 decimal places.

Conditional functions: These functions evaluate a condition and return a value based on the result. Examples include IF(), CASE, and COALESCE().

    SELECT IF(age>=18, 'adult', 'minor') as age_group FROM students;

This query returns "adult" if the student's age is greater than or equal to 18, and "minor" otherwise.

It's worth noting that, MySQL also supports User-Defined Functions, where you can define your own function using SQL statements and use it in your queries.

Functions are usually used in the SELECT statement, however, they can be used in other statements as well, such as INSERT, UPDATE and DELETE.

In MySQL, a function is a predefined and reusable set of instructions that perform a specific task. MySQL provides a wide range of built-in functions for various purposes, including:

Aggregate functions: These functions perform calculations on multiple rows of data and return a single value.
COUNT(expr) : Returns the number of rows that match the criteria in the expr.
    SELECT COUNT(*) FROM employees;

SUM(expr) : Returns the sum of the values in a column.
    SELECT SUM(salary) FROM employees;

AVG(expr) : Returns the average value of a column.

    SELECT AVG(age) FROM employees;

MIN(expr) : Returns the smallest value of a column.

    SELECT MIN(price) FROM products;

MAX(expr) : Returns the largest value of a column.

    SELECT MAX(age) FROM employees;

Date and time functions: These functions work with date and time data and can be used to extract parts of a date or time, add or subtract time, or format dates and times.
NOW(): Returns the current date and time.

    SELECT NOW();

`CURDATE():` Returns the current date.

    SELECT CURDATE();

DAY(date): Extracts the day of the month from a date.

    SELECT DAY(hire_date) FROM employees;

MONTH(date): Extracts the month from a date.

    SELECT MONTH(hire_date) FROM employees;

YEAR(date): Extracts the year from a date.

    SELECT YEAR(hire_date) FROM employees;

DATE_FORMAT(date, format): Formats the date according to the specified format.

    SELECT DATE_FORMAT(hire_date,'%Y-%m-%d') FROM employees;

String functions: These functions perform operations on strings, such as concatenating, extracting, or replacing substrings.
CONCAT(str1, str2, ...): Concatenates multiple strings.

    SELECT CONCAT(first_name, ' ', last_name) FROM employees;

SUBSTR(str, pos, len): Returns a substring from a string, starting from a specified position and with a specified length.

    SELECT SUBSTR(name,1,3) FROM products;

LENGTH(str): Returns the length of a string.

    SELECT LENGTH(name) FROM products;

UPPER(str): Converts a string to uppercase.

    SELECT UPPER(name) FROM products;

LOWER(str): Converts a string to lowercase.

    SELECT LOWER(name) FROM products;

Conversion functions: These functions convert data from one type to another, such as converting a number to a string or a date to a timestamp.
CAST(expr AS type): Converts an expression to a specified data type.

    SELECT CAST(price AS DECIMAL(10,2)) FROM products;

CONVERT(expr, type): Converts an expression to a specified data type.

Here are some examples of conversion functions in MySQL:

CAST(expr AS type): Converts an expression to a specified data type.

    SELECT CAST(price AS DECIMAL(10,2)) FROM products;

This query converts the "price" column to a decimal with 2 decimal places.

CONVERT(expr, type): Converts an expression to a specified data type.

    SELECT CONVERT(price, SIGNED) FROM products;

This query converts the "price" column to a signed integer.

BINARY(str): Converts a string to a binary string.

    SELECT BINARY(name) FROM products;

This query converts the "name" column to a binary string.

HEX(str): Converts a string to a hexadecimal string.

SELECT HEX(name) FROM products;
This query converts the "name" column to a hexadecimal string.

UNHEX(str): Converts a hexadecimal string to a string.

SELECT UNHEX(HEX(name)) FROM

Conditional functions:
In MySQL, conditional functions are used to evaluate a condition and return a value based on the result. Here are some examples of conditional functions in MySQL:

IF(condition, true_value, false_value): Evaluates a condition and returns a value based on the result.

    SELECT IF(age>=18, 'adult', 'minor') as age_group FROM students;

This query returns "adult" if the student's age is greater than or equal to 18, and "minor" otherwise.

CASE: Evaluates a list of conditions and returns a value based on the first true condition.

    SELECT name, 
           CASE 
               WHEN age < 18 THEN 'minor'
               WHEN age >= 18 AND age < 65 THEN 'adult'
               ELSE 'senior'
           END AS age_group
    FROM employees;

This query returns the age group of employees based on their age, "minor" if the age is less than 18, "adult" if the age is greater than or equal to 18 and less than 65 and "senior" if the age is greater than or equal to 65

COALESCE(expr1, expr2, ...): Returns the first non-NULL value in a list of expressions.

SELECT COALESCE(phone, email, address) as contact FROM customers;
This query returns the customer's phone number if it's available, otherwise email if it's available and otherwise address

It's worth noting that the above examples are just some of the most common conditional functions in MySQL, and you can use them in various ways to suit your needs.

## AND, OR, NOT

In MySQL, the logical operators AND, OR, and NOT are used to combine conditions in a query's WHERE clause to filter the result set.

AND: The AND operator is used to filter rows that match multiple conditions. The query returns only the rows where both conditions are true.

    SELECT * FROM employees WHERE age > 25 AND salary > 50000;

This query returns all rows from the "employees" table where the age is greater than 25 and the salary is greater than 50000.

OR: The OR operator is used to filter rows that match at least one of multiple conditions. The query returns the rows where either of the conditions is true or both.

    SELECT * FROM employees WHERE department = 'IT' OR department = 'HR';

This query returns all rows from the "employees" table where the department is 'IT' or 'HR'.

NOT: The NOT operator negates a condition. The query returns only the rows where the condition is not true.

    SELECT * FROM employees WHERE NOT department = 'IT';

This query returns all rows from the "employees" table where the department is not 'IT'

It's worth noting that these operators can be used in combination with each other to create complex conditions, and it's also important to use parenthesis to group the conditions to avoid confusion and get the expected results.

## WILD CARDS
In MySQL, a wildcard is a special character that can be used in a search to match any character(s) of a certain type. The two most commonly used wildcards are the percent sign ( % ) and the underscore ( _ ).

The percent sign ( % ) is used as a placeholder for any number of characters. For example, if you wanted to search for all customers with a last name starting with "S", you could use the following query:

    SELECT * FROM customers WHERE last_name LIKE 'S%';

The underscore ( _ ) is used as a placeholder for a single character. For example, if you wanted to search for all customers with a phone number that starts with "555" and is exactly 7 characters long, you could use the following query:

    SELECT * FROM customers WHERE phone_number LIKE '555____';

You can also combine both of the wildcard characters to create more complex search patterns.

Example:
SELECT * FROM customers WHERE phone_number LIKE '555_%__';
This query will return all the customers whose phone number starts with 555 and
have exactly 8 character long.
## ORDER BY

The ORDER BY clause in MySQL is used to sort the result set of a query in ascending or descending order based on one or more columns.

Example:


    SELECT * FROM employees 
    ORDER BY last_name, first_name;

This query will select all columns from the "employees" table and sort the result set by the "last_name" column in ascending order, and then by the "first_name" column in ascending order.

You can also specify the sort order using the keywords "ASC" (ascending) or "DESC" (descending) after the column name.

Example:


    SELECT * FROM employees 
    ORDER BY salary DESC;

This query will select all columns from the "employees" table and sort the result set by the "salary" column in descending order.

You can also use the ORDER BY clause in subqueries and join queries.


    SELECT e.first_name, e.last_name, d.name
    FROM employees e
    INNER JOIN departments d
    ON e.department_id = d.department_id
    ORDER BY d.name, e.last_name;

This query will select first_name, last_name and department name from employees table and join with departments table using department_id and sort the result set by department name, last_name.


## LIMIT
The LIMIT clause in MySQL is used to limit the number of rows returned in a query result.

Example:


    SELECT * FROM employees 
    LIMIT 5;

This query will select all columns from the "employees" table and return only the first 5 rows of the result set.

You can also specify the starting position of the result set and the number of rows to return using the LIMIT clause.

Example:


    SELECT * FROM employees
    LIMIT 10, 5;

This query will select all columns from the "employees" table, and return 5 rows starting from the 11th row of the result set.

You can also use the LIMIT clause in subqueries and join queries.


    SELECT e.first_name, e.last_name, d.name
    FROM employees e
    INNER JOIN departments d
    ON e.department_id = d.department_id
    ORDER BY e.last_name
    LIMIT 5;

This query will select first_name, last_name and department name from employees table and join with departments table using department_id, sort the result set by last_name and return only first 5 rows.

It's important to note that the LIMIT clause should be used after the ORDER BY clause, otherwise, it may return unexpected results.

## UNIONS
The UNION operator in MySQL is used to combine the result set of two or more SELECT statements into a single result set. The UNION operator removes duplicate rows from the result set.

Example:


    SELECT first_name, last_name FROM employees
    WHERE department = 'sales'
    UNION
    SELECT first_name, last_name FROM customers
    WHERE country = 'USA';

This query will select the first_name and last_name columns from the employees table where the department is 'sales', and the first_name and last_name columns from the customers table where the country is 'USA', and combine them into a single result set.

You can also use the UNION ALL operator, which includes duplicate rows in the result set:


    SELECT first_name, last_name FROM employees
    WHERE department = 'sales'
    UNION ALL
    SELECT first_name, last_name FROM customers
    WHERE country = 'USA';

This query will select the first_name and last_name columns from the employees table where the department is 'sales', and the first_name and last_name columns from the customers table where the country is 'USA', and combine them into a single result set including duplicate rows.

The SELECT statements in a UNION must have the same number of columns and the corresponding columns must have compatible data types.


    SELECT first_name, last_name, salary FROM employees
    UNION
    SELECT name, surname, age FROM customers;

This query will give an error because SELECT statements in a UNION must have the same number of columns and the corresponding columns must have compatible data types.

## SELF JOINS
A self join in MySQL is a regular join, but the table is joined with itself. Self joins are used when a table has a relationship with itself, such as when a manager is also an employee in the same table.

Example:


    SELECT e1.first_name as employee, e2.first_name as manager
    FROM employees e1
    JOIN employees e2
    ON e1.manager_id = e2.employee_id;

This query will join the "employees" table with itself, using the "manager_id" column in the first instance of the table (e1) and the "employee_id" column in the second instance of the table (e2). The query will return the first name of the employee and the first name of their manager.

You can also use aliases to give the joined table different names, so the query can distinguish between the two instances of the table.

Another example:


    SELECT e1.first_name as employee, e2.first_name as Colleague
    FROM employees e1
    JOIN employees e2
    ON e1.department_id = e2.department_id
    WHERE e1.employee_id != e2.employee_id;

This query will join the "employees" table with itself, using the "department_id" column in both instances of the table, and return the first name of the employee and the first name of their colleague who is working in the same department but not the same employee.

It is important to note that when joining a table with itself, you need to use aliases to distinguish between the two instances of the table, otherwise it will give an error. Also, you may need to use a condition to exclude the duplicate rows or the row that matches with itself.




## VIEWS
A view in MySQL is a virtual table that is based on the result of a SELECT statement. The SELECT statement can be as simple or as complex as necessary, and can include joins, aggregate functions, and where clauses, among other things.

Here is an example of creating a view in MySQL:


    CREATE VIEW vw_employee_info AS
    SELECT first_name, last_name, salary, department
    FROM employees
    WHERE salary > 50000;

In this example, a view named "vw_employee_info" is created and it contains the first name, last name, salary, and department of all employees who have a salary greater than $50,000.

You can query the view just like a table:


    SELECT * FROM vw_employee_info;

## INDEXES

An index in MySQL is a data structure that improves the performance of SELECT, UPDATE, and DELETE statements by allowing the database to quickly locate the specific rows that match a query.

There are several types of indexes in MySQL, including:

B-Tree indexes: This is the default index type in MySQL and is used for most types of data.

Hash indexes: These are used for exact-value lookups on large data sets.

Full-text indexes: These are used for full-text searches on large text data.

Spatial indexes: These are used for spatial data types such as POINT, LINESTRING, and POLYGON.

Here is an example of creating an index on a table in MySQL:


    CREATE INDEX idx_employee_last_name ON employees (last_name);

In this example, an index named "idx_employee_last_name" is created on the "last_name" column of the "employees" table.

You can also create a composite index with multiple columns:


CREATE INDEX idx_employee_last_first_name ON employees (last_name, first_name);
You can check the indexes for a table with the following query:


    SHOW INDEX FROM employees;

You can also drop an index with the following query:


    DROP INDEX idx_employee_last_name ON employees;

It's important to note that, creating indexes will take up space and slow down write operations, so it's recommended to use indexes judiciously and only on columns that are frequently searched or sorted. Additionally, it's important to analyze and maintain indexes regularly to ensure they remain efficient.

## SUBQUERIES
A subquery in MySQL is a query that is nested within another query. Subqueries can be used in various parts of a query, such as in the SELECT, FROM, WHERE, and HAVING clauses. Subqueries can also be used with various operators, such as IN, NOT IN, EXISTS, NOT EXISTS, ANY, and ALL.

Here are a few examples of using subqueries in MySQL:

**Using a subquery in the SELECT clause:**

    SELECT first_name, last_name, salary
    FROM employees
    WHERE salary > (SELECT AVG(salary) FROM employees);

In this example, the subquery in the WHERE clause calculates the average salary of all employees and the main query selects the first name, last name, and salary of all employees whose salary is greater than the average.

**Using a subquery in the FROM clause:**

    SELECT department, COUNT(*) as employee_count
    FROM (SELECT department FROM employees WHERE salary > 50000) as high_paid_employees
    GROUP BY department;

In this example, the subquery in the FROM clause selects the department of all employees whose salary is greater than $50,000, and the main query counts the number of employees in each department among the high-paid employees.

**Using a subquery with IN operator:**

    SELECT first_name, last_name
    FROM employees
    WHERE department IN (SELECT department FROM departments WHERE location = 'New York');

In this example, the subquery in the WHERE clause selects the department of all departments located in New York and the main query selects the first name and last name of all employees whose department is among the departments located in New York.

**Using a subquery with NOT IN operator:**

    SELECT first_name, last_name
    FROM employees
    WHERE department NOT IN (SELECT department FROM departments WHERE location = 'New York');

In this example, the subquery in the WHERE clause selects the department of all departments located in New York and the main query selects the first name and last name of all employees whose department is not among the departments located in New York.

**Using a subquery with EXISTS operator:**

    SELECT first_name, last_name
    FROM employees
    WHERE EXISTS (SELECT * FROM orders WHERE orders.employee_id = employees.employee_id);

In this example, the subquery in the WHERE clause selects all rows from the orders table where employee_id matches the employee_id of the employees table. The main query will select the first name and last name of all employees that have placed an order.

**Using a subquery with NOT EXISTS operator:**

    SELECT first_name, last_name
    FROM employees
    WHERE NOT EXISTS (SELECT * FROM orders WHERE orders.employee_id = employees.employee_id);

In this example, the subquery in the WHERE clause selects all rows from the orders table where employee_id matches the employee_id of the employees table. The main query will select the first name and last name of all employees that haven't placed an order.

It's important to note that subqueries can be nested to any level, but it's important to keep in mind that it can also make the query complex and hard to read and also can slow down the performance, so it's recommended to use subqueries judiciously and test their performance.

## GROUP BY
The GROUP BY clause in MySQL is used to group rows in a result set based on one or more columns. The GROUP BY clause is typically used with aggregate functions such as COUNT, SUM, AVG, MAX, and MIN to calculate a summary value for each group of rows.

Here are a few examples of using the GROUP BY clause in MySQL:

**Grouping rows by a single column:**

    SELECT department, COUNT(*) as employee_count
    FROM employees
    GROUP BY department;

In this example, the query groups the rows in the "employees" table by the "department" column and counts the number of employees in each department.

**Grouping rows by multiple columns:**

    SELECT department, location, COUNT(*) as employee_count
    FROM employees
    GROUP BY department, location;

In this example, the query groups the rows in the "employees" table by the "department" and "location" columns and counts the number of employees in each department and location.

**Using aggregate functions:**

    SELECT department, SUM(salary) as total_salary
    FROM employees
    GROUP BY department;

In this example, the query groups the rows in the "employees" table by the "department" column and calculates the total salary for each department using the SUM() aggregate function.

**Using the HAVING clause:**

    SELECT department, COUNT(*) as employee_count
    FROM employees
    GROUP BY department
    HAVING COUNT(*) > 10;

In this example, the query groups the rows in the "employees" table by the "department" column and counts the number of employees in each department. The HAVING clause is used to filter the result set and only shows the departments with more than 10 employees.

**Using ROLLUP operator**

    SELECT department, location, SUM(salary) as total_salary
    FROM employees
    GROUP BY department, location WITH ROLLUP;

In this example, the query groups the rows in the "employees" table by the "department" and "location" columns

## ROLLUP
The ROLLUP operator in MySQL is used to create subtotals and super-aggregate rows in a result set. The ROLLUP operator creates a result set that is similar to the one generated by the GROUP BY clause, but with additional rows that represent subtotals and grand totals for the columns specified in the GROUP BY clause.

Here are a few examples of using the ROLLUP operator in MySQL:

**Creating subtotals and grand totals:**

    SELECT department, SUM(salary) as total_salary
    FROM employees
    GROUP BY department WITH ROLLUP;

In this example, the query groups the rows in the "employees" table by the "department" column and calculates the total salary for each department using the SUM() aggregate function. The ROLLUP operator creates additional rows that represent subtotals for the "department" column and a grand total for all departments.

**Using multiple columns:**

    SELECT department, location, SUM(salary) as total_salary
    FROM employees
    GROUP BY department, location WITH ROLLUP;

In this example, the query groups the rows in the "employees" table by the "department" and "location" columns and calculates the total salary for each department and location using the SUM() aggregate function. The ROLLUP operator creates additional rows that represent subtotals for the "department" and "location" columns, subtotals for the "department" column, and a grand total for all departments and locations.

**Using the CUBE operator**

    SELECT department, location, SUM(salary) as total_salary
    FROM employees
    GROUP BY department, location WITH CUBE;

In this example, the query groups the rows in the "employees" table by the "department" and "location" columns and calculates the total salary for each department and location using the SUM() aggregate function. The CUBE operator creates additional rows that represent subtotals for all possible combinations of department and location, subtotals for the "department" and "location" columns and a grand total for all departments and locations.

The ROLLUP and CUBE operator can be useful when creating reports and visualizations that need to show subtotals and grand totals. However, it's important to note that these operators can generate a large number of rows and it can make the query complex and hard to read, so it's recommended to use them judiciously and test their performance.

## ON DELETE
The ON DELETE clause in MySQL is used to define the action that should be taken when a row in a parent table is deleted. This clause is typically used in the context of a foreign key constraint, which is used to enforce a link between a parent table and a child table.

Here are a few examples of using the ON DELETE clause in MySQL:

**CASCADE:**

    CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE CASCADE
    );

In this example, a foreign key constraint is created on the "orders" table that references the "customer_id" column in the "customers" table. The ON DELETE CASCADE clause specifies that when a row in the "customers" table is deleted, all corresponding rows in the "orders" table that reference that customer will also be deleted.

**SET NULL:**

    CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE SET NULL
    );

In this example, a foreign key constraint is created on the "orders" table that references the "customer_id" column in the "customers" table. The ON DELETE SET NULL clause specifies that when a row in the "customers" table is deleted, all corresponding rows in the "orders" table that reference that customer will have the value of the foreign key set to NULL.

**SET DEFAULT:**

    CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT DEFAULT 0,
      FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE SET DEFAULT
    );

In this example, a foreign key constraint is created on the "orders" table that references the "customer_id" column in the "customers" table. The ON DELETE SET DEFAULT clause specifies that when a row in the "customers" table is deleted, all corresponding rows in the "orders" table that reference that customer will have the value of the foreign key set to the default value (0 in this case).

**NO ACTION:**

    CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE NO ACTION
    );

In this example, a foreign key constraint is created on the "orders" table that references the "customer_id" column in the "customers" table. The ON DELETE NO ACTION clause specifies that when a row in the "customers" table is deleted, the corresponding rows in the "orders" table will not be affected and will remain as is.

It's important to note that the ON DELETE clause is only used for foreign key constraints on InnoDB tables. MyISAM tables do not enforce foreign key constraints, so the ON DELETE clause is not applicable.

## STORED PROCEDURES
A stored procedure in MySQL is a precompiled collection of SQL statements that can be stored in the database and called by the application. They are used to encapsulate a set of operations or queries that need to be executed repeatedly.

Here is an example of how to create a simple stored procedure in MySQL:


    DELIMITER //
    CREATE PROCEDURE get_employee_name (IN emp_id INT)
    BEGIN
        SELECT name FROM employees WHERE id = emp_id;
    END //
    DELIMITER ;

In this example, the stored procedure is named "get_employee_name" and it takes a single input parameter, "emp_id". Inside the procedure, a SELECT statement is executed to retrieve the name of an employee from the "employees" table where the id matches the input parameter.

To call the stored procedure, you would use the following syntax:


    CALL get_employee_name(5);

This would execute the stored procedure and return the name of the employee with an ID of 5.

It's worth to mention that stored procedures also can have output parameters and return values, using the keywords OUT and INOUT for output parameters, and return statement for return value respectively.

Additionally, you can also use control flow statements (IF, WHILE, etc) and transactions in stored procedures.

## TRIGGERS
A trigger in MySQL is a set of instructions that are automatically executed in response to a specific event, such as an insert, update, or delete operation on a table. They are used to enforce business rules, maintain data integrity, and perform other tasks that are not easily handled by the application.

Here is an example of how to create a simple trigger in MySQL:


    DELIMITER //
    CREATE TRIGGER update_employee_salary
    AFTER UPDATE ON employees
    FOR EACH ROW
    BEGIN
        IF NEW.salary < OLD.salary THEN
            INSERT INTO audit_log (employee_id, old_salary, new_salary)
            VALUES (NEW.id, OLD.salary, NEW.salary);
        END IF;
    END //
    DELIMITER ;

In this example, the trigger is named "update_employee_salary" and it is executed after an update operation is performed on the "employees" table. Inside the trigger, an IF statement is used to check if the new salary is lower than the old salary. If this condition is true, an INSERT statement is executed to insert a record into an "audit_log" table that contains the employee's ID, old salary, and new salary.

It's worth to mention that triggers also can be created before or instead of the operation, and they can be applied to multiple events, such as insert, update or delete. Also, they can be used to validate data, update other tables or perform any other action that requires executing SQL statements.

Additionally, you can also use control flow statements (IF, WHILE, etc) and transactions in triggers, similar as in stored procedures.


