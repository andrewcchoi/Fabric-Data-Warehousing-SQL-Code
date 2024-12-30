###Links and Resources
https://learn.microsoft.com/en-us/sql/relational-databases/views/views?view=sql-server-ver16

###SQL Code
```sql
CREATE VIEW tutorial_schema.vw_customer_order_qty
AS
SELECT
u.id as customer_id,
u.name as customer_name,
count(*) as number_of_orders
FROM tutorial_schema.orders o
LEFT JOIN tutorial_schema.users u
ON o.user_id = u.id
GROUP BY u.id, u.name;
```

```sql
DROP VIEW tutorial_schema.vw_customer_order_qty;
```