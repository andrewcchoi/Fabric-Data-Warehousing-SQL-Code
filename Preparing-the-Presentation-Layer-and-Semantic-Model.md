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