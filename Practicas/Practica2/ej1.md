## Ejercicio 1

Vuelo = (<u>codVuelo</u>, fecha, hora, cod_ciudad_origen, cod_ciudad_destino, cantidad_pasajes, codAerolinea)

Pasaje = (<u>codReserva</u>, asiento, codVuelo, codCliente, precio)

Aerolinea = (<u>codAerolinea</u>, nombre, origen)

Cliente = (<u>codCliente</u>, nombre, apellido, pasaporte, nacionalidad)

Ciudad = (<u>codCiudad</u>, nombre, pais) // pais string con el nombre del país correspondiente


**1. Listar datos personales de clientes que solo hayan viajado durante 2018.**

$$
  \pi_{\text{nombre, apellido, pasaporte, nacionalidad}}\left(
  \sigma_{\text{(fecha >= '01/01/2018') \textasciicircum (fecha <= '31/12/2018')}}(\text{Vuelo} |x| \text{Cliente})
\right)$$



**2. Borrar el vuelo con código de vuelo LOM3524.**

$$
  \text{Vuelo} \leftarrow \text{Vuelo} - \sigma_{\text{codVuelo='LOM3524'}}(\text{Vuelo})
$$


**3. Listar datos personales de cliente que realizaron viajes con destino ‘Cancún’ durante 2018, pero no volaron durante 2019**

$$
  \pi_{\text{nombre, apellido, pasaporte, nacionalidad}}(\sigma_{\text{(cod\_ciudad\_destino='Cancún') \textasciicircum (fecha >= '01/01/2018') \textasciicircum (fecha <= '31/12/2018')}}(\text{Vuelo} |x| \text{Cliente})) - 
  \pi_{\text{nombre, apellido, pasaporte, nacionalidad}}(\sigma_{\text{(fecha >= '01/01/2019') \textasciicircum (fecha <= '31/12/2019')}}(\text{Vuelo} |x| (\text{Cliente})))
$$


**4. Reportar información de vuelos con destino ‘Buenos Aires’ o que tengan pasajeros con nacionalidad ucraniana.**


$$
  \pi_{\text{codVuelo, fecha, hora, cod\_ciudad\_origen, cod\_ciudad\_destino, cantidad\_pasajes, codAerolinea}}(\sigma_{\text{(cod\_ciudad\_destino='Buenos Aires')}}(\text{Vuelo})) ~\cup~ 
  \pi_{\text{codVuelo, fecha, hora, cod\_ciudad\_origen, cod\_ciudad\_destino, cantidad\_pasajes, codAerolinea}}(\text{Vuelo} |x| (\sigma_{(Nacionalidad='Ucrania')}(\text{Pasaje} |x| \text{Cliente})))
$$


**5. Listar datos personales de clientes que volaron con destino ‘Salta’ y también realizaron vuelos con destino ‘Jujuy’.**

$$
  \pi_{\text{nombre, apellido, pasaporte, nacionalidad}}(\text{Cliente} |x| (\sigma_{(cod\_ciudad\_destino='Salta')}(\text{Vuelo} |x| \text{Pasaje}))) ~\cap~
  \pi_{\text{nombre, apellido, pasaporte, nacionalidad}}(\text{Cliente} |x| (\sigma_{(cod\_ciudad\_destino='Jujuy')}(\text{Vuelo} |x| \text{Pasaje})))
$$

**6. Listar información de aerolíneas que solo tengan vuelos con destino ‘Argentina’. Informar nombre y origen.**

$$
  \pi_{\text{nombre, origen}}(\text{Aerolinea} |x| (\sigma_{\text{(pais='Argentina') \textasciicircum (cod\_ciudad\_destino=codCiudad)}}(\text{Vuelo} |x| \text{Ciudad})))
$$

**7. Listar datos personales de clientes que viajaron con todas las aerolíneas.**

$$
  \pi_{\text{nombre, apellido, pasaporte, nacionalidad}}(\text{Cliente} |x| (\pi_{\text{codAerolinea, codCliente}}(\text{Cliente} |x| (\text{Pasaje} |x| \sigma_{\text{codVuelo, codAerolinea}}(\text{Vuelo}))) \% (\pi_{\text{codAerolinea}}))))
$$


**8. Lista la fecha, ciudad origen, ciudad destino, aerolínea y precio de los viajes del cliente con codigo 12345.**

$$
  \pi_{\text{(fecha, cod\_ciudad\_origen, cod\_ciudad\_destino, codAerolinea, precio)}}(\text{Vuelo} |x|(\sigma_{\text{(codCliente='12345')}}(\text{Cliente}) |x| \text{Pasaje})))
$$

**9. Listar las ciudades que no son destino de ningún vuelo.**

$$
  \pi_{\text{codCiudad, nombre, pais}}(\text{Ciudad}) - 
  \pi_{\text{codCiudad, nombre, pais}}(\sigma_{\text{(cod\_ciudad\_destino=codCiudad)}}(\text{Ciudad} |x| \text{Vuelo}))
$$