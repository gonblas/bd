# Tablas de salida

**Nota:** Utilizar ``load.sql`` para obtener la misma base de datos. Las salidas presentadas pueden tener errores.



1. Reportar nombre, dirección y teléfono de clientes que compraron a todos los empleados que viven en su localidad. (Asumir dirección=localidad).

| nombre          | direccion | telefono  |
|-----------------|-----------|-----------|
| Agustin Murray  | Tandil    | 987654321 |

---

2. Listar para cada empleado, la cantidad de ventas realizadas durante 2019. Reportar DNI, nombre, fn, dirección y cantidad de ventas. El listado debe estar ordenado por nombre y fn.

| dni      | nombre               | fn         | direccion | cant_ventas |
|----------|----------------------|------------|-----------|-------------|
| 11111111 | Castelli Juan Manuel  | 1980-05-15 | La Plata  | 1           |
| 22222222 | Ramiro Cabral        | 1975-10-10 | Tandil    | 1           |
| 33333333 | Ivan Polanis         | 1982-03-22 | La Plata  | 1           |
| 44444444 | Empleado4            | 1990-07-30 | Tandil    | 1           |
| 55555555 | Empleado5            | 1985-12-12 | La Plata  | 1           |

---

3. Listar datos personales de los empleados que tengan ventas con más de 50 artículos diferentes.

| dni      | nombre         | fn         | direccion |
|----------|----------------|------------|-----------|
| 22222222 | Ramiro Cabral  | 1975-10-10 | Tandil    |

---

4. Informar datos personales del mejor cliente. Aquel cuyo monto de ventas realizadas supera al resto de los clientes.

| dni      | nombre         | direccion | telefono  | sum      |
|----------|----------------|-----------|-----------|----------|
| 33445566 | Agustin Murray | Tandil    | 987654321 | 49000.00 |

---

5. Agregar una venta para el empleado Castelli Juan Manuel con nroTicket 1000 con la fecha y monto que desee para el cliente DNI 22369659.

| codventa | nroticket | codigoemp | codigocte | fecha      | montototal |
|----------|-----------|-----------|-----------|------------|------------|
| 11111    | 1000      | 10        | 100       | 2022-12-18 | 1.00       |

---

6. Listar DNI, nombre, fn y dirección de empleados que realizaron ventas a todos los clientes.

| dni      | nombre         | fn         | direccion |
|----------|----------------|------------|-----------|
| 33333333 | Ivan Polanis   | 1982-03-22 | La Plata  |

---

7. Reportar información de ventas (nroTicket, empleado, cliente, fecha, montoTotal) que tengan monto total superior a 10000 y el cliente no sea de ´Tandil´.

| nroticket | codigoemp | codigocte | fecha      | montototal |
|-----------|-----------|-----------|------------|------------|
| 1002      | 12        | 102       | 2019-07-20 | 11000.00   |

---

8. Listar datos personales de clientes que realizaron compras en 2019 pero no realizaron compras durante 2020.

| dni      | nombre   | direccion | telefono  |
|----------|----------|-----------|-----------|
| 44556677 | Cliente3 | La Plata  | 555555555 |
| 55667788 | Cliente4 | Tandil    | 666666666 |

---

9. Listar datos personales de empleados que participaron de ventas con algún producto con precioActual superior a 1000.

| dni      | nombre               | fn         | direccion |
|----------|----------------------|------------|-----------|
| 11111111 | Castelli Juan Manuel  | 1980-05-15 | La Plata  |
| 44444444 | Empleado4            | 1990-07-30 | Tandil    |
| 55555555 | Empleado5            | 1985-12-12 | La Plata  |
| 33333333 | Ivan Polanis         | 1982-03-22 | La Plata  |
| 22222222 | Ramiro Cabral        | 1975-10-10 | Tandil    |

---

10. Listar los datos de los productos que no fueron vendidos durante 2020.

| nombre      | presentacion | stock | stock_minimo | precioactual |
|-------------|--------------|-------|--------------|--------------|
| Producto D  | 1L           | 40    | 10           | 950.00       |
| Producto A  | 1kg          | 100   | 10           | 1200.00      |
| Producto B  | 500g         | 50    | 5            | 800.00       |
