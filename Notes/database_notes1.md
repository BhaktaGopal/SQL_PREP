## Database

### Types of Databases

#### SQL
- **Relational Database**
  - Data is stored in **tables** (rows + columns)
  - Tables are **related to each other**

#### NO-SQL
- **Key-Value**
  - Data stored as **key-value pairs**
- **Column-Based**
  - Data is grouped by **columns**
- **Graph**
  - Focus on **relationships between objects**
- **Document**
  - Structure is flexible
  - Data should fit into a **single document**

---

## Relational Database

### Types of SQL Commands

#### Data Definition Language (DDL)
- **CREATE**
- **ALTER**
- **DROP**

#### Data Manipulation Language (DML)
- **INSERT**
- **UPDATE**
- **DELETE**

#### Data Query Language (DQL)
- **SELECT**

---

## SQL Query Execution

### SQL Query Order

#### Coding Order
- **SELECT**
  - DISTINCT  
  - TOP  
- **FROM**
- **WHERE**
- **GROUP BY**
  - HAVING  
- **ORDER BY**

#### Execution Order
- **FROM**
- **WHERE**
- **GROUP BY**
- **HAVING**
- **SELECT**
- **DISTINCT**
- **ORDER BY**
- **TOP**

---

## TRUNCATE

- **TRUNCATE** is much faster than **DELETE**
- It ignores:
  - Checking
  - Logging

---

## Filtering Data

### Operators

#### Comparison Operators
- `=`, `<>`, `!=`, `>`, `>=`, `<`, `<=`

#### Logical Operators
- **AND**, **OR**, **NOT**

#### Range Operator
- **BETWEEN**
  - Boundary values are **inclusive**

#### Membership Operator
- **IN**, **NOT IN**

#### Search Operator
- **LIKE**
