# Modelo Físico

**Villano**(<u>nombre</u>, maldades, f_nac, calle, nro, piso)

**Telefono**(<u>telefono, nombre(fk)</u>)

**Minion**(<u>codigo</u>, nombre)

**Actual_Minion_Villano**(<u>nombre(fk), codigo(fk)</u>, f_inicio)

**Historico_Minion_Villano**(<u>nombre(fk), codigo(fk)</u>, f_inicio, f_fin)

**Violeta**(<u>codigo(fk)</u>)

**Mutacion**(<u>codigo_minion(fk), codigo_violeta(fk)</u>, fecha, tipo)