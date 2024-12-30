### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/queries/update-transact-sql?view=fabric

https://learn.microsoft.com/en-us/sql/t-sql/statements/delete-transact-sql?view=fabric

### SQL Code
```sql
update tutorial_schema.users_ctas
set name = 'Sadye Gibbson', email = 'sadye.gibbson@gmail.com'
where id = 2497;
```

```sql
update tutorial_schema.users_ctas
set name = upper(name)
```

```sql
delete from tutorial_schema.users_ctas
where id = 2482;
 ```

```sql
delete from tutorial_schema.users_ctas
where id = 2982;
```

```sql
delete from tutorial_schema.users_ctas;
```

```sql
drop table tutorial_schema.users_ctas;
```