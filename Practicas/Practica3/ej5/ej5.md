# Ejercicio 4

1. 
```sql
SELECT c.nombre, c.direccion, c.telefono
FROM Clientes c
JOIN Ventas v ON v.codigoCte = c.codigoCte
JOIN Empleados e ON e.codigoEmp = v.codigoEmp AND e.direccion = c.direccion
GROUP BY c.nombre, c.direccion, c.telefono
HAVING COUNT(DISTINCT e.codigoEmp) = (
    SELECT COUNT(*)
    FROM Empleados e2
    WHERE e2.direccion = c.direccion
);
```


2.
```sql
SELECT e.DNI, e.nombre, e.fn, e.direccion, COUNT(*) AS cant_ventas
FROM Empleados e
JOIN Ventas v ON v.codigoEmp = e.codigoEmp
WHERE fecha BETWEEN '2019-01-01' AND '2019-12-31'
GROUP BY e.DNI, e.nombre, e.fn, e.direccion;
```


3.
```sql
SELECT DISTINCT e.DNI, e.nombre, e.fn, e.direccion
FROM Empleados e
JOIN Ventas v ON v.codigoEmp = e.codigoEmp
JOIN DetalleVentas dv ON dv.codVenta = v.codVenta
JOIN Productos p ON p.idProducto = dv.idProducto
GROUP BY e.DNI, e.nombre, e.fn, e.direccion
HAVING COUNT(DISTINCT p.idProducto) > 50;
```


4.
```sql
SELECT c.DNI, c.nombre, c.direccion, c.telefono, SUM(v.montoTotal)
FROM Clientes c
JOIN Ventas v ON v.codigoCte = c.codigoCte
GROUP BY c.DNI, c.nombre, c.direccion, c.telefono
ORDER BY SUM(v.montoTotal) DESC
LIMIT 1;
```


5.
```sql
INSERT INTO Ventas(codVenta, nroTicket, codigoEmp, codigoCte, fecha, montoTotal)
VALUES (
  11111,
  1000,
  (SELECT codigoEmp FROM Empleados WHERE nombre = 'Castelli Juan Manuel'),
  (SELECT codigoCte FROM Clientes WHERE DNI = '22369659'),
  '2022-12-18',
  1
);
```


6.
```sql
SELECT e.DNI, e.nombre, e.fn, e.direccion
FROM Empleados e
JOIN Ventas v ON v.codigoEmp = e.codigoEmp
JOIN Clientes c ON c.codigoCte = v.codigoCte
GROUP BY e.codigoEmp, e.DNI, e.nombre, e.fn, e.direccion
HAVING COUNT(DISTINCT c.codigoCte) = (SELECT COUNT(*) FROM Clientes);
```


7.
```sql
SELECT v.nroTicket, v.codigoEmp, v.codigoCte, v.fecha, v.montoTotal
FROM Ventas v
JOIN Clientes c ON c.codigoCte = v.codigoCte
WHERE v.montoTotal > 10000 AND c.direccion <> 'Tandil';
```


8.
```sql
SELECT c.DNI, c.nombre, c.direccion, c.telefono
FROM Clientes c
JOIN Ventas v ON v.codigoCte = c.codigoCte
WHERE v.fecha BETWEEN '2019-01-01' AND '2019-12-31'

EXCEPT

SELECT c.DNI, c.nombre, c.direccion, c.telefono
FROM Clientes c
JOIN Ventas v ON v.codigoCte = c.codigoCte
WHERE v.fecha BETWEEN '2020-01-01' AND '2020-12-31';
```


9.
```sql
SELECT DISTINCT e.DNI, e.nombre, e.fn, e.direccion
FROM Empleados e
JOIN Ventas v ON v.codigoEmp = e.codigoEmp
JOIN DetalleVentas dv ON dv.codVenta = v.codVenta
JOIN Productos p ON p.idProducto = dv.idProducto
WHERE p.precioActual > 1000;
```


10.
```sql
SELECT p.nombre, p.presentacion, p.stock, p.stock_minimo, p.precioActual
FROM Productos p

EXCEPT

SELECT p.nombre, p.presentacion, p.stock, p.stock_minimo, p.precioActual
FROM Productos p
JOIN DetalleVentas dv ON dv.idProducto = p.idProducto
JOIN Ventas v ON v.codVenta = dv.codVenta
WHERE v.fecha BETWEEN '2020-01-01' AND '2020-12-31';
```