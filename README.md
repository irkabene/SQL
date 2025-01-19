# SQL Theory

## SELECT Statement
- *Use:*
Retrieves date from a database

- *Syntax:*
  ```SQL
      SELECT column1, column2, ..., columnN
      FROM table_name;
  ```
- Let's dissect this: <br/>
*SELECT:* This is a SQL keyword that indicates you want to fetch data. <br/>
*column1, column2, ..., columnN:* These are the names of the columns you want to fetch. If you want to fetch all available columns, you replace this part with an asterisk (*). <br/>
*FROM:* This is another SQL keyword. It specifies which table you want to fetch the data from. <br/>
*table_name:* This is the name of the table from which you want to retrieve data. <br/>

## Similar but not the same

- SELECT * : Fetches *all columns* from the specified table, helpful when you need complete rows.
- SELECT ALL: Fetches *all rows*, including duplicates, from specified columns, useful when duplicates are necessary for the analysis.


## UNION Operator
- *Use:*
  Used to combine the result sets of two or more SELECT statements. It returns all unique rows provided by the SELECT statements, meaning it eliminates duplicate rows from the results.

- *Syntax:*
```SQL
    SELECT first_name AS Name
    FROM actor
    UNION
    SELECT first_name AS Name
    FROM customer;
    //Returns unique (not 2 same) names from actor and customer columnes

```
## LIMIT Clause
- *Use:*
Used to set an upper limit on the number of tuples or records the query will return.

- *Syntax:*
``` SQL
    SELECT column1, column2, ..., columnN 
    FROM table_name 
    LIMIT number;
```
-LIMIT quite literally limits the number of rows you retrieve from your table.

## OFFSET Clause

-*Use:*
 Specify where to start fetching data from

 -*Syntax:*
 ```SQL
     SELECT column1, column2, ..., columnN 
     FROM table_name 
     LIMIT number 
     OFFSET number_of_rows_to_skip;
 // ex:if you have 10 rows with names and asks you to return the names from 6th to 10th row, you want LIMIT 5 and OFFSET 5 so it will skip the first 5 rows.
```
-OFFSET skips the number of rows mentioned before starting to fetch the data.

## SELECT DISTINCT Statement
-*Use:*
Used to fetch unique values from a specified column of a table 

-*For example:* <br/>
If you have a column with names of countries and there are some duplicates, with SELECT DISTINCT you ask SQL to fetch unique values from name column

## CONCAT Function
-*Use:*
Used to combine two or more strings into one.

-*Syntax:*
```SQL
  CONCAT(string1, string2, ..., stringN)
```
- *For example:* <br/>
Imagine we have a table called actor with columns first_name and last_name. We want to generate a list of full names of all actors. Let's use CONCAT to do this:
```SQL
    SELECT CONCAT(first_name, ' ', last_name) AS full_name
    FROM actor;
```
The resulting table will display the full_name of each actor, a column that doesn't exist in the actor table, but we just created on-the-fly with CONCAT.

## Alias in SQL
- An alias in SQL is a temporary name we give to a table or a column in our SQL query.

- *Syntax:*
```SQL
    SELECT column_name AS alias_name
    FROM table_name;
```

## WHERE Clause
- The WHERE clause in SQL is used to filter records based on specific conditions.
```SQL
  SELECT column1, column2, ...
  FROM table_name
  WHERE condition;
```
## Operators
1. *= (Equal):* This operator checks if the value in a column equals a specified value.
  ```SQL
    SELECT * 
    FROM film 
    WHERE title = 'AFRICAN EGG';
  ```
2. *<> or != (Not Equal):* This operator checks if the value in a column is not equal to a specified value.
```SQL
SELECT * 
FROM film 
WHERE rating <> 'G';
```
3. *> (Greater Than) and < (Less Than):* These operators check if the value in a column is greater than or less than a specified value.
```SQL
SELECT * 
FROM film 
WHERE rental_duration > 3;
```
4. *>= (Greater Than or Equal To) and <= (Less Than or Equal To):* These operators check if the value in a column is greater than or equal to, or less than or equal to a specified value.
```SQL
SELECT * 
FROM film 
WHERE rental_rate <= 2.99;
```
5. *BETWEEN:* This operator fetches the values within a range.
```SQL
  SELECT * 
  FROM film 
  WHERE rental_duration BETWEEN 5 AND 6;
```
6. *LIKE:* This operator is used to search for a specified pattern in a column.
```SQL
SELECT * 
FROM film 
WHERE title LIKE 'AM%';
```
- WHERE title LIKE 'AM%': This is the condition for filtering. It only includes films where the title starts with 'AM'. The '%' is a wildcard that matches any number of characters.

7.  *IN:* This operator allows you to specify multiple values in a WHERE clause.
```SQL
SELECT * 
FROM film 
WHERE rating IN ('G', 'PG', 'PG-13');
```
-WHERE rating IN ('G', 'PG', 'PG-13'): This is the condition for filtering. It only includes films where the rating is either 'G', 'PG', or 'PG-13'.

## Logical Operators

|Operator|Meaning|
|:------:|:-----:|
|ALL|	Return true if all comparisons are true|
|AND|	Return true if both expressions are true
|ANY|	Return true if any one of the comparisons is true.
|BETWEEN|	Return true if the operand is within a range
|EXISTS|	Return true if a subquery contains any rows
|IN|	Return true if the operand is equal to one of the value in a list
|LIKE|	Return true if the operand matches a pattern
|NOT|	Reverse the result of any other Boolean operator.
|OR| 	Return true if either expression is true
|SOME|	Return true if some of the expressions are true

## % Wildcards
- The % wildcard in SQL is a versatile tool that allows you to add flexibility to your search queries. It represents zero, one, or multiple characters in a string, helping you search for patterns, partial matches, or even misspelled data. Typically, the % wildcard is used with the LIKE operator in the WHERE clause of an SQL statement.

-Examples
|Code|Comments|
|:--:|:------:|
| WHERE movie_title LIKE 'A%';|The % wildcard allows us to search for all movie titles that start with 'A'|
| WHERE customer_last_name LIKE '%SON';|the % wildcard is searching for all customers whose last name ends with 'SON'|
| WHERE movie_title LIKE '%LOVE%'; | the % wildcard is used before and after 'LOVE', indicating we're looking for any movie title that contains the word 'LOVE', regardless of what comes before or after it|


