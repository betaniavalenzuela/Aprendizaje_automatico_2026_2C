# Regresión Logística 

## Evaluación del modelo

El modelo de Regresión Logística obtuvo una exactitud (**Accuracy**) de **73,53 %** sobre los datos de prueba. Esto significa que clasificó correctamente 25 de los 34 usuarios utilizados para evaluar el modelo.

A partir del reporte de clasificación y de la matriz de confusión se puede observar que el modelo tuvo un buen desempeño para identificar a los usuarios de **Linux**, ya que reconoció correctamente los 9 casos de esta clase.

En el caso de **Windows**, clasificó correctamente 12 de los 17 usuarios. Para **Macintosh**, clasificó correctamente 4 de los 8 casos.

La matriz de confusión permitió observar que algunos usuarios de Windows fueron clasificados como Linux y algunos usuarios de Macintosh fueron clasificados como Windows.

## Predicción de un nuevo usuario

Finalmente, se probó el modelo con un usuario nuevo utilizando los siguientes datos:

| Característica | Valor |
|---|---:|
| Duración de la visita | 300 segundos |
| Páginas vistas | 4 |
| Acciones realizadas | 8 |
| Valor de las acciones | 16 |

El modelo predijo que el sistema operativo utilizado por este usuario corresponde a la **clase 2, Linux**.

## Conclusión

En este trabajo se utilizó un modelo de **Regresión Logística** para clasificar usuarios según el sistema operativo que utilizan, utilizando como datos de entrada características relacionadas con su visita a un sitio web.

El modelo obtuvo una exactitud del 73,53 %, logrando clasificar correctamente la mayoría de los casos del conjunto de prueba. La matriz de confusión permitió analizar con mayor detalle los aciertos y errores para cada uno de los tres sistemas operativos.

Finalmente, se realizó una predicción utilizando los datos de un nuevo usuario. Para una visita de 300 segundos, con 4 páginas vistas, 8 acciones y un valor de acciones de 16, el modelo predijo Linux.