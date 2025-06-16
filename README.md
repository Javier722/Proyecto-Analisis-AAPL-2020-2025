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

### Resultados Obtenidos:

| año  | precio_cierre_promedio_anual | precio_cierre_maximo_anual | precio_cierre_minimo_anual | volumen_total_anual |
| :---: | :---: | :---: | :---: | :---: |
| 2020 | 108.25 | 133.34 | 78.33 | 212895973200.00 |
| 2021 | 138.01 | 177.00 | 113.68 | 228122068100.00 |
| 2022 | 152.41 | 178.65 | 124.43 | 220655045000.00 |
| 2023 | 170.87 | 196.67 | 123.42 | 148042572000.00 |
| 2024 | 206.27 | 258.40 | 164.01 | 143960681000.00 |
| 2025 | 219.20 | 246.78 | 172.19 | 6015363000.00 |


 ### Observación y Conclusiones Clave

* **Crecimiento Sostenido del Precio:** Podemos observar una clara tendencia a la alza en el precio del cierre promedio anual de Apple a lo largo de los años. Desde un promedio de $108.25 USD en el 2020 hasta $219.20 USD en 2025, lo cual demuestra un crecimiento significativo.
* **Aumento en Precios Maximos y Minimos:** Los precios maximos y minimos anuales tambien han seguido una trayectoria ascendente, lo cual sugiere que el valor general de la acción ha ido aumentando con el tiempo. Teniendo un pico maximo de $258.40 USD que se alcanzo en 2024
Volumen de Negociación Variable:
   * En los años **2020** y **2021** se registraron los volumenes de negociación más altos, lo que podría indicar un período de gran actividad en el mercado o un mayor interes y/o volatilidad en la acción.
   * A partir del **2023**, **2024**, y especialmente **2025**, el volumen total anual muestra una disminución notable. El volumen en 2025 es draasticamente mas bajo a los demas, esto se debe a que el dataset no cubre el año 2025 completo, ya que actualmente estamos en el mes de Junio del año 2025, por ello aun no se posee esta información.
* **Punto Alto en 2024:** El año 2024 se destaca como el año con el precio maximo absoluto en el rango de los datos ($258.40), y el promedio anual mas alto antes del 2025.



## Análisis Rendimiento Mes de Acciones de APPLE(AAPL)

### Consulta SQL

```sql
 SELECT
    EXTRACT(YEAR FROM fecha) AS año,
    EXTRACT(MONTH FROM fecha) AS mes,
    ROUND (AVG(precio_cierre), 2) AS precio_cierre_promedio_mensual,
    ROUND (MAX(precio_cierre), 2) AS precio_cierre_maximo_mensual,
    ROUND (MIN(precio_cierre), 2) AS precio_cierre_minimo_mensual,
    SUM(volumen) AS volumen_total_mensual
FROM
    aapl_daily_prices
GROUP BY
    año, mes
ORDER BY
    año, mes; 
```

### Resultados Obtenidos

| "año" | "mes" | "precio_cierre_promedio_mensual" | "precio_cierre_maximo_mensual" | "precio_cierre_minimo_mensual" | "volumen_total_mensual" |
|-------|-------|----------------------------------|--------------------------------|--------------------------------|-------------------------|
| 2020  | 6     | 84.90                            | 89.07                          | 78.33                          | 2970450400              |
| 2020  | 7     | 92.90                            | 103.29                         | 88.48                          | 3020283200              |
| 2020  | 8     | 114.19                           | 125.66                         | 105.89                         | 4070061100              |
| 2020  | 9     | 112.11                           | 130.67                         | 104.04                         | 3885245100              |
| 2020  | 10    | 113.37                           | 121.14                         | 106.01                         | 2894666500              |
| 2020  | 11    | 113.93                           | 117.35                         | 105.92                         | 2123077300              |
| 2020  | 12    | 124.17                           | 133.34                         | 118.80                         | 2322189600              |
| 2021  | 1     | 129.78                           | 139.65                         | 123.50                         | 2240262000              |
| 2021  | 2     | 128.46                           | 134.02                         | 118.20                         | 1833855600              |
| 2021  | 3     | 119.06                           | 124.85                         | 113.68                         | 2650418200              |
| 2021  | 4     | 128.78                           | 131.73                         | 120.17                         | 1889857500              |
| 2021  | 5     | 124.03                           | 129.49                         | 120.15                         | 1711934900              |
| 2021  | 6     | 127.18                           | 134.03                         | 120.90                         | 1606590000              |
| 2021  | 7     | 142.04                           | 145.96                         | 134.34                         | 1919035100              |
| 2021  | 8     | 145.19                           | 150.07                         | 142.41                         | 1461542800              |
| 2021  | 9     | 145.35                           | 153.57                         | 138.68                         | 1797835100              |
| 2021  | 10    | 142.67                           | 149.53                         | 136.37                         | 1565079200              |
| 2021  | 11    | 151.36                           | 162.24                         | 145.14                         | 1691029000              |
| 2021  | 12    | 170.34                           | 177.00                         | 158.85                         | 2444766700              |
| 2022  | 1     | 166.72                           | 178.65                         | 156.28                         | 2108446000              |
| 2022  | 2     | 166.87                           | 173.24                         | 157.31                         | 1627516300              |
| 2022  | 3     | 162.46                           | 175.88                         | 148.02                         | 2180800100              |
| 2022  | 4     | 163.95                           | 175.36                         | 153.87                         | 1687795600              |
| 2022  | 5     | 146.04                           | 163.16                         | 135.18                         | 2401040300              |
| 2022  | 6     | 137.59                           | 148.82                         | 128.01                         | 1749099800              |
| 2022  | 7     | 147.31                           | 159.94                         | 136.74                         | 1447125400              |
| 2022  | 8     | 164.44                           | 172.03                         | 154.95                         | 1510239600              |
| 2022  | 9     | 150.80                           | 161.07                         | 136.21                         | 2084722800              |
| 2022  | 10    | 142.92                           | 153.49                         | 136.34                         | 1868139700              |
| 2022  | 11    | 143.95                           | 149.36                         | 133.15                         | 1724847700              |
| 2022  | 12    | 136.11                           | 146.41                         | 124.43                         | 1675731200              |
| 2023  | 1     | 134.04                           | 144.06                         | 123.42                         | 1443652500              |
| 2023  | 2     | 149.18                           | 153.58                         | 143.57                         | 1307198900              |
| 2023  | 3     | 153.22                           | 163.04                         | 143.67                         | 1520266600              |
| 2023  | 4     | 163.18                           | 167.77                         | 158.29                         | 969709700               |
| 2023  | 5     | 170.82                           | 175.54                         | 163.92                         | 1275155500              |
| 2023  | 6     | 182.46                           | 192.05                         | 176.06                         | 1297101100              |
| 2023  | 7     | 190.50                           | 194.50                         | 186.22                         | 996066400               |
| 2023  | 8     | 179.45                           | 193.67                         | 172.51                         | 1322439400              |
| 2023  | 9     | 175.48                           | 188.07                         | 168.97                         | 1337586600              |
| 2023  | 10    | 173.17                           | 179.16                         | 165.46                         | 1172719600              |
| 2023  | 11    | 184.45                           | 190.06                         | 172.48                         | 1099586100              |
| 2023  | 12    | 192.90                           | 196.67                         | 188.05                         | 1062774800              |
| 2024  | 1     | 186.36                           | 193.76                         | 179.86                         | 1187219300              |
| 2024  | 2     | 183.59                           | 188.03                         | 179.66                         | 1161627000              |
| 2024  | 3     | 171.66                           | 178.58                         | 167.99                         | 1432782800              |
| 2024  | 4     | 168.59                           | 175.49                         | 164.01                         | 1245717000              |
| 2024  | 5     | 185.34                           | 191.45                         | 168.28                         | 1336537700              |
| 2024  | 6     | 205.30                           | 215.66                         | 192.22                         | 1723984500              |
| 2024  | 7     | 223.55                           | 233.73                         | 215.74                         | 1153099800              |
| 2024  | 8     | 220.78                           | 228.99                         | 206.27                         | 1122667000              |
| 2024  | 9     | 222.97                           | 232.18                         | 215.56                         | 1232140300              |
| 2024  | 10    | 229.25                           | 235.65                         | 220.91                         | 930736000               |
| 2024  | 11    | 227.20                           | 236.76                         | 221.23                         | 891640600               |
| 2024  | 12    | 248.72                           | 258.40                         | 239.01                         | 977916100               |
| 2025  | 1     | 234.02                           | 244.41                         | 222.10                         | 1200291700              |
| 2025  | 2     | 238.14                           | 246.78                         | 227.08                         | 862272300               |
| 2025  | 3     | 222.41                           | 238.76                         | 209.41                         | 1115239500              |
| 2025  | 4     | 200.92                           | 223.60                         | 172.19                         | 1606488200              |
| 2025  | 5     | 203.86                           | 213.04                         | 195.27                         | 1195728200              |
| 2025  | 6     | 201.70                           | 201.70                         | 201.70                         | 35343100                |



### Observación y Conclusiones Clave

**Tendencia de Crecimiento del Precio:** Los precios promedio del cierre siguen mostrando una tendencia sostenida al alza, con algunos meses de corrección natural
* **Picos Destacados:** El precio maximo mensual se alcanza con $258.40 USD en diciembre de 2024
* **Correcciones y consolidaciones:**Se observan ajustes en el precio después de periodos de crecimiento acelerado, especialmente desde Enero del 2025 con $234.02 USD hasta abril de 2025 donde hay una caida a $200.92 USD. Lo que puede indicar una fase de consolidación o correción despues de un año de fuertes ganancias.

**Volumen de transacciones** 
* El volumen de operaciones tiende a ser mas alto en periodos de incertidumbre o cambios bruscos en el precio. En abril de 2025, cuando el precio cayó significativamente, el volumen aumento a 1,606,488,200 lo que sugiere una mayor actividad por parte de los inversores.
* 


