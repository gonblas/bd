# Modelo Físico

**Persona**(<u>DNI</u>, nombre, apellido)

**Cliente**(<u>DNI(fk)</u>)

**Empleado**(<u>nroEmpleado, DNI(fk)</u>)

**Venta**(<u>nroTicket</u>, online, total, fecha)

**Empleado_Venta**(<u>nroEmpleado(fk), nroTicket(fk)</u>)

**Cliente_Venta**(<u>DNI(fk), nroTicket(fk)</u>)

**Producto**(<u>codigo</u>, nombre, descripcion, color, precio)

**Productos_vendidos**(<u>nroTicket(fk), codigo(fk)</u>, precio, cantidad)

**Sucursal**(<u>nombre</u>, calle, nro, local, piso)

**Empleado_Sucursal**(<u>nroEmpleado(fk), nombre(fk)</u>, fechaInicio, fechaFin)
