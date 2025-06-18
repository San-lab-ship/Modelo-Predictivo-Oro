# Predicción de la Recuperación de Oro en el Proceso de Purificación

Este proyecto tiene como objetivo desarrollar un modelo de machine learning capaz de predecir la recuperación de oro en dos etapas fundamentales del proceso de producción: rougher y final. La precisión en estas predicciones permite optimizar el rendimiento del proceso industrial y apoyar la toma de decisiones operativas.

---

##  Descripción del Problema

En la industria minera, conocer anticipadamente la eficiencia de recuperación de oro en distintas etapas del proceso de purificación es crucial para mejorar la productividad y reducir costos. Este proyecto busca construir un modelo predictivo que estime con precisión dichos valores, utilizando datos históricos del proceso y diversas características químicas y físicas de los materiales procesados.

---

##  Metodología

### 1. Preparación de los datos
- Limpieza de valores ausentes  
- Conversión de características temporales  
- Selección de variables relevantes para las etapas rougher y final  
- División en conjuntos de entrenamiento (16,860 muestras) y prueba (5,856 muestras), cada uno con 52 características numéricas seleccionadas

### 2. Entrenamiento y validación de modelos
Se entrenaron y evaluaron tres modelos de regresión supervisada:

- Regresión Lineal  
- Árbol de Decisión (`DecisionTreeRegressor`)  
- Bosque Aleatorio (`RandomForestRegressor`)  

Para garantizar la robustez de las métricas, se aplicó validación cruzada con **K-Fold**, lo que permitió obtener una evaluación confiable y reducir el riesgo de sobreajuste.

### 3. Selección y evaluación del modelo final
- El modelo con mejor desempeño en validación fue el **Árbol de Decisión**, con un sMAPE ponderado de **10.4442%**.
- Este modelo fue entonces entrenado con todo el conjunto de entrenamiento (16,860 observaciones) y evaluado con el conjunto de prueba independiente (5,856 observaciones).
- Se calcularon métricas de rendimiento específicas para ambas etapas del proceso: rougher y final.

---

# Resultados

Durante el entrenamiento, se aplicó validación cruzada con K-Fold para garantizar métricas robustas. Los resultados del sMAPE final ponderado para cada modelo fueron los siguientes:

| Modelo                  | sMAPE ponderado en validación (%) |
|-------------------------|------------------------------------|
| Regresión Lineal        | 13.3409                            |
| Bosque Aleatorio        | 11.9303                            |
| Árbol de Decisión       | **10.4442**                        |

El modelo con mejor desempeño fue el **Árbol de Decisión**, por lo que se seleccionó como modelo final.

Posteriormente se ajustó con el conjunto de entrenamiento completo (16,860 muestras y 52 características) y se evaluó con datos no vistos del conjunto de prueba (5,856 muestras y 52 características), obteniendo los siguientes resultados:

| Métrica                  | Valor (%)    |
|--------------------------|--------------|
| sMAPE etapa rougher      | 13.8283      |
| sMAPE etapa final        | 16.6869      |
| **sMAPE ponderado final**| **15.9722**  |

El modelo **Decision Tree Regressor** proporciona una estimación precisa y confiable en ambas etapas del proceso, incluso frente a datos no vistos, demostrando su potencial para ser aplicado en entornos reales de producción minera.


# Tecnologías Utilizadas

- Python 3.10  
- Pandas  
- NumPy  
- Scikit-learn  
- Matplotlib / Seaborn  
- Jupyter Notebook

---

## Estructura del Proyecto

modelo-predictivo-oro/
│
├── data/ # Archivos de datos (entrenamiento y prueba)
├── notebooks/ # Análisis exploratorio y desarrollo de modelos
├── models/ # Modelos entrenados y serializados (opcional)
├── utils/ # Funciones auxiliares para preprocesamiento, métricas, etc.
├── README.md # Este archivo
└── requirements.txt # Dependencias del proyecto


---

## Conclusión

El modelo desarrollado en este proyecto demuestra una alta efectividad para predecir la recuperación de oro en las etapas **rougher** y **final** del proceso de purificación. Luego de comparar múltiples enfoques, el **Árbol de Decisión** se destacó por su precisión y simplicidad, logrando un **sMAPE ponderado final de 15.9722%** al ser evaluado con datos no vistos.

Este desempeño, junto con una preparación rigurosa de los datos y una validación robusta, convierte al modelo en una herramienta confiable para su futura integración en sistemas de monitoreo industrial. Su implementación permitiría **optimizar procesos operativos, reducir pérdidas y mejorar la eficiencia en plantas de procesamiento de minerales**.


