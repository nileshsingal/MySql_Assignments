# MySql Assignments



    CREATE DATABASE : 

```MySql
    CREATE DATABASE retail;
```


    USE DATABASE : 

```MySql
    USE retail;
```


    CREATE TABLE salespeople : 

```MySql
    CREATE TABLE salespeople
    (
        SNUM int PRIMARY KEY,
        SNAME varchar(255),
        CITY char(20),
        COMM decimal(9,2)
    );
```
    INSERT VALUES : 

```MySql
    INSERT INTO salespeople
    values(1001,"Pell","London",.12),
    (1002,"Serres","San Jose",.13),
    (1004,"Motika","London",.11),
    (1007,"Rifkin","Barcelona",.15),
    (1003,"AxelRod","New York",.10),
    (1005,"Fran","London",.26);
```


    CREATE TABLE customers : 

```MySql
    CREATE TABLE Customers
    (
        CNUM int PRIMARY KEY,
        CNAME varchar(255),
        CITY char(20),
        RATING int,
        SNUM int,
        FOREIGN KEY(SNUM) REFERENCES salespeople (SNUM)
);

```

    INSERT VALUES : 

```MySql
    INSERT INTO customers values (2001,"Hoffman","London",100,1001),
    (2002,"giovanni","Rome",200,1003),
    (2003,"Liu","San Jose",200,1002),
    (2004,"Grass","Berlin",300,1002),
    (2006,"Clemens","London",100,1001),
    (2008,"Cisneros","San Jose",300,1007),
    (2007,"Pereira","Rome",100,1004);
```


    CREATE TABLE orders : 

```MySql
    CREATE TABLE orders
    (
        ONUM int primary key,
        AMT decimal(10,2),
        ODATE date,
        CNUM int,
        SNUM int,
        FOREIGN KEY (SNUM) REFERENCES salespeople(SNUM),
        FOREIGN KEY (CNUM) REFERENCES customers(CNUM)
    );
```


    INSERT VALUES : 

```MySql
    INSERT INTO orders
    values (3001,18.69,"96/03/10",2008,1007),
    (3003,767.19,"96/03/10",2001,1001),
    (3002,1900.10,"96/03/10",2007,1004),
    (3005,5160.45,"96/03/10",2003,1002),
    (3006,1098.16,"96/03/10",2008,1007),
    (3009,1713.23,"96/04/10",2002,1003),
    (3007,75.75,"96/04/10",2002,1003),
    (3008,4723.00,"96/05/10",2006,1001),
    (3010,1309.95,"96/06/10",2004,1002),
    (3011,9891.88,"96/06/10",2006,1001);
```






`1. List all the columns of the Salespeople table.`


```MySql
    SELECT * FROM salespeople;
```
`2. List all customers with a rating of 100.`

```MySql
    SELECT * FROM customer WHERE rating=100;
```


