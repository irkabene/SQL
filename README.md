#SQL Theory

##SELECT Statement
-*Use:*
Retrieves date from a database

-*Syntax:*
SELECT column1, column2, ..., columnN
FROM table_name;

- Let's dissect this:
*SELECT:* This is a SQL keyword that indicates you want to fetch data.
*column1, column2, ..., columnN:* These are the names of the columns you want to fetch. If you want to fetch all available columns, you replace this part with an asterisk (*).
*FROM:* This is another SQL keyword. It specifies which table you want to fetch the data from.
*table_name:* This is the name of the table from which you want to retrieve data.

#Similar but not the same

- SELECT * : Fetches *all columns* from the specified table, helpful when you need complete rows.
- SELECT ALL: Fetches *all rows*, including duplicates, from specified columns, useful when duplicates are necessary for the analysis.
