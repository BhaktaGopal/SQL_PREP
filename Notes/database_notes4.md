**FUNCTIONS IN SQL:**



* FUNCTION(column\_name)



***Types of functions:***



1. **Aggregate Functions:-**

&#x20;   Operate on multiple rows and return one value.



&#x20;   **Common Aggregate Functions:-**

&#x09;

|COUNT()|Number of rows|
|-|-|
|SUM()|Total sum|
|AVG()|Average|
|MIN()|Minimum value|
|MAX()|Maximum value|



**2.  Scalar Functions:-**

&#x09;Operate on each row individually	

   1. **String functions:-**

&#x09;

|UPPER()|UPPER('hello') → HELLO|
|-|-|
|LOWER()|LOWER('HELLO') → hello|
|LENGTH()/LEN()|length of string|
|SUBSTRING()|extract part|
|CONCAT()|join strings|



eg. SELECT UPPER(name) FROM users;



&#x20;  2. **Numeric functions:-**

|ROUND()|ROUND(12.345, 2)|
|-|-|
|ABS()|ABS(-10) → 10|
|CEIL()|CEIL(4.2) → 5|
|FLOOR()|FLOOR(4.8) → 4|



eg. SELECT ROUND(salary, 2) FROM employees;

&#x20;

&#x20;  3. **Date Functions:-**

|NOW()|Current date \& time|
|-|-|
|CURDATE()|Current date|
|YEAR()|Extract year|
|MONTH()|Extract month|



eg. SELECT YEAR(order\_date) FROM orders;

&#x20;  

&#x20;  4.**Conversion Functions:-**

|CAST()|CAST(123 AS CHAR)|
|-|-|
|CONVERT()|convert datatype|



eg. SELECT CAST(salary AS CHAR) FROM employees;



**3.Conditional Functions:-**

&#x09;CASE:-

&#x09;	works like *if-else-*



&#x09;	SELECT name,

&#x20;      			CASE 

&#x20;          		    WHEN salary > 5000 THEN 'High'

&#x20;          		    ELSE 'Low'

&#x20;      			END AS category

&#x09;	FROM employees;

&#x09;In MySQL-



&#x09;SELECT IF(salary > 5000, 'High', 'Low') FROM employees;



**4.NULL Functions:-**

&#x09;

|IFNULL()|replace NULL|
|-|-|
|COALESCE()|first non-null value|



eg. SELECT IFNULL(salary, 0) FROM employees;



**1. IFNULL() (MySQL)**

✅ Use Case:



**Replace NULL with a default value**



📌 Example Table: employees

|NAME|BONUS|SALARY|
|-|-|-|
|A|NULL|5000|
|B|2000|NULL|
|C|NULL|NULL|



**🔹 Query:-**	

&#x09;*SELECT name, IFNULL(salary, 0) AS salary*

&#x09;*FROM employees;*

🔹 **Output**

name	salary

A	5000

B	0

C	0



👉 NULL replaced with 0



**🔷 2. COALESCE() (More Powerful)**

✅ Use Case:



**Return first non-null value**



🔹 **Query:-**

&#x09;*SELECT name, COALESCE(bonus, salary, 0) AS income*

&#x09;*FROM employees;*

🔹 Output

name	income

A	5000

B	2000

C	0



👉 Priority:



**bonus → salary → 0**



**🔷 3. NULL in Calculations (Important)**

❌ Problem

SELECT salary + bonus FROM employees;



👉 If any value is NULL → result becomes NULL



✅ Fix

SELECT IFNULL(salary,0) + IFNULL(bonus,0) AS total

FROM employees;



**🔷 4. NULL in WHERE Clause**

❌ Wrong

WHERE salary = NULL   -- ❌

✅ Correct

WHERE salary IS NULL

🔹 Example

SELECT \*

FROM employees

WHERE salary IS NULL;



**🔷 5. NULLIF() (Less Known but Useful)**

✅ Use Case:



Returns NULL if two values are equal



📌 Example

SELECT NULLIF(10, 10);  -- returns NULL

SELECT NULLIF(10, 5);   -- returns 10

🔹 Practical Example



Avoid division by zero:



SELECT salary / NULLIF(bonus, 0)

FROM employees;



👉 If bonus = 0 → returns NULL instead of error



🔷 6. COALESCE vs IFNULL

Feature	IFNULL	COALESCE

Inputs	2 only	Multiple

Standard SQL	❌	✅

Flexibility	Low	High

🚀 Real Interview Examples

🔹 Replace NULL names

SELECT IFNULL(name, 'Unknown') FROM users;

🔹 Total salary safely

SELECT COALESCE(salary,0) + COALESCE(bonus,0)

FROM employees;

🔹 Find missing data

SELECT \*

FROM employees

WHERE salary IS NULL;

🔥 Key Takeaways

IFNULL(x, y) → replace NULL

COALESCE(a, b, c) → first non-null

NULLIF(a, b) → return NULL if equal

Always use IS NULL, not = NULL





#### **Important Rules:-**



*Aggregate functions cannot be used directly in WHERE*



**❌ Wrong:**



WHERE AVG(salary) > 5000



**✔️ Correct:**



HAVING AVG(salary) > 5000

