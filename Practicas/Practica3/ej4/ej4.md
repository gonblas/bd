# Ejercicio 4

1. 
```sql
SELECT DISTINCT p.nombre
FROM Pelicula p
JOIN Funcion f ON f.codP = p.codP
JOIN Sala s ON s.codS = f.codS
JOIN Cine c ON c.codC = s.codC
WHERE c.direccion ILIKE '%Avellaneda%'

INTERSECT

SELECT DISTINCT p.nombre
FROM Pelicula p
JOIN Funcion f ON f.codP = p.codP
JOIN Sala s ON s.codS = f.codS
JOIN Cine c ON c.codC = s.codC
WHERE c.direccion ILIKE '%La Plata%';
```


2.
```sql
SELECT DISTINCT p.nombre
FROM Pelicula p
JOIN Funcion f ON f.codP = p.codP
WHERE f.ocupacion < 30
ORDER BY p.nombre;
```


3.
```sql
SELECT c.nombre, c.direccion
FROM Cine c
JOIN Sala s ON s.codC = c.codC
JOIN Funcion f ON f.codS = s.codS
JOIN Pelicula p ON p.codP = f.codP
GROUP BY c.nombre, c.direccion
HAVING COUNT(DISTINCT p.codP) = (SELECT COUNT(*) FROM Pelicula);
```


4.
```sql
UPDATE Sala
SET nombreS = 'Sala Darin'
WHERE codS = 10;
```


5.
```sql
SELECT DISTINCT c.nombre, c.direccion
FROM Cine c
JOIN Sala s ON s.codC = c.codC
JOIN Funcion f ON f.codS = s.codS
JOIN Pelicula p ON p.codP = f.codP
WHERE p.nombre = '007 Bond: Sin tiempo para morir'

UNION 

SELECT DISTINCT c.nombre, c.direccion
FROM Cine c
JOIN Sala s ON s.codC = c.codC
JOIN Funcion f ON f.codS = s.codS
WHERE (f.fecha BETWEEN '2020-01-01' AND '2020-12-31')  AND (f.ocupacion > 0);
```


6.
```sql
SELECT DISTINCT p.nombre, p.descripcion, p.genero
FROM Pelicula p
JOIN Funcion f ON f.codP = p.codP
JOIN Sala s ON s.codS = f.codS
JOIN Cine c ON c.codC = s.codC
WHERE (c.nombre = 'Cinemark Hoyts' AND f.fecha <> CURRENT_DATE);
```


7.
```sql
SELECT c.nombre, p.nombre, SUM(f.ocupacion) AS espectadores
FROM Cine c
JOIN Sala s ON s.codC = c.codC
JOIN Funcion f ON f.codS = s.codS
JOIN Pelicula p ON p.codP = f.codP
WHERE f.fecha BETWEEN '2020-01-01' AND '2020-12-31'
GROUP BY c.nombre, p.nombre
ORDER BY c.nombre, p.nombre;
```


8.
```sql
DELETE FROM Sala s
USING Cine c
WHERE s.codC = c.codC
  AND c.codC = 5;

DELETE FROM Cine
WHERE nombre = 'Cine China Zorrilla';
```


9.
```sql
SELECT DISTINCT p.nombre, COUNT(*) AS cant_exhibiciones
FROM Pelicula p
JOIN Funcion f ON f.codP = p.codP
WHERE f.fecha BETWEEN '2020-01-01' AND '2020-12-31'
GROUP BY p.nombre;
```


10.
```sql
SELECT DISTINCT p.nombre
FROM Pelicula p
JOIN Funcion f ON f.codP = p.codP
WHERE f.fecha NOT BETWEEN '2020-01-01' AND '2020-12-31'

EXCEPT

SELECT DISTINCT p.nombre
FROM Pelicula p
JOIN Funcion f ON f.codP = p.codP
JOIN Sala s ON s.codS = f.codS
JOIN Cine c ON c.codC = s.codC
WHERE c.direccion LIKE '%La Plata%';
```