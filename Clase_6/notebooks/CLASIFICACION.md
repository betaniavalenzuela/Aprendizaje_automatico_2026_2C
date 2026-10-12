# **Aprendizaje Automático: clasificación de variedades de porotos**

## **1\. Introducción** 

En este trabajo de Aprendizaje Automático se busco clasificar distintas variedades de porotos a partir de sus características físicas. Para ello, se utilizó el dataset *Dry Bean Dataset*, que contiene información sobre el tamaño, la forma y otras propiedades geométricas de diferentes muestras de porotos.

El objetivo general es desarrollar y comparar dos modelos de clasificación, Árbol de Decisión y K-Nearest Neighbors (K-NN), para determinar cuál obtiene mejores resultados al predecir la variedad de un poroto a partir de sus características.

## **2\. Descripción y exploración del dataset**

Para comenzar, se cargó el archivo Excel y se exploró la estructura del conjunto de datos, se identificaron sus columnas y se verificó la existencia de valores faltantes.

El conjunto está formado por 13.611 registros y 17 columnas. De ellas, 16 corresponden a variables predictoras y una es la variable objetivo, denominada Class.

Entre las variables predictoras se encuentran Area (área), Perimeter (perímetro), MajorAxisLength y MinorAxisLength (longitudes de los ejes), Eccentricity (excentricidad), roundness (redondez) y Compactness (compacidad), entre otras. Estas características describen diferentes aspectos de la forma y el tamaño de cada muestra.

La variable objetivo contiene siete variedades: BARBUNYA, BOMBAY, CALI, DERMASON, HOROZ, SEKER y SIRA.

Durante la exploración se comprobó que no existen valores nulos, por lo que no fue necesario realizar un tratamiento de datos faltantes. También se observó que las clases no tienen la misma cantidad de registros. Por ejemplo, DERMASON cuenta con 3.546 muestras, mientras que BOMBAY tiene 522\. Esta diferencia es importante porque algunas variedades tienen más ejemplos disponibles para el entrenamiento que otras.

## **3\. Preparación de los datos**

Una vez explorado el conjunto, se separaron las variables predictoras de la variable objetivo. Para esto se utilizó X para almacenar las 16 características y y para guardar las variedades que se desean predecir.

Posteriormente, los datos se dividieron en dos grupos mediante la función train\_test\_split: el 80 % se destinó al entrenamiento y el 20 % a la prueba. De esta manera, se utilizaron 10.888 registros para entrenar los modelos y 2.723 para evaluar sus predicciones.

Se establecieron los parámetros random\_state=42 y stratify=y. El primero permite reproducir la misma división de datos al volver a ejecutar el código, mientras que el segundo mantiene aproximadamente la proporción de las siete variedades en los conjuntos de entrenamiento y prueba.

En el caso de K-NN, se aplicó además una estandarización mediante StandardScaler. Este procedimiento transforma las variables para que tengan una escala comparable, algo importante porque K-NN utiliza distancias para encontrar las muestras más cercanas. El escalador se ajustó con los datos de entrenamiento y luego se aplicó a los datos de prueba, evitando utilizar estos últimos para calcular los parámetros de transformación.

## **4\. Modelo Árbol de Decisión**

El Árbol de Decisión es un algoritmo de clasificación que aprende a separar las muestras mediante condiciones basadas en las variables predictoras. En cada división, el modelo selecciona una característica y un punto de corte para formar grupos que permitan distinguir las diferentes variedades.

Por ejemplo, puede establecer condiciones relacionadas con el área o el perímetro para separar determinados grupos de porotos. A medida que se avanza por las ramas del árbol, se aplican nuevas condiciones hasta obtener una predicción final.

Para el trabajo se utilizó DecisionTreeClassifier con random\_state=42. El modelo se entrenó con los datos de entrenamiento y posteriormente realizó predicciones sobre las 2.723 muestras reservadas para la prueba.

Una de las ventajas del Árbol de Decisión es que permite interpretar las reglas que utiliza para clasificar. Además, no necesita que las variables numéricas sean estandarizadas previamente.

### **Evaluación del Árbol de Decisión**

El modelo obtuvo un accuracy de 0,8917, equivalente al 89,17 % de aciertos. Esto indica que clasificó correctamente aproximadamente 8.830 de las 9.000. No; sobre el conjunto de prueba, de 2.723 muestras, el porcentaje de aciertos corresponde aproximadamente a 2.428 predicciones correctas.

El informe de clasificación mostró diferencias entre las variedades. BOMBAY obtuvo un F1-score de 1,00, mientras que SIRA alcanzó 0,81. Esto indica que el modelo tuvo un desempeño excelente con BOMBAY, pero encontró mayores dificultades para identificar correctamente todas las muestras de SIRA.

La matriz de confusión permite observar con mayor detalle estas diferencias. En ella, la diagonal principal representa las predicciones correctas, mientras que los valores fuera de esa diagonal corresponden a muestras clasificadas como otra variedad.

## **5\. Modelo K-Nearest Neighbors (K-NN)**

K-NN, es un algoritmo que clasifica una muestra nueva comparándola con las muestras de entrenamiento más cercanas. Para realizar la predicción, identifica los vecinos más próximos y utiliza sus clases para decidir a qué variedad pertenece la muestra analizada.

En este trabajo se configuró el parámetro n\_neighbors=5, por lo que el modelo considera los cinco vecinos más cercanos. 

El modelo se entrenó utilizando las 16 variables predictoras estandarizadas y luego se utilizó para predecir las variedades de las muestras de prueba.

### **Evaluación de K-NN**

El modelo obtuvo un accuracy de 0,9166, equivalente al 91,66 % de aciertos. Este resultado fue superior al obtenido por el Árbol de Decisión.

Al analizar el informe de clasificación, se observa que BOMBAY alcanzó un F1-score de 1,00 y HOROZ y SEKER obtuvieron valores de 0,95. Por otro lado, SIRA presentó un F1-score de 0,86, superior al 0,81 obtenido con el Árbol de Decisión.

Estos resultados indican que K-NN tuvo un buen desempeño general y mejoró la identificación de algunas variedades que presentaban mayores dificultades para el otro modelo.

### **Visualización de las regiones de decisión**

También se generó un gráfico utilizando ListedColormap, numpy.meshgrid y un mallado con paso de 0,2. Para construirlo se seleccionaron únicamente las variables Area y Perimeter, con el objetivo de representar las regiones donde el modelo predice cada variedad.

Los colores de fondo indican la clase que K-NN asignaría a cada zona del plano, mientras que los puntos representan las muestras reales del conjunto de prueba.

Este gráfico permite visualizar cómo el algoritmo utiliza la proximidad entre las muestras para clasificar. Sin embargo, es importante tener en cuenta que para generar una representación en dos dimensiones se entrenó un modelo adicional utilizando solamente esas dos variables. Por lo tanto, este gráfico sirve para comprender visualmente el funcionamiento de K-NN, pero no representa exactamente el modelo que obtuvo el accuracy de 91,66 %, que fue entrenado con las 16 variables.

## **6\. Métricas utilizadas para evaluar los modelos**

Para evaluar el rendimiento se utilizaron el accuracy, la precisión, el recall, el F1-score y la matriz de confusión. 

**Accuracy (exactitud):** mide la proporción de predicciones correctas sobre el total de muestras evaluadas. Es útil para comparar el rendimiento general de los modelos, aunque por sí sola no permite conocer qué variedades se clasifican mejor o peor.

**Precisión (precision):** indica qué proporción de las muestras predichas como pertenecientes a una variedad realmente pertenece a ella. Una precisión elevada significa que el modelo comete pocos falsos positivos para esa clase.

**Recall (exhaustividad):** mide qué proporción de las muestras que realmente pertenecen a una variedad fue identificada correctamente. Un recall elevado indica que el modelo logra detectar una mayor parte de los ejemplares de esa clase.

**F1-score:** combina la precisión y el recall mediante su media armónica. Es útil para comparar el equilibrio entre ambas métricas.

**Support:** es la cantidad de muestras reales de cada clase presentes en el conjunto de prueba. Por ejemplo, en el informe de clasificación aparecen 709 muestras DERMASON y 104 BOMBAY.

**Matriz de confusión:** muestra la relación entre las clases reales y las predichas. Permite identificar los aciertos y los errores, así como las variedades que el modelo tiende a confundir.

El informe de clasificación también presenta los promedios *macro avg* y *weighted avg*. El promedio macro calcula las métricas de las clases por separado y luego les asigna el mismo peso, mientras que el promedio ponderado considera la cantidad de muestras de cada clase. Como el conjunto de datos presenta diferencias en la cantidad de ejemplos por variedad, observar ambos promedios ayuda a complementar el análisis del accuracy.

## **7\. Comparación de los resultados**

Los resultados generales de ambos modelos fueron los siguientes:

| Métrica | Árbol de decisión | K-NN |
| :---- | :---- | :---- |
| Accuracy | 0,8917 | 0,9166 |
| Precisión macro | 0,91 | 0,93 |
| Recall macro | 0,91 | 0,93 |
| F1-score macro | 0,91 | 0,93 |
| F1-score ponderado | 0,89 | 0,920 |

K-NN obtuvo un accuracy de 91,66 %, mientras que el Árbol de Decisión alcanzó un 89,17 %. La diferencia es de aproximadamente 2,50 puntos porcentuales a favor de K-NN.

Además, K-NN presentó mejores promedios macro de precisión, recall y F1-score. Esto indica que su mejor desempeño no se limita únicamente a la cantidad total de aciertos, sino que también muestra una mejora general al considerar las métricas de las distintas variedades.

De todas maneras, no todas las métricas individuales favorecen a K-NN. Por ejemplo, para BARBUNYA, el recall del Árbol de Decisión fue de 0,90, mientras que el de K-NN fue de 0,88. Por eso es importante analizar cada clase y no quedarse solamente con los valores generales.

En cuanto a la interpretación, el Árbol de Decisión presenta la ventaja de mostrar reglas que ayudan a explicar cómo se realizan las clasificaciones. K-NN, en cambio, obtuvo mejores resultados en esta prueba, aunque depende de la elección de K, de las distancias y de la escala de las variables.

## **8\. Conclusión**

A partir de los resultados obtenidos, considero que K-NN es el modelo que mejor resolvió el problema de clasificación en esta experiencia. Alcanzó un accuracy de 91,66 %, superior al 89,17 % del Árbol de Decisión, y también obtuvo mejores promedios de precisión, recall y F1-score.

La diferencia entre los modelos no es demasiado grande, pero los resultados favorecen a K-NN en el conjunto de prueba utilizado. Por otra parte, el Árbol de Decisión continúa siendo una alternativa válida, especialmente cuando se busca comprender las reglas que utiliza el algoritmo para tomar decisiones.

Este trabajo permitió comprobar que es posible utilizar las características físicas de los porotos para predecir sus variedades mediante técnicas de Aprendizaje Automático. También permitió comprender que la evaluación de un modelo no depende de una sola métrica, sino que requiere analizar distintas medidas para conocer sus aciertos, sus errores y sus limitaciones.

