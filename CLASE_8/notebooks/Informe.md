# **Segmentación de clientes mediante K-Means**

## **Introducción y objetivo**

El objetivo de este trabajo es aplicar el algoritmo K-Means para identificar diferentes grupos de clientes según sus hábitos de compra y su comportamiento en el sitio web. Se busca reconocer características en común entre los clientes, teniendo en cuenta la frecuencia de compra, el ticket promedio, el tiempo en el sitio, la sensibilidad a los descuentos y la tasa de devoluciones.

## **Preparación de los datos**

El dataset cuenta con 700 registros y cinco variables numéricas. Primero, se eliminaron las columnas `noise_gauss` y `noise_uniform`, ya que no eran necesarias para el análisis.  
Luego, se utilizó `StandardScaler` para estandarizar las variables, porque tienen escalas diferentes. Esto permite que todas tengan una influencia más equilibrada al momento de formar los grupos.

## **Selección de la cantidad de clusters**

Para elegir la cantidad de grupos, se probaron distintos valores de k, entre 2 y 6, utilizando el método del codo y el coeficiente de Silhouette.

- ### **Método del codo**

En el gráfico se observa una disminución importante de la inercia al pasar de k \= 2 a k \= 3\. A partir de ese punto, la curva sigue descendiendo, pero el cambio es menos pronunciado en algunos tramos.  
Por este motivo, se consideró que k \= 3 era una opción razonable, ya que permite formar tres grupos sin aumentar demasiado la cantidad de segmentos.

- ### **Coeficiente de Silhouette**

También se utilizó el coeficiente de Silhouette para comparar los resultados. El valor más alto fue de 0,4610 para k \= 6  
Esto indica que k \= 6 presentó el mejor resultado según esta métrica. Sin embargo, también se tuvo en cuenta la facilidad para interpretar los grupos y el objetivo del trabajo.

## **Comparación entre k \= 3 y k \= 6**

Se compararon ambos modelos para observar las diferencias entre una segmentación más sencilla y otra más detallada.  
Con k \= 3 se obtienen tres perfiles generales de clientes, que resultan más fáciles de describir. En cambio, con k \= 6 se pueden identificar diferencias más específicas.  
Por ejemplo, los clusters 2 y 3 del modelo con seis grupos tienen un ticket promedio cercano a USD 450, pero presentan distintas tasas de devoluciones. Algo similar ocurre con los clusters 1 y 4, que tienen una frecuencia de compra y un ticket promedio similares, pero se diferencian en su sensibilidad a los descuentos.  
De esta manera, k \= 6 permite analizar más detalles, mientras que k \= 3 ofrece una visión más general de los clientes.

## **Elección de k \= 3**

Aunque k \= 6 obtuvo el mejor resultado de Silhouette, se eligió k \= 3 como modelo principal porque el método del codo muestra una disminución importante de la inercia entre k \= 2 y k \= 3\.  
Además, trabajar con tres grupos facilita la interpretación de los resultados y permite describir los principales perfiles de clientes de una manera sencilla. Por lo tanto, se consideró que esta opción era adecuada para el objetivo del trabajo.

## **Análisis de los centroides**

Los centroides permiten observar los valores promedio de las variables en cada grupo y conocer las principales características de los clientes.

* **Cluster 0: clientes frecuentes con ticket medio.** Realizan aproximadamente 12 compras mensuales, con un ticket promedio de USD 180\. Permanecen alrededor de 35 minutos en el sitio y presentan una sensibilidad a los descuentos de 0,54.  
    
* **Cluster 1: clientes con compras poco frecuentes y ticket alto.** Realizan aproximadamente 2 compras mensuales, con un ticket promedio de USD 450\. Permanecen unos 6 minutos en el sitio y presentan una tasa de devoluciones cercana a 0,38.  
    
* **Cluster 2: clientes con ticket bajo y frecuencia intermedia.** Realizan aproximadamente 4 compras mensuales, con un ticket promedio de USD 90\. Permanecen unos 10 minutos en el sitio y presentan una tasa de devoluciones cercana a 0,30.


Estos resultados muestran que los grupos tienen características diferentes en cuanto a la frecuencia y el importe de las compras, el tiempo de permanencia y las devoluciones.

## **Conclusión**

La aplicación de K-Means permitió identificar tres perfiles generales de clientes a partir de sus hábitos de compra y del uso del sitio web.  
Para seleccionar la cantidad de grupos, se compararon los resultados del método del codo y del coeficiente de Silhouette. Aunque este último favoreció a k \= 6, se eligió k \= 3 porque el gráfico del codo mostró una reducción importante de la inercia al pasar de dos a tres grupos y porque esta opción facilita la interpretación de los perfiles.  
En conclusión, la segmentación permitió reconocer diferencias entre clientes frecuentes con ticket medio, clientes que compran con menor frecuencia pero gastan más por compra y clientes con tickets más bajos y una frecuencia intermedia.

