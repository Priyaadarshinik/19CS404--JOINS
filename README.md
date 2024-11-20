# 19CS404--JOINS
# Register number: 212223240126
# AIM: 
To study and implement different types of joins. 
 
# THEORY: 
The SQL Joins clause is used to combine records from two or more tables in a database. A JOIN 
is a means for combining fields from two tables by using values common to each.The join is 
actually performed by the ‘where’ clause which combines specified rows of tables. 
 
Syntax: 
SELECT column 1, column 2, column 3... FROM table_name1, table_name2 
WHERE table_name1.column name = table_name2.columnname; 
 
# Types of Joins: 
●Inner Join 
●Left (Outer) Join 
●Right (Outer) Join 
●Full (Outer) Join 
 
INNER JOIN 
The INNER JOIN keyword selects records that have matching values in both tables. 
 
Syntax: 
SELECTcolumn_name(s) FROM table1 INNER JOIN table2 
ON table1.column_name = table2.column_name; 
 
LEFT JOIN 
The LEFT JOIN keyword returns all records from the left table (table1), and the matching 
records from the right table (table2). The result is 0 records from the right side, if there is no 
match. 
 
Syntax: 
SELECT column_name(s) 
FROM table1 
LEFT JOIN table2 
ON table1.column_name = table2.column_name; 
  
RIGHT JOIN 
The RIGHT JOIN keyword returns all records from the right table (table2), and the matching 
records from the left table (table1). The result is 0 records from the left side, if there is no match. 
 
Syntax: 
SELECT column_name(s) 
FROM table1 
RIGHT JOIN table2 
ON table1.column_name = table2.column_name; 
 
FULL OUTER JOIN 
The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or 
right (table2) table records. 
 
FULL OUTER JOIN and FULL JOIN are the same. 
 
Syntax: 
SELECT column_name(s) 
FROM table1 
FULL OUTER JOIN table2 
ON table1.column_name = table2.column_name 
WHERE condition; 
 
 
# Question 1: 
Write the SQL query that achieves the selection of all columns from the "salesman" table 
(aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for 
customers with the name 'Fabian Johns'. 
 
Answer: 
SELECT s.* 
FROM salesman s 
LEFT JOIN customer c ON s.salesman_id = c.salesman_id 
WHERE c.cust_name = 'Fabian Johns'; 
 
Output: 

 ![image](https://github.com/user-attachments/assets/8b91edc1-8978-4fb8-ac43-a7f93b172564)

 
# Question 2: 
From the following tables write a SQL query to locate those salespeople who do not live in the 
same city where their customers live and have received a commission of more than 12% from the 
company. Return Customer Name, customer city, Salesman, salesman city, commission.   
Sample table: customer 

![image](https://github.com/user-attachments/assets/db7f29fb-789c-4d07-ae4c-1e8b1adaa588)

Sample table: salesman 

![image](https://github.com/user-attachments/assets/b3b70d36-cd74-495e-bf14-b8265a23db8b)

 
Answer: 

SELECT  
    c.cust_name AS "Customer Name", 
    c.city AS "city", 
    s.name AS "Salesman", 
    s.city AS "city", 
    s.commission 
FROM  
    customer c 
JOIN  
    salesman s 
    ON c.salesman_id = s.salesman_id 
WHERE  
    c.city <> s.city 
    AND s.commission > 0.12; 
 
Output: 
 
![image](https://github.com/user-attachments/assets/6a7f8471-9111-4856-bf3f-93bb3112b1d6)

# Question 3: 
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" 
table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" 
table (aliased as "o"), with a left join on the "customer_id" column. 
 
Answer: 
SELECT  
    c.cust_name,  
    o.ord_no,  
    o.ord_date,  
    o.purch_amt 
FROM  
    customer c 
LEFT JOIN  
    orders o  
    ON c.customer_id = o.customer_id; 
 
Output: 
 
 ![image](https://github.com/user-attachments/assets/29bb166e-ad49-414e-8ff1-138e441a2540)

# Question 4: 
Write the SQL query that accomplishes the selection of all columns from the "patients" table and 
the first name of doctors from the "doctors" table, with an inner join on the "doctor_id" column. 
PATIENTS TABLE: 

![image](https://github.com/user-attachments/assets/e3c880bc-fe03-4eb6-8269-8dcbbd15a7c5)


DOCTORS TABLE: 

![image](https://github.com/user-attachments/assets/98aaa1e9-6594-47d0-b618-6f9385cd5548)

 
Answer: 
SELECT  
    p.patient_id,  
    p.first_name AS first_name,  
    p.last_name AS last_name,  
    p.date_of_birth,  
    p.admission_date,  
    p.discharge_date,  
    p.doctor_id,  
    d.first_name AS doctor_name 
FROM  
    patients p 
INNER JOIN  
    doctors d  
    ON p.doctor_id = d.doctor_id; 
 
Output: 

 ![image](https://github.com/user-attachments/assets/999eed75-5138-4847-87e3-9099330ff481)

# Question 5: 
From the following tables write a SQL query to display the customer name, customer city, grade, 
salesman, salesman city. The results should be sorted by ascending customer_id.   
Sample table: customer 

![image](https://github.com/user-attachments/assets/d80168d4-f019-489a-9aa1-04ce330d4c9f)

Sample table: salesman 

![image](https://github.com/user-attachments/assets/bec2dde0-aef3-47dc-b9c9-093c22aa5cc0)

 
Answer: 

SELECT  
    c.cust_name,  
    c.city AS city,  
    c.grade,  
    s.name AS Salesman,  
    s.city AS city 
FROM  
    customer c 
JOIN  
    salesman s  
    ON c.salesman_id = s.salesman_id 
ORDER BY  
    c.customer_id ASC; 
 
Output:
![image](https://github.com/user-attachments/assets/e3235d89-7e2b-4e3e-90a1-06302bf0f6c2)

 
 
# Question 6: 
Write the SQL query that achieves the selection of all columns from the "patients" table and the 
specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on 
the "doctor_id" column. 
PATIENTS TABLE: 

![image](https://github.com/user-attachments/assets/16d05b6b-3288-4319-b7e4-9461600e2b42)


DOCTORS TABLE: 

![image](https://github.com/user-attachments/assets/56a7c73f-8134-468c-b675-f6d65142f684)

 
Answer: 

SELECT  
    p.*,  
    d.specialization AS doctor_specialization 
FROM  
    patients p 
INNER JOIN  
    doctors d  
    ON p.doctor_id = d.doctor_id; 
 
Output: 

 ![image](https://github.com/user-attachments/assets/354396d1-c982-442c-9713-302e0c857ea7)

# Question 7: 
From the following tables write a SQL query to find those customers with a grade less than 300. 
Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered 
by ascending customer_id.  
Sample table: customer 

 ![image](https://github.com/user-attachments/assets/405eee2f-1502-45f1-84d9-a828286f5526)

Sample table: salesman 

![image](https://github.com/user-attachments/assets/16a804f1-aa74-408e-a651-8f35c2310674)

Answer: 

SELECT  
    c.cust_name,  
    c.city AS city,  
    c.grade,  
    s.name AS Salesman,  
    s.city AS city 
FROM  
    customer c 
INNER JOIN  
    salesman s  
    ON c.salesman_id = s.salesman_id 
WHERE  
    c.grade < 300 
ORDER BY  
    c.customer_id ASC; 
 
Output: 
 
![image](https://github.com/user-attachments/assets/8fefeed7-ebe5-4cf3-aa9c-8f42ea3aef22)

 
# Question 8: 
write a SQL query to find the salesperson and customer who reside in the same city. Return 
Salesman, cust_name and city. 
Sample table: salesman

![image](https://github.com/user-attachments/assets/1c214cf5-fc76-4516-9695-4dffd05c4387)

Sample table: customer 

![image](https://github.com/user-attachments/assets/0e742381-3b5d-4ad7-ae1a-aa8fc6b89040)

 
Answer: 

SELECT  
    s.name AS Salesman,  
    c.cust_name,  
    s.city 
FROM  
    salesman s 
INNER JOIN  
    customer c 
    ON s.city = c.city; 
 
Output: 
![image](https://github.com/user-attachments/assets/89a1bfe2-00d4-4d8d-8dbf-b527d3330f65)

 
 
# Question 9: 
Write the SQL query that accomplishes the selection of the first name from the "patients" table 
and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a 
condition filtering for patients with the first name 'Alice'. 

PATIENTS TABLE: 

![image](https://github.com/user-attachments/assets/39192e62-0e75-440b-a06f-5f7630e05d4e)

SURGERIES TABLE: 

![image](https://github.com/user-attachments/assets/27cdea84-27b9-460a-ba7f-e4d644b65945)

 
Answer: 

SELECT  
    p.first_name,  
    s.surgery_id,  
    s.patient_id,  
    s.surgeon_id,  
    s.surgery_date 
FROM  
    patients p 
INNER JOIN  
    surgeries s 
    ON p.patient_id = s.patient_id 
WHERE  
    p.first_name = 'Alice'; 
 
Output: 
 
 ![image](https://github.com/user-attachments/assets/dc330c8c-88bb-48db-ba3f-3f35c4dff6c3)

 
# Question 10: 
Write a SQL statement to join the tables salesman, customer and orders so that the same column 
of each table appears once and only the relational rows are returned.  
Sample table: orders 
![image](https://github.com/user-attachments/assets/50a362fe-8b49-40b3-858e-c9197f53e01b)

Sample table: customer 
![image](https://github.com/user-attachments/assets/1b46a5f4-b781-4cac-94c9-4ea68c2f633b)

Sample table : salesman 
![image](https://github.com/user-attachments/assets/b00db323-27ee-4460-aad6-c6590b6121da)

Answer: 

SELECT  
    o.ord_no, 
    o.purch_amt, 
    o.ord_date, 
    c.cust_name, 
    c.city AS customer_city, 
    c.grade, 
    s.name AS salesman_name, 
    s.city AS salesman_city, 
    s.commission 
FROM  
    orders o 
INNER JOIN  
    customer c ON o.customer_id = c.customer_id 
INNER JOIN  
    salesman s ON o.salesman_id = s.salesman_id; 
 
 
# Output: 

 ![image](https://github.com/user-attachments/assets/a3bb9655-b8b1-4f70-a9df-054435e474d1)

  
 
# Result: 
 
Thus , the SQL queries to implement different types of joins have been executed 
successfully.
