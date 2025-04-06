# Modelo Físico

**Artista**(<u>DNI</u>, nombre, apellido, fechaNac, calle, numero, piso, dpto, web)

**Telefono**(<u>telefono, DNI(fk)</u>)

**Actuacion**(<u>DNI(fk), (nombre, fecha)(fk)</u>)

**Evento**(<u>nombre, fecha, nombreTipo(fk), DNI(fk)</u>, descripcion)

**Tipo_Evento**(<u>nombre</u>)