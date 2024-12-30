### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/queries/select-order-by-clause-transact-sql?view=fabric


### SQL Code
```sql
select * from tutorial_schema.orders order by created_at asc;
```

```sql
select * from tutorial_schema.orders order by unit_price desc;
```

```sql
select * from tutorial_schema.orders order by user_id, created at;
```

```sql
select * from tutorial_schema.orders order by user_id desc, created at desc;
```

```sql
select top 10 * from tutorial_schema.orders;
```