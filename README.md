# Proyecto-Analisis-AAPL-2020-2025
Proyecto basado en SQL usando el dataset "apple_5yr_one.csv" tomando en Kaggle

## Análisis Anual del Rendimiento de Acciones de Apple (AAPL)

La primera parte del análisis se centra en evaluar el rendimiento de las acciones de Apple (AAPL) a nivel anual, observando el precio de cierre promedio, precios máximos y mínimos anuales, y el volumen total de operaciones. Esto nos da una macro visión de las tendencias de las acciones.

### Consulta SQL

```sql
SELECT
    EXTRACT(YEAR FROM fecha) AS "año",
    ROUND(AVG(precio_cierre), 2) AS precio_cierre_promedio_anual,
    ROUND(MAX(precio_cierre), 2) AS precio_cierre_maximo_anual,
    ROUND(MIN(precio_cierre), 2) AS precio_cierre_minimo_anual,
    ROUND(SUM(volumen), 2) AS volumen_total_anual
FROM
    aapl_daily_prices
GROUP BY
    "año"
ORDER BY
    "año";
```
### Resultados Obtenidos

|"año"|"precio_cierre_promedio_anual"|"precio_cierre_maximo_anual"|"precio_cierre_minimo_anual"|"volumen_total_anual"|
| :--- | <--------------------------- | :------------------------- | :------------------------- | :------------------ |
| 2020 | 108.25 | 133.34 | 78.33 | 21285973200.00 |
| 2021 | 138.01	| 177.00 |113.68 | 22812206100.00 |
| 2022 | 152.41	| 178.65 | 124.43 | 22065504500.00 |
| 2023 | 170.87 | 196.67 | 123.42 | 14804257200.00 |
| 2024 | 206.27 | 258.40 | 164.01 | 14396068100.00 |
| 2025 | 219.20 | 246.78 | 172.19 |	6015363000.00 |


 Observación y Conclusiones Clave

Crecimiento Sostenido del Precio: Podemos observar una clara tendencia a la alza en el precio del cierre promedio anual de Apple a lo largo de los años. Desde un promedio de $108.25 en el 2020 hasta $219.20 en 2025, lo cual demuestra un crecimiento significativo.
Aumento en Precios Maximos y Minimos: Los precios maximos y minimos anuales tambien han seguido una trayectoria ascendente, lo cual sugiere que el valor general de la acción ha ido aumentando con el tiempo. Teniendo un pico maximo de $258.40 que se alcanzo en 2024
Volumen de Negociación Variable:
* En los años 2020 y 2021 se registraron los volumenes de negociación más altos, lo que podría indicar un período de gran actividad en el mercado o un mayor interes y/o volatilidad en la acción.
* A partir del 2023, 2024, y especialmente 2025, el volumen total anual muestra una disminución notable. El volumen en 2025 es draasticamente mas bajo a los demas, esto se debe a que el dataset no cubre el año 2025 completo, ya que actualmente estamos en el mes de Junio del año 2025, por ello aun no se posee esta información.
* Punto Alto en 2024: El año 2024 se destaca como el año con el precio maximo absoluto en el rango de los datos ($258.40), y el promedio anual mas alto antes del 2025.
