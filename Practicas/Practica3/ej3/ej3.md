# Ejercicio 2

1. 
```sql
SELECT c.nombre, c.apellido, c.pasaporte, c.nacionalidad
FROM Cliente c
JOIN Pasaje p ON c.codCliente = p.codCliente
JOIN Vuelo v ON p.codVuelo = v.codVuelo
GROUP BY c.codCliente, c.nombre, c.apellido, c.pasaporte, c.nacionalidad
HAVING COUNT(DISTINCT v.codAerolinea) = (SELECT COUNT(*) FROM Aerolinea);
```


2.
```sql
SELECT c.codCliente, c.nombre, c.apellido, c.pasaporte, c.nacionalidad, COUNT(*) AS cant_vuelos_bsas
FROM Cliente c
JOIN Pasaje p ON p.codCliente = c.codCliente
JOIN Vuelo v ON v.codVuelo = p.codVuelo
JOIN Ciudad ci ON ci.codCiudad = v.cod_ciudad_destino
WHERE ci.nombre = 'Buenos Aires'
GROUP BY c.codCliente, c.nombre, c.apellido, c.pasaporte, c.nacionalidad;
```


3.
```sql
SELECT v.codVuelo, v.fecha, v.hora, v.cod_ciudad_origen, v.cod_ciudad_destino
FROM Vuelo v
JOIN Pasaje p ON p.codVuelo = v.codVuelo
GROUP BY v.codVuelo, v.fecha, v.hora, v.cod_ciudad_origen, v.cod_ciudad_destino
HAVING (COUNT(*) > v.cantidad_pasajes);
```


4.
```sql
SELECT c.nombre, c.apellido, c.pasaporte, c.nacionalidad
FROM Cliente c
JOIN Pasaje p ON p.codCliente = c.codCliente
JOIN Vuelo v ON v.codVuelo = p.codVuelo
WHERE (fecha BETWEEN '2018-01-01' AND '2018-12-31')

EXCEPT

SELECT c.nombre, c.apellido, c.pasaporte, c.nacionalidad
FROM Cliente c
JOIN Pasaje p ON p.codCliente = c.codCliente
JOIN Vuelo v ON v.codVuelo = p.codVuelo
WHERE (fecha NOT BETWEEN '2018-01-01' AND '2018-12-31')

ORDER BY apellido, nombre;
```


5.
```sql
SELECT ci.nombre, ci.pais, COUNT(*) AS cant_pasajeros
FROM Ciudad ci
JOIN Vuelo v ON v.cod_ciudad_destino = ci.codCiudad
JOIN Pasaje p ON p.codVuelo = v.codVuelo
GROUP BY ci.nombre, ci.pais;
```


6.
```sql
DELETE FROM Vuelo v WHERE v.codVUelo = 'LOM3524';
```


7.
```sql
SELECT DISTINCT c.nombre, c.apellido, c.pasaporte, c.nacionalidad
FROM Cliente c
JOIN Pasaje p ON p.codCliente = c.codCliente
JOIN Vuelo v ON v.codVuelo = p.codVuelo
JOIN Ciudad ci ON ci.codCiudad = v.cod_ciudad_destino
WHERE (ci.nombre = 'Cancún' AND fecha BETWEEN '2018-01-01' AND '2018-12-31')

EXCEPT

SELECT DISTINCT c.nombre, c.apellido, c.pasaporte, c.nacionalidad
FROM Cliente c
JOIN Pasaje p ON p.codCliente = c.codCliente
JOIN Vuelo v ON v.codVuelo = p.codVuelo
JOIN Ciudad ci ON ci.codCiudad = v.cod_ciudad_destino
WHERE (fecha BETWEEN '2019-01-01' AND '2019-12-31');
```


8.
```sql
SELECT DISTINCT v.codVuelo, v.fecha, v.hora, v.cod_ciudad_origen, v.cod_ciudad_destino
FROM Vuelo v
JOIN Ciudad ci ON ci.codCiudad = v.cod_ciudad_destino
WHERE (ci.nombre = 'Buenos Aires')

UNION

SELECT DISTINCT v.codVuelo, v.fecha, v.hora, v.cod_ciudad_origen, v.cod_ciudad_destino
FROM Vuelo v
JOIN Pasaje p ON p.codVuelo = v.codVuelo
JOIN Cliente c ON c.codCliente  = p.codCliente
WHERE (c.nacionalidad = 'Ucrania');
```


9.
```sql
SELECT DISTINCT c.nombre, c.apellido, c.pasaporte, c.nacionalidad
FROM Cliente c
JOIN Pasaje p ON p.codCliente = c.codCliente
JOIN Vuelo v ON v.codVuelo = p.codVuelo
JOIN Ciudad ci ON ci.codCiudad = v.cod_ciudad_destino
WHERE (ci.nombre = 'Jujuy')

INTERSECT

SELECT DISTINCT c.nombre, c.apellido, c.pasaporte, c.nacionalidad
FROM Cliente c
JOIN Pasaje p ON p.codCliente = c.codCliente
JOIN Vuelo v ON v.codVuelo = p.codVuelo
JOIN Ciudad ci ON ci.codCiudad = v.cod_ciudad_destino
WHERE (ci.nombre = 'Salta');
```


10.
```sql
SELECT DISTINCT a.nombre, a.origen
FROM Aerolinea a
JOIN Vuelo v ON v.codAerolinea = a.codAerolinea
JOIN Ciudad ci ON ci.codCiudad = v.cod_ciudad_destino
WHERE (ci.pais = 'Argentina')

EXCEPT

SELECT DISTINCT a.nombre, a.origen
FROM Aerolinea a
JOIN Vuelo v ON v.codAerolinea = a.codAerolinea
JOIN Ciudad ci ON ci.codCiudad = v.cod_ciudad_destino
WHERE (ci.pais <> 'Argentina');
```