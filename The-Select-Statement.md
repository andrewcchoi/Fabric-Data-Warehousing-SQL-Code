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