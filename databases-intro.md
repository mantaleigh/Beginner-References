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
       cid integer,             -- key in owner
       species enum('dog','cat','rabbit','iguana','hamster','gerbil','other'),
       other varchar(50),       -- "snakes, why did it have to be snakes?"
       name varchar(50),
       birthday date,
       sex enum('male','female'),
       neutered enum('y','n')
       );
```
