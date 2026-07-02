# <u> -------------------- Syntax in PostgreSQL -------------------- <u/>

## <u> PostgreSQL Operators <u/>

  - We can operate with different operators in the WHERE clause :

### 01. Equal To

  - The = operator is used when you want to return all records where a column is equal to a specified value:

  - Example, Return all records where the brand is 'Volvo':

        SELECT * FROM cars
        WHERE brand = 'Volvo';

### 02. Less Than

  - The < operator is used when you want to return all records where a column is less than a specified value.

  - Example, Return all records where the year is less than 1975:

        SELECT * FROM cars
        WHERE year < 1975;

### 03. Greater Than

  - The > operator is used when you want to return all records where a columns is greater than a specified value.

  - Example, Return all records where the year is greater than 1975:

        SELECT * FROM cars
        WHERE year > 1975;

### 04. Less Than or Equal To

  - The <= operator is used when you want to return all records where a column is less than, or equal to, a specified value.

  - Example, Return all records where the year is less than or equal to 1975:

        SELECT * FROM cars
        WHERE year <= 1975;

### 05. Greater Than or Equal to

  - The >= operator is used when you want to return all records where a columns is greater than, or equal to, a specified value.

  - Example, Return all records where the year is greater than or equal 1975:

        SELECT * FROM cars
        WHERE year >= 1975;

### 06. Not Equal To

  - The <> operator is used when you want to return all records where a column is NOT equal to a specified value:

  - Example, Return all records where the brand is NOT 'Volvo':

        SELECT * FROM cars
        WHERE brand <> 'Volvo';

  - You will get the same result with the != operator:

  - Example, Return all records where the brand is NOT 'Volvo':

        SELECT * FROM cars
        WHERE brand != 'Volvo';

### 07. LIKE

  - The LIKE operator is used when you want to return all records where a column is equal to a specified pattern.

  - The pattern can be an absolute value like 'Volvo', or with a wildcard that has a special meaning.

  - There are two wildcards often used in conjunction with the LIKE operator:

        The percent sign %, represents zero, one, or multiple characters.
        The underscore sign _, represents one single character.

  - Example, Return all records where the model STARTS with a capital 'M':

        SELECT * FROM cars
        WHERE model LIKE 'M%';

### 08. ILIKE

  - Same as the LIKE operator, but ILIKE is case insensitive.

  - Example, Return all records where the model start with a 'm':

        SELECT * FROM cars
        WHERE model ILIKE 'm%';

### 09. AND

  - The logical AND operator is used when you want to check more that one condition:

  - Example, Return all records where the brand is 'Volvo' and the year is 1968:

        SELECT * FROM cars
        WHERE brand = 'Volvo' AND year = 1968;

### 10. OR

  - The logical OR operator is used when you can accept that only one of many conditions is true:

  - Example, Return all records where the brand is 'Volvo' OR the year is 1975:

        SELECT * FROM cars
        WHERE brand = 'Volvo' OR year = 1975;

### 11. IN

  - The IN operator is used when a column's value matches any of the values in a list:

  - Example, Return all records where the brand is present in this list: ('Volvo', 'Mercedes', 'Ford'):

        SELECT * FROM cars
        WHERE brand IN ('Volvo', 'Mercedes', 'Ford');

### 12. BETWEEN
  
  - The BETWEEN operator is used to check if a column's value is between a specified range of values:

  - Example, Return all records where the year is between 1970 and 1980:

        SELECT * FROM cars
        WHERE year BETWEEN 1970 AND 1980;

  - The BETWEEN operator includes the from and to values, meaning that in the above example, the result would include cars made in 1970 and 1980 as well.

### 13. IS NULL

  - The IS NULL operator is used to check if a column's value is NULL:

  - Example, Return all records where the model is NULL:

        SELECT * FROM cars
        WHERE model IS NULL;

### 14. NOT

  - The NOT operator can be used together with LIKE, ILIKE, IN, BETWEEN, and NULL operators to reverse the truth of the operator.

  - Example: NOT LIKE, Return all records where the brand does NOT start with a capital 'B' (case sensitive):

        SELECT * FROM cars
        WHERE brand NOT LIKE 'B%';

  - Example: NOT ILIKE, Return all records where the brand does NOT start with a 'b' (case insensitive):

        SELECT * FROM cars
        WHERE brand NOT ILIKE 'b%';

  - Example: NOT IN, Return all records where the brand is NOT present in this list: ('Volvo', 'Mercedes', 'Ford'):

        SELECT * FROM cars
        WHERE brand NOT IN ('Volvo', 'Mercedes', 'Ford');

  - Example: NOT BETWEEN, Return all records where the year is NOT between 1970 and 1980:

        SELECT * FROM cars
        WHERE year NOT BETWEEN 1970 AND 1980;

  - The NOT BETWEEN operator excludes the from and to values, meaning that in the above example, the result would not include cars made in 1970 and 1980.

  - Example: IS NOT NULL, Return all records where the model is NOT null:

        SELECT * FROM cars
        WHERE model IS NOT NULL;

  - The cars table has no columns with NULL values, so the example above will return all 4 rows.

## <u> Select Data <u/>

  - To retrieve data from a database, we use the SELECT statement.

### Specify Columns

  - By specifying the column names, we can choose which columns to select:

        SELECT customer_name, country FROM customers;

### Return ALL Columns

  - Specify a * instead of the column names to select all columns:

        SELECT * FROM customers;

## <u> The SELECT DISTINCT Statement <u/>

  - The SELECT DISTINCT statement is used to return only distinct (different) values.

  - Inside a table, a column often contains many duplicate values and sometimes you only want to list the different (distinct) values.

  - Example, Select only the DISTINCT values from the country column in the customers table:

        SELECT DISTINCT country FROM customers;

  - Even though the customers table has 91 records, it only has 21 different countries, and that is what you get as a result when executing the SELECT DISTINCT statement above

        SELECT COUNT(DISTINCT)

  - We can also use the DISTINCT keyword in combination with the COUNT statement, which in the example below will return the number of different countries there are in the customers table.

  - Example, Return the number of different countries there are in the customers table:

        SELECT COUNT(DISTINCT country) FROM customers;

## <u> Filter Records <u/>

  - The WHERE clause is used to filter records.

  - It is used to extract only those records that fulfill a specified condition.

  - If we want to return only the records where city is London, we can specify that in the WHERE clause:

        SELECT * FROM customers
        WHERE city = 'London';

### Text Fields vs. Numeric Fields

  - PostgreSQL requires quotes around text values.

  - However, numeric fields should not be enclosed in quotes:

        SELECT * FROM customers
        WHERE customer_id = 19;

  - Quotes around numeric fields will not fail, but it is good practice to always write numeric values without quotes.

## <u> Sort Data <u/>

  - The ORDER BY keyword is used to sort the result in ascending or descending order.

  - The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword to Sort the table by price:

        SELECT * FROM products
        ORDER BY price;

### DESC

  - The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.

  - Example, Sort the table by price, in descending order:

        SELECT * FROM products
        ORDER BY price DESC;

### Sort Alphabetically

  - For string values the ORDER BY keyword will order alphabetically:

  - Example, Sort the table by product name:

        SELECT * FROM products
        ORDER BY product_name;

### Alphabetically DESC

  - To sort the table reverse alphabetically, use the DESC keyword:

  - Example, Sort the table by product name, in descending order:

        SELECT * FROM products
        ORDER BY product_name DESC;

## <u> The LIMIT Clause <u/>

  - The LIMIT clause is used to limit the maximum number of records to return.

  - Example, Return only the 20 first records from the customers table:

        SELECT * FROM customers
        LIMIT 20;

### The OFFSET Clause

  - The OFFSET clause is used to specify where to start selecting the records to return.

  - If you want to return 20 records, but start at number 40, you can use both LIMIT and OFFSET.

  - Note: The first record is number 0, so when you specify OFFSET 40 it means starting at record number 41.

  - Example, Return 20 records, starting from the 41th record:

        SELECT * FROM customers
        LIMIT 20 OFFSET 40;

## <u> PostgreSQL MIN and MAX Functions <u/>

### MIN

  - The MIN() function returns the smallest value of the selected column.

  - Example, Return the lowest price in the products table:

        SELECT MIN(price)
        FROM products;

### MAX

  - The MAX() function returns the largest value of the selected column.

  - Example, Return the highest price in the products table:

        SELECT MAX(price)
        FROM products;

### Set Column Name

  - When you use MIN() or MAX(), the returned column will be named min or max by default. To give the column a new name, use the AS keyword.

  - Example, Return the lowest price, and name the column lowest_price:

        SELECT MIN(price) AS lowest_price
        FROM products;

## <u> COUNT <u/>

  - The COUNT() function returns the number of rows that matches a specified criterion.

  - If the specified criterion is a column name, the COUNT() function returns the number of rows with that name.

  - Example, Return the number of customers from the customers table:

        SELECT COUNT(customer_id)
        FROM customers;

  - Note: NULL values are not counted.

  - By specifying a WHERE clause, you can e.g. return the number of customers that comes from London:

  - Example, Return the number of customers from London:

        SELECT COUNT(customer_id)
        FROM customers
        WHERE city = 'London';

## <u> SUM <u/>

  - The SUM() function returns the total sum of a numeric column.

  - The following SQL statement finds the sum of the quantity fields in the order_details table:

  - Example, Return the total amount of ordered items:

        SELECT SUM(quantity)
        FROM order_details;
  
  - Note: NULL values are ignored.
