# Modelo Físico

**Clinica**(<u>razonSocial</u>, calle, nro, depto, piso)

**Atencion**(<u>nroAtencion</u>, razonSocial(fk) , fechaHora, requiereDomicilio, notas)

**Producto**(<u>codigo</u>, nombre, presentacion, stock, precio)

**Producto_Clinica**(<u>razonSocial(fk), codigo(fk)</u>)

**Remedio**(<u>codigo(fk)</u>, accionTerapeutica)

**Animal**(<u>animal, codigo(fk)</u>)
