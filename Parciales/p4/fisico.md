# Ejercicio 2 - Modelo Físico

**Cliente**(<u>dni</u>, cuil, telefono?, nroTarjeta, fechaVtoTarjeta)

**Cliente VIP**(<u>dni</u>)

**Beneficio**(<u>nombre</u>)

**ben_vip**(<u>dni(fk), nombre(fk)</u>)

**Cuenta**(<u>nroCuenta</u>, fechaApertura)

**CC**(<u>dni(fk), nroCuenta(fk)</u>, esTitular)

**Movimiento**(<u>nro, nroCuenta(fk)</u>, desc, fecha)
