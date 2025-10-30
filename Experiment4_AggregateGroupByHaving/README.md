# Experiment 4: Aggregate Functions, Group By and Having Clause

## DEVOLOPED BY:NAVEEN.S
## REGISTER NUMBER:212223240106

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**

<img width="1286" height="670" alt="image" src="https://github.com/user-attachments/assets/31976ea0-75bf-4243-9666-bf081b0d1453" />


```sql
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);

```

**Output:**

<img width="1263" height="525" alt="image" src="https://github.com/user-attachments/assets/7a7b097e-39cf-4878-bb42-58976b987cd8" />


**Question 2**

<img width="1285" height="589" alt="image" src="https://github.com/user-attachments/assets/f29ef182-1721-48e1-86ce-6164b768274e" />


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);

```

**Output:**

<img width="1286" height="551" alt="image" src="https://github.com/user-attachments/assets/2b6aaf32-b76b-4f5d-9cbd-9defe8f04f4c" />

**Question 3**

<img width="1288" height="525" alt="image" src="https://github.com/user-attachments/assets/32385514-e97d-4d13-9d3b-bdbc33e1b3ad" />


```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);
```

**Output:**

<img width="1288" height="425" alt="image" src="https://github.com/user-attachments/assets/06d7d140-f642-4ec6-899d-31b3c0985e8e" />


**Question 4**

<img width="1285" height="664" alt="image" src="https://github.com/user-attachments/assets/eb712385-f52e-42e0-b396-a6790cfeb438" />



```sql
SELECT student_name, grade
FROM grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="1286" height="477" alt="image" src="https://github.com/user-attachments/assets/5fc7ad34-691c-4fcb-a95a-5dcbef7db25f" />


**Question 5**

<img width="1273" height="614" alt="image" src="https://github.com/user-attachments/assets/ac7cce0f-0575-495f-b974-ff3fb4a4334e" />


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM orders
    WHERE ord_date = '2012-10-10'
);
```

**Output:**

<img width="1285" height="487" alt="image" src="https://github.com/user-attachments/assets/5b98c443-5c04-4f9c-82ac-2bdb206fb25a" />


**Question 6**

![image](https://github.com/user-attachments/assets/ddb513e9-d0dd-4ccc-a25a-2ca4b7aa5079)


```sql
SELECT 
  COUNT(DISTINCT age) AS COUNT
FROM employee;
```

**Output:**

![image](https://github.com/user-attachments/assets/a21d4163-6297-456f-9546-8b006ce9f684)

**Question 7**

![image](https://github.com/user-attachments/assets/ff99991a-9ebf-46b3-99da-ad81d2fb0648)


```sql
SELECT 
  COUNT(*) AS COUNT
FROM customer
WHERE city != 'Noida';
```

**Output:**

![image](https://github.com/user-attachments/assets/ac49ab6c-2e9e-40a5-8688-04cca6a4495c)


**Question 8**

![image](https://github.com/user-attachments/assets/59e5c8ba-5690-4600-9923-98e88c8c701a)


```sql
SELECT 
  address, 
  SUM(salary)
FROM customer1
GROUP BY address
HAVING SUM(salary) > 2000;
```

**Output:**

![image](https://github.com/user-attachments/assets/07c6142c-3c22-471f-bdcd-437e145239ac)


**Question 9**

![image](https://github.com/user-attachments/assets/31ce49c3-a895-4667-92a6-163adf798228)

```sql
SELECT 
  category_id, 
  AVG(Price) 
FROM products
GROUP BY category_id
HAVING AVG(price) BETWEEN 10 AND 15;
```

**Output:**

![image](https://github.com/user-attachments/assets/5515b5eb-9b08-4a5b-bae1-eac3e29bc439)


**Question 10**

![image](https://github.com/user-attachments/assets/b4b8da44-8deb-4c7b-8b8a-f8a763339bef)


```sql
SELECT 
  age, 
  AVG(income)
FROM employee
GROUP BY age
HAVING AVG(income) BETWEEN 300000 AND 500000;
```

**Output:**

![image](https://github.com/user-attachments/assets/8689ff22-a9cd-4034-99a4-fbf98f2662aa)

## GRADE

<img width="1452" height="80" alt="image" src="https://github.com/user-attachments/assets/9de9c271-70aa-403c-8859-1997e79ca736" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
