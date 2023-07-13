# Lesson

## Brief

### Preparation

Basic understanding of RDBMS tables and columns.

### Lesson Overview

This lesson introduces database concepts and data modelling. Learners will be able to perform data modelling and create ERD from case study.

---

## Part 1 - Introduction to relational databases

Conceptual knowledge, refer to slides.

---

## Part 2 - Data modelling

### SQL Data Types

Here are the common data types, every database has its own set of data types.

| Data Type  | Description                |
| ---------- | -------------------------- |
| `INT`      | Integer, whole number.     |
| `VARCHAR`  | Variable length character. |
| `TEXT`     | Long text.                 |
| `DATE`     | Date.                      |
| `TIME`     | Time.                      |
| `DATETIME` | Date and time.             |
| `BOOLEAN`  | True or false.             |

### ERD Tools

Use [dbdiagram.io](https://dbdiagram.io/d) to design and create ERD. Sign in with your Google or Github account.

### Case Study

#### Scenario 1

Construct an ER diagram for a car insurance company whose customers own one or more cars each. Each car has associated with it zero to any number of recorded accidents.

Each entity has the following attributes:

- Customer: id, name, address, phone, email
- Car: id, make, model, year, car_plate
- Accident: id, date, location, description, car_id

Use the following DBML to create the ERD.

```dbml
Table customers {
  id int [pk, increment]
  name varchar
  address varchar
  phone varchar
  email varchar
}

Table cars {
  id int [pk, increment]
  make varchar
  model varchar
  year int
  car_plate varchar
  customer_id int
}

Table accidents {
  id int [pk, increment]
  date datetime
  location varchar
  description text
  car_id int
}

Ref: cars.customer_id > customers.id // many-to-one

Ref: accidents.car_id > cars.id // many-to-one
```

#### Scenario 2

Construct an ER diagram for a school system whose classes have students and teachers. Each student belongs to a single class. Each teacher may teach more than one class, and each class may have more than one teacher.

Each entity has the following attributes:

- Student: id, name, address, phone, email, class_id
- Teacher: id, name, address, phone, email
- Class: id, name, teacher_id

#### Scenario 3

Construct an ER diagram for a company that sells movies online. The company has a website where customers can browse available movies and place orders. Each order can contain multiple movies.
