# Commenting Out Code in SQL

>Especially useful in SQL Injections

In SQL, the syntax for commenting out code varies depending on the specific database management system (DBMS) you are using. Here are the common ways to comment out code in different SQL dialects:

1. SQL Server, MySQL, and SQLite:
   - Single-line comment: Use two dashes "--" at the beginning of the line to comment out the entire line.
   ```sql
   -- This is a comment
   SELECT * FROM table_name;
   ```
   - Multi-line comment: Enclose the commented section between "/*" and "*/".
   ```sql
   /* This is a
      multi-line comment */
   SELECT * FROM table_name;
   ```

2. Oracle:
   - Single-line comment: Use two dashes "--" at the beginning of the line to comment out the entire line.
   ```sql
   -- This is a comment
   SELECT * FROM table_name;
   ```
   - Multi-line comment: Enclose the commented section between "/*" and "*/".
   ```sql
   /* This is a
      multi-line comment */
   SELECT * FROM table_name;
   ```

3. PostgreSQL:
   - Single-line comment: Use two dashes "--" at the beginning of the line to comment out the entire line.
   ```sql
   -- This is a comment
   SELECT * FROM table_name;
   ```
   - Multi-line comment: Enclose the commented section between "/*" and "*/".
   ```sql
   /* This is a
      multi-line comment */
   SELECT * FROM table_name;
   ```

Remember to adapt these commenting styles to the specific DBMS you are using, as some databases may have additional or different commenting syntax.