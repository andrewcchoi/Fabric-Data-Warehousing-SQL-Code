### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/statements/create-procedure-transact-sql?view=sql-server-ver16

### SQL Code
```sql
CREATE PROCEDURE 
    tutorial_schema.demo_proc
AS 
CREATE TABLE tutorial_schema.temp_table (name varchar(255), age INT);
INSERT INTO tutorial_schema.temp_table values ('Jon', 35);


EXEC tutorial_schema.demo_proc 
```
```sql
ALTER PROCEDURE
    tutorial_schema.demo_proc
AS 
SELECT * FROM tutorial_schema.orders;

EXEC tutorial_schema.demo_proc;
```

```sql
ALTER PROCEDURE 
    tutorial_schema.demo_proc (@price DECIMAL(10,2))
AS 
SELECT * FROM tutorial_schema.orders WHERE total > @price;

EXEC tutorial_schema.demo_proc @price = 80;
```

```sql
EXEC tutorial_schema.demo_proc 80;
```


```sql
ALTER PROCEDURE 
    tutorial_schema.demo_proc (@price DECIMAL(10,2) = 0)
AS 
SELECT * FROM tutorial_schema.orders WHERE total > @price;
```

```sql
ALTER PROCEDURE 
    tutorial_schema.demo_proc (@price INT = 0, @input_date DATE = '1970-01-01')
AS 
SELECT * FROM tutorial_schema.orders WHERE total > @price and created_at > @input_date;
```

```sql
DROP PROCEDURE tutorial_schema.demo_proc;
```

