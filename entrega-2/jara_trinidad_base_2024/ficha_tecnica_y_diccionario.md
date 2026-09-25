# Ficha Técnica y Diccionario de Datos — Temporada 2024

## Ficha Técnica

* **Fuente de los datos:**
  1. *Construcción propia:* Dataset diseñado, compilado y estructurado por nosotros.
  2. *Datos deportivos, aforos y asistencia:* Recopilados y cotejados desde informes oficiales de la ANFP, el programa Estadio Seguro y reportes de prensa en [Emol](https://www.emol.com/especiales/2024/deportes/campeonato-2024/calendario-y-resultados.asp), [La Tercera](https://www.latercera.com/el-deportivo/noticia/la-u-arrasa-en-historico-balance-de-publico-en-2024/VN32L27TEBD6FKAGI4VDNGKGPE/?), [Cooperativa](https://www.cooperativa.cl/noticias/deportes/futbol/liga-de-primera/la-u-supero-a-colo-colo-y-se-alzo-como-el-equipo-con-mayor-convocatoria/2024-11-23/103410.html?) y [AS Chile](https://chile.as.com/futbol/ranking-de-publico-y-aforo-campeonato-nacional-2024-la-batalla-que-la-u-le-gano-a-colo-colo-n/?).
  3. *Precios de entradas:* Levantamiento directo desde comunicados institucionales de los clubes y plataformas oficiales de ticketaje (PuntoTicket y Ticketplus).
* **Metodología de la construcción de la base:**
  1. Recopilación manual y estructuración inicial de datos por equipo local (Colo-Colo, Universidad de Chile, Universidad Católica).
  2. Unificación y limpieza programática en Python para integrar los registros en una sola estructura relacional.
  3. Omisión de encabezados decorativos superiores mediante la detección dinámica del campo clave `Fecha N°`.
  4. Homologación de variables a la convención `snake_case`.
  5. Conversión explícita de caracteres vacíos o no reportados (`-`) a valores nulos (`NaN`).
  6. Recálculo estandarizado de la tasa de ocupación real: `porcentaje_ocupacion_calc = (publico_controlado / aforo_autorizado) * 100`.
  7. Clasificación categórica de la variable `tipo_rival` para identificar automáticamente encuentros entre los tres clubes de mayor convocatoria ("3 grandes").
* **Alcance de los datos:** Comprende la totalidad de los partidos disputados en condición de local por Colo-Colo, Universidad de Chile y Universidad Católica durante las 30 jornadas del Campeonato Nacional de Primera División de Chile 2024 (45 encuentros).
* **Características de los datos:** Estructura de datos tipo panel donde la unidad fundamental de análisis es el *partido individual disputado como local*. Presenta variables categóricas, numéricas continuas, discretas y temporales.
* **Otras observaciones sobre la base:**
  * Para resguardar la rigurosidad periodística, la base no realiza imputación sintética de datos. Los vacíos informativos originales en precios o asistencias no reportadas se conservan como valores nulos (`NaN`).
  * Los cálculos de ocupación se realizan filtrando exclusivamente aquellos registros que cuentan con la totalidad de sus campos consolidados.

---

## Diccionario de Datos

| Nombre de la Variable | Descripción | Tipo de Dato | Valores Posibles | Observaciones Editoriales |
| :--- | :--- | :--- | :--- | :--- |
| `id_partido` | Identificador alfanumérico único por partido | Texto | `PART_2024_001` a `PART_2024_045` | Generado secuencialmente en el proceso de unificación |
| `temporada` | Año correspondiente al campeonato disputado | Entero | `2024` | Fijo para el conjunto de datos 2024 |
| `fecha_numero` | Jornada oficial según el fixture del torneo | Texto | `Fecha 1` a `Fecha 30` | Mantiene la denominación del calendario oficial |
| `fecha_calendario` | Fecha de disputa del encuentro | Fecha | `DD/MM/YYYY` | Fecha exacta en que se jugó el partido |
| `hora` | Horario oficial de inicio del partido | Tiempo | `HH:MM` (Formato 24 hrs) | Utilizado para analizar el impacto del horario |
| `equipo_local` | Club que organiza y ejerce la localía | Texto | `Colo-Colo`, `Universidad de Chile`, `Universidad Católica` | Define el universo de la muestra analizada |
| `equipo_visitante` | Club rival en la jornada | Texto | Nombre de los clubes de 1ª División 2024 | Utilizado para definir la jerarquía del rival |
| `tipo_rival` | Categorización según el nivel de convocatoria | Categórico | `Clásico / Alta Convocatoria`, `Rival Regular` | Se asigna "Clásico" si el rival es uno de los 3 grandes |
| `estadio` | Recinto deportivo donde se disputó el juego | Texto | `Estadio Monumental`, `Estadio Nacional`, `Santa Laura`, etc. | Recinto efectivamente utilizado |
| `goles_local` | Cantidad de goles marcados por el equipo local | Entero | $\ge 0$ | Marcador del equipo local |
| `goles_visita` | Cantidad de goles marcados por el equipo visitante | Entero | $\ge 0$ | Marcador del equipo visitante |
| `resultado_local` | Condición final del equipo local | Categórico | `Victoria`, `Empate`, `Derrota` | Derivado directamente del marcador del partido |
| `aforo_autorizado` | Capacidad máxima de espectadores aprobada | Entero | `10.000` a `45.000` | Límite fijado por las autoridades regionales |
| `publico_controlado` | Cantidad oficial de asistentes que ingresaron | Entero / Nulo | Asistentes con boleto registrado | Presenta nulos (`NaN`) en fechas no reportadas |
| `porcentaje_ocupacion_calc` | Tasa efectiva de llenado del recinto deportivo | Flotante / Nulo | `0.00%` a `100.00%` | Fórmula: `(publico_controlado / aforo_autorizado) * 100` |
