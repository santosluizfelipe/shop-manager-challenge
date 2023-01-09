1. Extract nouns from the user stories or specification
# EXAMPLE USER STORY:
# (analyse only the relevant part - here the final line).

As a shop manager
So I can know which items I have in stock
I want to keep a list of my shop items with their name and unit price.

As a shop manager
So I can know which items I have in stock
I want to know which quantity (a number) I have for each item.

As a shop manager
So I can manage items
I want to be able to create a new item.

As a shop manager
So I can know which orders were made
I want to keep a list of orders with their customer name.

As a shop manager
So I can know which orders were made
I want to assign each order to their corresponding item.

As a shop manager
So I can know which orders were made
I want to know on which date an order was placed. 

As a shop manager
So I can manage orders
I want to be able to create a new order.

recipes , name, cooking_time, rating
2. Infer the Table Name and Columns
Put the different nouns in this table. Replace the example with your own nouns.

Nouns:
students names, cohort names, starting dates

3. Decide the column types.
Here's a full documentation of PostgreSQL data types.

Most of the time, you'll need either text, int, bigint, numeric, or boolean. If you're in doubt, do some research or ask your peers.

Remember to always have the primary key id as a first column. Its type will always be SERIAL.

# EXAMPLE:

|Record                   | Properties     |
|-------------------------|----------------|
|items                      name, price, quantity
|orders                   | costumer_name, date


Table students
id SERIAL
name text

Table cohorts
id SERIAL
name text
starting_date date

4. Write the SQL.
-- EXAMPLE
```
Can a item have many orders? yes
Can a order have many items? Yes

Student -> many to many -> Cohort
The foreign key is on students (cohort_id)
```

-- file: movies_table.sql

-- Replace the table name, columm names and types.

CREATE TABLE cohorts (
  id SERIAL PRIMARY KEY,
  name text,
  starting_date date
);

CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  name text,
  cohort_id int,
  constraint fk_cohort foreign key(cohort_id) references cohorts(id)
);
5. Create the table.