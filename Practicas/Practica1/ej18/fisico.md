# Modelo Físico

**Persona**(<u>dni</u>, apellidoYNombre, nro, calle, dpto, piso)

**Cliente**(<u>dni(fk)</u>)

**Empleado**(<u>cuit, dni(fk)</u>)

**Area**(<u>area, cuit(fk)</u>)

**Supervision**(<u>dni_supervisado(fk), dni_supervisor(fk)</u>)

**Compra**(<u>nroTicket</u>, cuit(fk), precio)

**Producto**(<u>codigo</u>, nombre, precio, stock)

**Compra_Precio**(<u>nroTicket(fk), codigo(fk)</u>, precio, cantidad)

