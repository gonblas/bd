# Tablas de salida

**Nota:** Utilizar ``load.sql`` para obtener la misma base de datos. Las salidas presentadas pueden tener errores.


1. Listar datos personales de clientes que viajaron con todas las aerolíneas.

nombre | apellido | pasaporte | nacionalidad 
--------+----------+-----------+--------------
Juan   | Pérez    | A12345    | Argentina
María  | Gómez    | B67890    | Argentina
Luis   | Martínez | C54321    | Argentina

2. Reportar para cada cliente, la cantidad de vuelos realizados con destino buenos aires. Se debe informar datos personales del cliente y cantidad de vuelos.

 codcliente | nombre |  apellido  | pasaporte | nacionalidad | cant_vuelos_bsas 
------------+--------+------------+-----------+--------------+------------------
          1 | Juan   | Pérez      | A12345    | Argentina    |                1
          2 | María  | Gómez      | B67890    | Argentina    |                1
          3 | Luis   | Martínez   | C54321    | Argentina    |                1
          4 | Olena  | Shevchenko | UA9999    | Ucrania      |                6
          5 | Carlos | Ruiz       | D88888    | Argentina    |                3
          6 | Lucía  | Fernández  | E77777    | Argentina    |                2
          7 | Pedro  | Torres     | F66666    | Argentina    |                1
          8 | Ana    | Méndez     | G55555    | Argentina    |                1

3. Listar información de vuelos sobrevendidos, vendió más pasajes que los disponibles para el vuelo. Indicar codVuelo, fecha, hora, ciudad desde donde sale el vuelo y la ciudad donde llega.

 codvuelo |   fecha    |   hora   | cod_ciudad_origen | cod_ciudad_destino 
----------+------------+----------+-------------------+--------------------
 104      | 2018-06-05 | 09:15:00 |                 6 |                  4
 102      | 2018-03-10 | 10:30:00 |                 6 |                  2
 106      | 2018-04-01 | 16:00:00 |                 4 |                  1
 101      | 2018-01-15 | 08:00:00 |                 6 |                  1
 110      | 2018-09-09 | 17:00:00 |                 5 |                  2
 105      | 2019-07-12 | 14:45:00 |                 5 |                  1
(6 rows)


4. Listar datos personales de clientes que solo hayan viajado durante 2018. Ordenar por apellido y nombre.

 nombre | apellido | pasaporte | nacionalidad 
--------+----------+-----------+--------------
 Marta  | López    | H44444    | Argentina
 Ana    | Méndez   | G55555    | Argentina
 Sofía  | Núñez    | I33333    | Argentina
 Pedro  | Torres   | F66666    | Argentina
(4 rows)


5. Listar para cada ciudad la cantidad de pasajeros que llegaron durante 2018. Indicar nombre, país y cantidad de pasajeros.

    nombre    |   pais    | cant_pasajeros 
--------------+-----------+----------------
 Cancún       | México    |              4
 Jujuy        | Argentina |              4
 Salta        | Argentina |              8
 Buenos Aires | Argentina |             16
(4 rows)

6. Borrar el vuelo con código de vuelo LOM3524.
```sql
SELECT * FROM Vuelo v WHERE v.codVUelo = 'LOM3524';
```

 codvuelo |   fecha    |   hora   | cod_ciudad_origen | cod_ciudad_destino | cantidad_pasajes | codaerolinea 
----------+------------+----------+-------------------+--------------------+------------------+--------------
 LOM3524  | 2021-01-01 | 06:30:00 |                 6 |                  1 |                1 |            3
(1 row)

```sql
DELETE FROM Vuelo v WHERE v.codVUelo = 'LOM3524';
```

DELETE 1

```sql
SELECT * FROM Vuelo v WHERE v.codVUelo = 'LOM3524';
```
 codvuelo | fecha | hora | cod_ciudad_origen | cod_ciudad_destino | cantidad_pasajes | codaerolinea 
----------+-------+------+-------------------+--------------------+------------------+--------------
(0 rows)


7. Listar datos personales de cliente que realizaron viajes con destino ‘Cancún’ durante 2018, pero no volaron durante 2019.

 nombre | apellido | pasaporte | nacionalidad 
--------+----------+-----------+--------------
 Marta  | López    | H44444    | Argentina
(1 row)


8. Reportar información de vuelos con destino ‘Buenos Aires’ o que tengan pasajeros con nacionalidad ucraniana.

 codvuelo |   fecha    |   hora   | cod_ciudad_origen | cod_ciudad_destino 
----------+------------+----------+-------------------+--------------------
 101      | 2018-01-15 | 08:00:00 |                 6 |                  1
 105      | 2019-07-12 | 14:45:00 |                 5 |                  1
 106      | 2018-04-01 | 16:00:00 |                 4 |                  1
 107      | 2018-08-08 | 11:00:00 |                 6 |                  1
 PAR2025  | 2025-06-01 | 07:45:00 |                 5 |                  8

9.  Listar datos personales de clientes que volaron con destino ‘Salta’ y también realizaron vuelos con destino ‘Jujuy’.

 nombre | apellido | pasaporte | nacionalidad 
--------+----------+-----------+--------------
 María  | Gómez    | B67890    | Argentina
 Luis   | Martínez | C54321    | Argentina
 Juan   | Pérez    | A12345    | Argentina
 Carlos | Ruiz     | D88888    | Argentina
(4 rows)


10. Listar información de aerolíneas que solo tengan vuelos con destino ‘Argentina’. Informar nombre y origen.

        nombre         |  origen   
-----------------------+-----------
 LATAM                 | Chile
 Aerolíneas Argentinas | Argentina
(2 rows)