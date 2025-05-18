# Ejercicio 2 - Modelo Físico


**Persona**(<u>DNI</u>, ApellidoyNombre, direccion)

**Cliente**(<u>DNI</u>)

**Empleado**(<u>DNI</u>, CUIT)

**Area**(<u>nombre, DNI_empleado(fk)</u>)

**Supervision**(<u>DNI_supervisor, DNI_supervisado</u>)

**Compra**(<u>Nro_ticket</u>, precio, DNI_cliente(fk), DNI_empleado(fk)?)

**Producto**(<u>codigo</u>, nombre, precio, stock)

**tiene**(<u>Nro_ticket(fk), codigo(fk)</u>, precio, cantidad)

