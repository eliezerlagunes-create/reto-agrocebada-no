# Reto AgroCebada FIRA 2026 · Equipo "No"

Universidad Anáhuac Puebla · Eliezer Lagunes, Michell Flores, Katia Gutierrez, Erika Piñon y Adrian Hernández

Predicción del rendimiento de cebada de temporal 2025 (t/ha) de 59 parcelas en Hidalgo, Puebla y Tlaxcala, entrenando con 138 parcelas de rendimiento conocido y datos públicos: Sentinel-2, Landsat, Planet, precipitación CHIRPS, temperatura CHIRTS-ERA5 y topografía de INEGI.

**Página de resultados:** (pendiente: liga de GitHub Pages)

## Resultados

- Modelo final: regresión lineal con el municipio, la longitud y la latitud.
- Validación cruzada (5 grupos × 3 repeticiones): RMSE 0.489 t/ha, MAE 0.340 t/ha y R² 0.645. Con el promedio general el RMSE sería 0.851 t/ha.
- Comparamos regresión lineal, Ridge, k vecinos, bosque aleatorio, XGBoost y una red neuronal, y elegimos el modelo con la regla de un error estándar.
- Las variables de satélite, clima y topografía no mejoraron el error: la ubicación explica la mayor parte del rendimiento.
- Las predicciones de las 59 parcelas van de 2.44 a 4.69 t/ha y están en `No_prediccion.csv`.

## Contenido

| Archivo | Qué es |
|---|---|
| `index.html`, `style.css`, `app.js` | Página de resultados (GitHub Pages) |
| `pagina_*.csv`, `pagina_parcelas.geojson`, `graficas/` | Datos y gráficas que usa la página |
| `No_prediccion.csv` | Predicción de las 59 parcelas (ID_POLIGONO, RENDIMIENTO_T_HA) |
| `notebook/` | Notebook con todo el proceso: lectura de datos, variables, Spearman, comparación de modelos y predicciones |
| `requirements.txt` | Librerías necesarias para correr el notebook |

## Cómo correr el notebook

1. Instalar Python 3.10 o más reciente y las librerías: `pip install -r requirements.txt`
2. Descargar `DataSet.zip` desde la plataforma del reto y ponerlo en la carpeta `notebook/`, junto al notebook. No se incluye aquí porque los datos son de FIRA.
3. Abrir el notebook y correr todas las celdas. Tarda uno o dos minutos y vuelve a generar `No_prediccion.csv` y los archivos de la página.

## Summary (English)

We predicted the 2025 barley yield (t/ha) of 59 rainfed parcels in Hidalgo, Puebla and Tlaxcala, Mexico, using 138 parcels with known yield and public satellite, climate and terrain data. We compared linear regression, Ridge, k nearest neighbors, random forest, XGBoost and a neural network with repeated cross-validation. The final model is a linear regression with the municipality, longitude and latitude (RMSE 0.489 t/ha, MAE 0.340 t/ha, R² 0.645). Satellite, climate and terrain variables did not improve the error: location explains most of the yield.

## Fuentes de datos

- FIRA (2026). Reto AgroCebada FIRA 2026: conjunto de datos y su documentación.
- Funk, C., et al. (2015). CHIRPS. *Scientific Data, 2*, 150066. https://doi.org/10.1038/sdata.2015.66
- Climate Hazards Center (2025). CHIRTS-ERA5. https://doi.org/10.15780/G2F08J
- INEGI (2025). Continuo de Elevaciones Mexicano 4.0.
