# Ficha Técnica: Análisis de Programación y Aforos - Fútbol Chileno (Temporada 2025)

## 1. Ficha General del Proyecto
- **Tema:** Análisis de programación (días y horarios), aforos autorizados y emparejamientos de los tres equipos de alta convocatoria de Santiago (Colo-Colo, Universidad de Chile y Universidad Católica) durante la temporada 2025.
- **Autor / Editor:** Juan Pablo Rubio Herrera.
- **Asignatura / Contexto:** Data Journalism Project / Entrega de Visualización de Datos.
- **Herramientas utilizadas:** Python, Pandas, Altair (Google Colab) y Visual Studio Code para la estructura del repositorio en GitHub.

---

## 2. Características de los Datos
- **Cobertura temporal:** Partidos correspondientes al campeonato oficial de la temporada 2025 en condición de local para los tres clubes seleccionados (15 partidos por cada institución, totalizando la muestra analizada).
- **Formatos de entrega:** 
  - Archivo plano estructurado en formato CSV (`datos_partidos_limpios.csv`).
  - Archivo interactivo en formato web (`visualizacion.html`).
  - Vista previa estática (`visualization.png`).

---

## 3. Diccionario de Variables Incorporadas
La base de datos procesada contiene 18 columnas analíticas. Las principales variables se detallan a continuación:

| Variable | Tipo de Dato | Descripción |
| :--- | :--- | :--- |
| **Fecha N°** | Categórica / Numérica | Identificador del número de fecha oficial del campeonato (ej: Fecha 1, Fecha 2). |
| **Fecha** | Fecha (Date) | Día exacto en que se disputó el encuentro (estandarizado en formato `aaaa-mm-dd`). |
| **Hora** | Texto / Hora | Franja horaria de inicio programada originalmente para el partido. |
| **Hora decimal** | Numérica (Float) | Transformación matemática de la hora de inicio a formato decimal (ej. 17:30 = 17,5) para su ubicación precisa en el eje Y del gráfico. |
| **Día de la semana** | Categórica | Día en el que se desarrolló el cotejo (Lunes a Domingo). |
| **Tipo de día** | Categórica | Segmentación temporal que distingue entre *Fin de semana* y *Día de semana*. |
| **Rival** | Categórica | Nombre oficial del equipo contrincante que visitó al club anfitrión. |
| **Estadio** | Categórica | Recinto deportivo oficial donde se llevó a cabo el encuentro de local. |
| **Goles Local** | Numérica | Cantidad de goles convertidos por el equipo anfitrión. |
| **Goles Visita** | Numérica | Cantidad de goles convertidos por el equipo visitante. |
| **Resultado** | Categórica | Condición final del partido para el equipo local (*Victoria*, *Derrota* o *Empate*). |
| **Aforo Autorizado** | Numérica (Int) | Capacidad máxima de espectadores permitida por la autoridad competente y la organización para el evento. |
| **Equipo** | Categórica | Club anfitrión del partido (*Colo-Colo*, *Universidad de Chile* o *Universidad Católica*). |
| **Tipo de partido** | Categórica | Variable clave que diferencia los duelos en *Clásico* (si el rival es otro de los tres equipos del estudio) y *Regular* (resto de los contrincantes). |
| **Franja horaria** | Categórica | Segmentación operativa del horario del partido (Antes de las 17:00, 17:00 a 18:59, 19:00 o más). |
| **Público Controlado** | Numérica | Cantidad de asistentes reales registrados en los torniquetes (campo condicionado a la llegada oficial de datos de transparencia). |
| **% Ocupación** | Numérica (Float) | Proporción resultante entre el público controlado y el aforo autorizado. |
| **Precio Más B. (CLP)** | Numérica | Valor en pesos chilenos correspondiente al ticket de menor precio comercializado para el encuentro. |

---

## 4. Observaciones y Limitaciones de la Base de Datos
- **Aforos vs. Asistencia Real:** Los valores de aforo reflejan los techos autorizados por los organismos de seguridad y administración, los cuales suelen sufrir modificaciones de última hora según la contingencia. Las variables de asistencia real y precios se encuentran en proceso de consolidación mediante solicitudes de acceso a la información y vías alternativas.
- **Criterio de Clásico:** Para efectos estrictos de este modelo analítico, la categoría de "clásico" se delimita exclusivamente a los enfrentamientos cruzados entre Colo-Colo, Universidad de Chile y Universidad Católica, omitiendo de esta categoría específica otros duelos de carácter tradicional regional o institucional.

---

## 5. Fuentes de Información Oficiales
1. **Calendario y Fixture:** Emol - Cobertura especial y resultados del Campeonato Nacional ([Ver fuente](https://www.emol.com/especiales/2025/deportes/campeonato-2025/calendario-y-resultados.asp)).
2. **Aforos, Balances y Convocatoria:** Informes técnicos y balances del programa Estadio Seguro y la ANFP, analizados a través de reportajes de *La Tercera* ([Reporte de asistencia](https://www.latercera.com/el-deportivo/noticia/a-cuatro-fechas-del-final-que-equipo-ha-llevado-mas-publico-como-local-en-la-liga-de-primera/) y [Análisis de infraestructura y aforos](https://www.latercera.com/el-deportivo/noticia/claro-arena-a-un-ano-las-cifras-proyecciones-y-la-tarea-de-la-uc/)).