# Documentación del Proyecto: Análisis de Aforos y Programación del Fútbol Chileno

Repositorio individual para el desarrollo del reportaje y visualización de datos de los partidos de local de Colo-Colo, Universidad de Chile y Universidad Católica.

---

## 1. Proceso de Visualización y Decisiones Tomadas
- **Herramienta utilizada:** Google Colab (Python) y la librería de visualización **Altair**.
- **Pasos del proceso:**
  1. Se cargó un archivo Excel oficial (`partidos_asistencia_y_precios_2025 OFICIAL.xlsx`) que contenía las tres pestañas correspondientes a cada equipo.
  2. Se limpió el archivo ignorando las primeras filas de encabezado institucional y tomando los datos reales a partir de la fila estructurada.
  3. Se unieron las tres pestañas en una sola tabla maestra de datos, agregando una columna identificadora para cada club (`Equipo`).
  4. Se mapearon las variables de fecha, hora, rival, estadio y aforo autorizado para ser procesadas por Altair.
  5. Se diseñó un gráfico de dispersión (scatter plot) interactivo que cruza la **Fecha** en el eje X, la **Hora de inicio** en el eje Y, el **Aforo autorizado** mediante el tamaño de los círculos, y el tipo de partido mediante colores para distinguir clásicos de duelos regulares.
  6. Finalmente, el gráfico interactivo fue exportado en formato **HTML** (`visualizacion.html`) y su vista previa en imagen estática para integrarla en la crónica en Markdown (`cronica.md`).

---

## 2. Base de Datos, Procesamiento y Selección
- **Por qué se seleccionó:** La base de datos es indispensable para contrastar la percepción pública sobre las galerías semivacías con la realidad logística de la programación de los partidos de los tres equipos de alta convocatoria en Santiago.
- **Proceso de limpieza:** El archivo original en Excel con pestañas separadas fue procesado mediante scripts de `pandas` en Python. Se eliminaron valores nulos en filas vacías, se estandarizaron los nombres de las columnas clave (`Fecha N°`, `Fecha`, `Hora`, `Rival`, `Estadio`, `Aforo Autorizado`) y se consolidó todo en una única estructura tabular limpia que posteriormente se exportó en formato plano **CSV** para garantizar su total replicabilidad.

---

## 3. Preguntas que responde la visualización
La visualización de datos final permite responder interrogantes clave planteadas en la investigación:
* ¿Existe un trato preferencial en los horarios y días de la semana para los clásicos en comparación con los partidos regulares?
* ¿Cómo se distribuye la carga de partidos nocturnos o en días hábiles entre los tres equipos grandes de la capital?
* ¿De qué manera las capacidades máximas autorizadas de los estadios (Monumental, Nacional, Santa Laura/San Carlos) condicionan la convocatoria potencial de cada fecha?

---

## 4. Ficha Técnica de la Base de Datos

### Características generales
* **Cobertura:** Partidos de condición de local de Colo-Colo, Universidad de Chile y Universidad Católica.
* **Formato de entrega:** Archivo plano CSV (`datos_partidos_limpios.csv`).

### Variables incorporadas (Diccionario de datos)
| Variable | Descripción |
| :--- | :--- |
| **Fecha N°** | Identificador de la fecha del campeonato nacional (ej: Fecha 2, Fecha 4). |
| **Fecha** | Día exacto en que se disputó el encuentro (formato YYYY-MM-DD). |
| **Hora** | Franja horaria de inicio programada para el partido. |
| **Rival** | Equipo contrincante que visitó el estadio en dicha fecha. |
| **Estadio** | Recinto deportivo donde se llevó a cabo el encuentro de local. |
| **Goles Local / Visita** | Marcador deportivo registrado en el partido. |
| **Resultado** | Condición final del encuentro para el equipo local (Victoria, Derrota, Empate). |
| **Aforo Autorizado** | Capacidad máxima de público permitida por la autoridad para el evento. |
| **Equipo** | Club anfitrión del partido (Colo-Colo, Universidad de Chile o Universidad Católica). |

### Observaciones sobre los datos
* Los datos de aforo reflejan las autorizaciones previas de la autoridad competente y los recintos, existiendo variaciones según las condiciones de seguridad de cada jornada.
* El registro de asistencia real (público controlado) se encuentra sujeto a solicitudes pendientes mediante el portal de transparencia, por lo que esta base se centra en la dimensión estructural de la programación.