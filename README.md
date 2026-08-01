# ¿Los jugadores valen lo que cobran?
### Análisis de valor, rendimiento y gestión de minutos en la NBA — caso Golden State Warriors

Proyecto de análisis de datos que cruza salario y rendimiento (Win Shares) de la NBA entre 2010 y 2025, con un foco específico en la evaluación del roster de Golden State Warriors (2021-2025): qué jugadores están infravalorados o sobrepagados respecto al mercado, y cómo gestiona el equipo la carga de minutos de sus jugadores.

## 🎯 Objetivo

Responder, desde la perspectiva de un analista de GSW, a tres preguntas:

- ¿Qué jugadores del roster están infravalorados o sobrepagados respecto al mercado?
- ¿Cómo se compara el gasto y el rendimiento de GSW con el resto de la liga?
- ¿Gestiona el coaching staff la carga de minutos de forma eficiente, y hay jugadores en riesgo por sobrecarga?

## 📊 Fuentes de datos

Datasets principales

Kaggle — ratin21: "NBA Player Stats and Salaries 2010-2025". Estadísticas básicas por jugador y temporada más salarios. URL: kaggle.com/datasets/ratin21/nba-player-stats-and-salaries-2010-2025
Kaggle — sumitrodatta: "NBA Stats (1947-present)". Estadísticas avanzadas históricas compiladas desde Basketball-Reference, incluyendo Win Shares, PER, VORP y BPM. Actualizado hasta la temporada 2025-26. URL: kaggle.com/datasets/sumitrodatta/nba-aba-baa-stats

Fuentes de validación

Basketball-Reference (basketball-reference.com) — fuente original de los datos estadísticos NBA. Usada para contrastar la calidad de los datasets de Kaggle.
Spotrac (spotrac.com) — fuente de referencia para validación de salarios y estructura del salary cap NBA.
HoopsHype (hoopshype.com) — fuente secundaria de validación de salarios.

## 🗂️ Estructura del repositorio

```
├── Análisis NBA.ipynb           # Notebook completo: limpieza, EDA, análisis, exportación
├── Análisis NBA.pbix            # Dashboard interactivo (5 páginas)
├── README.md
├── capturas/                    # Capturas de cada página del dashboard
└── data/
    ├── Advanced.csv                                     # Dataset Kaggle (sumitrodatta)
    ├── NBA_Player_Stats_and_Salaries_2010-2025.csv      # Dataset Kaggle (ratin21)
    ├── Player Award Shares.csv                          # Dataset Kaggle (sumitrodatta)
    ├── Player_Season_Info.csv                           # Dataset Kaggle (sumitrodatta)
    ├── Player_Totals.csv                                # Dataset Kaggle (sumitrodatta)
    ├── Team_Summaries.csv                               # Dataset Kaggle (sumitrodatta)
    ├── nba_analisis_final.csv                           # Dataset unificado, salida del EDA
    └── Data Power BI/
        ├── pbi_mercado_nba.csv
        ├── pbi_roster_gsw_detalle.csv
        ├── pbi_roster_gsw_media.csv
        ├── pbi_carga_minutos_equipos.csv
        ├── pbi_carga_minutos_gsw.csv
        └── pbi_carga_minutos_jugadores.csv
```

## 🛠️ Tecnologías utilizadas

- **Python**: pandas, matplotlib, seaborn
- **Power BI Desktop**: dashboard interactivo, medidas DAX, segmentadores

## 📈 Dashboard (Power BI)

5 páginas de navegación:

1. **Portada**
2. **Mercado NBA** — valor de mercado por franquicia, evolución salario/WS-millón (2010-2025), top jugadores infra/sobrevalorados.
3. **Roster GSW** — comparación GSW vs liga, scatterplot salario/valor por jugador, detalle de roster (2021-2025).
4. **Gestión de minutos** — carga de minutos por equipo, ranking de eficiencia de GSW, carga individual por jugador.
5. **Conclusiones y propuestas** — recomendaciones de fichajes, renovaciones y gestión de carga.

## 🏀 Vocabulario propio de la NBA
 
- **Salary cap**: límite de gasto salarial que la liga fija cada temporada por equipo. En la NBA es un "tope blando" (*soft cap*): los equipos pueden superarlo mediante excepciones específicas (ej. retener a sus propios jugadores), pero pagando un impuesto de lujo (*luxury tax*) si se pasan de un segundo umbral.

- **Contrato máximo (max contract)**: el salario más alto que un jugador puede firmar, calculado como un porcentaje del salary cap (25%, 30% o 35%) según sus años de experiencia en la liga. No depende de una negociación libre; es un techo fijado por las reglas del convenio colectivo.

- **Contrato a dos vías (two-way contract)**: contrato especial, limitado a jugadores jóvenes con poca experiencia, que les permite alternar entre el equipo NBA y su filial de G League. Tiene un salario mucho más bajo que un contrato NBA estándar y un límite de días que el jugador puede pasar con el equipo grande.

- **WS (Win Shares)**: estadística avanzada que estima cuántas victorias del equipo son atribuibles a un jugador concreto, combinando su aportación ofensiva y defensiva en un solo número. Es la métrica de rendimiento central de este análisis, usada para calcular la eficiencia salarial (`ws_por_millon`).

- **WS/millón**: no es una métrica oficial de la NBA, sino una creada para este análisis: `ws` dividido entre el salario en millones de dólares. Indica cuántas victorias aporta un jugador por cada millón que cobra — es la base para clasificar a un jugador como infravalorado o sobrepagado.

**Posiciones (`pos`):**
 
- **PG (Point Guard / Base)**: organiza el juego, suele tener más asistencias y menos tamaño físico que el resto de posiciones.
- **SG (Shooting Guard / Escolta)**: especialista en anotación exterior, normalmente el mejor tirador del equipo.
- **SF (Small Forward / Alero)**: posición híbrida, combina anotación, defensa y algo de creación de juego.
- **PF (Power Forward / Ala-Pívot)**: juega cerca del aro, aporta rebote y físico, cada vez con más capacidad de tiro exterior en el juego moderno.
- **C (Center / Pívot)**: la posición más alta e interior, protege el aro y domina el rebote.

## 📖 Glosario de columnas con significado propio de la NBA
 
| Columna | Significado |
|---|---|
| `season` | Temporada NBA (año de finalización, ej. 2024 = temporada 2023-24) |
| `team` | Abreviatura del equipo (3 letras) |
| `pos` | Posición (PG, SG, SF, PF, C) |
| `ws` | Win Shares totales de la temporada (ver Vocabulario) |
| `ws_medio` | WS medio del equipo o jugador, según la tabla |
| `ws_por_millon` | `ws` dividido entre `salario_millones` — mide la eficiencia salarial: cuántas victorias aporta cada millón de dólares pagado |
| `per` | Player Efficiency Rating, medida global de producción por minuto |
| `vorp` | Value Over Replacement Player, valor del jugador frente a un sustituto de nivel mínimo |
| `categoria_valor` | Etiqueta (Infravalorado / Valor de mercado / Sobrepagado) asignada según los percentiles 33 y 66 de `ws_por_millon` en toda la liga |
| `minutos_por_partido` | Minutos jugados de media por partido |
| `minutos_totales` | Minutos totales acumulados en el periodo analizado |
| `partidos_totales` | Número de partidos jugados |
| `temporadas` | Número de temporadas del jugador presentes en el dataset de GSW |
| `jugadores` | Número de jugadores considerados en el promedio de ese equipo |
| `nombre_completo` / `ciudad` / `latitud` / `longitud` | Datos de localización de la franquicia, usados en el mapa de la página "Mercado NBA" |

## 💡 Insights clave

- GSW supera a la media de la liga en eficiencia salarial (WS/millón) en aproximadamente un **+30%** en el periodo 2021-2025.
- **Trayce Jackson-Davis** es el jugador más infravalorado del roster (4,16 WS/millón en 2024).
- GSW ocupa el **puesto 5 de 30** en eficiencia de rotación (WS medio vs minutos/partido).
- **Stephen Curry** y **Draymond Green** concentran la mayor carga de minutos del equipo en edades de mayor riesgo físico (36 y 34 años).
- **Kevon Looney** es el modelo de gestión de carga más eficiente del roster: menos minutos, mejor rendimiento relativo.

## ✅ Recomendaciones
 
1. **Renovar a Jackson-Davis.** Mayor WS/millón del roster; prioridad máxima antes de que llegue a agencia libre.
2. **Renovar a Podziemski.** Infravalorado dos temporadas consecutivas; renovar a precio de mercado medio.
3. **Evaluar a Kuminga.** En el umbral entre infravalorado y valor de mercado; la próxima temporada es decisiva para la decisión.
4. **Priorizar pívots en fichajes.** Es la posición con mejor retorno por dólar invertido en el mercado actual.
5. **Gestionar la carga de Curry y Green.** Reducir 2-3 minutos por partido; es el principal riesgo físico del roster dada su edad.
6. **Mantener el modelo de rotación actual.** GSW está en el puesto 5 de 30 en eficiencia; Kevon Looney es la referencia interna de gestión de carga a extender a los jugadores jóvenes.

## ▶️ Cómo reproducir el análisis
 
1. Instala las librerías necesarias:
```bash
pip install pandas matplotlib seaborn
```
2. Abre y ejecuta el notebook en orden, de arriba a abajo:
```bash
jupyter notebook "Análisis NBA.ipynb"
```
 
El notebook parte de los datasets Kaggle en `data/` y genera los seis CSVs de `data/Data Power BI/`, listos para cargar en `Análisis NBA.pbix`.

## ✍️ Autora

Cristina Sáenz Llorente
