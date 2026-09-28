```
create table  user_activity(
user_id UInt32,
activity_type LowCardinality(String),
activity_date DateTime
)
engine = MergeTree
order by user_id
partition by toYYYYMMDD(activity_date)
```

До мутаций:

![1790619736597](images/README/1790619736597.png)

После мутаций:

![1790619774494](images/README/1790619774494.png)

Проверка мутаций:

![1790619852132](images/README/1790619852132.png)

Удаление партиции:

```
alter table `default`.user_activity drop partition '20260501';
```

До удаления:

![1790619890932](images/README/1790619890932.png)

После удаления:

![1790619905147](images/README/1790619905147.png)
