# MySQL Exercises Based on the Northwind Schema

This README provides a comprehensive guide to major MySQL subjects using the Northwind schema. Each section includes a brief explanation of the concept and three exercises to help you practice.

## Prerequisites

1. [Lab-1](../1%20-%20MySQL%20on%20docker/db/readme.md)

---

## 1. SELECT

The `SELECT` statement is used to retrieve data from a database.

### Exercises:

1. Select all columns from the `Customers` table.
   ```sql
   SELECT * FROM Customers;
   ```
2. Retrieve only the `CustomerName` and `City` columns from the `Customers` table.
3. Select all products from the `Products` table with their `ProductID` and `ProductName`.

---

## 2. WHERE, AND, OR, NOT

The `WHERE` clause filters rows based on conditions. Combine conditions with `AND`, `OR`, and `NOT`.

### Exercises:

1. Select customers from `Customers` who are located in `Berlin` or `London`.
   ```sql
   SELECT * FROM Customers WHERE City = 'Berlin' OR City = 'London';
   ```
2. Find all orders from the `Orders` table where the `OrderDate` is after '2023-01-01' and the `ShippedDate` is not null.
3. Retrieve employees from the `Employees` table who are not managers (check the `Title` column).

---

## 3. ORDER BY

The `ORDER BY` clause sorts the result set by one or more columns.

### Exercises:

1. Retrieve all customers, sorted by `City` in ascending order.
   ```sql
   SELECT * FROM Customers ORDER BY City ASC;
   ```
2. Select all products from the `Products` table, sorted by `UnitPrice` in descending order.
3. Retrieve all employees, sorted first by `Country` and then by `LastName`.

---

## 4. LIMIT

The `LIMIT` clause restricts the number of rows returned.

### Exercises:

1. Retrieve the first 5 rows from the `Orders` table.
   ```sql
   SELECT * FROM Orders LIMIT 5;
   ```
2. Retrieve the top 10 products with the highest `UnitPrice`.
3. Find the first 3 customers in alphabetical order by `CustomerName`.

---

## 5. MAX and MIN

The `MAX` and `MIN` functions return the highest and lowest values in a column.

### Exercises:

1. Find the maximum `UnitPrice` from the `Products` table.
   ```sql
   SELECT MAX(UnitPrice) AS MaxPrice FROM Products;
   ```
2. Find the minimum `OrderDate` from the `Orders` table.
3. Retrieve the employee with the maximum `HireDate`.

---

## 6. SUM

The `SUM` function calculates the total value of a numeric column.

### Exercises:

1. Calculate the total `Quantity` of products sold in the `OrderDetails` table.
   ```sql
   SELECT SUM(Quantity) AS TotalQuantity FROM OrderDetails;
   ```
2. Find the total revenue (`UnitPrice * Quantity`) for all orders in the `OrderDetails` table.
3. Calculate the total freight cost from the `Orders` table.

---

## 7. LIKE

The `LIKE` operator is used for pattern matching.

### Exercises:

1. Find all customers whose names start with 'A'.
   ```sql
   SELECT * FROM Customers WHERE CustomerName LIKE 'A%';
   ```
2. Retrieve all products whose names contain 'Ch'.
3. Find all employees whose titles end with 'Manager'.

---

## 8. JOIN

The `JOIN` clause combines rows from two or more tables.

### Exercises:

1. Retrieve all orders along with the customer name.
   ```sql
   SELECT Orders.OrderID, Customers.CustomerName
   FROM Orders
   JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
   ```
2. Retrieve product names along with their supplier names.
3. Find all employees who made sales along with the order details.

---

## 9. GROUP BY

The `GROUP BY` clause groups rows sharing a property so that aggregate functions can be applied.

### Exercises:

1. Count the number of orders placed by each customer.
   ```sql
   SELECT CustomerID, COUNT(*) AS OrderCount
   FROM Orders
   GROUP BY CustomerID;
   ```
2. Find the total quantity of products sold for each product in the `OrderDetails` table.
3. Calculate the total revenue for each category in the `Products` table.

---

## 10. HAVING

The `HAVING` clause filters grouped data.

### Exercises:

1. Find customers who placed more than 5 orders.
   ```sql
   SELECT CustomerID, COUNT(*) AS OrderCount
   FROM Orders
   GROUP BY CustomerID
   HAVING COUNT(*) > 5;
   ```
2. Retrieve categories with total product prices exceeding $10,000.
3. Find employees who made sales totaling more than $50,000.

---

## 11. ALIASES

Aliases assign a temporary name to a table or column.

### Exercises:

1. Use an alias for `CustomerName` as `Name` in the `Customers` table.
   ```sql
   SELECT CustomerName AS Name FROM Customers;
   ```
2. Create an alias for the calculated revenue (`UnitPrice * Quantity`) as `Revenue` in the `OrderDetails` table.
3. Use an alias for the `Employees` table as `E` and select `E.LastName`.

---

## 12. EXISTS

The `EXISTS` operator checks for the existence of rows in a subquery.

### Exercises:

1. Find customers who placed at least one order.
   ```sql
   SELECT * FROM Customers
   WHERE EXISTS (
       SELECT 1 FROM Orders WHERE Orders.CustomerID = Customers.CustomerID
   );
   ```
2. Retrieve products that are part of any order.
3. Find employees who supervised other employees (check `ReportsTo` column).

---

## 13. UNION

The `UNION` operator combines the result sets of two or more `SELECT` statements.

### Exercises:

1. Retrieve all `CustomerName` from `Customers` and `Suppliers`.
   ```sql
   SELECT CustomerName FROM Customers
   UNION
   SELECT SupplierName FROM Suppliers;
   ```
2. Combine two queries: orders from 2022 and 2023.
3. Retrieve all cities from `Customers` and `Suppliers`, removing duplicates.

---
