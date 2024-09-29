# SQL_sales_query
CREATE TABLE Sales (
     SaleID INT,
     ProductID INT, 
     CustomerID INT,
     SaleDate DATE,
     Amount DECIMAL(10, 2)
);

INSERT INTO Sales (SaleID, ProductID, CustomerID, SaleDate, Amount)
VALUES
    (1, 1, 1001, '2024-09-01', 100.00),
    (2, 2, 1002, '2024-09-02', 150.00),
    (1000, 3, 1003, '2024-09-30', 200.00);

SELECT ProductID, SUM(Amount) AS TotalSales
FROM Sales
GROUP BY ProductID;

SELECT DATE_FORMAT(SaleDate, '%Y-%m') AS Month, SUM(Amount) AS TotalSales
FROM Sales
GROUP BY DATE_FORMAT(SaleDate, '%Y-%m')
ORDER BY Month;

SELECT CustomerID, COUNT(*) AS PurchaseCount
FROM Sales
GROUP BY CustomerID
HAVING COUNT(*) > 5;
