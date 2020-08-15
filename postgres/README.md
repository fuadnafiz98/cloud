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
- execute postgresql `$ psql`

- show all database `\l`

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

- **connection info** `\conninfo`
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

  `select \* from person between date '2000-01-01' and '2000-02-02'

- **select table**
  `select * from pg_catalog.pg_tables where tableowner='demo02';`

- **MAX, MIN, AVG**

- **group by**

  - TODO: write details

- **in**

  - in

  ```sql
    SELECT *
    FROM Car
    WHERE make in ('Dodge', 'Volvo', 'Jeep')
  ```

  - not in

  ```sql
    SELECT *
    FROM Car
    WHERE make not in ('Dodge', 'Volvo', 'Jeep')
  ```

- **between**

  -

  ```sql
  SELECT * FROM Car
  WHERE price BETWEEN '$2.00' AND '$4.00'
  ```

### JOINS

- create two table and insert data

```sql
CREATE TABLE basket_a (
    a INT PRIMARY KEY,
    fruit_a VARCHAR (100) NOT NULL
  );

  CREATE TABLE basket_b (
      b INT PRIMARY KEY,
      fruit_b VARCHAR (100) NOT NULL
  );

  INSERT INTO basket_a (a, fruit_a)
  VALUES
      (1, 'Apple'),
      (2, 'Orange'),
      (3, 'Banana'),
      (4, 'Cucumber');

  INSERT INTO basket_b (b, fruit_b)
  VALUES
      (1, 'Orange'),
      (2, 'Apple'),
      (3, 'Watermelon'),
      (4, 'Pear');
```

- 4 types of join

  - inner join - inner join creates output table only contains the rows that matches the specific condition.
    `sql SELECT a, fruit_a, b, fruit_b FROM basket_a INNER JOIN basket_b ON fruit_a = fruit_b;`

  - left join

    - left join prints all the rows of left database along with the colums of the right table which meets the condition.

    ```sql
    SELECT
    a,
    fruit_a,
    b,
    fruit_b
    FROM
    basket_a
    LEFT JOIN basket_b
    ON fruit_a = fruit_b;
    ```

    > NOTE: `left join` `left outer join` ??

  - right join

    - right join does the same thing, print all rows from the right table and only the columns from left column that meets the condition.

    ```sql
    SELECT
    a,
    fruit_a,
    b,
    fruit_b
    FROM
    basket_a
    RIGHT JOIN basket_b
    ON fruit_a = fruit_b;
    ```

  - outer join

    - returns all rows but prints the matching rows first

    ```sql

    ```

- **Self Join**

  - lets create a employee table and insert some data
    ```sql
    CREATE TABLE employee (
      employee_id  INT not null primary key,
      first_name varchar(50),
      last_name varchar(50),
      job_title varchar(50),
      salary INT,
      reports_to INT,
      office_id INT
    )
    INSERT INTO employee(
      employee_id,
      first_name,
      last_name,
      job_title,
      salary,
      reports_to,
      office_id
    ) values(1, 'fuad', 'nafiz', 'swe', '100', 2, 10),
    (2, 'fuad', 'nafiz', 'swe', '100', , 10),
    (3, 'fuad', 'nafiz', 'swe', '100', 2, 10)
    ```
  - here all employee reports to the second employee, so if we want the employee imformation as well as their respective managers then we can query
    ```sql
    SELECT * from
    employee
    JOIN
    employee
    ON employee.reports_to = employee.employee_id
    ```

- **UNIONS**

  -
