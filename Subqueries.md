### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/queries/subqueries-azure-sql-data-warehouse-parallel-data-warehouse?view=fabric

### SQL Code
```sql
SELECT
a.* FROM
(SELECT * FROM tutorial_schema.products) as a;
```

```sql
SELECT
* FROM
tutorial_schema.orders
WHERE quantity > (select avg(quantity) from tutorial_schema.orders);
```

```sql
SELECT
* FROM
tutorial_schema.products
WHERE id in (
	     select 
	     top 10 
	     product_id 
	     from tutorial_schema.orders 
	     group by product_id 
	     order by sum(quantity) desc
	     );
```