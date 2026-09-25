# Investigación: Ocupación de Estadios en el Fútbol Chileno (2024-2025)

## Hipótesis 
La ocupación de los estadios en los partidos de local de Colo-Colo, Universidad de Chile y Universidad Católica no está determinada por el precio de las entradas, sino por factores contextuales y de programación como el atractivo del rival (clásicos o partidos de alta convocatoria) y el día u horario del encuentro.

## Preguntas de investigación 
* **Pregunta Principal:**

 ¿Qué combinación de factores (programación, rival o precio) explica en mayor medida la tasa de ocupación de los estadios en el fútbol chileno?

* **Preguntas Secundarias:**
 ¿Qué relación existe entre el precio de la entrada y el porcentaje de ocupación?

¿Cómo varía la ocupación según el rival?

¿Existe una relación entre el momento deportivo del equipo local y la ocupación?

¿Cómo cambia la ocupación según el día y horario del partido?

¿Cómo afectan las restricciones de aforo o de público visitante al porcentaje de ocupación?

¿Qué características tienen los partidos con mayor y menor ocupación?


## Avance del proyecto en relación con la hipótesis y preguntas
La revisión de las bases de datos originales recopiladas para las temporadas 2024 y 2025 nos permitió enfocar el problema hacia un análisis multivariable. Inicialmente, creíamos que el precio de la entrada era el factor más relevante para la asistencia. Sin embargo, al analizar las diferencias entre partidos regulares y de alta convocatoria (clásicos), observamos indicios de demanda inelástica: en encuentros decisivos o clásicos, la asistencia roza el aforo permitido aun cuando el precio de las entradas es mayor.

Respecto a la calidad de los datos recopilados, nos encontramos con vacíos en registros históricos de asistencia oficial y precios de ciertos partidos de 2024, además de encuentros de 2025. Ajustamos nuestra metodología para manejar estos datos faltantes de manera transparente (vía valores nulos `NaN`), enfocando los cruces cuantitativos en los partidos con datos consolidados y verificables. De igual manera, hicimos una solicitud en el portal de transparencia para poder contar con los datos más adelante, por temas de plazos los datos no alcanzaron a llegarnos.

## Síntesis de la historia
La historia webstory sigue un arquetipo de **descubrimiento y explicación**. Comienza cuestionando la idea de que la baja asistencia a los estadios responda únicamente al costo de las entradas. A través de visualizaciones interactivas de cada encuentro, guiamos al usuario por un recorrido analítico:

1. **La relación precio-asistencia:** Exploración inicial entre la tarifa más accesible y el % de ocupación.

2. **El factor del rival:** Comparación entre clásicos y partidos regulares para evaluar la disposición de pago de la hinchada.

3. **La logística del hincha (día y hora):** Análisis del impacto de programar encuentros en días laborales o en horarios nocturnos.

4. **Casos extremos:** Comparación entre los partidos con mayor y menor ocupación para explicar la fórmula multivariable del llenado de estadios.
