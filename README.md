# CRUD with NodeJS and Postgresql

## Content
- Run Postgress with Docker
- Create Database and Table
- Insert Data into Table
- Run NodeJS App
- Perform CRUD API

### Run Postgresql with Docker
```
docker run --name postgresql -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=Pass987! -p 5432:5432 -v postgres_data:/var/lib/postgresql/data -d postgres
```

```
docker exec -it postgresql /bin/bash
psql -U admin
```

### Create Database and List Database
```
admin=# CREATE DATABASE your_db_name;
admin=# \l
                                             List of databases
   Name    | Owner | Encoding |  Collate   |   Ctype    | ICU Locale | Locale Provider | Access privileges 
-----------+-------+----------+------------+------------+------------+-----------------+-------------------
 admin     | admin | UTF8     | en_US.utf8 | en_US.utf8 |            | libc            | 
 db_name   | admin | UTF8     | en_US.utf8 | en_US.utf8 |            | libc            | 
 postgres  | admin | UTF8     | en_US.utf8 | en_US.utf8 |            | libc            | 
 template0 | admin | UTF8     | en_US.utf8 | en_US.utf8 |            | libc            | =c/admin         +
           |       |          |            |            |            |                 | admin=CTc/admin
 template1 | admin | UTF8     | en_US.utf8 | en_US.utf8 |            | libc            | =c/admin         +
           |       |          |            |            |            |                 | admin=CTc/admin
(5 rows)

admin=# \c dbb_name
You are now connected to database "db_name" as user "admin".
```

### Create Table and Select Table
```
crud= # \d
CREATE TABLE table_name(
   column1 datatype,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
   PRIMARY KEY( one or more columns )
);

crud=# \d
             List of relations
 Schema |      Name      |   Type   | Owner 
--------+----------------+----------+-------
 public | contact        | table    | admin
 public | contact_id_seq | sequence | admin
(2 rows)
```

### Insert Data into Table
```
crud=# INSERT INTO TABLE_NAME (column1, column2, column3,...columnN)
VALUES (value1, value2, value3,...valueN);

crud=# SELECT * FROM contact;
 id | nickname |                      address                       
----+----------+----------------------------------------------------
  1 | David    | Texas                                             
  4 | agus     | bandung                                           
  5 | abdul    | solo                                              
(3 rows)
```

### Run NodeJS App
```
npm install
node server.js
```

### Perform CRUD API with Postman
READ
![get1.png](./img/get1.png)
![get2.png](./img/get2.png)

DELETE
![del.png](./img/del.png)

CREATE
![post.png](./img/post.png)

UPDATE
![put.png](./img/put.png)