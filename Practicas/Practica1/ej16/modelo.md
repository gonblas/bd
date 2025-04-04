# Modelo Físico

**Cliente**(<u>dni</u>, cuil, tarjetaCredito)

**ClienteVIP**(<u>dni(fk)</u>)

**Beneficio**(<u>beneficio, dni(fk)</u>)

**Telefono**(<u>telefono, dni(fk)</u>)

**Cuenta**(<u>nroCuenta</u>, fechaApertura)

**Cliente_Cuenta**(<u>dni(fk), nroCuenta(fk)</u>, esTitular)

**Movimiento**(<u>nroCuenta(fk)</u>, desc, fecha, nro)
