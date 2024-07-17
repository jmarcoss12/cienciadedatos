# Examen Final de Ciencia de Datos para la Economía

Iniciamos cargando el dataset `nba_logreg2.csv` usando la función `pd.read_csv` de la librería pandas. Utilizamos la función `head` para visualizar las primeras 5 filas de nuestro dataframe. Luego, realizamos un análisis estadístico con la función `describe`, que nos proporciona la cantidad de datos, media, desviación estándar, valores mínimos y máximos, y los tres cuartiles de cada columna. Como primer paso, estandarizamos nuestras variables continuas. Creamos un nuevo dataframe aplicando `StandardScaler` y utilizando `fit_transform` para estandarizar los datos. Con los datos ya estandarizados, verificamos si existe alguna relación entre las variables utilizando la correlación de Pearson y generando una matriz de correlación. 

Posteriormente, calculamos el índice de KMO para determinar la idoneidad de nuestras variables para el análisis de componentes principales (PCA). Utilizamos los autovalores del dataframe estandarizado para seleccionar la cantidad de componentes óptimos, seleccionando aquellos con autovalores mayores o iguales a 0,8. De esta forma, determinamos que 4 componentes son adecuados para el PCA. Aplicamos la función `PCA` de sklearn indicando la cantidad de componentes óptimos, entrenamos y transformamos nuestro dataframe normalizado, obteniendo un nuevo dataframe reducido. La varianza explicada por cada componente y la varianza acumulada indican que nuestros 4 componentes explican el 81,7% de la varianza original de los datos. Generamos un dataframe con las componentes calculadas y analizamos la colinealidad usando el método de Pearson.

En la siguiente parte, utilizamos el algoritmo LazyClassifier, que aplica múltiples modelos de clasificación a nuestros datos de manera automatizada. Segmentamos los datos, instanciamos el modelo y este entrena y evalúa varios modelos de clasificación, ordenándolos según su desempeño. Para este análisis, seleccionamos la columna 'TARGET_5Yrs' como variable objetivo, que indica si un jugador ha jugado más de 5 años en la NBA (1) o no (0). El modelo que obtuvo la mejor precisión fue el SGDClassifier. Entre los mejores modelos de clasificación que analizamos están: 

1. Support Vector Machines (SVM), que maximiza el margen entre los vectores de soporte.
2. Logistic Regression, que predice la probabilidad de que una muestra pertenezca a una clase específica.
3. Random Forest Classifier, que combina múltiples árboles de decisión para mejorar la generalización.
4. AdaBoost, que entrena clasificadores débiles secuencialmente, mejorando iterativamente.
5. K-Nearest Neighbors (KNN), que predice basándose en la votación de los vecinos más cercanos.
6. Decision Tree, que clasifica los datos basándose en sus características.
7. XGBoost, que optimiza la precisión mediante árboles de decisión secuenciales y paralelización.

Para la última parte del examen, utilizamos el Random Forest Classifier. Instanciamos el modelo con `RandomForestClassifier`, entrenamos el modelo y generamos predicciones, evaluando el desempeño con una matriz de confusión. Calculamos las métricas del modelo: 

- **Accuracy**: 67% de precisión en las predicciones.
- **Precisión**: El 55% de los datos positivos y el 72% de los datos negativos fueron clasificados correctamente.
- **Recall**: El modelo identifica correctamente el 45% de los jugadores con menos de 5 años y el 79% de los jugadores con más de 5 años en la NBA.
- **F1 Score**: Buen equilibrio entre precisión y recall para jugadores con más de 5 años (75%) y moderado equilibrio para los de menos de 5 años (50%).
- **Cohen Kappa**: Una puntuación de 0.2499, indicando una fiabilidad moderada y superando la coincidencia aleatoria.

En conclusión, aunque el modelo Random Forest Classifier no es perfecto, proporciona predicciones moderadamente buenas para nuestros datos. Existen otros modelos que podrían superar su desempeño, pero este modelo no hace una mala predicción.

