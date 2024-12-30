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