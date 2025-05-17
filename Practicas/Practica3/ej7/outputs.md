# Tablas de salida

**Nota:** Utilizar ``load.sql`` para obtener la misma base de datos. Las salidas presentadas pueden tener errores.

1. Listar aplicaciones de proyectos que se terminaron luego de la fecha prevista de fin. Indicar nombre del proyecto, área de aplicación, departamento correspondiente, fecha de inicio y fin, y fecha prevista de fin. Ordenar por nombre de proyecto y área.

|    nombreproyecto     |         nombrea         |  nombred  |  fechaini  |  fechafin  | fechaprevistafin |
| :-------------------: | :---------------------: | :-------: | :--------: | :--------: | :--------------: |
| Proyecto RedAvanzada   | Infraestructura Patrick |   Redes   | 2021-01-01 | 2021-12-31 |    2021-10-31    |

2. Reportar para cada área la cantidad de proyectos finalizados durante 2020. Informar nombre de área y cantidad de proyectos finalizados.

|         nombrea          | cant_proyectos |
| :---------------------: | :------------: |
|   Automatización Bob    |       1        |
|       IA Plankton       |       1        |
| Infraestructura Patrick |       1        |
|   Monitoreo Calamardo   |       1        |
|      Soporte Gary       |       0        |
|   Desarrollo Arenita    |       1        |
| Ciberseguridad Don Cangrejo |    0      |

3. Listar información de departamentos que no tengan proyectos terminados.

|    nombred     |
| :------------: |
| Departamento X |

4. Listar información de proyectos que tengan no menos 50 aplicaciones finalizadas. Ordenar por cantidad de aplicaciones.

|  nombreproyecto  | cant_aplicaciones |
| :--------------: | :---------------: |
| Proyecto Masivo  |        51         |

5. Agregar un nuevo proyecto con la información que desee.

INSERT 0 1

6. Listar información de proyectos que tengan aplicación en todas las áreas.

|  nombreproyecto  |
| :--------------: |
| Proyecto Masivo  |
| Proyecto Multizona |

7. Listar información de departamentos que no tengan aplicaciones registradas.

|    nombred     |
| :------------: |
| Departamento X |

8. Listar información de proyectos que tenga alguna aplicación con fecha de comienzo inferior a 2010 y aún no se terminó. Informar nombre de proyecto, área, fecha inicio y fecha prevista fin.

|   nombreproyecto    |         nombrea         |  fechaini  | fechaprevistafin |
| :-----------------: | :---------------------: | :--------: | :--------------: |
| Proyecto Histórico  | Infraestructura Patrick | 2009-03-01 |    2010-01-01    |
| Proyecto Legendario |   Monitoreo Calamardo   | 2008-07-15 |    2011-01-01    |

9. Listar información de de todas las áreas que componen el departamento de ‘Redes’.

| coddepto |         nombrea         |            descripcion             |
| :------: | :---------------------: | :-------------------------------: |
|    1     | Infraestructura Patrick | Área técnica liderada por Patrick |
|    1     |   Monitoreo Calamardo   |    Supervisión por Calamardo      |

10. Listar información de proyectos que sólo tengan aplicaciones finalizadas durante 2019.

|  nombreproyecto  |   avance   |      descproyecto      |   objetivos    |
| :--------------: | :--------: | :--------------------: | :------------: |
| Proyecto 2019-B  | Finalizado |   Otro proyecto 2019   | Grandes logros |
| Proyecto 2019-A  | Finalizado | Proyecto completo 2019 |   Éxito total  |
