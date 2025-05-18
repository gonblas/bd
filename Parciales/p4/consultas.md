# Consultas

1.
```sql
SELECT o.nombre, t.nombre, e.fecha, e.capacidad
FROM Espectaculo e
JOIN Teatro t USING (numero)
JOIN Obra o USING (nombre)
WHERE e.fecha BETWEEN CURRENT_DATE AND '2022-12-31';
```


2.
```sql
SELECT o.nombre, o.cantidad_integrantes, o.descripcion, o.genero
FROM Obra o
JOIN Espectaculo e USING (nombre)
JOIN Teatro t USING (numero)
GROUP BY o.nombre, o.cantidad_integrantes, o.descripcion, o.genero
HAVING COUNT(DISTINCT t.numero) = (SELECT COUNT(*) FROM Teatro);
```


3.
```sql
SELECT o.nombre, o.cantidad_integrantes, o.descripcion, o.genero
FROM Obra o
JOIN Espectaculo e USING (nombre)
WHERE e.fecha BETWEEN '2021-01-01' AND '2021-12-31';

EXTRACT 

SELECT o.nombre, o.cantidad_integrantes, o.descripcion, o.genero
FROM Obra o
JOIN Espectaculo e USING (nombre)
WHERE e.fecha BETWEEN '2019-01-01' AND '2019-12-31';
```


4.
```sql
SELECT DISTINCT t.numero, t.nombre, t.domicilio
FROM Teatro t
JOIN Espectaculo e USING (numero)
WHERE e.nombre = 'La Odisea';

INTERSECT

SELECT DISTINCT t.numero, t.nombre, t.domicilio
FROM Teatro t
JOIN Espectaculo e USING (numero)
WHERE e.nombre = 'Un Balcón con Visitas';
```


5.
```sql
SELECT o.nombre, o.cantidad_integrantes, o.descripcion, o.genero, COUNT(e.fecha) AS cant_espectaculos
FROM Obra o
LEFT JOIN Espectaculo e USING (nombre)
GROUP BY o.nombre, o.cantidad_integrantes, o.descripcion, o.genero;
```


6.
```sql
SELECT e.numero, e.nombre, e.fecha, e.capacidad
FROM Espectaculo e
JOIN Entrada en ON e.numero = en.numero AND e.nombre = en.nombre AND e.fecha = en.fecha
GROUP BY e.numero, e.nombre, e.fecha, e.capacidad
HAVING COUNT(*) = e.capacidad;
```

