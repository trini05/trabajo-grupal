## 4. Documentación

### Historial de Procesos y Decisiones

La presente documentación detalla rigurosamente el proceso de depuración, transformación y análisis de la base de datos de partidos, asistencias, aforos y precios del fútbol chileno para la temporada 2025. El objetivo central de este trabajo es garantizar la absoluta transparencia, auditabilidad y replicabilidad de la investigación periodística, permitiendo que cualquier equipo de reporteros o editores pueda verificar el origen de las cifras y la lógica detrás de cada cálculo.

#### 1. Fases del Proceso de Limpieza y Estandarización de Datos
El tratamiento de la información se dividió en cuatro etapas metodológicas secuenciales:
* **Fase 1: Inspección Estructural y Diagnóstico Inicial.** Se cargó el archivo original `partidos_asistencia_y_precios_2025 OFICIAL.xlsx` utilizando entornos de programación en Python (librería `pandas`) para auditar la estructura de las hojas correspondientes a los tres clubes principales (Colo-Colo, Universidad de Chile y Universidad Católica). Se detectó que las primeras tres filas de cada hoja contenían metadatos y títulos desplazados, por lo que se estableció la cuarta fila (`header=3`) como el encabezado real de las columnas.
* **Fase 2: Homogeneización de Nombres y Estructuras.** Se unificaron los nombres de las columnas entre las distintas hojas. Se identificó que la hoja de Colo-Colo carecía originalmente de la columna explícita de "Puntos", la cual fue calculada programáticamente a partir de la columna "Resultado" (Asignando 3 puntos por "Victoria", 1 por "Empate" y 0 por "Derrota") para mantener la paridad estructural con las bases de Universidad de Chile y Universidad Católica.
* **Fase 3: Tratamiento de Valores Faltantes (Missing Values) y Anomalías.** Se analizaron las columnas de "Público Controlado" y "Precio Más Bajo". Se constató que los registros de Colo-Colo presentaban celdas vacías en asistencia controlada, mientras que otras instituciones registraban valores consistentes. Se decidió conservar los valores nulos explícitamente sin realizar imputaciones arbitrarias para evitar sesgos en el análisis de afluencia de público, documentando transparentemente esta limitación. Asimismo, los caracteres de guión (`-`) utilizados en porcentajes de ocupación sin datos se transformaron a nulos (`NaN`) para facilitar operaciones matemáticas posteriores.
* **Fase 4: Exportación y Validación Cruzada.** Las tablas limpias fueron validadas mediante consultas de integridad referencial, asegurando que las sumas de partidos coincidieran con el calendario oficial del Campeonato Nacional 2025.

#### 2. Herramientas Tecnológicas Utilizadas
* **Python (Entorno de Análisis de Datos):** Utilizado para la lectura automatizada de archivos Excel, inspección de tipos de datos, limpieza de cadenas de texto y resolución de inconsistencias estructurales entre hojas.
* **Pandas y OpenPyXL:** Librerías para la manipulación tabular y estructuración de matrices de datos.
* **Git y Markdown:** Herramientas de versionamiento y redacción documental para asegurar el formato de entrega exigido.

#### 3. Criterios de Selección de las Fuentes de Datos
Las fuentes elegidas corresponden exclusivamente a los registros oficiales de los tres clubes de mayor convocatoria del fútbol chileno. La selección de Colo-Colo, Universidad de Chile y Universidad Católica se fundamenta en los siguientes criterios periodísticos:
* **Representatividad de la Convocatoria:** Concentran históricamente más del 70% de la masa de espectadores y recaudación de taquilla del fútbol profesional en Chile, siendo los termómetros ideales para analizar el impacto económico de los precios de entradas.
* **Disponibilidad y Comparabilidad:** Son las instituciones que poseen mayor trazabilidad en sus reportes de aforos y precios de galerías, permitiendo contrastar la gestión de seguridad (Estadio Seguro) frente a la economía de los hinchas.

#### 4. Ejemplos de Preguntas Periodísticas Respondidas mediante Tablas Dinámicas (Pivot Tables)
A partir de la base de datos limpia, es posible construir múltiples tablas dinámicas para responder a interrogantes de investigación periodística. A continuación se detallan tres ejemplos concretos:

* **Pregunta 1: ¿Cuál es el club que registra el mayor precio promedio en su entrada más baja (galería/general) y cómo se relaciona con su porcentaje de ocupación del estadio?**
  * *Construcción de la Tabla Dinámica:* Agrupando por la variable **Club**, calculando el promedio de la variable **Precio Más Bajo (CLP)** y el promedio de la variable **% Ocupación**.
  * *Utilidad Periodística:* Permite investigar si los clubes que encarecen sus entradas más económicas experimentan una caída directa en la asistencia relativa de sus hinchas o si, por el contrario, la demanda es inelástica debido a la fidelidad de la fanaticada.
  
* **Pregunta 2: ¿Existe una correlación directa entre jugar con un aforo autorizado reducido (menor a 20.000 espectadores) y la obtención de triunfos deportivos de local?**
  * *Construcción de la Tabla Dinámica:* Segmentando la base cruzando **Estadio / Aforo Autorizado (categorizado en rangos)** frente a la variable **Resultado** (conteo de Victorias, Empates y Derrotas).
  * *Utilidad Periodística:* Permite comprobar la hipótesis periodística de si los recintos con menor capacidad o las sanciones de aforo parcial merman la presión local y afectan el rendimiento deportivo del equipo organizador.

* **Pregunta 3: ¿Cómo varían los precios de las entradas más bajas según el nivel de convocatoria y la jerarquía del rival de turno?**
  * *Construcción de la Tabla Dinámica:* Cruzando la variable **Rival** o tipificando partidos de alta convocatoria ("Clásicos" y partidos ante equipos de alta convocatoria) frente al promedio de **Precio Más Bajo (CLP)** y **Aforo Autorizado**.
  * *Utilidad Periodística:* Permite develar si los clubes implementan dinámicas de alza de precios ("partidos clase A" o "alta demanda") frente a rivales atractivos, analizando posibles abusos tarifarios o discriminación de precios hacia los sectores populares de las hinchadas.
