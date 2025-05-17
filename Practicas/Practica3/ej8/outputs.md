# Tablas de salida

**Nota:** Utilizar `load.sql` para obtener la misma base de datos. Las salidas presentadas pueden tener errores.

---

1. Reportar nombre y apellido, dirección y teléfono del cartero que realizó más envíos.

| nombreyape   | direccion        | telefono | count |
|:------------:|:----------------:|:--------:|:-----:|
| Mateo Romero | Calle Falsa 123  | 111-2222 |   8   |

---

2. Listar para cada sucursal, la cantidad de envíos realizados a alguna dirección de envío que contenga el string ‘Ju’. Informar nombre de sucursal y cantidad de envíos correspondiente. Ordenar por nombre sucursal.

| nombres         | count |
|:---------------:|:-----:|
| El Progreso     |   6   |
| La Amistad      |   1   |
| Santa Rosa      |   0   |
| Tucuman Central |   0   |
| Tucuman Norte   |   0   |

---

3. Listar datos personales de carteros que entregaron envíos a todas las sucursales.

| nombreyape | direccion | telefono |
|:----------:|:---------:|:--------:|
| *(0 rows)* |           |          |

Agus, mateo y manu deberían tener 4. Hay una que no tiene envíos para testear otro inciso.

---

4. Informar cantidad de envíos no entregados del mes de mayo de 2019.

| cant_envios |
|:-----------:|
|      4      |

---

5. Borrar al cliente con IDCLIENTE: 334.

`DELETE 1`

---

6. Listar datos personales de carteros que no entregaron envío a clientes (receptor) residentes en ‘La Plata’ pero sí realizaron envíos de clientes (emisor) que residen en ‘Wilde’.

| nombreyape     | direccion       | telefono |
|:--------------:|:---------------:|:--------:|
| Agustin Murray | Calle Real 50   | 333-4444 |
| Mateo Romero   | Calle Falsa 123 | 111-2222 |

---

7. Reportar información de sucursales que realizaron envíos durante 2020 o que tengan dirección en Tucuman.

| nombres         | direccions         | telefonos |
|:---------------:|:------------------:|:---------:|
| El Progreso     | Av Juana Manso 200 | 555-2222  |
| Tucuman Central | Calle Tucuman 300  | 555-3333  |
| Tucuman Norte   | Av Tucuman 400     | 555-4444  |

---

8. Listar datos personales de clientes que no realizaron envíos a la sucursal con nombre ‘La Amistad’.

| dni      | nombreyape | direccion      | telefono |
|:--------:|:-----------:|:--------------:|:--------:|
| 22222222 | Cliente E   | Otra Ciudad    | 666-1111 |
| 27329880 | Cliente C   | La Plata 456   | 666-9999 |

---

9. Listar datos personales de carteros que realizaron envíos durante 2019 a clientes con DNI inferior a 27329882.

| nombreyape     | direccion              | telefono |
|:--------------:|:----------------------:|:--------:|
| Agustin Murray | Calle Real 50          | 333-4444 |
| Lucas Fernandez| Calle 9 de Julio 123   | 444-5555 |
| Manuel Savenia | Av Siempre Viva 742    | 222-3333 |
| Mateo Romero   | Calle Falsa 123        | 111-2222 |

---

10. Listar los datos de los carteros que aún no hayan realizado ninguna entrega.

| nombreyape               | direccion      | telefono |
|:------------------------:|:--------------:|:--------:|
| Ivan Trolanis No Entrega | City Bell 342  | 221-5555 |
