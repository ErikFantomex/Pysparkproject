# Proyecto Big Data con Spark
Proyecto de Big Data con el objetivo de utilizar PySpark.

# Competencia de Kaggle
Se le proporcionan datos históricos de ventas diarias. La tarea consiste en prever la cantidad total de productos vendidos en cada tienda para el conjunto de pruebas. Tenga en cuenta que la lista de tiendas y productos cambia ligeramente cada mes. Crear un modelo robusto que pueda manejar estas situaciones es parte del reto.

# ¿Para qué utilizamos PySpark?
A lo largo del proyecto se utilizó PySpark para paralelizar todas las acciones correspondientes a la lectura de los datos, así como todo el preprocesamiento que se les aplicó antes de emplearlos en el entrenamiento de regresión lineal y Random Forest Regression que vienen también incluidos dentro de la paquetería de Spark para Python, para finalmente obtener una predicción haciendo uso del paralelizar los procesos posibles a lo largo de su desarrollo.

# ¿Qué hicimos?
Predecir primero el nivel superior. (Por ejemplo: predecir primero las ventas totales)
A continuación, calcule las ponderaciones que denotan la proporción de las ventas totales que hay que dar a la previsión del nivel básico (Ej:) la contribución de las ventas del artículo a las ventas totales
Hay diferentes maneras de llegar a los "pesos".
 - **Proporciones medias históricas** - Media simple de la contribución del artículo a las ventas en los últimos meses
 - **Proporción de medias históricas** - La ponderación es la relación del valor medio de la serie inferior por el valor medio de la serie total (Ej: Ponderación(artículo1)= media(artículo1)/media(ventas_total))
 - **Proporciones previstas** - Predecir la proporción en el futuro utilizando los cambios en las proporciones pasadas
Utilice estas ponderaciones para calcular las previsiones base y otros niveles.

# Conclusiones
El modelo de regresión Random Forest es mejor que el modelo de regresión lineal. Todavía hay muchas cosas que se pueden mejorar para obtener mejores predicciones, como por ejemplo
 - Utilizar un rango de valores atípicos más estricto (de recuento de ventas y precios de artículos),
 - Rellenar los datos que faltan con la media o la mediana del producto en todos los meses en lugar de sólo 0,
 - Diseñar más características basadas en el retardo y en la ventana móvil, Crear un modelo de conjunto utilizando muchos modelos de regresión diferentes,
 - Utilizar la biblioteca statsmodel para extraer la tendencia y la estacionalidad más precisas de las series temporales para utilizarlas como características,
 - Usar un algoritmo de ajuste de hiperparámetros, PySpark sólo soporta K-Fold Cross Validation, que no es adecuado para problemas de previsión de series temporales,
 - Utilizar una red neuronal recurrente como LSTM en lugar de convertir este conjunto de datos en un problema de regresión.
