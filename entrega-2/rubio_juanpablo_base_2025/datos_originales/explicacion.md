# Origen de los Datos y Fuentes de Información — Temporada 2025

## 1. Dónde y cómo se obtuvieron los datos
Esta base de datos fue construida mediante un proceso de recopilación, cruce y verificación desde fuentes primarias y secundarias:

1. **Fixture, Horarios, Marcadores y Puntos 2025:**
   La estructura del calendario, partidos programados, horarios, resultados y puntos obtenidos por fecha se obtuvo del seguimiento en vivo y actualización oficial del fixture 2025.
   * **Fuente Principal:** [Emol - Calendario y Resultados Campeonato 2025](https://www.emol.com/especiales/2025/deportes/campeonato-2025/calendario-y-resultados.asp)

2. **Asistencia, Aforo y Convocatoria 2025:**
   Los datos de público controlado, aforo autorizado por la autoridad y el análisis comparativo de la convocatoria durante la temporada 2025 se obtuvieron de los reportes consolidados y rankings difundidos por medios de comunicación especializados:
   * **24 Horas:** Ranking de asistencia de los equipos chilenos con mayor convocatoria ([Ver artículo](https://www.24horas.cl/deportes/futbol-nacional/colo-colo-o-la-u-el-ranking-de-los-equipos-chilenos-con-mas-asistencia)).
   * **ADN Radio:** Balance anual de asistencia y público llevado a los estadios durante el torneo 2025 ([Ver balance 2025](https://www.adnradio.cl/2025/12/27/colo-colo-la-u-o-la-uc-este-fue-el-equipo-chileno-que-llevo-mas-publico-a-los-estadios-durante-2025/)).
   * **AS Chile:** Ranking de público controlado y uso de aforo en los estadios del fútbol chileno ([Ver ranking aforo 2025](https://chile.as.com/futbol/ranking-de-publico-y-aforo-en-los-estadios-campeonato-nacional-2025-fecha-26-del-futbol-chileno-f202511-n/)).

## 2. Tratamiento de Datos
* Para los datos faltantes de aquellos partidos sin informe de asistencia o sin precio publicado conservan el valor nulo (`NaN`), evitando caer en errores de información.

## Aclaración importante
Hay datos que no están incluidos en la base de datos, si bien incluimos los links con los promedios de aforo, estos no son 100% útiles para nuestro estudio, por lo que estamos esperando la respuesta del portal de transparencia con los datos oficiales.