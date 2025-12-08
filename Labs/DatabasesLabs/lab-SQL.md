# Database Lab: Performing a Conditional Search (SQL Queries)

## Objective
- Write a search condition by using the WHERE clause
- Use the BETWEEN operator
- Use the LIKE operator with wildcard characters
- Use the AS operator to create a column alias
- Use functions in a SELECT statement
- Use functions in a WHERE clause

## Sample Query
1. Connected to the Command Host EC2 instance using AWS Session Manager.

2. Established a database session via the terminal using the command mysql -u root --password='re:St@rt!9'.

3. Verified the schema by running SHOW DATABASES; and confirming the existence of the world database.

4. Filtered records by number range using the verbose syntax: WHERE Population >= 50000000 AND Population <= 100000000;.

5. Optimized the range search by rewriting the query with the cleaner and more readable BETWEEN operator.

6. Aggregated data by using the SUM() function in the SELECT clause combined with the LIKE operator in the WHERE clause to find the total population of all countries in "Europe" (WHERE Region LIKE "%Europe%";).

7. Improved output readability by adding a column alias to the aggregated result using AS "Europe Population Total".

8. Handled case insensitivity in search criteria by using the LOWER() function on the target column in the WHERE clause to find countries in Central regions.

9. Completed the challenge by writing a query that used SUM(SurfaceArea) and SUM(Population) with column aliases to calculate the total land area and population for "North America."

## Challenges
I struggled with queries using wild characters, and functions. I remedied this by going onto w3schools.com to help me grasp these concepts.

## Screenshot
![alt text](<images/SQL queries/MySQLshellConnected.png>)
* User successfully authenticated and entered the MySQL shell.

![alt text](<images/SQL queries/QueryPopulationRange1.png>)
![alt text](<images/SQL queries/QueryPopulationRange2.png>)
* Result set where the population is clearly within the specified range.

![alt text](<images/SQL queries/EuropePopulationTotal.png>)
* The output of the aggregated European population total with a descriptive column header.

![alt text](<images/SQL queries/RegionQuery.png>)
* Demonstrates that the query returned all relevant records regardless of the original casing in the Region column.

## Takeaways
- A well-constructed SQL query is primarily defined by its filtering logic. The WHERE clause is your primary tool for filtering and should be used to reduce the dataset.
- The LIKE operator combined with wildcards is essential for flexible text searching when exact matches aren't possible (e.g., searching for parts of a name or address).
- Using AS to create column aliases should be standard practice in production environments, making aggregated results (SUM, AVG, COUNT) immediately understandable to anyone reading the query output.
- Tools like BETWEEN are not just for readability; they make the intent of range searching explicit.