# HackerRank-SQL-Intermediate-Test

Product Sales Per City

SELECT ci.city_name, pr.product_name, ROUND(SUM(ii.line_total_price), 2) AS tot
FROM city ci, customer cu, invoice i, invoice_item ii, product pr 
WHERE ci.id = cu.city_id AND cu.id = i.customer_id AND i.id = ii.invoice_id AND ii.product_id = pr.id 
GROUP BY ci.city_name, pr.product_name 
ORDER BY tot DESC, ci.city_name, pr.product_name 

Customer Spending 

SELECT c.customer_name, CAST(SUM(i.total_price) AS DECIMAL(9,6)) AS total
FROM customer c
INNER JOIN invoice i ON c.id = i.customer_id
GROUP BY c.customer_name
HAVING SUM(i.total_price) < 0.25 * (SELECT AVG(total_price) FROM invoice)
ORDER BY total DESC;

Certificate Link : https://www.hackerrank.com/certificates/6032dbf025e6
