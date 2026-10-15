# Entrega 03 - Visualización individual

## Programación y rivales: ¿cuándo y contra quién juegan los grandes de Santiago? (Temporada 2024)


## 1. Qué se hizo y por qué

Esta visualización es **complementaria** a las que mostrarán la asistencia. Los datos de asistencia oficial y de precios de 2024 aún están incompletos (los solicitamos por el portal de transparencia y no llegaron a tiempo, pero estamos recopilandolos por vías alternativas confiables), así que esta pieza se concentra en las dos primeras variables de la hipótesis grupal que sí están completas: la **programación** (día y horario) y el **rival** (clásico o partido regular).

La visualización responde, en parte, a estas preguntas de investigación del proyecto:
- ¿Cómo cambia la ocupación según el día y horario del partido? (describe la programación, que es el escenario donde después se medirá la ocupación)
- ¿Cómo varía la ocupación según el rival? (distingue clásicos de partidos regulares)
- ¿Cómo afectan las restricciones de aforo? (muestra el aforo autorizado de cada partido)

Cuando se complete la columna de asistencia, el mismo gráfico puede mostrar la ocupación real cambiando el color a `% Ocupación`.

Además, nos sirve para ilustrar cómo están repartidos los partidos en los meses y horarios.

## 2. Base de datos utilizada

**Archivo original:** un CSV propio cargado en el la entrega (este incluye 45 partidos y 13 columnas)
**Archivo procesado:** el CSV pero procesado (los mismos 45 partidos, pero con 18 columnas), fue generado por el notebook.

**Por qué se eligió:** es la base limpia que preparamos en las entregas anteriores con los partidos de local de los tres equipos en 2024 (15 por equipo). Tiene completas las columnas de fecha, hora, rival, estadio, resultado y aforo autorizado. Las columnas de asistencia (`Público Controlado`, `% Ocupación`) y de precio (`Precio Más Bajo (CLP)`) están vacías por ahora y se van a completar cuando lleguen los datos.

**Fuentes originales:** La base de datos fue construida mediante un proceso de recopilación, cruce y verificación desde fuentes primarias y secundarias:

1. **Calendario, Horarios y Resultados:**
   Los datos sobre el fixture, las fechas disputadas, horarios, estadios y marcadores finales se extrajeron de la cobertura especial de resultados del Campeonato 2024.
   * **Fuente:** [Emol - Calendario y Resultados Campeonato 2024](https://www.emol.com/especiales/2024/deportes/campeonato-2024/calendario-y-resultados.asp)

2. **Asistencia, Aforo Autorizado y Convocatoria:**
   La información sobre el público controlado, los aforos autorizados por la autoridad y el análisis del % de ocupación de los estadios se obtuvo a partir de los balances oficiales e informes del programa Estadio Seguro y la ANFP, difundidos y analizados por medios de comunicación deportivos:
   * **La Tercera:** Reporte del balance histórico de público y asistencia del torneo 2024 ([Ver artículo](https://www.latercera.com/el-deportivo/noticia/la-u-arrasa-en-historico-balance-de-publico-en-2024/VN32L27TEBD6FKAGI4VDNGKGPE/?)).
   * **Cooperativa:** Informe de convocatoria y ranking de asistencia por equipo ([Ver artículo](https://www.cooperativa.cl/noticias/deportes/futbol/liga-de-primera/la-u-supero-a-colo-colo-y-se-alzo-como-el-equipo-con-mayor-convocatoria/2024-11-23/103410.html?)).
   * **AS Chile:** Ranking detallado de público vs. aforo permitido y comparativa entre los clubes principales ([Ver ranking aforo](https://chile.as.com/futbol/ranking-de-publico-y-aforo-campeonato-nacional-2024-la-batalla-que-la-u-le-gano-a-colo-colo-n/?) y [Ver ranking de público general](https://chile.as.com/futbol/ranking-de-publico-campeonato-nacional-2024-el-sorprendente-tercer-grande-del-futbol-chileno-n/?)).

### Procesamiento paso a paso

| Paso | Qué se hizo | Por qué |
|---|---|---|
| 1 | Se cargó el CSV original | Punto de partida replicable |
| 2 | `Fecha` pasó a formato de fecha, aceptando `dd/mm/aaaa` y `aaaa-mm-dd` | El CSV original trae día/mes/año; leerlo sin indicar el formato confunde día con mes |
| 3 | `Hora` pasó a número decimal (17:30 = 17,5) en `Hora decimal` | Poder ubicar la hora en un eje numérico |
| 4 | Se creó `Día de la semana` y `Tipo de día` (fin de semana / día de semana) | Analizar la programación |
| 5 | Se unificó "Iquique" con "Deportes Iquique" | Era el mismo equipo con dos nombres distintos |
| 6 | Se creó `Tipo de partido`: *Clásico* si el rival es otro de los tres equipos del estudio, *Regular* en los demás casos | Separar los partidos de alta convocatoria esperable |
| 7 | Se creó `Franja horaria` (antes de las 17:00, 17:00 a 18:59, 19:00 o más) | Resumir el horario en tramos |
| 8 | `% Ocupación` se convirtió a número; los vacíos quedaron como `NaN` | No imputar ni inventar datos faltantes |
| 9 | Se ordenó por equipo y fecha, y se guardó el CSV procesado | Dejar la base lista para graficar |

## 3. Decisiones de diseño de la visualización

- **Un punto por partido.** Así se ve cada encuentro y no solo promedios, coherente con la idea de la webstory de explorar cada partido.
- **Eje X: fecha. Eje Y: hora de inicio.** Muestra juntos el calendario de la temporada y los horarios.
- **Un panel por equipo (facetas).** Permite comparar la carga de cada club sin mezclar los puntos.
- **Color: clásico (rojo) o regular (gris).** El rojo destaca los 6 clásicos sobre el resto.
- **Tamaño: aforo autorizado.** Incorpora el efecto del estadio y de las restricciones de aforo.
- **Tooltip** con equipo, rival, fecha, día, hora, estadio, resultado y aforo, en la versión HTML.
- **Subtítulo con el hallazgo principal**, verificado contra los datos: los 6 clásicos se jugaron en fin de semana y ninguno de noche.

## 4. Problemas encontrados y cómo se resolvieron

Al ejecutar el notebook en Google Colab aparecieron errores por el **formato de las fechas**. La causa era que el CSV original usa día/mes/año, mientras que el archivo procesado que genera el propio notebook usa año-mes-día, y el código asumía solo uno de los dos. Además, una primera corrección hacía que el notebook leyera el archivo ya procesado en lugar del original, lo que impedía replicarlo desde cero.

La versión final (`v2`) carga siempre el CSV original, prueba primero el formato `aaaa-mm-dd` y luego `dd/mm/aaaa`, y se detiene con un aviso si alguna fecha no se puede interpretar.

## 5. Preguntas que puede responder la visualización

- ¿En qué días y horarios se juegan los clásicos? (siempre en fin de semana, entre las 15:00 y las 18:00)
- ¿Cuántos partidos se juegan de noche o entre semana, y contra qué rivales?
- ¿Qué equipo carga con más partidos nocturnos o en días laborales?
- ¿Cómo varía el aforo autorizado según el estadio y el tipo de rival?
- ¿Cómo se distribuyen los partidos a lo largo de la temporada y cuándo hay pausas?

Con la asistencia completa, además: ¿se llenan más los clásicos de fin de semana por la tarde que los partidos nocturnos o de semana?

## 6. Limitaciones

- No hay datos de asistencia ni de precio en esta versión, por lo que **no se puede afirmar nada sobre la ocupación real**.
- El aforo mostrado es el **autorizado**, no la cantidad de público.
- La definición de "clásico" se limita a los partidos entre los tres equipos del estudio; no incluye otros duelos tradicionales.

## 7. Herramientas

Python, pandas y Altair, ejecutados en Google Colab. Para revisar la ejecución y corregir errores de código se utilizó Gemini, que era lo sugerido por Google Colab; las cifras se verificaron contra la base de datos.

## 8. Cómo replicar

1. Abrir el notebook en Google Colab.
2. Ejecutar todas las celdas en orden.
3. Cuando lo pida, subir el CSV origninal
4. Se generan el CSV procesado, el HTML y el JPG.
