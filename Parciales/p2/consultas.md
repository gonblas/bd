# Consultas

1.
```sql
SELECT pt.codP, pt.cantDias, pt.cantPersonas, pt.precio, pt.disponible, pt.destino, pt.detalles, tp.detalle, p.codPromo, p.desde, p.hasta, p.condición, p.descuento
FROM PaquetesTuristicos pt
JOIN Promocion p USING (codP)
JOIN Tipo_Promocion tp USING (codPromo)
WHERE p.descuento > 20;
```


2.
```sql
SELECT pt.codP, pt.cantDias, pt.cantPersonas, pt.precio, pt.disponible, pt.destino, pt.detalles
FROM PaquetesTuristicos pt

EXCEPT

SELECT pt.codP, pt.cantDias, pt.cantPersonas, pt.precio, pt.disponible, pt.destino, pt.detalles
FROM PaquetesTuristicos pt
JOIN Promocion p USING (codP)
GROUP BY pt.codP, pt.cantDias, pt.cantPersonas, pt.precio, pt.disponible, pt.destino, pt.detalles;
```


3.
```sql
SELECT pt.codP, pt.cantDias, pt.cantPersonas, pt.precio, pt.disponible, pt.destino, pt.detalles
FROM PaquetesTuristicos pt
JOIN Promocion p USING (codP)
JOIN Tipo_Promocion tp USING (codPromo)
GROUP BY pt.codP, pt.cantDias, pt.cantPersonas, pt.precio, pt.disponible, pt.destino, pt.detalles
HAVING COUNT(DISTINCT tp.codPromo) = (SELECT COUNT(*) FROM Tipo_Promocion);
```


4.
```sql
UPDATE PaquetesTuristicos 
SET precio=20.256, cantDias=4
WHERE codP = 12345;
```


5.
```sql
SELECT pt.codP, pt.cantDias, pt.cantPersonas, pt.precio, pt.disponible, pt.destino, pt.detalles, COUNT(*)
FROM PaquetesTuristicos pt
JOIN Detalle d USING (codP)
JOIN Compra c USING (ticket)
WHERE c.fecha BETWEEN '2022-01-01' AND '2022-12-31'
GROUP BY pt.codP, pt.cantDias, pt.cantPersonas, pt.precio, pt.disponible, pt.destino, pt.detalles
HAVING COUNT(*) > 10;
```


6.
```sql
SELECT SUM(d.cantidad * d.precio_unitario) AS importe_total, SUM(d.cantidad * d.precio_unitario - d.descuento) AS importe_a_cobrar, COUNT(d.codP)
FROM Compra c
JOIN Detalle d USING (ticket)
WHERE c.ticket = 123456789;
```

