# schema & instance

[https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=584&x=501&y=202&w=991&h=391&store=1&accept=image%2F*&auth=LCA%2094fe86f96fa404a34b6b264a0b3720ba7e69c3d94db3abe392976eacff4ffde6-ts%3D1721880450](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=584&x=501&y=202&w=991&h=391&store=1&accept=image%2F*&auth=LCA%2094fe86f96fa404a34b6b264a0b3720ba7e69c3d94db3abe392976eacff4ffde6-ts%3D1721880450)

Logical Structure of Table

```sql
create table t1
(
sn int,
name varchar2(10) ,
age numeric(2)
);
desc t1;
```

if we describe the table then we see the logical structure of table that is known as schema of table

(it is static in nature but it can be changed with proper permission and authorization) 

| s.no | name | data |
| --- | --- | --- |
|  |  |  |
|  |  |  |
|  |  |  |

### instance of table

once the schema of table is created then different types of operations such as insert delete and update/ modify are performed on the table if we view the table at any moment , the obtained result / output is known as instance of table for that time (it is dynamic in nature which keeps changing)

[https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=742&x=265&y=134&w=1250&h=747&store=1&accept=image%2F*&auth=LCA%20785d7af0b3cf16e6643c689030d25438c7627e5580b938c31a298c1b679237a5-ts%3D1721880450](https://documents.lucid.app/documents/cee76dc4-25c6-4752-9711-484e7c50ee4e/pages/0_0?a=742&x=265&y=134&w=1250&h=747&store=1&accept=image%2F*&auth=LCA%20785d7af0b3cf16e6643c689030d25438c7627e5580b938c31a298c1b679237a5-ts%3D1721880450)