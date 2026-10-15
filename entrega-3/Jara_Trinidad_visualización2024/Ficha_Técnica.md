# Ficha técnica de la base de datos

## Partidos de local de Colo-Colo, Universidad de Chile y Universidad Católica · Temporada 2024

## 1. Características de los datos

| Característica | Detalle |
|---|---|
| Unidad de observación | Un partido de local de uno de los tres equipos |
| Número de observaciones | 45 (15 por equipo) |
| Número de variables | 18 (13 de la base original y 5 creadas en el procesamiento) |
| Periodo cubierto | 23 de febrero al 10 de noviembre de 2024 |
| Equipos | Colo-Colo, Universidad de Chile, Universidad Católica |
| Estadios | Estadio Monumental (Colo-Colo), Estadio Nacional (Universidad de Chile), Estadio Santa Laura (Universidad Católica, 14 partidos) y Estadio Bicentenario La Florida (Universidad Católica, 1 partido) |
| Rivales distintos | 16 |
| Tipos de partido | 6 clásicos y 39 regulares |
| Formato | CSV, una fila por partido |
| Fuentes originales | [COMPLETAR: fuentes de cada dato de la base original] |

## 2. Variables incorporadas

- **Equipo:** equipo que juega de local.
- **Fecha N°:** jornada del campeonato (por ejemplo, "Fecha 3").
- **Fecha:** día en que se jugó el partido.
- **Hora:** hora de inicio.
- **Rival:** equipo visitante.
- **Estadio:** estadio donde se jugó.
- **Goles Local / Goles Visita:** goles de cada equipo.
- **Resultado:** victoria, empate o derrota del equipo local.
- **Aforo Autorizado:** capacidad máxima de público autorizada para el partido.
- **Público Controlado:** público registrado oficialmente. [CONFIRMAR definición] Sin datos por ahora.
- **% Ocupación:** porcentaje del aforo ocupado. Sin datos por ahora.
- **Precio Más Bajo (CLP):** precio de la entrada más barata. Sin datos por ahora.

Variables creadas en el procesamiento:

- **Hora decimal:** la hora como número (17:30 equivale a 17,5).
- **Día de la semana:** lunes a domingo, calculado desde la fecha.
- **Tipo de día:** fin de semana o día de semana.
- **Tipo de partido:** clásico (el rival es otro de los tres equipos del estudio) o regular.
- **Franja horaria:** antes de las 17:00, de 17:00 a 18:59, o 19:00 en adelante.

## 3. Observaciones sobre la base de datos

- **Asistencia y precio sin datos.** Las columnas `Público Controlado`, `% Ocupación` y `Precio Más Bajo (CLP)` están vacías en los 45 partidos. Los datos se solicitaron por el portal de transparencia y no llegaron a tiempo. Los vacíos se mantienen como `NaN`, sin imputar.
- **Aforo autorizado no es asistencia.** `Aforo Autorizado` indica cuánta gente podía entrar, no cuánta fue. Varía entre 9.000 y 45.000 según el estadio y el partido.
- **Una sola temporada.** La base cubre solo 2024. La temporada 2025 está a cargo de otro integrante del equipo, por lo que los datos no son comparables entre años en esta versión.
- **Unificación de nombres.** En la base original el rival "Iquique" aparece con un nombre distinto al de "Deportes Iquique". Se unificaron bajo "Deportes Iquique".
- **`Fecha N°` es texto.** Al ordenar por esa columna, "Fecha 10" aparece antes que "Fecha 2". Para ordenar cronológicamente hay que usar `Fecha`.
- **Formato de fechas.** El CSV original guarda la fecha como `dd/mm/aaaa`; el procesado la guarda como `aaaa-mm-dd`. Leer la fecha sin indicar el formato puede confundir día con mes o producir un error.
- **Definición de "clásico".** Se usa una definición operativa: partidos entre Colo-Colo, Universidad de Chile y Universidad Católica (6 partidos en 2024). No incluye otros duelos tradicionales, como los que involucran a Unión Española.
- **Partido fuera del estadio habitual.** La Universidad Católica jugó un partido en el Estadio Bicentenario La Florida (aforo de 9.000), distinto de su sede habitual en Santa Laura.
- **Resultado consistente.** El campo `Resultado` coincide con los goles en los 45 partidos: 26 victorias, 10 empates y 9 derrotas del equipo local.
- **Muestra pequeña.** Con 45 partidos, la base sirve para describir patrones de programación, no para hacer inferencias estadísticas sobre toda la liga.

## 4. Base de datos
Las declaradas en la sección de documentación.