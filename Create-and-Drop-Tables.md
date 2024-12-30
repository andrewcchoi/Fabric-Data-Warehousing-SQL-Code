### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/statements/create-table-azure-sql-data-warehouse?view=fabric
https://learn.microsoft.com/en-us/sql/t-sql/statements/drop-table-transact-sql?view=fabric

### SQL Code
```sql
create table WarehouseTutorial.tutorial_schema.new_table_1
(
    first_column int not null,
    second_column varchar(10),
    third_column DATE
);
```

```sql
create table new_table_1
(
    first_column int not null,
    second_column varchar(10),
    third_column DATE
);
```

```sql
DROP TABLE WarehouseTutorial.dbo.new_table_1;
DROP TABLE WarehouseTutorial.tutorial_schema.new_table_1;
```