# Modelo Físico

**Disfraz**(<u>nombre</u>, descripcion, costo, tela, color)

**Ejemplar**(<u>codigo, nombre(fk)</u>, talle, estado)

**Cliente**(<u>id_cliente</u>, telefono, calle, numero, piso, dpto)

**Alquiler**(<u>fecha_com, fecha_tent, id_cliente(fk)</u>, costo, fecha_devol)

**Relacion_ejemplar_cliente**(<u>(nombre, codigo)(fk), (fecha_com, fecha_tent, id_cliente)(fk)</u>, fecha, precio)

**Institucion**(<u>id_cliente(fk)</u>, nombre, descripcion)

**Persona**(<u>id_cliente(fk)</u>, DNI, nyap, email)