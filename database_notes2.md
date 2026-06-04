## Combining Data

### Joins

#### a. Basic Joins
- **Inner Join**
- **Left Join**
- **Right Join**
- **Full Join**

---

#### b. Advanced Joins

### i. Left Anti Join
- Returns rows from the **left table** that have **no match in the right table**

**Query Example:**
```sql
SELECT *
FROM customers AS c
LEFT JOIN orders AS o
ON c.id = o.customer_id
WHERE o.customer_id IS NULL;
```

---

### ii. Right Anti Join
- Returns rows from the **right table** that have **no match in the left table**

**Query Example:**
```sql
SELECT *
FROM customers AS c
RIGHT JOIN orders AS o
ON c.id = o.customer_id
WHERE c.id IS NULL;
```

---

### iii. Full Anti Join
- Returns rows that **do not match in either table**
- Combines unmatched rows from **both left and right tables**

**Query Example:**
```sql
SELECT *
FROM orders AS o
FULL JOIN customers AS c
ON c.id = o.customer_id
WHERE c.id IS NULL OR o.customer_id IS NULL;
```

---

### iv. Cross Join
- Combines **every row from left table** with **every row from right table**
- Produces **all possible combinations (Cartesian Product)**

**Query Example:**
```sql
SELECT *
FROM customers
CROSS JOIN orders;
```

---

### v. When to Use Which Join?

- **Only Matching Rows**
  - Use **Inner Join**

- **All Rows**
  - **One Side Important (Master Table)** → Use **Left Join**
  - **Both Sides Important** → Use **Full Join**

- **Only Unmatching Rows**
  - **One Side (Master Table)** → Use **Left Anti Join**
  - **Both Sides Important** → Use **Full Anti Join**

---

### vi. How to Join Multiple Tables?
- Use multiple **JOIN clauses** sequentially

**Example:**
```sql
SELECT *
FROM table1
JOIN table2 ON condition1
JOIN table3 ON condition2;
```
