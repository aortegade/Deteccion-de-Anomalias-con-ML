# Deteccion-de-Anomalias-con-ML

## Descripción
La Detección de Anomalías en el Análisis de Comportamiento de Usuario (UEBA) es un campo crucial en ciberseguridad. Este proyecto se centra en identificar patrones inusuales o actividades sospechossas de usuarios dentro de una red organizacional utilizando técnicas de aprendizaje automático. La detección temprana de anomalías permite una respuesta proactiva antes posibles incidentes de ciberseguridad.

## Conjunto de Datos
Se ha empleado el conjunto de datos CERT r4.2., de la universidad Carnegie Mellon. Para que se ejecute el código correctamente, es necesario que los ficheros del dataset se encuentren en el directorio 'data'.

El conjunto de datos se ha capturado en forma de grafo, y posteriormente se han extraído métricas de red, a fin de añadir nuevas características. El código se encuentra en el directorio 'processing'.

## Preprocesamiento
Tanto las tareas de limpieza, transformación e ingeniería de características se encuentran en los notebooks del directorio 'processing'.

## Experimentación
A continuación se detallan los algoritmos empleados. El ajuste de hiperparámetros se ha realizado mediante GridSearchCV, aplicando también Cross-Validation.
El código se encuentra en el directorio 'model'. 

### Algoritmos de detección de anomalías
Se tratan de algoritmos de aprendizaje no supervisado que pretenden aislar los valores atípicos de aquellos que se consideren normales tras el entrenamiento. Son los siguientes:

- Isolation Forest (IF)
- One-Class SVM (OCSVM)
- Density-Based LOF (DBLOF)

### Algoritmos de clasificación
Como norma general, los algoritmos de aprendizaje tienden una tendencia natural hacia la clase mayoritaria. En conjuntos de datos desbalanceados, esto presenta un problema. Se ha implementado la técnica de sobremuestreo SMOTE para rebalancear el conjunto. Se emplearon hasta un total de tres algoritmos de aprendizaje supervisado:

- Random Forests (RF)
- Máquinas de Soporte Vectorial (SVM)
- Gradient Boosting (GB): se entrena con la entrada de las predicciones de IF, DBLOF y RF.

## Evaluación de los Modelos
Se ha comparado el rendimiento de los modelos usando la métrica F1-Score por clases. Además, se ha utilizado la métrica AUC para medir la capacidad de discriminación del modelo.
