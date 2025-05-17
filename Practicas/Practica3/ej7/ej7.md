# Ejercicio 4

1. 
```sql
SELECT p.nombreProyecto, ar.nombreA, d.nombreD, ap.fechaIni, ap.fechaFin, ap.fechaPrevistaFin
FROM Aplicacion ap
JOIN Proyecto p USING (codProyecto)
JOIN Area ar USING (codArea)
JOIN Departamento d USING (codDepto)
WHERE ap.fechaFin > ap.fechaPrevistaFin
ORDER BY p.nombreProyecto, ar.nombreA;
```


2.
```sql
SELECT ar.nombreA, 
       COUNT(CASE 
                WHEN ap.fechaFin BETWEEN '2020-01-01' AND '2020-12-31' 
                THEN 1 
            END) AS cant_proyectos
FROM Area ar
LEFT JOIN Aplicacion ap USING (codArea)
LEFT JOIN Proyecto p USING (codProyecto)
GROUP BY ar.nombreA;
```

3. Si avance es un porcentaje se debe preguntar por si el avance es el 100%.
```sql
SELECT d.nombreD
FROM Departamento d

EXCEPT 

SELECT d.nombreD
FROM Departamento d
LEFT JOIN Area ar USING (codDepto)
LEFT JOIN Aplicacion ap USING (codArea) 
LEFT JOIN Proyecto p USING (codProyecto)
WHERE (p.avance = 'Finalizado');
```


4.
```sql
SELECT p.nombreProyecto, COUNT(*) AS cant_aplicaciones
FROM Proyecto p
JOIN Aplicacion ap USING (codProyecto)
GROUP BY p.nombreProyecto
HAVING (COUNT(*) > 50);
```


5.
```sql
SELECT INTO Proyecto (codProyecto, nombreProyecto, avance, descProyecto, objetivos)
VALUES (1111, 'Proyecto Murray', 'Finalizado', 'Un proyecto muy bueno', 'Bla Bla Bla');
```


6.
```sql
SELECT p.nombreProyecto
FROM Proyecto p
JOIN Aplicacion ap USING (codProyecto)
JOIN Area ar USING (codArea)
GROUP BY p.nombreProyecto
HAVING COUNT(DISTINCT ar.codArea) = (SELECT COUNT(*) FROM Area);
```


7.
```sql
SELECT d.nombreD
FROM Departamento d

EXCEPT

SELECT d.nombreD
FROM Departamento d
JOIN Area ar USING (codDepto)
JOIN Aplicacion ap USING (codArea);
```


8.
```sql
SELECT DISTINCT p.nombreProyecto, ar.nombreA, ap.fechaIni, ap.fechaPrevistaFin
FROM Proyecto p
JOIN Aplicacion ap USING (codProyecto)
JOIN Area ar USING (codArea)
WHERE ap.fechaIni < '2010-01-01' AND ap.fechaFin IS NULL;
```


9.
```sql
SELECT DISTINCT ar.codDepto, ar.nombreA, ar.descripcion
FROM Area ar
JOIN Departamento d USING (codDepto)
WHERE d.nombreD = 'Redes';
```


10.
```sql
SELECT DISTINCT p.nombreProyecto, p.avance, p.descProyecto, p.objetivos
FROM Proyecto p
JOIN Aplicacion ap USING (codProyecto)
WHERE ap.fechaFin BETWEEN '2019-01-01' AND '2019-12-31'

EXCEPT

SELECT DISTINCT p.nombreProyecto, p.avance, p.descProyecto, p.objetivos
FROM Proyecto p
JOIN Aplicacion ap USING (codProyecto)
WHERE ap.fechaFin NOT BETWEEN '2019-01-01' AND '2019-12-31';
```