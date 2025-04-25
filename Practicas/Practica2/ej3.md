## Ejercicio 3

Persona= (<u>DNI</u>, Apellido, Nombre, Fecha_Nacimiento, Estado_Civil, Genero)

Alumno = (<u>DNI</u>, Legajo, Año_Ingreso)

Profesor = (<u>DNI</u>, Matricula, Nro_Expediente)

Titulo = (<u>Cod_Titulo</u>, Nombre, Descripción)

Titulo-Profesor = (<u>Cod_Titulo, DNI</u>, Fecha)

Curso = (<u>Cod_Curso, Nombre</u>, Descripción, Fecha_Creacion, Cantidad_Horas)

Alumno-Curso = (<u>DNI, Cod_Curso, Año</u>, Desempeño, Calificación)

Profesor-Curso = (<u>DNI, Cod_Curso, Fecha_Desde</u>, Fecha_Hasta)



**1. Listar nombre, descripción y fecha de creación de los cursos que se encuentra  inscripto el alumno con legajo 1089.**

\[
\begin{aligned}
\text{AlumnoParticular} &\leftarrow 
\pi_{\text{DNI}}
\left(
\sigma_{Legajo='1089'}
(\text{Alumno})
\right) \\[1em]
\text{CursosAlumnoParticular} &\leftarrow 
\pi_{\text{Cod\_Curso}}
\left(
\text{AlumnoParticular} \bowtie \text{Alumno-Curso}
\right) \\[1em]
\pi_{Nombre, Descripción, Fecha\_Creacion}(&\text{CursosAlumnoParticular} \bowtie 
\text{Curso})
\end{aligned}
\]


**2. Agregar un profesor con los datos que prefiera y con título ‘Licenciado en Sistemas’.**

\[
\begin{aligned}
\text{Persona} &\leftarrow \text{Persona} ~\cup~ \{12334789, \text{'Gimenez'}, \text{'Milton'}, \text{'12/10/1860'}, \text{'Soltero'}, \text{'Masculino'}\} \\[1em]
\text{Profesor} &\leftarrow \text{Profesor} ~\cup~ \{12334789, \text{'MKl782'}, 1290\} \\[1em]
\text{Titulo} &\leftarrow \text{Titulo-Profesor} ~\cup~ \{\text{'AHG78'}, \text{‘Licenciado en Sistemas’}, \text{'El título consiste en...'}\} \\[1em]
\text{Titulo-Profesor} &\leftarrow \text{Titulo-Profesor} ~\cup~ \{\text{'AHG78'}, 12334789, \text{'12/12/1905'}\}
\end{aligned}
\] 



**3. Listar el DNI, apellido, nombre, género y fecha de nacimiento de los alumnos inscriptos al curso con nombre “tuning de oracle” en 2019 y que no tengan calificación superior a 5 en ningún curso.**


\[
\begin{aligned}
\text{CursoOracle} &\leftarrow 
\pi_{\text{Cod\_Curso}}
\left(
\sigma_{Nombre=\text{“tuning de oracle”}}
(\text{Curso})
\right) \\[1em]
\text{Curso-Alumno2019} &\leftarrow 
\pi_{\text{DNI, Cod\_Curso}}
\left(
\sigma_{Año='2019'}
(\text{Curso-Alumno})
\right) \\[1em]
\text{AlumnosOracle2019} &\leftarrow 
\pi_{\text{DNI}}
\left(
\text{CursoOracle} \bowtie \text{Curso-Alumno2019}
\right) \\[1em]
\text{AlumnosConNotaMayorA5} &\leftarrow 
\pi_{\text{DNI}}
\left(
\sigma_{Calificacion>5}
(\text{Curso-Alumno})
\right) \\[1em]
\pi_{DNI, Apellido, Nombre, Fecha\_Nacimiento, Genero}&(Persona \bowtie (\text{AlumnosOracle2019} - 
\text{AlumnosConNotaMayorA5}))
\end{aligned}
\]


**4. Listar el DNI, apellido, nombre y legajo de alumnos que realizaron cursos durante 2018 pero no cursaron durante 2019.**


\[
\begin{aligned}
\text{AlumnosCursaronEn2018} &\leftarrow 
\pi_{\text{DNI}}
\left(
\sigma_{Año=2018}
(\text{Alumno-Curso})
\right) \\[1em]
\text{AlumnosCursaronEn2019} &\leftarrow 
\pi_{\text{DNI}}
\left(
\sigma_{Año=2019}
(\text{Alumno-Curso})
\right) \\[1em]
\pi_{DNI, Apellido, Nombre, Legajo}(\text{Persona} \bowtie& \text{Alumno} \bowtie (\text{AlumnosOracle2019} - 
\text{AlumnosConNotaMayorA5}))
\end{aligned}
\]




**5. Listar nombre, apellido, DNI, fecha de nacimiento, estado civil y género de profesores que tengan cursos activos actualmente o tengan como alumno al alumno con DNI:34567487.**

Supongo que la Fecha\_Hasta es NULL si el profesor sigue activo en un curso. También puede compararse la fecha actual con Fecha\_Hasta.

\[
\begin{aligned}
\text{ProfesoresActivos} &\leftarrow 
\pi_{\text{DNI}}
\left(
\sigma_{Fecha\_Hasta=NULL}
(\text{Profesor-Curso})
\right) \\[1em]
\text{CursosDelAlumno} &\leftarrow 
\pi_{\text{Cod\_Curso}}
\left(
\sigma_{DNI=34567487}
(\text{Alumno-Curso})
\right) \\[1em]
\text{ProfesoresDelAlumno} &\leftarrow 
\pi_{\text{DNI}}
\left(
\text{CursosDelAlumno} \bowtie \text{Profesor-Curso}
\right) \\[1em]
\pi_{DNI, Apellido, Nombre, Fecha\_Nacimiento, Estado\_Civil, Genero}(\text{Persona} \bowtie& (\text{ProfesoresActivos} ~\cup~ 
\text{ProfesoresDelAlumno}))
\end{aligned}
\]


**6. Dar de baja el alumno con DNI 38746662.**

\[
\begin{aligned}
\text{Alumno-Curso} &\leftarrow \text{Alumno-Curso} - \sigma_{DNI=38746662}(Alumno-Curso) \\[1em]
\text{Alumno} &\leftarrow \text{Alumno} - \sigma_{DNI=38746662}(Alumno) \\[1em]
\text{Persona} &\leftarrow \text{Persona} - \sigma_{DNI=38746662}(Persona) \\[1em]
\end{aligned}
\]

**7. Listar información de alumnos que realizaron todos los cursos.**


\[
\begin{aligned}
\text{TodosLosCursos} &\leftarrow 
\pi_{\text{Cod\_Curso}}
\left(
\text{Curso}
\right) \\[1em]
\text{AlumnadoCurso} &\leftarrow 
\pi_{\text{DNI, Cod\_Curso}}
\left(
\text{Alumno-Curso}
\right) \\[1em]
\pi_{DNI, Legajo, Año\_Ingreso}(\text{Alumno} \bowtie& (\text{AlumnadoCurso} ~\%~
\text{TodosLosCursos}))
\end{aligned}
\]



**8. Listar información de los alumnos que cursaron en 2018 y también cursaron en 2019.**


\[
\begin{aligned}
\text{AlumnosCursaronEn2018} &\leftarrow 
\pi_{\text{DNI}}
\left(\sigma_{Año=2018}
(\text{Alumno-Curso})
\right) \\[1em]
\text{AlumnosCursaronEn2019} &\leftarrow 
\pi_{\text{DNI}}
\left(\sigma_{Año=2019}
(\text{Alumno-Curso})
\right) \\[1em]
\pi_{DNI, Legajo, Año\_Ingreso}(\text{Alumno} \bowtie& (\text{AlumnosCursaronEn2018} ~\cap~
\text{AlumnosCursaronEn2019}))
\end{aligned}
\]