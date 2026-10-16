# Ocupación de estadios y programación en el fútbol chileno (2025)

## 1. Crónica: ¿Cuándo y contra quién juegan los grandes de Santiago?

Cuando se habla de estadios con espacios vacíos en el fútbol chileno, la primera sospecha suele ser el precio de las entradas. Pero antes de llegar a esa discusión conviene mirar algo más básico: cuándo y contra quién se programan los partidos.

El gráfico reúne los partidos que Colo-Colo, la Universidad de Chile y la Universidad Católica jugaron de local en 2025. Cada punto o barra representa un encuentro: su posición muestra la fecha y la hora de inicio, su capacidad refleja el aforo autorizado, y su distribución agrupa a los rivales y equipos locales del torneo.

### Los clásicos y los fines de semana mandan
La gran mayoría de los duelos se concentran en los fines de semana. Los horarios de la tarde —especialmente entre las 15:00 y las 18:00— siguen siendo la ventana preferida para albergar los encuentros de mayor convocatoria, incluyendo los cruces entre los tres grandes del fútbol chileno.

### La noche y la semana, para los demás
En el otro extremo, los partidos programados en horario nocturno (a las 19:00 o más tarde) o en días hábiles de lunes a viernes debieron lidiar con una menor flexibilidad logística, compartiendo gran parte de esta carga horaria y semanal frente a diversos rivales del campeonato.

### No todos cargan con lo mismo
La distribución de localías muestra matices importantes según el recinto. Mientras la Universidad de Chile ejerció de local en el Estadio Nacional con aforos autorizados entre 40.000 y 45.000 espectadores, y Colo-Colo hizo lo propio en el Estadio Monumental (con aforos de 35.000 a 42.000), la Universidad Católica alternó entre el Estadio Santa Laura (12.000 espectadores) y el Estadio San Carlos de Apoquindo (20.000 espectadores).

### Lo que este gráfico todavía revela a medias
Esta visualización cuenta cómo se programa el fútbol, pero al mantenerse en blanco las casillas de asistencia real y público controlado en los registros oficiales, queda pendiente la pieza central de la discusión. Cuando esos datos terminen de completarse, el mismo análisis servirá para responder lo que importa: si los partidos con rival atractivo y horario de fin de semana por la tarde atraen efectivamente a más hinchas, y si esa variación pesa tanto como el precio de la entrada.

---

## 2. Documentación del Proceso Metodológico

### Proceso de Visualización y Decisiones Tomadas
- **Consolidación de fuentes:** Se unificaron las tres hojas independientes del archivo institucional original correspondientes a Colo-Colo, Universidad de Chile y Universidad Católica en un único marco de datos estructurado.
- **Filtrado y limpieza:** Se descartaron filas vacías y se estandarizaron los tipos de datos numéricos (precios en pesos chilenos y aforos autorizados) y de fechas mediante scripts de Python.
- **Diseño:** Se desarrolló una visualización original utilizando la librería **Altair**, diseñada para integrarse en una webstory y exportada tanto en formato interactivo (`.html`) como estático (`.jpg`).

### Selección y Procesamiento de la Base de Datos
Se seleccionó esta base porque recopila de manera oficial los partidos de local, horarios, estadios y precios mínimos de entrada del Campeonato Nacional 2025, permitiendo contrastar la hipótesis sobre los factores que determinan la asistencia. Los datos se procesaron mediante un archivo CSV consolidado (`partidos_asistencia_y_precios_2025_procesado.csv`).

### Preguntas que Responde la Visualización
- ¿Cómo varía el precio más bajo de las entradas según el equipo rival y el club organizador?
- ¿Existen diferencias significativas en las tarifas base entre partidos de alta convocatoria (clásicos) y rivales de menor arrastre?
- ¿De qué manera la capacidad del estadio (aforo autorizado) condiciona la oferta de localidades?

---

## 3. Ficha Técnica de la Base de Datos

| Variable | Descripción |
| :--- | :--- |
| `Equipo Local` | Nombre del club que ejerce la localía (Colo-Colo, U. de Chile o U. Católica). |
| `Fecha N°` | Número de la fecha correspondiente en el calendario oficial. |
| `Fecha` | Día en que se programó el encuentro (AAAA-MM-DD). |
| `Hora` | Hora oficial de inicio del partido. |
| `Rival` | Equipo contrincante que visita al club local. |
| `Estadio` | Recinto deportivo donde se disputó el encuentro. |
| `Goles Local` | Cantidad de goles convertidos por el equipo local. |
| `Goles Visita` | Cantidad de goles convertidos por el equipo visitante. |
| `Resultado` | Condición del marcador final (Victoria, Empate, Derrota). |
| `Aforo Autorizado` | Capacidad máxima de espectadores permitida. |
| `Público Controlado` | Asistentes reales (en blanco institucionalmente). |
| `% Ocupación` | Porcentaje de ocupación calculado (en blanco institucionalmente). |
| `Precio Más Bajo (CLP)` | Valor mínimo en pesos chilenos para las entradas. |
| `Puntos` | Unidades obtenidas por el equipo local en dicho encuentro. |