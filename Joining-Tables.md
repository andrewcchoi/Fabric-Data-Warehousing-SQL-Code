### Links and Resources
https://learn.microsoft.com/en-us/sql/relational-databases/performance/joins?view=sql-server-ver16
https://www.w3schools.com/sql/sql_join.asp


### SQL Code
```sql
SELECT
o.*,
p.*
FROM tutorial_schema.orders o
JOIN tutorial_schema.products p
ON o.product_id = p.id;
```

```sql
SELECT
o.*,
p.title,
p.category
FROM tutorial_schema.orders o
JOIN tutorial_schema.products p
ON o.product_id = p.id;
```

```sql
SELECT
o.*,
p.title,
p.category,
u.*
FROM tutorial_schema.orders o
LEFT JOIN tutorial_schema.products p
ON o.product_id = p.id
LEFT JOIN tutorial_schema.users u
ON o.user_id = u.id;
```

```sql
SELECT
o.*,
p.title,
p.category,
u.name,
u.source
FROM tutorial_schema.orders o
LEFT JOIN tutorial_schema.products p
ON o.product_id = p.id
LEFT JOIN tutorial_schema.users u
ON o.user_id = u.id;
```