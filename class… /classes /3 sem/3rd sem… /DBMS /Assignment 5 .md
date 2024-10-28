# Assignment 5

**Assignment-5**

**[Based on relational operators]**

Consider Table Emp with following data and write SQL for queries given below:

("Aman", Delhi, "1234567890", 31, 65000),

("Priay", "ludhiyana", "2345678901", 42, 80000),

("Pawan", "Kanpur", "3456789012", 46, 95000),

("Rajani", "Varansi", "4567890123", 35, 61000),

("Aditya", "Prayagraj", "5678901234", 42, 75000),

("menu", "Kanpur", "6789012345", 38, 74000),

("Meeran", "Lucknow", "7890123456", 40, 60000);

1. Find the name of employees who live in Lucknow
2. Find the record of employees who live in kanpur
3. Find the name and city of employees who live in kanpur and age is greater than 40
4. Find the record of employees who live in kanpur or Varanasi
5. Find the record off employees who live in kanpur and Varanasi and their age is less than 40
6. Find the name and mobile number of employees who don't belong to Lucknow and their age is more than 40
7. Find the name and city of employees who nither belong to kanpur nor prayagraj

Here are the SQL queries for each of your questions:

### 1. Find the name of employees who live in Lucknow.

```sql
SELECT name
FROM Emp
WHERE city = 'Lucknow';

```

### 2. Find the record of employees who live in Kanpur.

```sql
SELECT *
FROM Emp
WHERE city = 'Kanpur';

```

### 3. Find the name and city of employees who live in Kanpur and age is greater than 40.

```sql
SELECT name, city
FROM Emp
WHERE city = 'Kanpur'
AND age > 40;

```

### 4. Find the record of employees who live in Kanpur or Varanasi.

```sql
SELECT *
FROM Emp
WHERE city = 'Kanpur'
OR city = 'Varanasi';

```

### 5. Find the record of employees who live in Kanpur and Varanasi and their age is less than 40.

```sql
SELECT *
FROM Emp
WHERE (city = 'Kanpur' OR city = 'Varanasi')
AND age < 40;

```

### 6. Find the name and mobile number of employees who don't belong to Lucknow and their age is more than 40.

```sql
SELECT name, mobile
FROM Emp
WHERE city <> 'Lucknow'
AND age > 40;

```

### 7. Find the name and city of employees who neither belong to Kanpur nor Prayagraj.

```sql
SELECT name, city
FROM Emp
WHERE city <> 'Kanpur'
AND city <> 'Prayagraj';

```

These queries should work based on the structure of the given `Emp` table and your requested conditions.