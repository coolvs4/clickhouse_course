```
create user jhon IDENTIFIED WITH plaintext_password BY 'qwerty';

create role devs;

GRANT SELECT ON *.* TO devs;

GRANT devs TO jhon;

select * from system.users

select  *from system.grants

select * from system.roles
```

![1790426287779](images/README/1790426287779.png)

![1790426297587](images/README/1790426297587.png)

![1790426302919](images/README/1790426302919.png)
