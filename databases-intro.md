# Intro to Databases References and Code

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



## MySQLdb Example Code:


## Things I won't cover: 

* Most of the things in this lesson from CS304: http://cs.wellesley.edu/~cs304/lectures/04-MySQL-DML/
* Installing & setting up MySQL


