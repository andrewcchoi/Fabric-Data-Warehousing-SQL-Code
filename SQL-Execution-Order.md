### Links and Resources
https://www.geeksforgeeks.org/order-of-execution-of-sql-queries/

https://stackoverflow.com/questions/68012344/sql-order-of-execution-vs-order-of-writing

### SQL Code

```sql
-- invalid column reference in where clause
SELECT
category as product_category
from tutorial_schema.products 
where product_category = 'Gadget';
```

```sql
SELECT
category as product_category
from tutorial_schema.products 
where category = 'Gadget';
```

```sql
SELECT
case 
    when quantity > 60 then 'Large Volume'
    when quantity > 20 then 'Mid Volumn'
    else 'Low Volume'
end as order_size,
count(id) as number_of_orders
from tutorial_schema.orders 
group by 
case 
    when quantity > 60 then 'Large Volume'
    when quantity > 20 then 'Mid Volumn'
    else 'Low Volume'
end;
```


```sql
SELECT
p.category,
count(o.id) as number_of_orders,
sum(o.quantity) as total_quantity
from tutorial_schema.orders o
left join tutorial_schema.products p
on o.product_id = p.id
group by p.category;
```