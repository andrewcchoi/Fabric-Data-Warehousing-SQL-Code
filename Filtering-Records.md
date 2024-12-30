### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/language-elements/operator-precedence-transact-sql?view=sql-server-ver16


### SQL Code
```sql
select * from tutorial_schema.products where category = 'Gadget';
```

```sql
select * from tutorial_schema.products where price > 50;
```

```sql
select * from tutorial_schema.products where price >= 50 and price <=60;
```

```sql
select * from tutorial_schema.products where price between 50 and 60;
```

```sql
select * from tutorial_schema.products where category = 'Gadget' or category = 'Gizmo'
```

```sql
select * from tutorial_schema.products where category in ('Gadget', 'Gizmo');
```

```sql
select
*
from tutorial_schema.products
where (category = 'Gadget' or category = 'Gizmo') and price > 80;
```

```sql
select
   distinct
   top 10
   *
from tutorial_schema.products
where category = 'Gadget'
order by price desc;
```



