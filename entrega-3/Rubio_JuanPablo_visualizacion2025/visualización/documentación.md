# Programación y rivales: ¿cuándo y contra quién juegan los grandes de Santiago? (Temporada 2024)

## 1. Qué se hizo y por qué
Esta visualización es complementaria a las que mostrarán la asistencia. Los datos de asistencia oficial y de precios de 2024 aún están incompletos (los solicitamos por el portal de transparencia y no llegaron a tiempo, pero estamos recopilándolos por vías alternativas confiables), así que esta pieza se concentra en las dos primeras variables de la hipótesis grupal que sí están completas: la programación (día y horario) y el rival (clásico o partido regular).

La visualización responde, en parte, a estas preguntas de investigación del proyecto:
- ¿Cómo cambia la ocupación según el día y horario del partido? (describe la programación, que es el escenario donde después se medirá la ocupación).
- ¿Cómo varía la ocupación según el rival? (distingue clásicos de partidos regulares).
- ¿Cómo afectan las restricciones de aforo? (muestra el aforo autorizado de cada partido).

Cuando se complete la columna de asistencia, el mismo gráfico podrá mostrar la ocupación real cambiando el color a % Ocupación. Además, nos sirve para ilustrar cómo están repartidos los partidos en los meses y horarios.

---

## 2. Base de datos utilizada
- **Archivo original:** un CSV propio cargado en la entrega (este incluye los partidos y columnas base del campeonato).
- **Archivo procesado:** el CSV procesado a través del script y el notebook de Python (`datos_partidos_limpios.csv`).
- **Por qué se eligió:** es la base limpia que preparamos con los partidos de local de los tres equipos en 2024. Tiene completas las columnas de fecha, hora, rival, estadio, resultado y aforo autorizado. Las columnas de asistencia (Público Controlado, % Ocupación) y de precio (Precio Más Bajo - CLP) están vacías por ahora y se completarán cuando lleguen los datos definitivos.

### Fuentes originales
La base de datos fue construida mediante un proceso de recopilación, cruce y verificación desde fuentes primarias y secundarias:
1. **Calendario, Horarios y Resultados:** Los datos sobre el fixture, las fechas disputadas, horarios, estadios y marcadores finales se extrajeron de la cobertura especial de resultados del campeonato.
   - *Fuente:* [Emol - Calendario y Resultados Campeonato](https://www.emol.com/especiales/2025/deportes/campeonato-2025/calendario-y-resultados.asp).
2. **Asistencia, Aforo Autorizado y Convocatoria:** La información sobre el público controlado, los aforos autorizados por la autoridad y el análisis del % de ocupación de los estadios se obtuvo a partir de los balances oficiales e informes del programa Estadio Seguro y la ANFP, difundidos y analizados por medios de comunicación deportivos:
   - *La Tercera:* [Reporte del balance histórico de público y asistencia del torneo](https://www.latercera.com/el-deportivo/noticia/a-cuatro-fechas-del-final-que-equipo-ha-llevado-mas-publico-como-local-en-la-liga-de-primera/).
   - *La Tercera:* [Análisis de infraestructura, proyecciones y aforos de los recintos deportivos](https://www.latercera.com/el-deportivo/noticia/claro-arena-a-un-ano-las-cifras-proyecciones-y-la-tarea-de-la-uc/).
   - *La Tercera:* [Informe de convocatoria y ranking de asistencia por equipo](https://www.latercera.com/el-deportivo/noticia/a-cuatro-fechas-del-final-que-equipo-ha-llevado-mas-publico-como-local-en-la-liga-de-primera/).

### Procesamiento paso a paso

| Paso | Qué se hizo | Por qué |
| :--- | :--- | :--- |
| **1** | Se cargó el CSV original. | Establecer un punto de partida replicable. |
| **2** | La fecha pasó a formato de fecha, aceptando `dd/mm/aaaa` y `aaaa-mm-dd`. | El CSV original trae día/mes/año; leerlo sin indicar el formato confunde día con mes. |
| **3** | La hora pasó a número decimal (`17:30 = 17,5`) en la variable `Hora decimal`. | Poder ubicar la hora de inicio en un eje numérico preciso. |
| **4** | Se crearon las variables `Día de la semana` y `Tipo de día` (fin de semana / día de semana). | Analizar y segmentar la programación temporal. |
| **5** | Se unificó "Iquique" con "Deportes Iquique". | Corregir inconsistencias: era el mismo equipo con dos nombres distintos. |
| **6** | Se creó `Tipo de partido`: *Clásico* si el rival es otro de los tres equipos del estudio, *Regular* en los demás casos. | Separar y aislar los partidos de alta convocatoria esperable. |
| **7** | Se creó `Franja horaria` (antes de las 17:00, 17:00 a 18:59, 19:00 o más). | Resumir el horario del encuentro en tramos operativos lógicos. |
| **8** | El `% Ocupación` se convirtió a número; los vacíos quedaron como `NaN`. | Evitar imputar o inventar datos faltantes antes de tiempo. |
| **9** | Se ordenó por equipo y fecha, guardando el CSV procesado (`datos_partidos_limpios.csv`). | Dejar la base estructurada y lista para ser graficada. |

---

## 3. Decisiones de diseño de la visualización
- **Un punto por partido:** Permite observar cada encuentro de forma individual y no solo como promedios abstractos, coherente con la idea de la webstory.
- **Eje X (fecha) y Eje Y (hora de inicio):** Muestran en conjunto el calendario completo de la temporada y la distribución de los horarios.
- **Un panel por equipo (facetas):** Facilita comparar la carga logística de cada club sin mezclar los puntos en un solo gráfico confuso.
- **Color:** Distingue entre clásico (rojo) y regular (gris). El rojo destaca visualmente los 6 clásicos sobre el resto de la cartelera.
- **Tamaño:** Representa el aforo autorizado, incorporando de manera gráfica el efecto de la capacidad del estadio y las restricciones de la autoridad.
- **Tooltip interactivo:** Incluye detalles de equipo, rival, fecha, día, hora, estadio, resultado y aforo en la versión HTML.
- **Subtítulo analítico:** Incorpora el hallazgo principal verificado contra los datos: los 6 clásicos se jugaron exclusivamente en fin de semana y ninguno de noche.

---

## 4. Problemas encontrados y cómo se resolvieron
Al ejecutar el notebook en Google Colab aparecieron errores iniciales por el formato de las fechas. La causa era que el CSV original utiliza el estándar día/mes/año, mientras que el archivo procesado que genera de forma interna el notebook usa año-mes-día, y el código asumía solo uno de los dos formatos de manera estricta. Además, una primera corrección hacía que el notebook leyera por error el archivo ya procesado en lugar del original, lo que impedía replicar todo el flujo desde cero.

La versión final implementada carga siempre de forma limpia el CSV original, evalúa primero el formato `aaaa-mm-dd` y luego `dd/mm/aaaa`, deteniendo la ejecución con una alerta clara si alguna fecha específica no se puede interpretar de forma correcta.

---

## 5. Preguntas que puede responder la visualización
- ¿En qué días y horarios se juegan los clásicos? (siempre en fin de semana, entre las 15:00 y las 18:00).
- ¿Cuántos partidos se juegan de noche o entre semana, y contra qué rivales?
- ¿Qué equipo carga con más partidos nocturnos o en días laborales?
- ¿Cómo varía el aforo autorizado según el estadio y el tipo de rival?
- ¿Cómo se distribuyen los partidos a lo largo de la temporada y cuándo se producen pausas?
- *Con la asistencia completa, además permitirá responder:* ¿Se llenan más los clásicos de fin de semana por la tarde que los partidos nocturnos o de semana?

---

## 6. Limitaciones
- No se cuenta con los datos definitivos de asistencia ni de precios en esta versión preliminar, por lo que no es posible emitir afirmaciones concluyentes sobre la ocupación real de las tribunas.
- El aforo reflejado en los círculos corresponde estrictamente a la capacidad autorizada por la autoridad, no al volumen de público que asistió efectivamente.
- La definición operativa de "clásico" se restringió exclusivamente a los enfrentamientos entre los tres equipos del estudio, sin contemplar otros duelos tradicionales del fútbol nacional.

---

## 7. Herramientas
- **Python**, **pandas** y **Altair**, ejecutados en un entorno de **Google Colab**. 
- Para la revisión de la sintaxis y corrección de errores de código se consultó la asistencia técnica integrada recomendada por la plataforma, verificando estrictamente todas las cifras contra la base de datos oficial.

---

## 8. Cómo replicar
1. Abrir el notebook de trabajo en Google Colab.
2. Ejecutar todas las celdas de código en orden correlativo.
3. Cuando el sistema lo solicite, cargar el archivo CSV original de la temporada.
4. El script generará de forma automática el CSV procesado (`datos_partidos_limpios.csv`), el archivo interactivo (`visualizacion.html`) y su vista previa estática.