# Ejercicio 2 - Modelo Físico

**Artista**(<u>DNI</u>, Nombre, Apellido, web?, direccion, fechaNac)

**Telefono**(<u>numero, DNI</u>)

**Evento**(<u>nombre, fecha</u>, descripcion, nombre_tipo_evento(fk), dni_director(fk))

**Tipo de evento**(<u>nombre</u>)

**Actuacion**(<u>DNI_artista(fk), (nombre, fecha)(fk)</u>)