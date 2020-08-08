# POSTGRESQL

## Installation

  go to `https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-0://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04` for installation

### Setup

- check postgresql status `sudo service postgresql status`
- activate postgresql `sudo service postgresql start`
- restart postgresql `sudo service postgresql restart`

### change password of default `postgres` account

- login as postgres user `sudo -i -u postgres`
- run `psql`
- run `\password` and reset your password

**create user**

- run `sudo -u postgres createuser --interactive`

- **add user**
  - add user `sudo adduser fuadnafiz98`
  - login to user `sudo -i -u fuadnafiz98`
  - run `psql`

- __connection info__ `\conninfo`
-
- **create new database**

  - run `sudo -u postgres createdb demo`

**connect to localhost**

- run `\c <database_name>`

- list database `\l`
- drop database `drop database <name>`

**create database**

```bash
create table person (
id BIGSERIAL not null primary key,
firstName varchar(50) not null,
lastName varchar(50) not null,
gender varchar(10) not null,
dateOfBirth DATE not null
);
```

- list database `\d`
- list table `\dt`
- inspect table `\d <table_name>`
- drop table `drop table <table_name>`

- **insert into table**

```bash
insert into person (
firstName, 
lastName, 
gender,
dateOfBirth
) values( 'fuad', 'muhtasim', 'male', DATE '1998-03-01');
```






























