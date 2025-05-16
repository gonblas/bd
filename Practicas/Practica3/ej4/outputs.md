# Tablas de salida

**Nota:** Utilizar ``load.sql`` para obtener la misma base de datos. Las salidas presentadas pueden tener errores.


1. Reportar información de películas exhibidas en cines de ‘Avellanada’ y que posean funciones en cines de ‘La Plata’.

      nombre       
-------------------
 Avengers: Endgame
 Soul
 Tenet
 Parasite
(4 rows)

2. Reportar todas las películas que fueron exhibidas en funciones con menos de 30 espectadores. Ordenar por nombre de película.

  nombre   
-----------
 Coco
 Frozen II
(2 rows)

3. Listar nombre y dirección de los cines que exhiban todas las películas.

     nombre     |      direccion       
----------------+----------------------
 Cinemark Hoyts | Av. 51 543, La Plata
(1 row)

4. Modificar el nombre a: ‘Sala Darin’, de la sala con código 10.

```sql
SELECT * FROM SALA WHERE codS = 10;
```

 cods |   nombres   |  descripcion   | capacidad | codc 
------+-------------+----------------+-----------+------
   10 | Sala Murray | Sala histórica |        90 |    5
(1 row)

```sql
UPDATE Sala
SET nombreS = 'Sala Darin'
WHERE codS = 10;
```

UPDATE 1

```sql
SELECT * FROM SALA WHERE codS = 10;
```

SELECT * FROM SALA WHERE codS = 10;
 cods |  nombres   |  descripcion   | capacidad | codc 
------+------------+----------------+-----------+------
   10 | Sala Darin | Sala histórica |        90 |    5
(1 row)

5. Listar nombre y dirección de cines donde se exhiba la película: ‘007 Bond: Sin tiempo para morir’ o que tengan funciones con ocupación durante 2020.

        nombre        |             direccion             
----------------------+-----------------------------------
 Cine Lomas           | Calle España 123, Lomas de Zamora
 Cinemark Hoyts       | Av. 51 543, La Plata
 Multiplex Avellaneda | Calle Mitre 400, Avellaneda
 Showcase La Plata    | Calle 44 2045, La Plata
(4 rows)

6. Reportar nombre, descripción y género de películas exhibidas en el Cine: ´Cinemark Hoyts´ pero que no tengan programadas funciones en dicho cine para el dia de hoy.

      nombre       |                descripcion                |     genero      
-------------------+-------------------------------------------+-----------------
 Avengers: Endgame | Última batalla de los Vengadores          | Acción
 Coco              | Historia de un niño mexicano y su familia | Animación
 El Padrino        | Saga de crimen organizado                 | Drama
 Frozen II         | Aventura en tierras mágicas               | Animación
 Inside Out        | Las emociones de una niña                 | Animación
 Parasite          | Drama coreano sobre desigualdad           | Thriller
 Tenet             | Película de ciencia ficción y espionaje   | Ciencia Ficción
(7 rows)


7. Reportar para cada cine la cantidad de espectadores por película durante 2020. Indicar nombre del cine, nombre de la película y cantidad de espectadores. Ordenar por cine y luego por película.

        nombre        |             nombre              | espectadores 
----------------------+---------------------------------+--------------
 Cine Lomas           | 007 Bond: Sin tiempo para morir |           95
 Cinemark Hoyts       | Avengers: Endgame               |           35
 Cinemark Hoyts       | Coco                            |           25
 Cinemark Hoyts       | El Padrino                      |           50
 Cinemark Hoyts       | Frozen II                       |           60
 Cinemark Hoyts       | Parasite                        |           30
 Cinemark Hoyts       | Tenet                           |           45
 Multiplex Avellaneda | Parasite                        |           55
 Multiplex Avellaneda | Soul                            |           75
 Multiplex Avellaneda | Tenet                           |           40
 Showcase La Plata    | El Padrino                      |          100
 Showcase La Plata    | Parasite                        |           85
(12 rows)

8. Borrar el cine con nombre ‘Cine China Zorrilla’.

Se elimina el siguiente cine y sus respectivas salas, funciones asociadas:

 codc |       nombre        |           direccion           
------+---------------------+-------------------------------
    5 | Cine China Zorrilla | Calle Uruguay 123, Montevideo
(1 row)



9. Reportar para cada película, nombre y la cantidad de veces que fue exhibida durante 2020.

             nombre              | cant_exhibiciones 
---------------------------------+-------------------
 007 Bond: Sin tiempo para morir |                 1
 Frozen II                       |                 1
 Tenet                           |                 2
 El Padrino                      |                 2
 Soul                            |                 1
 Parasite                        |                 3
 Avengers: Endgame               |                 1
 Coco                            |                 1
(8 rows)

10. Listar las películas que no se hayan exhibido en 2020 en ningún cine de La Plata.

 nombre 
--------
 Minari
(1 row)