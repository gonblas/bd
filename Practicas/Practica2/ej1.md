## Ejercicio 1

Vuelo = (<u>codVuelo</u>, fecha, hora, cod_ciudad_origen, cod_ciudad_destino, cantidad_pasajes, codAerolinea)

Pasaje = (<u>codReserva</u>, asiento, codVuelo, codCliente, precio)

Aerolinea = (<u>codAerolinea</u>, nombre, origen)

Cliente = (<u>codCliente</u>, nombre, apellido, pasaporte, nacionalidad)

Ciudad = (<u>codCiudad</u>, nombre, pais) // pais string con el nombre del país correspondiente


**1. Listar datos personales de clientes que solo hayan viajado durante 2018.**

\[
\begin{aligned}
\text{ClientesViajaron2018} &\leftarrow 
\pi_{\text{codCliente}}
\left(
\sigma_{\text{fecha} \geq \text{"01/01/2018"} \land \text{fecha} \leq \text{"31/12/2018"}}
(\text{Vuelo}) \bowtie \text{Pasaje}
\right) \\[1em]
\text{ClientesViajaronEnOtrosAños} &\leftarrow 
\pi_{\text{codCliente}}
\left(
\sigma_{\text{fecha} < \text{"2018-01-01"} \lor \text{fecha} > \text{"2018-12-31"}}
(\text{Vuelo}) \bowtie \text{Pasaje}
\right) \\[1em]
\text{Cliente} &\bowtie 
(\text{ClientesViajaron2018} - \text{ClientesViajaronEnOtrosAños})
\end{aligned}
\]



**2. Borrar el vuelo con código de vuelo LOM3524.**

\[
  \text{Vuelo} \leftarrow \text{Vuelo} - \sigma_{\text{codVuelo='LOM3524'}}(\text{Vuelo})
\]


**3. Listar datos personales de cliente que realizaron viajes con destino ‘Cancún’ durante 2018, pero no volaron durante 2019**


\[
\begin{aligned}
\text{CiudadCancun} &\leftarrow \pi_{\text{codCiudad}}(\sigma_{\text{nombre} = \text{"Cancún"}}(\text{Ciudad})) \\[1em]
Vuelos2018 &\leftarrow \pi_{codVuelo, cod\_ciudad\_destino}(\sigma_{(\text{fecha} \geq \text{"01/01/2018"}) \land (\text{fecha} \leq \text{"31/12/2018"})}(\text{Vuelo}))\\[1em]
\text{VuelosCancun2018} &\leftarrow \pi_{\text{codVuelo}}(Vuelos2018 \bowtie \text{CiudadCancun}) \\[1em]
\text{ClientesACancunEn2018} &\leftarrow \pi_{\text{codCliente}}(\text{VuelosCancun2018} \bowtie \text{Pasaje}) \\[1em]
\text{ClientesViajaronEn2019} &\leftarrow \pi_{\text{codCliente}}(\sigma_{(\text{fecha} \geq \text{"01/01/2019"}) \land (\text{fecha} \leq \text{"31/12/2019"})}(\text{Vuelo}) \bowtie \text{Pasaje}) \\[1em]
\text{Clientes} &\bowtie (\text{ClientesACancunEn2018} - \text{ClientesViajaronEn2019})
\end{aligned}
\]



**4. Reportar información de vuelos con destino ‘Buenos Aires’ o que tengan pasajeros con nacionalidad ucraniana.**


\[
\begin{aligned}
\text{CiudadBsAs} &\leftarrow \pi_{\text{codCiudad}}(\sigma_{\text{nombre} = \text{'Buenos Aires'}}(\text{Ciudad})) \\[1em]
VuelosBsAs &\leftarrow \pi_{codVuelo}(\sigma_{cod\_ciudad\_destino=codCiudad}(\text{Vuelo} \bowtie \text{CiudadBsAs}))\\[1em]
\text{ClientesUcranianos} &\leftarrow \pi_{codCliente}(\sigma_{nacionalidad='Ucraniana'}(\text{Cliente}))\\[1em]
\text{VuelosConUcranianos} &\leftarrow \pi_{codVuelo}(Pasaje \bowtie ClientesUcranianos) \\[1em]
\text{Vuelo} &\bowtie (\text{VuelosBsAs} ~\cup~  \text{VuelosConUcranianos})
\end{aligned}
\]


**5. Listar datos personales de clientes que volaron con destino ‘Salta’ y también realizaron vuelos con destino ‘Jujuy’.**


\[
\begin{aligned}
\text{CiudadSalta} &\leftarrow \pi_{\text{codCiudad}}(\sigma_{\text{nombre} = \text{'Salta'}}(\text{Ciudad})) \\[1em]
\text{CiudadJujuy} &\leftarrow \pi_{\text{codCiudad}}(\sigma_{\text{nombre} = \text{'Jujuy'}}(\text{Ciudad})) \\[1em]
ClientesASalta &\leftarrow \pi_{codCliente}(\sigma_{cod\_ciudad\_destino=codCiudad}(\text{Vuelo} \bowtie \text{CiudadSalta}) \bowtie Pasaje)\\[1em]
ClientesAJujuy &\leftarrow \pi_{codCliente}(\sigma_{cod\_ciudad\_destino=codCiudad}(\text{Vuelo} \bowtie \text{CiudadJujuy}) \bowtie Pasaje)\\[1em]
\text{Cliente} &\bowtie (\text{ClientesASalta} ~\cap~  \text{ClientesAJujuy})
\end{aligned}
\]

**6. Listar información de aerolíneas que solo tengan vuelos con destino ‘Argentina’. Informar nombre y origen.**

\[
\begin{aligned}
\text{CiudadesArg} &\leftarrow \pi_{\text{codCiudad}}(\sigma_{\text{pais} = \text{'Argentina'}}(\text{Ciudad})) \\[1em]
\text{CiudadesNoArg} &\leftarrow \pi_{codCiudad}(\text{Ciudad}) - \text{CiudadesArg}  \\[1em]
\text{AerolineasDestinoArg} &\leftarrow \pi_{codAerolinea}(\sigma_{cod\_ciudad\_destino=codCiudad}(\text{Vuelo} \bowtie \text{CiudadesArg}))\\[1em]
\text{AerolineasOtroDestino} &\leftarrow \pi_{codAerolinea}(\sigma_{cod\_ciudad\_destino=codCiudad}(\text{Vuelo} \bowtie \text{CiudadesNoArg}))\\[1em]
\pi_{nombre, origen}(\text{Aerolinea} &\bowtie (\text{AerolineaDestinoArg} - \text{AerolineasOtroDestino}))
\end{aligned}
\]

**7. Listar datos personales de clientes que viajaron con todas las aerolíneas.**

\[
\begin{aligned}
\text{ClientesAerolineas} &\leftarrow \pi_{\text{codAerolinea, codCliente}}(\text{Vuelo} \bowtie \text{Pasaje}) \\[1em]
\text{TodasLasAerolineas} &\leftarrow \pi_{\text{codAerolinea}}(\text{Aerolinea})  \\[1em]
\text{Cliente} &\bowtie (\text{ClientesAerolineas} \% \text{TodasLasAerolineas})
\end{aligned}
\]

**8. Lista la fecha, ciudad origen, ciudad destino, aerolínea y precio de los viajes del cliente con codigo 12345.**

\[
\begin{aligned}
\text{PasajesCliente} &\leftarrow 
\sigma_{\text{codCliente} = 12345}(\text{Pasaje}) \\[1em]
\text{VuelosCliente} &\leftarrow 
\text{PasajesCliente} \bowtie \text{Vuelo} \\[1em]
\text{CiudadOrigen} &\leftarrow 
\rho_{\text{codCiudad} \rightarrow \text{codCiudadOrigen}, \text{nombre} \rightarrow \text{nombreOrigen}}(\text{Ciudad}) \\[0.5em]
\text{CiudadDestino} &\leftarrow 
\rho_{\text{codCiudad} \rightarrow \text{codCiudadDestino}, \text{nombre} \rightarrow \text{nombreDestino}}(\text{Ciudad}) \\[1em]
\text{ConCiudadOrigen} &\leftarrow 
\text{VuelosCliente} \bowtie \text{CiudadOrigen} \\[1em]
\text{ConCiudadDestino} &\leftarrow 
\text{ConCiudadOrigen} \bowtie \text{CiudadDestino} \\[1em]
\text{ConAerolinea} &\leftarrow 
\text{ConCiudadDestino} \bowtie \text{Aerolinea} \\[1em]
\text{ResultadoFinal} &\leftarrow 
\pi_{\text{fecha, nombreOrigen, nombreDestino, nombre, precio}}(\text{ConAerolinea})
\end{aligned}
\]



**9. Listar las ciudades que no son destino de ningún vuelo.**


\[
\begin{aligned}
\text{CiudadesQueSonDestino} &\leftarrow \pi_{codCiudad}(\sigma_{\text{(cod\_ciudad\_destino=codCiudad)}}(\text{Ciudad} \bowtie \text{Vuelo})) \\[1em]
\text{TodasLasCiudades} &\leftarrow \pi_{codCiudad}(Ciudad) \\[1em]
\pi_{\text{codCiudad, nombre, pais}}&(Ciudad \bowtie (\text{TodasLasCiudades} - \text{CiudadesQueSonDestino}))
\end{aligned}
\]
