# Modelo Físico

**Persona**(<u>DNI</u>, nombre, apellido)

**Telefono**(<u>numero, DNI(fk)</u>)

**Paciente**(<u>DNI, matricula(fk)</u>)

**Medico**(<u>matricula, DNI(fk)</u>)

**Especializacion**(<u>nombre</u>)

**Especificaciones_medicas**(<u>matricula(fk), nombre_especializacion(fk)</u>)

**Clinica**(<u>razon_social</u>, calle, nro, piso, dpto)

**Clinicas_medico**(<u>matricula(fk), razon_social(fk)</u>, fecha_inicio, fecha_fin)