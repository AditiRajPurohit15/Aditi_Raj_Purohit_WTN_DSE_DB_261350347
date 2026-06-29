# SQL Joins Assignment

---

## Question 1

### Problem Statement
Perform a natural join between the `EMP` and `DEPT` tables to display the employee number, name, salary, department name, and location for each employee.

### SQL Query
```sql
SELECT EMPNO, ENAME, SAL, DNAME, LOC
FROM EMP NATURAL JOIN DEPT;
```

---

## Question 2

### Problem Statement
Display the job, manager, salary, commission, and department name of all salesmen using an equi join.

### SQL Query
```sql
SELECT E.JOB, E.MGR, E.SAL, E.COMM, D.DNAME
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND E.JOB = 'SALESMAN';
```

---

## Question 3

### Problem Statement
Display the name, job, department number, and department name of all employees working in DALLAS.

### SQL Query
```sql
SELECT E.ENAME, E.JOB, E.DEPTNO, D.DNAME
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND D.LOC = 'DALLAS';
```

---

## Question 4

### Problem Statement
Perform a self join to display each employee's name and number along with their manager's name and number.

### SQL Query
```sql
SELECT E.ENAME AS "Employee",
       E.EMPNO AS "Emp#",
       M.ENAME AS "Manager",
       M.EMPNO AS "Mgr#"
FROM EMP E, EMP M
WHERE E.MGR = M.EMPNO;
```

---

## Question 5

### Problem Statement
Use an outer join to display all employees and their managers, including employees (like KING) with no manager.

### SQL Query
```sql
SELECT E.ENAME AS "Employee",
       E.EMPNO AS "Emp#",
       M.ENAME AS "Manager",
       M.EMPNO AS "Mgr#"
FROM EMP E
LEFT OUTER JOIN EMP M
ON E.MGR = M.EMPNO
ORDER BY E.EMPNO;
```

---

## Question 6

### Problem Statement
Display the structure of the `SALGRADE` table and fetch each employee's name, job, department name, salary, and their salary grade.

### SQL Query

**To display the structure:**

```sql
DESC SALGRADE;
```

**To fetch employee salary grades:**

```sql
SELECT E.ENAME,
       E.JOB,
       D.DNAME,
       E.SAL,
       S.GRADE
FROM EMP E, DEPT D, SALGRADE S
WHERE E.DEPTNO = D.DEPTNO
AND E.SAL BETWEEN S.LOSAL AND S.HISAL;
```

---

## Question 7

### Problem Statement
Display all departments and their employees, including departments without any employees.

### SQL Query
```sql
SELECT E.ENAME, D.DNAME
FROM EMP E
RIGHT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

---

## Question 8

### Problem Statement
Display employees who were hired before their managers, showing employees' and managers' names and hire dates.

### SQL Query
```sql
SELECT E.ENAME AS "Emp Name",
       E.HIREDATE AS "Emp Hiredate",
       M.ENAME AS "Mgr Name",
       M.HIREDATE AS "Mgr Hiredate"
FROM EMP E
JOIN EMP M
ON E.MGR = M.EMPNO
WHERE E.HIREDATE < M.HIREDATE;
```

---

## Question 9

### Problem Statement
Perform a join using the `USING` clause to display the employee number, name, department name, and location for all clerks.

### SQL Query
```sql
SELECT EMPNO, ENAME, DNAME, LOC
FROM EMP
JOIN DEPT USING (DEPTNO)
WHERE JOB = 'CLERK';
```

---

## Question 10

### Problem Statement
Display the name, salary, manager, and department name for employees with a salary greater than 2000 using the `ON` clause.

### SQL Query
```sql
SELECT E.ENAME,
       E.SAL,
       E.MGR,
       D.DNAME
FROM EMP E
JOIN DEPT D
ON E.DEPTNO = D.DEPTNO
WHERE E.SAL > 2000;
```

---

## Question 11

### Problem Statement
Perform a left outer join to display all employees and their department details.

### SQL Query
```sql
SELECT E.EMPNO,
       E.ENAME,
       E.JOB,
       E.DEPTNO,
       D.DNAME,
       D.LOC
FROM EMP E
LEFT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

---

## Question 12

### Problem Statement
Perform a right outer join to display each department and its employees, including departments with no employees.

### SQL Query
```sql
SELECT E.ENAME,
       D.DNAME
FROM EMP E
RIGHT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

---

## Question 13

### Problem Statement
Perform a full outer join to display employee numbers along with department names and locations.

### SQL Query
```sql
SELECT E.EMPNO,
       D.DNAME,
       D.LOC
FROM EMP E
FULL OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```