# Laboratorio de Regresión Lineal

Aplicación web para explorar relaciones entre variables mediante regresión lineal simple y múltiple. Carga un archivo CSV, elige una variable dependiente y uno o más predictores; el análisis y los datos se procesan localmente en el navegador.

## Ejecutar

Abre `index.html` en un navegador. También puedes servir el proyecto desde la carpeta raíz:

```bash
python3 -m http.server 8000
```

Luego visita <http://localhost:8000>.

La aplicación utiliza Chart.js para los gráficos, PapaParse para leer CSV y Google Fonts para la tipografía. Estas bibliotecas se cargan desde CDN, por lo que se necesita conexión a internet para que todas las funciones estén disponibles.

## Uso

1. Carga un CSV con encabezados en la primera fila.
2. Selecciona la variable dependiente (Y).
3. Marca una o varias variables independientes (X).
4. Pulsa **Calcular regresión** para ver las métricas, el gráfico y los coeficientes.

Las columnas disponibles para Y y X deben ser numéricas. El archivo puede incluir otras columnas, pero no se mostrarán como variables del modelo. Las filas con valores faltantes o no numéricos en las columnas seleccionadas se excluyen del cálculo. Se requieren más observaciones completas que parámetros del modelo.

Ejemplo de CSV:

```csv
horas_estudio,asistencia,nota
2,80,55
4,85,68
6,90,79
8,95,91
```

## Resultados

- **R²:** proporción de la variabilidad de Y explicada por el modelo.
- **R² ajustado:** R² corregido según el número de predictores y observaciones.
- **RMSE:** raíz del error cuadrático medio, expresada en las unidades de Y.
- **Coeficientes:** incluye el intercepto y el coeficiente estimado para cada predictor.
- **Gráfico:** para regresión simple muestra los puntos y la recta estimada; para regresión múltiple compara los valores observados con los predichos.

El modelo se estima por mínimos cuadrados ordinarios con intercepto. Si los predictores son redundantes o presentan colinealidad exacta, la aplicación informa que no puede estimar los coeficientes.

## Estructura

```text
index.html       Interfaz de la aplicación
css/styles.css   Estilos y diseño adaptable
js/app.js        Lectura de CSV, regresión y gráficos
```
