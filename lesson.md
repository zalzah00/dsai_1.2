# Lesson

## Brief

### Preparation

Basic understanding of RDBMS tables and columns.

### Lesson Overview

This lesson introduces database concepts and data modeling. Learners will be able to perform data modeling and create ERD from case study.

---

## Part 1 - Introduction to relational databases

Conceptual knowledge, refer to slides.

---

## Part 2 - Data modeling

### 2.1 SQL Data Types

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

### 2.2 Entity-relationship diagram (ERD)

An entity-relationship diagram (ERD) is a visual representation of entities and their relationships in a database. ERD is a data modeling technique. It is a graphical representation of data requirements for a database.

#### 2.2.1 Entities

An entity is a real-world object, for example, an employee, bank account, car, etc. An entity has attributes that represent properties such as an employee has a name, age, and salary. An entity set is a collection of similar entities. For example, all employees have some common attributes.

#### 2.2.2 Relationships

A relationship is an association among entities. For example, an employee works at a department, a car has a model, etc. A relationship set is a collection of similar relationships. For example, all employees work at some department. A relationship can have attributes. For example, the salary of an employee in a department.

#### 2.2.3 Cardinality

Cardinality represents the number of entities in one entity set, which can be associated with the number of entities of another entity set. There are three types of cardinality:

- One to one: One entity from entity set A can be associated with at most one entity of entity set B and vice versa.
- One to many: One entity from entity set A can be associated with more than one entity of entity set B, but an entity from entity set B can be associated with at most one entity of entity set A.
- Many to many: One entity from entity set A can be associated with more than one entity of entity set B and vice versa.

### 2.3 ERD Tools

Use [dbdiagram.io](https://dbdiagram.io/d) to design and create ERD. Sign in with your Google or Github account.

### 2.4 Case Study

#### 2.4.1 Scenario 1

Construct an ERD for a car insurance company whose customers own one or more cars each. Each car has associated with it zero to any number of recorded accidents.

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

#### 2.4.2 Scenario 2

Construct an ERD for a school system whose classes have students and teachers. Each student belongs to a single class. Each teacher may teach more than one class, and each class may have more than one teacher.

Each entity has the following attributes:

- Student: id, name, address, phone, email, class_id
- Teacher: id, name, address, phone, email
- Class: id, name, teacher_id

#### 2.4.3 Scenario 3

Construct an ERD for a company that sells movies online. The company has a website where customers can browse available movies and place orders. Each order can contain multiple movies.
