# Ejercicio 2

1. 
```sql
SELECT DISTINCT e.nombre, e.apellido, e.DNI, e.fecha_nac, e.especialidad
FROM Esteticista e
JOIN Aplicacion a ON e.codEst = a.codEst
WHERE EXTRACT(YEAR FROM a.fecha) = 2019

EXCEPT

SELECT DISTINCT e.nombre, e.apellido, e.DNI, e.fecha_nac, e.especialidad
FROM Esteticista e
JOIN Aplicacion a ON e.codEst = a.codEst
WHERE EXTRACT(YEAR FROM a.fecha) <> 2019
ORDER BY nombre, apellido, DNI;
```


2.
```sql
SELECT AVG(c.edad) AS promedio_edad
FROM Cliente c
JOIN Aplicacion a ON a.codCliente = c.codCliente
JOIN ProductoAplicado pa ON pa.nroAplicacion = a.nroAplicacion
JOIN Producto p ON p.codProd = pa.codProd
WHERE p.nombreP LIKE '%ura'
GROUP BY p.nombreP;
```


3.
```sql
SELECT p.nombreP, p.descripcion, p.stock, p.precio, COUNT(*) AS cantAplicaciones
FROM Producto p
JOIN ProductoAplicado pa ON pa.codProd = p.codProd
GROUP BY p.codProd
ORDER BY cantAplicaciones DESC;
```



4.
```sql
SELECT DISTINCT e.nombre, e.apellido, e.DNI, e.fecha_nac, e.especialidad
FROM Esteticista e

EXCEPT

SELECT DISTINCT e.nombre, e.apellido, e.DNI, e.fecha_nac, e.especialidad
FROM Esteticista e
JOIN Aplicacion a ON a.codEst = e.codEst
JOIN Cliente c ON c.codCliente = a.codCliente
WHERE c.edad < 25;
```


5.
```sql
UPDATE Producto
SET precio = precio*1.2
WHERE nombreP = 'tintura';
```


6.
```sql
SELECT c.nombreYAp, c.DNI, c.telefono, c.direccion, c.sexo, c.edad
FROM Cliente c
JOIN Aplicacion a ON a.codCliente = c.codCliente
WHERE EXTRACT(YEAR FROM a.fecha) = 2018

EXCEPT

SELECT c.nombreYAp, c.DNI, c.telefono, c.direccion, c.sexo, c.edad
FROM Cliente c
JOIN Aplicacion a ON a.codCliente = c.codCliente
WHERE EXTRACT(YEAR FROM a.fecha) = 2019;
```


7.
```sql
SELECT p.nombreP, p.descripcion, p.stock, p.precio
FROM Producto p
JOIN ProductoAplicado pa ON pa.codProd = p.codProd
JOIN Aplicacion a ON a.nroAplicacion = pa.nroAplicacion
JOIN Cliente c ON c.codCliente = a.codCliente
WHERE (c.sexo = 'F' AND pa.precio < 500); 
```


8.
```sql
SELECT p.nombreP, p.descripcion, p.stock, p.precio, c.DNI
FROM Producto p
JOIN ProductoAplicado pa ON pa.codProd = p.codProd
JOIN Aplicacion a ON a.nroAplicacion = pa.nroAplicacion
JOIN Cliente c ON c.codCliente = a.codCliente
WHERE (c.DNI = '38329663');
```


9.
```sql
SELECT p.codProd, p.nombreP, p.descripcion, p.stock, p.precio
FROM Producto p
JOIN ProductoAplicado pa ON pa.codProd = p.codProd
JOIN Aplicacion a ON a.nroAplicacion = pa.nroAplicacion
JOIN Esteticista e ON e.codEst = a.codEst
GROUP BY p.codProd, p.nombreP, p.descripcion, p.stock, p.precio
HAVING (COUNT(DISTINCT e.codEst) = (SELECT COUNT(*) FROM Esteticista));
```


10.
```sql
WITH ClienteGasto AS (
  SELECT c.codCliente, c.nombreYAp, SUM(a.costoTotal) AS totalGastado
  FROM Cliente c
  JOIN Aplicacion a ON c.codCliente = a.codCliente
  GROUP BY c.codCliente, c.nombreYAp
),
MaxGasto AS (
  SELECT MAX(totalGastado) AS maximoGasto
  FROM ClienteGasto
)
SELECT cg.nombreYAp, cg.totalGastado
FROM ClienteGasto cg
JOIN MaxGasto mg ON cg.totalGastado = mg.maximoGasto;
```