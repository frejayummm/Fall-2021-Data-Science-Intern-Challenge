# Fall-2021-Data-Science-Intern-Challenge
Fall 2021 Data Science Intern Challenge 

Please complete the following questions, and provide your thought process/work. You can attach your work in a text file, link, etc. on the application page. Please ensure answers are easily visible for reviewers!


# Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

1.Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
- 
2.What metric would you report for this dataset?
- 
3.What is its value?
- 293.715

# Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

1. How many orders were shipped by Speedy Express in total?
```
SELECT COUNT(*) 
FROM Orders 
JOIN Shippers 
ON Shippers.ShipperID = Orders.ShipperID 
WHERE Shippers.ShipperName="Speedy Express"
```
- output is 54

2. What is the last name of the employee with the most orders?
```
SELECT Employees.LastName, COUNT(*) 
FROM Orders
JOIN Employees
ON Orders.EmployeeID = [Employees].EmployeeID
GROUP BY Employees.LastName
ORDER BY COUNT(*) DESC;
```
- output is Peacock with 40 orders.

3. What product was ordered the most by customers in Germany?
```
SELECT Orders.OrderID, Customers.Country
FROM Orders
JOIN Customers
ON Orders.CustomerID = Orders.CustomerID
WHERE Customers.Country="Germany";
```
- Then we have the order id and the country.
```
ELECT Orders.OrderID, Customers.Country, OrderDetails.Quantity, Products.ProductName
FROM Orders, OrderDetails
JOIN Customers ON Orders.CustomerID=Customers.CustomerID
JOIN Products ON OrderDetails.ProductID=Products.ProductID
WHERE Country='Germany';


SELECT ProductName, Quantity, COUNT(*) as "NumOrders"
FROM Products_Ordered
GROUP BY ProductName;

SELECT ProductName, Quantity, NumOrders, (Quantity * Orders) AS TotalOrdered
FROM Product_Orders
ORDER BY TotalOrdered desc
LIMIT 1;
```
