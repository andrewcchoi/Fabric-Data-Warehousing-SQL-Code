### Links and Resources
https://learn.microsoft.com/en-us/fabric/data-warehouse/clone-table

https://learn.microsoft.com/en-us/fabric/data-warehouse/time-travel

### SQL Code
```sql
CREATE TABLE tutorial_schema.users_clone AS CLONE OF tutorial_schema.users;
```

```sql
DELETE FROM tutorial_schema.users_clone where source = 'Organic';
```

```sql
DELETE FROM tutorial_schema.users_clone where source = 'Organic';
```

```sql
-- add any timestamp value prior to the deletion of Organically sourced users but after table creation
SELECT * FROM tutorial_schema.users_clone 
OPTION (FOR TIMESTAMP AS OF 'insert timestamp here');
```