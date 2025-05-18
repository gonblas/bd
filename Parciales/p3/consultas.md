# Consultas

1.
```sql
SELECT p.DNI, p.nombreYApellido, p.domicilio, p.telefono, t.hora_turno, o.nombre, o.descripcion
FROM Paciente
JOIN Turno t USING (DNI)
LEFT JOIN ObraSocial o USING (nombre)
WHERE t.nombre_estudio = 'Endoscopia' AND t.fecha_turno = '2022-06-30';
```


2.
```sql
SELECT o.nombre, o.descripcion
FROM ObraSocial o
JOIN Turno t USING (nombre)
GROUP BY o.nombre, o.descripcion
HAVING COUNT(DISTINCT t.nombre_estudio) = (SELECT COUNT(*) FROM Estudio);
```


3.
```sql
SELECT DISTINCT p.DNI, p.nombreYApellido, p.domicilio, p.telefono
FROM Paciente p
JOIN Turno t USING (DNI)
WHERE t.fecha_turno BETWEEN '2021-01-01' AND '2021-12-31'

EXCEPT

SELECT p.DNI, p.nombreYApellido, p.domicilio, p.telefono
FROM Paciente p
JOIN Turno t USING (DNI)
WHERE t.fecha_turno BETWEEN '2019-01-01' AND '2019-12-31';
```


4.
```sql
DELETE FROM Turno WHERE DNI = 10756963;
DELETE FROM Paciente WHERE DNI = 10756963;
```


5.
```sql
SELECT e.nombre_estudio, e.grado_complejidad, e.requiere_acompañante, COUNT(t.fecha_turno) AS cant_turnos_2022
FROM Estudio e
LEFT JOIN Turno t ON t.nombre_estudio = e.nombre_estudio AND t.fecha_turno BETWEEN '2022-01-01' AND '2022-12-31'
GROUP BY e.nombre_estudio, e.grado_complejidad, e.requiere_acompañante;
```


6.
```sql
SELECT p.DNI, p.nombreYApellido, p.domicilio, p.telefono
FROM Paciente p
JOIN Turno t USING (DNI)
WHERE t.fecha_turno BETWEEN '2020-01-01' AND '2020-12-31'
GROUP BY p.DNI, p.nombreYApellido, p.domicilio, p.telefono
HAVING COUNT(*) > 5;
```

