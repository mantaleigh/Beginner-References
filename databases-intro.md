# Intro to Databases References and Code

Basically a condensed version of an early lecture from Wellesley CS304: http://cs.wellesley.edu/~cs304/lectures/03-MySQL-Admin-and-DDL/ (thanks, Scott!)

Slides: https://drive.google.com/file/d/0BxoZvjkjdnucbTFDOFFPMnBkUVE/view?usp=sharing

## Example DDL: 

```sql
-- An example database for a veterinarian's office.  We have owner,
-- and patient tables

drop table if exists vet_owner;
create table vet_owner(
       cid integer auto_increment primary key,
       name varchar(50) not null,
       address varchar(100),
       balance decimal(8,2) default 0,     -- up to $999,999.99 is plenty
       email varchar(50) default null,     -- email address
       ads_ok enum('y','n') default 'n',   -- is it okay to send spam?
       phone char(10)
       );

drop table if exists vet_pet;
create table vet_pet(
       cid integer,             -- refers to the key in owner
       species enum('dog','cat','rabbit','iguana','hamster','gerbil','other'),
       other varchar(50),
       name varchar(50),
       birthday date,
       sex enum('male','female'),
       neutered enum('y','n')
       );
```

## Inserting: 

```sql
insert into vet_owner(cid,name,address,email,phone) values
       (1,'Homer Simpson','Springfield','','555-1234'),
       (2,'Bill Clinton','Chappaqua, NY','ex-pres@hotmail.com','555-0000'),
       (3,'Barack Obama','Chicago','president@whitehouse.gov','555-5555'),
       (4,'Old MacDonald','Vermont','eieio@gmail.com','555-1234');

insert into vet_pet(cid,species,name) values
       (1,'dog','Santa''s Little Helper'),
       (1,'cat','Snowball'),
       (1,'cat','Snowball II'),
       (2,'dog','Buddy'),
       (3,'dog','Bo'),
       (4,'other','Dolly Llama');
       
-- Inserting only one row: 
insert into vet_pet(cid,species,name,sex) values (2,'dog','Molly','female');
```

## Updating: 

```sql 
-- this will update Bo
UPDATE pet
SET neutered = 'Y'
WHERE cid=3 AND name='Bo';

-- if we had a unique pet id, the WHERE statement here would be simpler
```

## Deleting:

Homer decides to take his vets to a different vet:
```sql 
DELETE FROM pets WHERE cid=1;
DELETE FROM customer WHERE cid=1;
```

## Queries: 

### Basic select statements
```sql 
select * from vet_owner; 

select name from vet_pet;

SELECT name,email,balance
FROM vet_owner
WHERE balance > 0;
```

### More select statements

#### All Pets
```sql
SELECT name,breed,weight
FROM pets;
All Heavy Pets
```

#### Heavy Pets
```sql
SELECT name,breed,weight
FROM pets
WHERE weight > 50
```

#### Breed Average Weight
```sql
SELECT breed,avg(weight) -- using an aggregate function
FROM pets
GROUP BY breed
Heavy Breeds
```

#### Choose among groups using a HAVING clause
```sql
SELECT breed,avg(weight)
FROM pets
GROUP BY breed
HAVING avg(weight) > 50
```

### Sorting

#### Breeds in alphabetical order (ascending)
```sql
SELECT breed,avg(weight)
FROM pets
GROUP BY breed
ORDER BY breed asc
```

#### Breeds listed in descending order of weight
```sql
SELECT breed,avg(weight)
FROM pets
GROUP BY breed
ORDER BY avg(weight) desc
```

## MySQLdb Example Code:
```python
#!/usr/bin/python

import MySQLdb

database = "CODINGGROUND"
username = 'root'
password = 'root'

# Open database connection
db = MySQLdb.connect(unix_socket='/home/cg/mysql/mysql.sock', host='localhost', user=username, passwd=password, db=database )

# prepare a cursor object using cursor() method
cursor = db.cursor(MySQLdb.cursors.DictCursor)

sql = "select * from users"

try:
   cursor.execute(sql)
   results = cursor.fetchall()
   print "<table style='width:100%'>"
   for row in results:
      id   = row["id"]
      name = row["name"]
      age  = row["age"]
      sex  = row["sex"]
      print "<tr><td>%d</td><td>%s</td><td>%d</td><td>%s</td></tr>"%  (id, name, age, sex)

   print "</table>"
except:
   print "Error: unable to fecth data"

db.close()
```

Run here: http://www.tutorialspoint.com/python_mysql_online.php

## Things I won't cover: 

* Most of the things in this lesson from CS304: http://cs.wellesley.edu/~cs304/lectures/04-MySQL-DML/
* Installing & setting up MySQL
* Preventing SQL injection vulnerabilities (!!! important if you're putting input from the user into your db - but no time)
 - https://xkcd.com/327/
* Maybe some other stuff you wish I would have thought to tell you or had time to tell you ¯\_(ツ)_/¯


