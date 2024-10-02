문제 1
![screen](./)

```
select a.item_id, item_name from ITEM_INFO as a
inner join item_tree as b on
a.item_id = b.item_id
where parent_item_id is null
```