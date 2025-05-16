### 1. Clientes que viajaron con todas las aerolíneas

| nombre | apellido | pasaporte | nacionalidad |
| :----: | :------: | :-------: | :----------: |
|  Juan  |  Pérez   |  A12345   |  Argentina   |
| María  |  Gómez   |  B67890   |  Argentina   |
|  Luis  | Martínez |  C54321   |  Argentina   |

---

### 2. Cantidad de vuelos a Buenos Aires por cliente

| codcliente | nombre |  apellido  | pasaporte | nacionalidad | cant_vuelos_bsas |
| :--------: | :----: | :--------: | :-------: | :----------: | :---------------: |
|     1      |  Juan  |   Pérez    |  A12345   |  Argentina   |         1         |
|     2      | María  |   Gómez    |  B67890   |  Argentina   |         1         |
|     3      |  Luis  | Martínez   |  C54321   |  Argentina   |         1         |
|     4      | Olena  | Shevchenko |  UA9999   |   Ucrania    |         6         |
|     5      | Carlos |   Ruiz     |  D88888   |  Argentina   |         3         |
|     6      | Lucía  | Fernández  |  E77777   |  Argentina   |         2         |
|     7      | Pedro  |  Torres    |  F66666   |  Argentina   |         1         |
|     8      |  Ana   |  Méndez    |  G55555   |  Argentina   |         1         |

---

### 3. Vuelos sobrevendidos

| codvuelo |   fecha    |   hora   | cod_ciudad_origen | cod_ciudad_destino |
| :------: | :--------: | :------: | :----------------: | :-----------------: |
|   104    | 2018-06-05 | 09:15:00 |         6          |          4          |
|   102    | 2018-03-10 | 10:30:00 |         6          |          2          |
|   106    | 2018-04-01 | 16:00:00 |         4          |          1          |
|   101    | 2018-01-15 | 08:00:00 |         6          |          1          |
|   110    | 2018-09-09 | 17:00:00 |         5          |          2          |
|   105    | 2019-07-12 | 14:45:00 |         5          |          1          |

---

### 4. Clientes que viajaron solo en 2018

| nombre | apellido | pasaporte | nacionalidad |
| :----: | :------: | :-------: | :----------: |
| Marta  |  López   |  H44444   |  Argentina   |
|  Ana   |  Méndez  |  G55555   |  Argentina   |
| Sofía  |  Núñez   |  I33333   |  Argentina   |
| Pedro  |  Torres  |  F66666   |  Argentina   |

---

### 5. Pasajeros que llegaron por ciudad en 2018

|   nombre    |   pais    | cant_pasajeros |
| :---------: | :-------: | :------------: |
|  Cancún     |  México   |       4        |
|  Jujuy      | Argentina |       4        |
|  Salta      | Argentina |       8        |
| Buenos Aires| Argentina |      16        |

---

### 6. Vuelo eliminado LOM3524 (confirmación)

Antes del borrado:

| codvuelo |   fecha    |   hora   | cod_ciudad_origen | cod_ciudad_destino | cantidad_pasajes | codaerolinea |
| :------: | :--------: | :------: | :----------------: | :-----------------: | :--------------: | :----------: |
| LOM3524  | 2021-01-01 | 06:30:00 |         6          |          1          |        1         |      3       |

Después del borrado:

_(0 rows)_

---

### 7. Clientes que viajaron a Cancún en 2018 pero no en 2019

| nombre | apellido | pasaporte | nacionalidad |
| :----: | :------: | :-------: | :----------: |
| Marta  |  López   |  H44444   |  Argentina   |

---

### 8. Vuelos a Buenos Aires o con pasajeros ucranianos

| codvuelo |   fecha    |   hora   | cod_ciudad_origen | cod_ciudad_destino |
| :------: | :--------: | :------: | :----------------: | :-----------------: |
|   101    | 2018-01-15 | 08:00:00 |         6          |          1          |
|   105    | 2019-07-12 | 14:45:00 |         5          |          1          |
|   106    | 2018-04-01 | 16:00:00 |         4          |          1          |
|   107    | 2018-08-08 | 11:00:00 |         6          |          1          |
| PAR2025  | 2025-06-01 | 07:45:00 |         5          |          8          |

---

### 9. Clientes que volaron a Salta y Jujuy

| nombre | apellido | pasaporte | nacionalidad |
| :----: | :------: | :-------: | :----------: |
| María  |  Gómez   |  B67890   |  Argentina   |
|  Luis  | Martínez |  C54321   |  Argentina   |
|  Juan  |  Pérez   |  A12345   |  Argentina   |
| Carlos |   Ruiz   |  D88888   |  Argentina   |

---

### 10. Aerolíneas con vuelos solo a Argentina

|         nombre         |  origen   |
| :--------------------: | :-------: |
|         LATAM          |   Chile   |
| Aerolíneas Argentinas  | Argentina |
