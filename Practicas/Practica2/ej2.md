## Ejercicio 2

Cliente = (<u>codCliente</u>, nombreYAp, DNI, telefono, direccion, sexo, edad)

Esteticista = (<u>codEst</u>, nombre, apellido, DNI, fecha_nac, especialidad)

Producto = (<u>codProd</u>, nombreP, descripcion, stock, precio)

ProductoAplicado = (<u>nroAplicacion, codProd</u>, cantidad, precio) // precio del producto al momento de realizar la aplicación al cliente

Aplicacion = (<u>nroAplicacion</u>, codEst, codCliente, costoTotal, fecha)




**1. Listar datos personales de esteticistas que solo hayan atendido durante 2019.**

\[
\begin{aligned}
\text{Esteticistas2019} &\leftarrow 
\pi_{\text{codEst}}
\left(
\sigma_{(\text{fecha} \geq \text{"01/01/2019"}) \land (\text{fecha} \leq \text{"31/12/2019"})}
(\text{Aplicacion})
\right) \\[1em]
\text{EsteticistasOtrosAños} &\leftarrow 
\pi_{\text{codEst}}
\left(
\sigma_{(\text{fecha} \lt \text{"01/01/2019"}) \land (\text{fecha} \gt \text{"31/12/2019"})}
(\text{Aplicacion})
\right) \\[1em]
\pi_{nombre, apellido, DNI, fecha_nac, especialidad}(&\text{Esteticista} \bowtie 
(\text{Esteticistas2019} - \text{EsteticistasOtrosAños}))
\end{aligned}
\]


**2. Listar datos personales de esteticistas que no realizaron ninguna aplicación a clientes menores de 25 años.**

\[
\begin{aligned}
\text{ClientesMenos25} &\leftarrow 
\pi_{\text{codCliente}}
\left(
\sigma_{(edad<25)}
(\text{Cliente})
\right) \\[1em]
\text{EsteticistasAtiendenMenos25} &\leftarrow 
\pi_{\text{codEst}}
\left(
\text{Aplicacion} \bowtie \text{ClientesMenos25}
\right) \\[1em]
\text{TodasLasEsteticistas} &\leftarrow 
\pi_{\text{codEst}}
\left(
\text{Esteticista}
\right) \\[1em]
\pi_{nombre, apellido, DNI, fecha\_nac, especialidad}(\text{Esteticista} &\bowtie 
(\text{TodasLasEsteticistas} - \text{EsteticistasAtiendenMenos25}))
\end{aligned}
\]


**3. Actualizar el precio de los productos de nombre ‘tintura’ incrementando 20% su valor actual.**

\[
\begin{aligned}
\delta_{precio=precio*1.20}(\sigma_{nombreP='tintura'}(Producto))
\end{aligned}
\]


**4. Listar datos personales de clientes que se realizaron alguna aplicación durante 2018 pero no se atendieron en 2019.**

\[
\begin{aligned}
\text{Clientes2018} &\leftarrow 
\pi_{\text{codCliente}}
\left(
\sigma_{(\text{fecha} \geq \text{"01/01/2018"}) \land (\text{fecha} \leq \text{"31/12/2018"})}
(\text{Aplicacion})
\right) \\[1em]
\text{Clientes2019} &\leftarrow 
\pi_{\text{codCliente}}
\left(
\sigma_{(\text{fecha} \lt \text{"01/01/2019"}) \land (\text{fecha} \gt \text{"31/12/2019"})}
(\text{Aplicacion})
\right) \\[1em]
\pi&_{nombreYAp, DNI, telefono, direccion, sexo, edad}(\text{Cliente} \bowtie 
(\text{Clientes2018} - \text{Clientes2019}))
\end{aligned}
\]



**5. Reportar nombre, descripción, stock y precio de productos que se utilizaron en mujeres y que tengan alguna aplicación donde el precio al momento de la aplicación fue inferior a $500.**


\[
\begin{aligned}
\text{ClientesMujeres} &\leftarrow \pi_{codCliente}(\sigma_{(sexo='Femenino')}(Cliente))
\\[1em]
\text{AplicacionesAMujeres} &\leftarrow 
\pi_{\text{nroAplicacion}}
\left(
\text{Aplicacion} \bowtie \text{ClientesMujeres}
\right) \\[1em]
\pi_{\text{nombreP, descripcion, stock, precio}}
&\left(\sigma_{(precio<500)}(\text{AplicacionesAMujeres} \bowtie \text{ProductoAplicado})
\right)
\end{aligned}
\]



**6. Listar información de productos utilizados en las aplicaciones realizadas al cliente con DNI: 38329663.**

\[
\begin{aligned}
\text{ClienteParticular} &\leftarrow \pi_{codCliente}(\sigma_{(dni='38329663')}(\text{Cliente}))
\\[1em]
\text{AplicacionesAlCliente} &\leftarrow \pi_{nroAplicacion}(\text{Aplicacion} \bowtie \text{ClienteParticular})
\\[1em]
\pi_{\text{nombreP, descripcion, stock, precio}}
&\left(\text{AplicacionesAlCliente} \bowtie \text{ProductoAplicado}
\right)
\end{aligned}
\]


**7. Listar datos de productos utilizados por todos los esteticistas.**

\[
\begin{aligned}
\text{ProductoAplicadosPorEst} &\leftarrow \pi_{codEst, codProd}(\text{ProductoAplicado} \bowtie \text{Aplicacion}))
\\[1em]
\text{TodosLosEsteticistas} &\leftarrow \pi_{codEst}(\text{Esteticista})
\\[1em]
\pi_{\text{nombreP, descripcion, stock, precio}}
&\left(\text{Producto} \bowtie (\text{ProductoAplicadosPorEst}  \% \text{TodosLosEsteticistas})
\right)
\end{aligned}
\]


**8. Listar los clientes que no tienen aplicaciones en el año actual.**

\[
\begin{aligned}
\text{Aplicaciones2025} &\leftarrow \pi_{nroAplicacion, codCliente}(\sigma_{(\text{fecha} \geq \text{"01/01/2025"}) \land (\text{fecha} \leq \text{"31/12/2025"})}\text({Aplicacion})))
\\[1em]
\text{Clientes2025} &\leftarrow \pi_{codCliente}(\text{Aplicaciones2025} \bowtie \text{Cliente})
\\[1em]
\text{TodosLosClientes} &\leftarrow \pi_{codCliente}(\text{Cliente})
\\[1em]
\pi_{\text{codCliente, nombreYAp, DNI, telefono, direccion, sexo, edad}}
&\left(\text{Cliente} \bowtie (\text{TodosLosClientes} - \text{Clientes2025})
\right)
\end{aligned}
\]


**9. Listar a los esteticistas Peinadores (especialidad), que no hayan realizado aplicaciones con un costo mayor a $2000.**

\[
\begin{aligned}
\text{Peinadores} &\leftarrow \pi_{codEst}(\sigma_{especialidad='Peinador'}\text({\text{Esteticista}})))
\\[1em]
\text{EsteticistasAplicMayorA2000} &\leftarrow \pi_{codEst}(\sigma_{(costoTotal>2000)}(\text{Aplicacion}))
\\[1em]
\pi_{\text{codEst, nombre, apellido, DNI, fecha\_nac, especialidad}}
&\left(\text{Esteticista} \bowtie (\text{Peinadores} - \text{EsteticistasAplicMayorA2000})
\right)
\end{aligned}
\]
