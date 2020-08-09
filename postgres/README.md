# POSTGRESQL

## Initial Installation on Ubuntu(18.04)

- you can always go [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-0://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04) for more information

- run
  ```bash
  $ sudo apt update 
  $ sudo apt install postgresql postgresql-contrib
  ```
- create a new ubuntu user 
  ```bash
  $ sudo adduser demo
  ```
- switch to new user
  ```bash
  $ sudo -i -u demo
  ```

- create new database
  ```bash
  $ createdb demodb
  ```
- execute postgresql   `$ psql`

- show all database  `\l`

- connect to database
  ```bash
  $ \c deomdb
  ```

- create table
  ```bash
  create table person (
    id BIGSERIAL not null primary key,
    firstName varchar(50) not null,
    lastName varchar(50) not null,
  );
  ```

- show all table `\d`
- show column of one table `\d <table_name>`

  - ```bash
    $ \d person
    ```

- insert data

  ```bash
  insert into person (
  firstName, 
  lastName, 
  ) values( 'fuad', 'muhtasim');
  ```

- select data 

  ```bash
  $ select * from person
  ```


## Links

  - [mock data](https://www.mockaroo.com/)


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

- **limit output** 

  `select * from person limit 10;`

- **offset**

  starts from offset position
  ```bash
  select * from person offset 5;
  ```

- **select query in array**

  `select * from person where country in ('bangladesh', 'india', 'england', 'spain');`

- **between**

  `select * from person between date '2000-01-01' and '2000-02-02'

- **select table**
  `select * from pg_catalog.pg_tables where tableowner='demo02';`

- **MAX, MIN, AVG**

- **group by**

  - TODO: write details 

- 
