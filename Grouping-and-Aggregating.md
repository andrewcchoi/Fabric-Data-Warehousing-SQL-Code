### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/functions/aggregate-functions-transact-sql?view=fabric

### SQL Code
```sql
select sum(quantity) as total_units from tutorial_schema.orders;
```

```sql
select count(id) as total_orders from tutorial_schema.orders;
```

```sql
select count(*) as total_orders from tutorial_schema.orders;
```

```sql
select product_id, count(*) as total_orders from tutorial_schema.orders group by product_id;
```

```sql
select 
   user_id,
   product_id, 
   sum(quantity) as total_quantity,
   count(*) as total_orders 
from tutorial_schema.orders 
group by user_id, product_id;
```

```sql
select 
   category,
   count(*) as total_products
from tutorial_schema.orders 
where category != 'Widget'
group by category;
```

```sql
select 
   category,
   count(*) as total_products
from tutorial_schema.orders 
where category != 'Widget'
group by category
having count(*)>50;
```