# Modelo Físico

**Compañia**(<u>nombre</u>, cuit, comision, dir_completa)

**Email**(<u>email, nombre(fk)</u>)

**Telefono**(<u>numero, nombre(fk)</u>)

**Cliente**(<u>id</u>, direccion, telefono)

**Persona_Fisica**(<u>id(fk)</u>, dni, apellido, nombre)

**Persona_Juridica**(<u>id(fk)</u>, cuit, razon_social)

**Tarjeta**(<u>nro</u>, cod_seg, fecha_venc, nombre_entidad(fk), nombre_banco(fk))

**Entidad**(<u>nombre</u>)

**Banco**(<u>nombre</u>)

**Siniestro**(<u>(nombre_poliza, nombre_compañia)(fk), fecha, descripcion</u>, contacto_3eros)

**Cupon_de_pago**(<u>(nombre_poliza, nombre_compañia)(fk), monto, fecha_venc</u>, fecha_pago)

**Poliza**(<u>nombre_poliza, nombre_compañia(fk)</u>, monto, franquicia, costo_mes, fecha_desde, fecha_hasta, nombre_cobertura(fk), id_cliente)

**Renovacion**(<u>nombre_pol_referencia, nombre_pol_referenciada</u>)

**Tarjeta_Poliza**(<u>(nombre_poliza, nombre_compañia)(fk), nro_tarjeta(fk)</u>)

