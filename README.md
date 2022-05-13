See jupyter notebook for details:
https://github.com/TonyHFu/shopify/blob/master/shopify.ipynb

## Part 1

Think about what could be going wrong with our calculation. Think about a better way to evaluate this data.

**A. The mean is distorted because of extremely large values.**

What metric would you report for this dataset?

**A. The median**

What is its value?

**A. 284**

## Part 2

How many orders were shipped by Speedy Express in total?

```SELECT Shippers.ShipperName, COUNT(*)
FROM Orders
INNER JOIN Shippers
  ON Orders.ShipperID=Shippers.ShipperID
GROUP BY Shippers.ShipperName;
```

**A. 54**

What is the last name of the employee with the most orders?

```
SELECT Employees.LastName, COUNT(*) as NumOrders
FROM Employees
INNER JOIN Orders
  ON Orders.EmployeeID=Employees.EmployeeID
GROUP BY Employees.LastName
ORDER BY NumOrders DESC;
```

**A. Peacock**

What product was ordered the most by customers in Germany?

```
SELECT ProductName, SUM(OrderDetails.Quantity) as QuantityOrdered, Customers.Country
FROM Customers
INNER JOIN Orders
  ON Customers.CustomerID=Orders.CustomerID
JOIN OrderDetails
  ON OrderDetails.OrderID=Orders.OrderID
JOIN Products
  ON Products.ProductID=OrderDetails.ProductID
WHERE Customers.Country="Germany"
GROUP BY ProductName
ORDER BY QuantityOrdered DESC;
```

**A. Boston Crab Meat**
