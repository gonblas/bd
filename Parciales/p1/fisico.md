# Ejercicio 2 - Modelo Físico


**Persona**(<u>dni</u>, nombre, apellido)

**Telefono**(<u>numero, dni(fk)</u>)

**Profesional**(<u>matricula</u>, dni(fk), email)

**Paciente**(<u>dni</u>, direccion)

**Especialidad**(<u>nombre</u>)

**pro_esp**(<u>nombre(fk), matricula(fk)</u>)

**Internacion**(<u>fechaIngreso, dni_paciente(fk)</u>, causa, nro_pieza, matricula(fk))

**Medicacion**(<u>nombre</u>)

**int_IDmed**(<u>(fechaIngreso, dni_paciente)(fk), nombre_med(fk)</u>, dosis)

**Turno**(<u>fecha, hora, dni_paciente(fk)</u>, asistio)