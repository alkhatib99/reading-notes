# Introduction to SQL

---

## sql (Structured Query Language)

Its a language designed to  manipulate and transform data from a relational database

---

## Relational databases

**relational database represents a collection of related (two-dimensional) tables.**

---

### SQL COMMANDS

- To retrieve data from a SQL database, we need to write "SELECT"

`SELECT column, another_column, …`

`FROM mytable;`

- To get a specific rows in the table we can use "WHERE" 

`SELECT column, another_column, …`

`FROM mytable`

`WHERE condition`

    `AND/OR another_condition
    AND/OR …;`

- to discard rows that have a duplicate column value "DISTINCT"

    `SELECT DISTINCT column, another_column, …`
  
`FROM mytable`

`WHERE condition(s);`

- Using the "JOIN" clause in a query, we can combine row data across two separate tables using this unique key.
 The first of the joins that we will introduce is the "INNER JOIN".
 `SELECT column, another_table_column, …`
`FROM mytable`

`INNER JOIN another_table`

  `ON mytable.id = another_table.id`
`WHERE condition(s)`

`ORDER BY column, … ASC/DESC`

`LIMIT num_limit OFFSET num_offset;`

---

### sql table

![sql table](images/sql.png)

---

### Screenshots

> these are tasks 1-6.
![task1](./img/task1.PNG)
![task2](./img/task2.PNG)
![task3](./img/task3.PNG)
![task4](./img/task4.PNG)
![task5](./img/review1.PNG)
![task6](./img/task6.PNG)
> these are tasks 13-18
![task13](./img/task13.PNG)
![task14](./img/task14.PNG)
![task15](./img/task15.PNG)
![task16](./img/task16.PNG)
![task17](./img/task17.PNG)
![task18](./img/task18.PNG).
