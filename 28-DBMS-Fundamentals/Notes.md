# Day 28 - DBMS Fundamentals

## Goal
Understand relational database concepts before diving into SQL - foundational for database administration, security, and most backend/security tooling.

---

## 1. Relational Database Concepts

A **Relational Database Management System (RDBMS)** stores data in tables (relations) made up of rows (records) and columns (fields/attributes).

Examples: MySQL, PostgreSQL, Microsoft SQL Server, Oracle DB, SQLite.

Why "relational"? Tables can be related to one another through shared keys, avoiding data duplication.

## 2. ER Diagrams (Entity-Relationship Diagrams)

A visual representation of database structure before implementation.

Components:
- **Entity**: a real-world object/concept represented as a table (e.g., Customer, Order)
- **Attribute**: a property of an entity (e.g., Customer Name, Order Date) - becomes a column
- **Relationship**: how entities connect (e.g., a Customer "places" an Order)

Relationship types:
- **One-to-One**: one record in Table A relates to exactly one in Table B
- **One-to-Many**: one record in Table A relates to many in Table B (most common, e.g., one Customer has many Orders)
- **Many-to-Many**: many records in Table A relate to many in Table B (usually implemented via a junction/bridge table)

## 3. Normalization

The process of organizing data to reduce redundancy and improve data integrity.

### 1NF (First Normal Form)
- Each column contains atomic (indivisible) values
- No repeating groups/arrays in a single column

### 2NF (Second Normal Form)
- Must satisfy 1NF
- No partial dependency - every non-key column depends on the ENTIRE primary key (relevant for composite keys)

### 3NF (Third Normal Form)
- Must satisfy 2NF
- No transitive dependency - non-key columns depend only on the primary key, not on other non-key columns

Example of normalization in practice:
```
Unnormalized:
OrderID | CustomerName | CustomerEmail | Product
1       | John         | john@x.com    | Laptop

Normalized (split into two tables):
Customers: CustomerID | Name | Email
Orders: OrderID | CustomerID | Product
```

## 4. Keys

- **Primary Key (PK)**: uniquely identifies each row in a table; cannot be NULL, must be unique
- **Foreign Key (FK)**: a column that references the Primary Key of another table, establishing a relationship between tables
- **Unique Key**: ensures all values in a column are unique, but (unlike PK) can allow one NULL value

Example:
```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    Email VARCHAR(255) UNIQUE
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

---

## Interview Questions

**Q1. What is normalization and why is it important?**
The process of structuring database tables to reduce data redundancy and improve integrity, by following rules like 1NF, 2NF, and 3NF.

**Q2. Difference between Primary Key and Foreign Key?**
A Primary Key uniquely identifies rows within its own table; a Foreign Key references the Primary Key of another table to create a relationship between them.

**Q3. What is a One-to-Many relationship? Give an example.**
One record in a table relates to multiple records in another table - e.g., one Customer can place many Orders.

**Q4. Can a Foreign Key be NULL?**
Yes, typically - unless explicitly constrained otherwise, since not every record may need to reference another table's row.

## Key Takeaways
- Understood relational database fundamentals and RDBMS examples
- Learned ER diagram components: entities, attributes, relationships
- Learned normalization through 1NF, 2NF, 3NF with examples
- Understood Primary Key, Foreign Key, and Unique Key concepts
