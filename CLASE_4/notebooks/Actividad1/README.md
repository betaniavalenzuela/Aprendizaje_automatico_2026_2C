# Análisis de Consumo Cultural y Uso de Internet

## Descripción del proyecto

En este proyecto se realizó un análisis de un conjunto de datos sobre consumo cultural. El objetivo principal fue estudiar la relación entre diferentes actividades culturales y el tiempo de uso de Internet.

Para su realizacion se aplico técnicas de análisis exploratorio de datos y un modelo de **Regresión Lineal Múltiple**.

## Datos utilizados

El conjunto de datos contiene información de 250 personas y 451 variables relacionadas con diferentes aspectos del consumo cultural.

Para el modelo se seleccionaron las siguientes variables:

- Edad
- Horas de uso de radio
- Horas dedicadas a escuchar música
- Horas dedicadas a leer diarios
- Horas de televisión
- Horas de videojuegos

La variable que se intentó estimar fue:

**Horas de uso de Internet**

## Análisis realizado

Primero se realizó una exploración general del conjunto de datos, observando su estructura, tipos de variables, valores estadísticos y posibles valores faltantes.

Luego se analizaron las relaciones entre las variables mediante una matriz de correlación y diferentes gráficos.

A partir de este análisis se seleccionaron las variables utilizadas para construir el modelo de Regresión Lineal Múltiple.

Los datos fueron divididos en un conjunto de entrenamiento y otro de prueba. Posteriormente se entrenó el modelo y se realizaron predicciones sobre los datos de prueba.

## Resultados del modelo

El modelo obtuvo los siguientes resultados:

- **MAE:** 4,10 horas
- **MSE:** 31,08
- **R²:** 0,255
- **Varianza explicada:** 0,266

El valor de R² indica que el modelo logra explicar aproximadamente el **25,5 % de la variabilidad** de las horas de uso de Internet en los datos de prueba.

Entre las variables utilizadas, la edad presentó una relación negativa con las horas de Internet, mientras que las horas dedicadas a la música y a los videojuegos presentaron relaciones positivas dentro del modelo.

## Conclusión

Los resultados muestran que las variables seleccionadas aportan información para estimar el tiempo de uso de Internet, pero no son suficientes para explicar completamente su comportamiento.

El error obtenido también muestra que las predicciones pueden alejarse varios horas de los valores reales. Esto indica que existen otros factores que podrían influir en el uso de Internet y que no fueron incluidos en este modelo.

El trabajo permitió aplicar un modelo de Regresión Lineal Múltiple sobre datos reales, analizar sus resultados mediante diferentes métricas y visualizar la relación entre los valores reales y las predicciones.

