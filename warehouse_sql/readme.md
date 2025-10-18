Countries With Sales

SELECT DISTINCT co.CountryName
FROM Sales s
JOIN Customers cu ON s.CustomerID = cu.CustomerID
JOIN Cities ci ON cu.CityID = ci.CityID
JOIN Countries co ON ci.CountryID = co.CountryID;


Employees Transaction Count

SELECT SalesPersonID, FirstName,  COUNT(TransactionNumber) AS transactions
FROM Sales JOIN Employees
ON Sales.SalesPersonID = Employees.EmployeeID
GROUP BY SalesPersonID, FirstName
ORDER BY COUNT(TransactionNumber) DESC

High Revenue Products

SELECT TOP 5 ProductName, Revenue, CategoryName
FROM Sales JOIN Products
ON Sales.ProductID = Products.ProductID
JOIN Category ON Category.CategoryID = Products.ProductID
GROUP BY ProductName, Revenue, CategoryName
ORDER BY Revenue DESC


Products Demographic Distribution

SELECT 
    co.CountryName,
    ca.CategoryName,
    COUNT(*) AS Purchases
FROM Sales s
JOIN Customers cu ON s.CustomerID = cu.CustomerID
JOIN Cities ci ON cu.CityID = ci.CityID
JOIN Countries co ON ci.CountryID = co.CountryID
JOIN Products p ON s.ProductID = p.ProductID
JOIN Category ca ON ca.CategoryID = p.CategoryID
GROUP BY co.CountryName, ca.CategoryName;

Revenue Per Country 

WITH cte_x AS (
    SELECT 
        c.CityID, 
        SUM(s.Revenue) AS Revenue
    FROM Sales s
    JOIN Customers cu
        ON s.CustomerID = cu.CustomerID
    JOIN Cities c
        ON c.CityID = cu.CityID
    GROUP BY c.CityID
)
SELECT 
    c.CityName,
    co.CountryName, 
    cte_x.Revenue
FROM cte_x
JOIN Cities c 
    ON c.CityID = cte_x.CityID
JOIN Countries co 
    ON co.CountryID = c.CountryID
GROUP BY c.CityName, co.CountryName, cte_x.Revenue


Top Categories

SELECT TOP 3 ca.CategoryName, 
ROUND(SUM(s.Revenue),0) AS Rev
FROM Sales s
JOIN Products p ON s.ProductID = p.ProductID
JOIN Category ca ON ca.CategoryID = p.CategoryID
GROUP BY ca.CategoryName
ORDER BY Rev
