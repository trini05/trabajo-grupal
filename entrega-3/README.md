# Entrega 03 - Ocupación de estadios en el fútbol chileno (2024-2025)

## Hipótesis actual
La ocupación de los estadios en los partidos de local de Colo-Colo, Universidad de Chile y Universidad Católica no está determinada por el precio de las entradas, sino por factores contextuales y de programación: el atractivo del rival (clásicos o partidos de alta convocatoria) y el día y horario del encuentro.

## Preguntas de investigación actuales
**Principal:** ¿Qué combinación de factores (programación, rival o precio) explica en mayor medida la ocupación de los estadios?

**Secundarias:**
- ¿Qué relación existe entre el precio de la entrada y el porcentaje de ocupación?
- ¿Cómo varía la ocupación según el rival?
- ¿Cómo cambia según el día y el horario del partido?
- ¿Existe relación con el momento deportivo del equipo local?
- ¿Cómo afectan las restricciones de aforo o de público visitante?
- ¿Qué características tienen los partidos con mayor y menor ocupación?

## Avance del proyecto
Las bases de 2024 y 2025 nos hicieron pasar de una sola variable a un análisis multivariable. Al comienzo creíamos que el precio era el factor más relevante. Al comparar partidos regulares con clásicos vimos indicios de demanda inelástica: en los clásicos la asistencia se acerca al aforo permitido aun con entradas más caras.

En esta entrega cada integrante trabajó una temporada. La visualización de 2024 muestra la programación: los seis clásicos de local se jugaron en fin de semana, entre las 15:00 y las 18:00, y ninguno de noche. Los 11 partidos nocturnos y los 8 de días de semana fueron todos regulares. Esto refuerza nuestro enfoque multivariable: rival y programación van de la mano, por lo que no conviene atribuir a uno solo el efecto sobre la ocupación.

Los datos tienen límites. Faltan registros de asistencia oficial y de precios en partidos de 2024 y 2025. Los mantuvimos como valores nulos (`NaN`) y centramos los cruces en partidos con datos verificables. Solicitamos los faltantes por el portal de transparencia, pero no llegaron a tiempo; los incorporaremos cuando estén disponibles.

## Síntesis de la historia
La webstory sigue un arquetipo de descubrimiento y explicación. Comienza cuestionando que la baja asistencia responda solo al costo de las entradas y guía al lector, con visualizaciones de cada partido, por cuatro etapas:

1. **Precio y ocupación:** relación entre la tarifa más accesible y el porcentaje de ocupación.
2. **El rival:** clásicos frente a partidos regulares.
3. **La logística del hincha:** efecto del día y el horario, en particular las jornadas laborales y nocturnas.
4. **Casos extremos:** partidos con mayor y menor ocupación, para explicar la combinación de factores que llena un estadio.