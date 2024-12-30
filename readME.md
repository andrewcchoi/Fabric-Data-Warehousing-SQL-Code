# Fabric-Data-Warehousing-SQL-Code

The pages displayed below correspond to the lectures in the section **Data Warehousing and Power BI**
1. [Create and Drop Schemas](#create-and-drop-schemas)
1. [Create and Drop Tables](#create-and-drop-tables)
1. [Inserting Records Into a Table (and first look at the Select Statement)](#inserting-records-into-a-table-and-first-look-at-the-select-statement)
1. [The Select Statement](#the-select-statement)
1. [Selecting Distinct Records](#selecting-distinct-records)
1. [Functions and Expressions](#functions-and-expressions)
1. [Ordering and Limiting your Results](#ordering-and-limiting-your-results)
1. [Filtering Records](#filtering-records)
1. [Grouping and Aggregating](#grouping-and-aggregating)
1. [Joining Tables](#joining-tables)
1. [SQL Execution Order](#sql-execution-order)
1. [Create Table As Select](#create-table-as-select)
1. [Updating and Deleting Records](#updating-and-deleting-records)
1. [Subqueries](#subqueries)
1. [Views](#views)
1. [Zero Copy Clones and Time Travel](#zero-copy-clones-and-time-travel)
1. [Stored Procedures](#stored-procedures)
1. [Preparing the Presentation Layer and Semantic Model](#preparing-the-presentation-layer-and-semantic-model)

## Create and Drop Schemas
### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/statements/create-schema-transact-sql?view=fabric
https://learn.microsoft.com/en-us/sql/t-sql/statements/drop-schema-transact-sql?view=fabric

### SQL Code
```sql
CREATE SCHEMA tutorial_schema;
```

```sql
DROP SCHEMA tutorial_schema;
```
[top](#Fabric-Data-Warehousing-SQL-Code)
## Create and Drop Tables
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Inserting Records Into a Table (and first look at the Select Statement)
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## The Select Statement
```sql
select id, product_id, quantity from tutorial_schema.orders;
```

```sql
select id, product_id, quantity from WarehouseTutorial.tutorial_schema.orders;
```

```sql
select [id], [product_id], [quantity] from tutorial_schema.orders;
```

```sql
select product_id, quantity, id from tutorial_schema.orders;
```

```sql
select * from tutorial_schema.orders;
```

```sql
select id, * from tutorial_schema.orders;
```

```sql
select id as order_id from tutorial_schema.orders;
```

```sql
select id, id as order_id from tutorial_schema.orders;
```

```sql
select id as order_id, price as unit_price from tutorial_schema.orders;
```

```sql
select id order_id, price as unit_price from tutorial_schema.orders;
```

```sql
select tutorial_schema.orders.id, tutorial_schema.orders.price as unit_price from tutorial_schema.orders;
```


```sql
select t1.id, t1.price as unit_price from tutorial_schema.orders as t1;
```

```sql
select t1.id, t1.price as unit_price from tutorial_schema.orders t1;
```
[top](#Fabric-Data-Warehousing-SQL-Code)

## Selecting Distinct Records
```sql
select distinct category from tutorial_schema.products;
```

```sql
select distinct category, title from tutorial_schema.products;
```

```sql
select distinct * from tutorial_schema.products;
```
[top](#Fabric-Data-Warehousing-SQL-Code)

## Functions and Expressions
### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/functions/functions?view=sql-server-ver16

https://learn.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings

https://learn.microsoft.com/en-us/sql/t-sql/language-elements/expressions-transact-sql?view=sql-server-ver16

### SQL Code

-- arithmetic expressions
```sql
select *, quantity * unit_price as order_amount from tutorial_schema.orders;
select id, created_at, product_id, quantity, unit_price, quantity * unit_price as order_amount from tutorial_schema.orders;
select id, created_at, product_id, quantity, unit_price, quantity * 1.2 as price_after_tax from tutorial_schema.orders;
```

-- round
```sql
select id, created_at, product_id, quantity, unit_price, round(unit_price,1) from tutorial_schema.orders;
```

-- current_timestamp
```sql
select id, created_at, current_timestamp from tutorial_schema.orders;
```

--datediff
```sql
select id, created_at, current_timestamp, datediff(day, created_at, current_timestamp) as days_elapsed from tutorial_schema.orders;
```

--concat
```sql
select id, created_at, city, state, concat(city,', ', state) as address from tutorial_schema.users
```

-format
```sql
select id, created_at, format(created_at, 'MMMM / yy') as month_year from tutorial_schema.users
```

-- case expression
```sql
select
unit_price,
case
  when unit_price > 80 then 'high'
  when unit_price > 20 then 'moderate'
  else 'low'
end as price_class
from tutorial_schema.orders;
```
[top](#Fabric-Data-Warehousing-SQL-Code)

## Ordering and Limiting your Results
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Filtering Records
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Grouping and Aggregating
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Joining Tables
### Links and Resources
https://learn.microsoft.com/en-us/sql/relational-databases/performance/joins?view=sql-server-ver16
https://www.w3schools.com/sql/sql_join.asp


### SQL Code
```sql
SELECT
o.*,
p.*
FROM tutorial_schema.orders o
JOIN tutorial_schema.products p
ON o.product_id = p.id;
```

```sql
SELECT
o.*,
p.title,
p.category
FROM tutorial_schema.orders o
JOIN tutorial_schema.products p
ON o.product_id = p.id;
```

```sql
SELECT
o.*,
p.title,
p.category,
u.*
FROM tutorial_schema.orders o
LEFT JOIN tutorial_schema.products p
ON o.product_id = p.id
LEFT JOIN tutorial_schema.users u
ON o.user_id = u.id;
```

```sql
SELECT
o.*,
p.title,
p.category,
u.name,
u.source
FROM tutorial_schema.orders o
LEFT JOIN tutorial_schema.products p
ON o.product_id = p.id
LEFT JOIN tutorial_schema.users u
ON o.user_id = u.id;
```
[top](#Fabric-Data-Warehousing-SQL-Code)

## SQL Execution Order
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Create Table As Select
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Updating and Deleting Records
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Subqueries
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Views
### Links and Resources
https://learn.microsoft.com/en-us/sql/relational-databases/views/views?view=sql-server-ver16

### SQL Code
```sql
CREATE VIEW tutorial_schema.vw_customer_order_qty
AS
SELECT
u.id as customer_id,
u.name as customer_name,
count(*) as number_of_orders
FROM tutorial_schema.orders o
LEFT JOIN tutorial_schema.users u
ON o.user_id = u.id
GROUP BY u.id, u.name;
```

```sql
DROP VIEW tutorial_schema.vw_customer_order_qty;
```
[top](#Fabric-Data-Warehousing-SQL-Code)

## Zero Copy Clones and Time Travel
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
[top](#Fabric-Data-Warehousing-SQL-Code)

## Stored Procedures
### Links and Resources
https://learn.microsoft.com/en-us/sql/t-sql/statements/create-procedure-transact-sql?view=sql-server-ver16

### SQL Code
```sql
CREATE PROCEDURE 
    tutorial_schema.demo_proc
AS 
CREATE TABLE tutorial_schema.temp_table (name varchar(255), age INT);
INSERT INTO tutorial_schema.temp_table values ('Jon', 35);


EXEC tutorial_schema.demo_proc 
```
```sql
ALTER PROCEDURE
    tutorial_schema.demo_proc
AS 
SELECT * FROM tutorial_schema.orders;

EXEC tutorial_schema.demo_proc;
```

```sql
ALTER PROCEDURE 
    tutorial_schema.demo_proc (@price DECIMAL(10,2))
AS 
SELECT * FROM tutorial_schema.orders WHERE total > @price;

EXEC tutorial_schema.demo_proc @price = 80;
```

```sql
EXEC tutorial_schema.demo_proc 80;
```


```sql
ALTER PROCEDURE 
    tutorial_schema.demo_proc (@price DECIMAL(10,2) = 0)
AS 
SELECT * FROM tutorial_schema.orders WHERE total > @price;
```

```sql
ALTER PROCEDURE 
    tutorial_schema.demo_proc (@price INT = 0, @input_date DATE = '1970-01-01')
AS 
SELECT * FROM tutorial_schema.orders WHERE total > @price and created_at > @input_date;
```

```sql
DROP PROCEDURE tutorial_schema.demo_proc;
```
[top](#Fabric-Data-Warehousing-SQL-Code)

## Preparing the Presentation Layer and Semantic Model
### SQL Code

```sql
EXEC sp_rename 'tutorial_schema.orders' 'stg_orders';
EXEC sp_rename 'tutorial_schema.products' 'stg_products';
EXEC sp_rename 'tutorial_schema.reviews' 'stg_reviews';
EXEC sp_rename 'tutorial_schema.users' 'stg_users';
```

```sql
CREATE TABLE tutorial_schema.fact_orders
AS
SELECT 
id,
created_at,
convert(varchar(50), format(created_at, 'yyyy-MM')) as year_month,
user_id,
product_id,
quantity,
unit_price,
quantity*unit_price as total_order_amount
FROM
tutorial_schema.stg_orders; 
```

```sql
CREATE TABLE tutorial_schema.fact_reviews
AS
SELECT 
id,
created_at,
product_id,
rating
FROM
tutorial_schema.stg_reviews; 
```

```sql
CREATE TABLE tutorial_schema.dim_products
AS
SELECT 
id,
created_at,
title,
category,
vendor
FROM
tutorial_schema.stg_products; 
```

```sql
CREATE TABLE tutorial_schema.dim_users
AS
SELECT 
id,
created_at,
city,
state,
zip,
source
FROM
tutorial_schema.stg_users; 
```
