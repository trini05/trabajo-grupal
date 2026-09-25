# Origen de los Datos y Fuentes de Información — Temporada 2024

## 1. Dónde y cómo se obtuvieron los datos
La base de datos fue construida mediante un proceso de recopilación, cruce y verificación desde fuentes primarias y secundarias:

1. **Calendario, Horarios y Resultados:**
   Los datos sobre el fixture, las fechas disputadas, horarios, estadios y marcadores finales se extrajeron de la cobertura especial de resultados del Campeonato 2024.
   * **Fuente:** [Emol - Calendario y Resultados Campeonato 2024](https://www.emol.com/especiales/2024/deportes/campeonato-2024/calendario-y-resultados.asp)

2. **Asistencia, Aforo Autorizado y Convocatoria:**
   La información sobre el público controlado, los aforos autorizados por la autoridad y el análisis del % de ocupación de los estadios se obtuvo a partir de los balances oficiales e informes del programa Estadio Seguro y la ANFP, difundidos y analizados por medios de comunicación deportivos:
   * **La Tercera:** Reporte del balance histórico de público y asistencia del torneo 2024 ([Ver artículo](https://www.latercera.com/el-deportivo/noticia/la-u-arrasa-en-historico-balance-de-publico-en-2024/VN32L27TEBD6FKAGI4VDNGKGPE/?)).
   * **Cooperativa:** Informe de convocatoria y ranking de asistencia por equipo ([Ver artículo](https://www.cooperativa.cl/noticias/deportes/futbol/liga-de-primera/la-u-supero-a-colo-colo-y-se-alzo-como-el-equipo-con-mayor-convocatoria/2024-11-23/103410.html?)).
   * **AS Chile:** Ranking detallado de público vs. aforo permitido y comparativa entre los clubes principales ([Ver ranking aforo](https://chile.as.com/futbol/ranking-de-publico-y-aforo-campeonato-nacional-2024-la-batalla-que-la-u-le-gano-a-colo-colo-n/?) y [Ver ranking de público general](https://chile.as.com/futbol/ranking-de-publico-campeonato-nacional-2024-el-sorprendente-tercer-grande-del-futbol-chileno-n/?)).


## 2. Tratamiento de Datos
* En los casos donde la información de asistencia o precio no contó con un respaldo oficial verificado, el valor se dejó como nulo (`NaN`) para garantizar la transparencia de la investigación.

## Aclaración importante
Hay datos que no están incluidos en la base de datos, si bien incluimos los links con los promedios de aforo, estos no son 100% útiles para nuestro estudio, por lo que estamos esperando la respuesta del portal de transparencia con los datos oficiales.