# Documentación del Proceso de Limpieza, Metodología y Decisiones Editoriales (Temporada 2024)

## 1. Explicación del Proceso de Limpieza de Datos

El proceso de limpieza, estandarización y consolidación de la base de datos de la temporada 2024 fue realizado íntegramente por nosotros utilizando el lenguaje de programación Python. El objetivo fundamental fue estructurar, validar y transformar un conjunto de registros recopilados manualmente desde diversas fuentes en una base de datos única, estandarizada, relacional y analíticamente funcional.

### Paso 1: Lectura Adaptativa e Identificación de Encabezados
Durante la etapa de estructuración de las planillas iniciales, se detectó que los datos ingresados contenían celdas combinadas, títulos institucionales y formatos decorativos en las primeras filas. Para evitar errores en la lectura de los datos, implementamos un algoritmo de inspección fila por fila en Python. Este script rastreó en cada hoja la presencia exacta de la cadena de texto "Fecha N°", reconociendo dinámicamente dicha posición como el punto de inicio de los encabezados reales y descartando las filas de formato superior.

### Paso 2: Homologación y Estandarización de Variables (Snake Case)
Los nombres de las columnas en los borradores iniciales contenían caracteres especiales, mayúsculas, acentos, espacios dobles y signos de puntuación (por ejemplo, `% Ocupación` o `Precio Más Bajo (CLP)`). Aplicamos una transformación completa para renombrar todas las columnas bajo el estándar internacional `snake_case` (minúsculas y guiones bajos). Esta estandarización previene errores de sintaxis en consultas programáticas y asegura la interoperabilidad entre diferentes entornos analíticos como Python, R y SQL.

### Paso 3: Identificación de Entidades y Creación de Claves Primarias
Para permitir análisis relacionales y comparativos sin perder la trazabilidad de la fuente o el club:
* Extrajimos el nombre de la hoja de cálculo (`Colo-Colo`, `Universidad de Chile`, `Universidad Católica`) y lo inyectamos dinámicamente como el valor de la variable `equipo_local`.
* Asignamos la variable `temporada` con el valor constante `2024`.
* Generamos un identificador único por registro (`id_partido`) mediante una clave alfanumérica secuencial (`PART_2024_001`, `PART_2024_002`, etc.), garantizando la unicidad de la clave primaria para cada evento deportivo.

### Paso 4: Tratamiento de Datos Faltantes (Sintaxis y Transparencia Periodística)
En el periodismo de datos, la integridad de la información es un pilar ético innegociable. Durante el proceso de levantamiento y revisión, detectamos que en diversas jornadas los datos de asistencia oficial (`publico_controlado`) o de precios de boletería no se encontraban disponibles ni consolidados públicamente, figurando originalmente con guiones (`-`), espacios en blanco o textos nulos.

Aplicamos las siguientes reglas estrictas:
* Limpieza de caracteres no numéricos y conversión de guiones (`-`) a valores nulos explícitos (`NaN` de NumPy).
* **Decisión metodológica clave:** Rehusamos categóricamente la imputación de valores inventados, promedios móviles o estimaciones sintéticas. Imputar datos de asistencia o precios en un reportaje periodístico distorsionaría la realidad de los hechos y vulneraría la rigurosidad de la investigación. Los vacíos informativos se documentan de forma explícita y transparente.

### Paso 5: Recálculo Riguroso de Tasas y Creación de Variables Categóricas
1. **Recálculo del Porcentaje de Ocupación (`porcentaje_ocupacion_calc`):** En lugar de confiar ciegamente en los valores de ocupación precalculados en las planillas borrador (que presentaban imprecisiones de redondeo), programamos una regla de cálculo directo:
   $$\text{porcentaje\_ocupacion\_calc} = \frac{\text{publico\_controlado}}{\text{aforo\_autorizado}} \times 100$$
   Este cálculo se ejecuta condicionalmente únicamente cuando ambos valores de entrada existen y son mayores a cero.
2. **Clasificación por Convocatoria (`tipo_rival`):** Con el fin de responder a nuestra hipótesis sobre el comportamiento inelástico de la demanda en partidos de alta rivalidad, construimos una variable categórica que diferencia automáticamente entre partidos regulares y partidos de alta convocatoria. Definimos la categoría *"Clásico / Alta Convocatoria"* para todos aquellos partidos donde el club visitante corresponde a alguno de los otros dos equipos denominados "grandes" del fútbol chileno.

---

## 2. Lista de Fuentes Utilizadas y Justificación

Para construir y contrastar nuestra base de datos con el máximo nivel de precisión, veracidad y rigor periodístico, seleccionamos y consultamos las siguientes fuentes oficiales y de prensa deportiva:

1. **Emol - Calendario, Programación y Resultados del Campeonato 2024:**
   * **Enlace:** [https://www.emol.com/especiales/2024/deportes/campeonato-2024/calendario-y-resultados.asp](https://www.emol.com/especiales/2024/deportes/campeonato-2024/calendario-y-resultados.asp)
   * **Justificación:** Elegimos esta fuente para estructurar el fixture base del dataset, ya que ofrece el registro cronológico más detallado y verificado de las 30 fechas del torneo 2024, incluyendo horarios exactos, recintos deportivos utilizados y marcadores finales de cada encuentro.

2. **La Tercera (El Deportivo) - Balance Histórico de Público 2024:**
   * **Enlace:** [https://www.latercera.com/el-deportivo/noticia/la-u-arrasa-en-historico-balance-de-publico-en-2024/VN32L27TEBD6FKAGI4VDNGKGPE/?](https://www.latercera.com/el-deportivo/noticia/la-u-arrasa-en-historico-balance-de-publico-en-2024/VN32L27TEBD6FKAGI4VDNGKGPE/?)
   * **Justificación:** Nos permitió auditar y contrastar las cifras agregadas de asistencia acumulada por club a lo largo de toda la temporada 2024, corroborando las cifras presentadas por el programa Estadio Seguro.

3. **Cooperativa - Informe Convocatoria y Asistencia 2024:**
   * **Enlace:** [https://www.cooperativa.cl/noticias/deportes/futbol/liga-de-primera/la-u-supero-a-colo-colo-y-se-alzo-como-el-equipo-con-mayor-convocatoria/2024-11-23/103410.html?](https://www.cooperativa.cl/noticias/deportes/futbol/liga-de-primera/la-u-supero-a-colo-colo-y-se-alzo-como-el-equipo-con-mayor-convocatoria/2024-11-23/103410.html?)
   * **Justificación:** Constituyó un respaldo periodístico independiente clave para validar las cifras totales de venta de boletos y el promedio de asistencia por partido de nuestra base.

4. **AS Chile - Ranking de Público y Aforo Campeonato Nacional 2024:**
   * **Enlaces:** [Ranking Aforo 2024](https://chile.as.com/futbol/ranking-de-publico-y-aforo-campeonato-nacional-2024-la-batalla-que-la-u-le-gano-a-colo-colo-n/?) | [Ranking de Público General 2024](https://chile.as.com/futbol/ranking-de-publico-campeonato-nacional-2024-el-sorprendente-tercer-grande-del-futbol-chileno-n/?)
   * **Justificación:** Nos aportó el desglose detallado partido a partido de la relación entre el aforo autorizado por las autoridades regionales y el público efectivamente controlado en las galerías.

5. **Sistemas Oficiales de Ticketaje (PuntoTicket y Ticketplus) y Comunicados de los Clubes:**
   * **Justificación:** Fueron la fuente primaria e irrefutable desde donde recopilamos manualmente las tarifas de la entrada más barata (galería/general) comercializada formalmente para cada encuentro.

---

## 3. Preguntas de Análisis Respondidas con la Base Limpia

Mediante la generación de tablas dinámicas (*pivot tables*) con la base de datos que construimos y limpiamos, respondemos a tres interrogantes fundamentales para nuestro reportaje periodístico:

### Pregunta 1: ¿Existe una diferencia sustancial en la tasa de ocupación de los estadios según el costo de la entrada más barata?
* **Análisis con Tabla Dinámica:** Agrupando los datos por rangos tarifarios de `precio_entrada_min` y promediando la variable `porcentaje_ocupacion_calc`.
* **Utilidad Periodística:** Esta consulta permite contrastar directamente nuestra hipótesis de trabajo. Si los estadios registran tasas de ocupación elevadas (superiores al 80%) en rangos de precios altos, se demuestra que el precio no opera como una barrera disuasoria absoluta para el hincha.

### Pregunta 2: ¿Cómo influye la categoría del rival (Clásicos vs. Rivales Regulares) en el precio aplicado y en la asistencia lograda?
* **Análisis con Tabla Dinámica:** Creando una tabla pivote con `tipo_rival` en las filas y `equipo_local` en las columnas, calculando simultáneamente el precio promedio y el porcentaje de ocupación.
* **Utilidad Periodística:** Revela las políticas de precios diferenciados adoptadas por las directivas de los clubes. Permite visibilizar cómo en partidos de alta convocatoria el valor del boleto suele incrementarse, alcanzando de todas formas niveles máximos de llenado del recinto.

### Pregunta 3: ¿De qué manera la franja horaria y la programación de los partidos condicionan la asistencia de público?
* **Análisis con Tabla Dinámica:** Agrupando los partidos por la variable `hora` de inicio y cruzándolos con la asistencia promedio registrada (`publico_controlado`).
* **Utilidad Periodística:** Expone el impacto logístico que tienen las decisiones de programación impuestas por las cadenas de televisión y la autoridad sobre la experiencia del asistente al estadio, identificando los horarios que castigan la presencia de hinchas en las galerías.