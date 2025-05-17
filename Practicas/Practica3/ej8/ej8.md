# Ejercicio 8

1. 
```sql
SELECT ca.nombreYApe, ca.direccion, ca.telefono, COUNT(*)
FROM Cartero ca
JOIN Envio e USING (DNI)
GROUP BY ca.nombreYApe, ca.direccion, ca.telefono
ORDER BY COUNT(*) DESC
LIMIT 1;
```

2.
```sql
SELECT s.nombreS, COUNT(e.direccionEntrega)
FROM Sucursal s
LEFT JOIN Envio e ON e.IDSUC = s.IDSUC AND e.direccionEntrega LIKE '%Ju%' 
GROUP BY s.nombreS
ORDER BY s.nombreS;
```

3. 
```sql
SELECT ca.nombreYApe, ca.direccion, ca.telefono
FROM Cartero ca
JOIN Envio e USING (DNI)
JOIN Sucursal s USING (IDSUC)
GROUP BY ca.nombreYApe, ca.direccion, ca.telefono
HAVING COUNT(DISTINCT s.IDSUC) = (SELECT COUNT(*) FROM Sucursal);
```


4.
```sql
SELECT COUNT(*) AS cant_envios
FROM Envio e
WHERE e.recibido = FALSE AND e.fecha BETWEEN '2019-05-01' AND '2019-05-31';
```


5.
```sql
DELETE FROM Cliente WHERE IDCLIENTE = 334;
```


6.
```sql
SELECT ca.nombreYApe, ca.direccion, ca.telefono
FROM Cartero ca
JOIN Envio e USING (DNI)
JOIN Cliente cl ON cl.IDCLIENTE = e.IDCLIENTEEnvia
WHERE e.recibido = TRUE AND cl.direccion LIKE '%Wilde%'

INTERSECT

SELECT ca.nombreYApe, ca.direccion, ca.telefono
FROM Cartero ca
JOIN Envio e USING (DNI)
JOIN Cliente cl ON cl.IDCLIENTE = e.IDCLIENTERecibe
WHERE e.recibido = FALSE AND cl.direccion LIKE '%La Plata%';
```


7.
```sql
SELECT s.nombreS, s.direccionS, s.telefonoS
FROM Sucursal s
JOIN Envio e USING (IDSUC)
WHERE e.fecha BETWEEN '2020-01-01' AND '2020-12-31'

UNION

SELECT s.nombreS, s.direccionS, s.telefonoS
FROM Sucursal s
WHERE s.direccionS LIKE '%Tucuman%';
```


8.
```sql
SELECT cl.DNI, cl.nombreYApe, cl.direccion, cl.telefono
FROM Cliente cl

EXCEPT

SELECT cl.DNI, cl.nombreYApe, cl.direccion, cl.telefono
FROM Cliente cl
JOIN Envio e ON e.IDCLIENTEEnvia = cl.IDCLIENTE
JOIN Sucursal s USING (IDSUC)
WHERE s.nombreS = 'La Amistad';
```


9.
```sql
SELECT DISTINCT ca.nombreYApe, ca.direccion, ca.telefono
FROM Cartero ca
JOIN Envio e USING (DNI)
JOIN Cliente cl ON cl.IDCLIENTE = e.IDCLIENTEEnvia OR cl.IDCLIENTE = e.IDCLIENTERecibe
WHERE (e.fecha BETWEEN '2019-01-01' AND '2019-12-31') AND (cl.DNI < '27329882');
```


10.
```sql
SELECT DISTINCT ca.nombreYApe, ca.direccion, ca.telefono
FROM Cartero ca

EXCEPT

SELECT DISTINCT ca.nombreYApe, ca.direccion, ca.telefono
FROM Cartero ca
JOIN Envio e USING (DNI)
WHERE e.recibido = TRUE;
```
