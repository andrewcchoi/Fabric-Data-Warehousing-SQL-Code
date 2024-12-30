### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/statements/create-table-as-select-azure-sql-data-warehouse?view=fabric


### SQL Code
```sql
create table WarehouseTutorial.tutorial_schema.users_ctas
as
select * from WarehouseTutorial.tutorial_schema.users;
```

```sql
create table tutorial_schema.top_10_vendors_qty
as
select 
top 10
p.vendor,
sum(o.quantity) as total_quantity
from tutorial_schema.orders o
join tutorial_schema.products p
on o.product_id = p.id
group by p.vendor
order by total_quantity desc;
```