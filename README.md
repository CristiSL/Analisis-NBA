# ¿Los jugadores de la NBA valen lo que cobran?
### Análisis de valor, rendimiento y gestión de minutos en la NBA — caso Golden State Warriors (GSW)

Proyecto de análisis de datos que cruza salario y rendimiento (Win Shares) de la NBA entre 2010 y 2025, con un foco específico en la evaluación del roster de Golden State Warriors (2021-2025): qué jugadores están infravalorados o sobrepagados respecto al mercado, y cómo gestiona el equipo la carga de minutos de sus jugadores.

📄 Los resultados, insights y recomendaciones del análisis están en **[ANALISIS.md](./ANALISIS.md)**. Este README cubre solo la parte técnica del proyecto.

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
├── README.md                    # Este archivo — parte técnica
├── ANALISIS.md                  # Resultados, insights y recomendaciones
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
