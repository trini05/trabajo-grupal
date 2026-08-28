# **Análisis base de datos**

## Autor y publicación de los datos
Esta base será construida mediante la recopilación de información publicada por los clubes, plataformas oficiales de venta de entradas y registros de prensa. Para el componente económico se utilizarán además fuentes oficiales del Estado para determinar el sueldo mínimo vigente durante cada período. Y revisaremos los datos de Estadio Seguro.
Las principales fuentes para reconstruir el precio de las entradas serán los sitios oficiales de Colo-Colo, Universidad de Chile y Universidad Católica, sus plataformas o empresas oficiales de venta de entradas y publicaciones realizadas por los clubes antes de cada partido. En caso de que esta información no se encuentre disponible, revisaremos archivos de prensa y registros públicos que hayan informado los precios de los encuentros.
Para el sueldo mínimo utilizaremos registros oficiales del Ministerio del Trabajo y la normativa publicada por la Biblioteca del Congreso Nacional, considerando el monto que se encontraba vigente en la fecha específica de cada partido.

## Contenido
La base contendrá información correspondiente a los partidos de local de Colo-Colo, Universidad de Chile y Universidad Católica durante las temporadas 2024 y 2025.
Cada fila corresponderá a un partido e incorporará variables relacionadas con el precio de asistir y con el contexto en que se disputó el encuentro, dentro de estos datos de contexto, la fecha, hora, equipos participantes, precio de la entrada general más barata disponible, sector correspondiente y sueldo mínimo vigente.
Además, se incorporarán variables relacionadas con el momento deportivo del equipo local, como su posición en la tabla y los puntos obtenidos en sus últimos tres partidos.
Las variables contempladas inicialmente son: ID del partido (algún número asignado por nosotros para después poder hacer el cruce de datos), temporada, fecha, hora, equipo local, equipo visitante, precio de la entrada más barata, sueldo mínimo vigente, porcentaje del sueldo mínimo que representa la entrada, posición del equipo local, puntos obtenidos en los últimos tres partidos y observaciones.
## Pertinencia
La incorporación de variables de contexto permitirá evitar atribuir automáticamente las diferencias de convocatoria al precio. Un partido puede tener una entrada más cara, pero también puede corresponder a un clásico, enfrentar a dos equipos de alta convocatoria o disputarse en un momento deportivo relevante. **Por esto, permitirá analizar el precio junto con otras características que potencialmente se relacionan con la asistencia.**

## Metodología
La base será construida mediante recopilación manual de información. Para cada partido se buscarán todos los datos, procurando mantener el mismo criterio de comparación entre los tres clubes. 
Cuando los partidos no cuenten con información disponible, se recurrirá a registros de prensa, publicaciones archivadas y otros documentos que permitan verificar el valor de la entrada.
Las variables relacionadas con el rendimiento deportivo se obtendrán a partir de las tablas de posiciones y resultados de las respectivas temporadas. El día y horario serán obtenidos de la programación oficial de los campeonatos, mientras que las restricciones de aforo y público visitante serán contrastadas con información de clubes, autoridades y registros de prensa.
En todos los casos se registrará la fuente utilizada y se señalarán como datos faltantes aquellos valores que no puedan ser comprobados. No se estimarán precios o cifras de asistencia cuando no exista una fuente que permita respaldarlos.
Sin embargo, si no es posible obtener información completa partido a partido, evaluaremos trabajar con datos disponibles en los informes de Estadio Seguro, utilizando promedios de asistencia y aforo por club y temporada.
