# Resultados del análisis
 
## 🧭 Respuesta directa: ¿los jugadores de la NBA valen lo que cobran?
 
**En conjunto, no siempre y la tendencia va a peor.** Entre 2010 y 2025 el salario medio de la liga casi se ha triplicado (de 4 a 11 millones), mientras que la eficiencia salarial media (victorias generadas por cada millón pagado) ha bajado. Cobrar más ya no implica rendir más; ambas variables se han desacoplado con el tiempo.
 
**Golden State Warriors es la excepción, no la norma.** El equipo paga un 20% más que la media de la liga por jugador (11,8M frente a 9,8M), pero lo compensa con un 29,3% más de eficiencia salarial que esa misma media. GSW no es un caso de sobrepago generalizado, es una franquicia que gasta por encima de la media y lo justifica con rendimiento.
 
**El riesgo del equipo no está en el presupuesto, está en la gestión física.** Cuatro jugadores: Stephen Curry (33,7 min/partido, 36 años), Jimmy Butler (31,7 min/partido, 35 años), Klay Thompson (30,7 min/partido, 33 años) y Draymond Green (29,6 min/partido, 34 años) concentran la mayor carga de minutos del roster en las edades de mayor riesgo de lesión. Es la principal alerta que se desprende del análisis de gestión de minutos, no el salario en sí.

## 🏀 Vocabulario propio de la NBA
 
- **Salary cap**: límite de gasto salarial que la liga fija cada temporada por equipo. En la NBA es un "tope blando" (*soft cap*): los equipos pueden superarlo mediante excepciones específicas, pero pagando un impuesto de lujo (*luxury tax*) si se pasan de un segundo umbral.
- **Contrato máximo (max contract)**: el salario más alto que un jugador puede firmar, calculado como un porcentaje del salary cap (25%, 30% o 35%) según sus años de experiencia en la liga. No depende de una negociación libre; es un techo fijado por las reglas del convenio colectivo.
- **Contrato a dos vías (two-way contract)**: contrato especial, limitado a jugadores jóvenes con poca experiencia, que les permite alternar entre el equipo NBA y su filial de G League. Tiene un salario mucho más bajo que un contrato NBA estándar y un límite de días que el jugador puede pasar con el equipo NBA.
- **WS (Win Shares)**: estadística avanzada que estima cuántas victorias del equipo son atribuibles a un jugador concreto, combinando su aportación ofensiva y defensiva en un solo número. Es la métrica de rendimiento central de este análisis, usada para calcular la eficiencia salarial (`ws_por_millon`).
- **WS/millón**: no es una métrica oficial de la NBA, sino una creada para este análisis: `ws` dividido entre el salario en millones de dólares. Indica cuántas victorias aporta un jugador por cada millón que cobra, es la base para clasificar a un jugador como infravalorado o sobrepagado.
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
| `ws_por_millon` | `ws` dividido entre `salario_millones`, mide la eficiencia salarial: cuántas victorias aporta cada millón de dólares pagado |
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
 
- GSW supera a la media de la liga en eficiencia salarial (WS/millón) en un **29,3%** en el periodo 2021-2025.
- **Trayce Jackson-Davis** es el jugador más infravalorado del roster (4,16 WS/millón en 2024).
- GSW ocupa el **puesto 5 de 30** en eficiencia de rotación (WS medio vs minutos/partido).
- **Stephen Curry, Jimmy Butler, Klay Thompson y Draymond Green** concentran la mayor carga de minutos del equipo en edades de mayor riesgo físico (36, 35, 33 y 34 años).
- **Kevon Looney** es el modelo de gestión de carga más eficiente del roster: menos minutos, mejor rendimiento relativo.

## ✅ Recomendaciones
 
1. **Renovar a Jackson-Davis.** Mayor WS/millón del roster; prioridad máxima antes de que llegue a agencia libre.
2. **Renovar a Podziemski.** Infravalorado dos temporadas consecutivas; renovar a precio de mercado medio.
3. **Evaluar a Kuminga.** Está en valor de mercado (ni infravalorado ni sobrepagado), sin margen claro todavía a su favor; su evolución en la próxima temporada será determinante para decidir si conviene ampliar su contrato.
4. **Priorizar pívots en fichajes.** Es la posición con mejor retorno por dólar invertido en el mercado actual.
5. **Gestionar la carga de Curry, Butler, Klay y Green.** Reducir 2-3 minutos por partido a los cuatro; son el principal riesgo físico del roster dada su edad.
6. **Mantener el modelo de rotación actual.** GSW está en el puesto 5 de 30 en eficiencia; Kevon Looney es la referencia interna de gestión de carga a extender a los jugadores jóvenes.