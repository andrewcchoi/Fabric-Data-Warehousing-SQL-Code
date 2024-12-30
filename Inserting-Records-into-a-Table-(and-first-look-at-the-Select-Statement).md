### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/statements/insert-transact-sql?view=fabric

### SQL Code

```sql
CREATE TABLE WarehouseTutorial.tutorial_schema.new_table_1
(
first_column int NOT NULL, second_column varchar(10), third_column date
);
```
```sql
select 
first_column, 
second_column, 
third_column 
from WarehouseTutorial.tutorial_schema.new_table_1;
```

```sql
select 
*
from WarehouseTutorial.tutorial_schema.new_table_1;
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(10, 'hello', '2020-01-01');
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(11, 'hello2', '2021-01-01'),
(12, 'hello3', '2022-01-01')
;
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
('hello', 'hello', '2020-01-01');
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(100, 100, '2020-01-01');
```
```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(100, 'hello4', '30-01-2021');
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(100, 'hello4', '2021-01-30');
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(100, 'hello4');
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(100, 'hello4', NULL);
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(NULL, 'hello4', '2024-01-01');
```
```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
VALUES 
(10, 'hello again', '2020-01-01');
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_1
(third_column, second_column, first_column)
VALUES 
('2020-01-01', 'howdy', 999);
```


```sql
CREATE TABLE WarehouseTutorial.tutorial_schema.new_table_2
(
first_column int NOT NULL, second_column varchar(10), third_column date
);
```

```sql
insert into WarehouseTutorial.tutorial_schema.new_table_2
select * from WarehouseTutorial.tutorial_schema.new_table_1;
```

```sql
select * from WarehouseTutorial.tutorial_schema.new_table_2
```

```sql
drop table WarehouseTutorial.tutorial_schema.new_table_1;
drop table WarehouseTutorial.tutorial_schema.new_table_2;
```