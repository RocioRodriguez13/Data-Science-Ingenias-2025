# Análisis Predictivo de Densidad de Estaciones de Servicio en CABA

Este proyecto de Data Science desarrolla un modelo de aprendizaje supervisado para clasificar y predecir la densidad espacial de estaciones de servicio en la Ciudad Autónoma de Buenos Aires. A través de técnicas de ingeniería de variables, comparación de algoritmos y optimización de hiperparámetros, se transforma un problema geoespacial en una tarea de clasificación robusta y con aplicaciones prácticas.

---

## 1. Resumen del Proyecto

El objetivo principal fue construir un modelo capaz de determinar si una estación de servicio se encuentra en una zona de **alta**, **media** o **baja densidad**, basándose en sus características geográficas y administrativas. El proyecto abarca el ciclo completo de un problema de ciencia de datos:

- **Análisis Exploratorio de Datos (EDA)**: Comprensión inicial de la distribución y características de las 230 estaciones.
- **Ingeniería de Variables**: Creación de una métrica de densidad (`clase_densidad`) utilizando el algoritmo k-Vecinos más Cercanos (k-NN) y la métrica de distancia Haversine.
- **Modelado y Evaluación**: Comparación de múltiples algoritmos de clasificación (Random Forest, Regresión Logística, KNN) mediante validación cruzada.
- **Optimización de Hiperparámetros**: Ajuste fino del mejor modelo (Random Forest) con GridSearchCV para maximizar su rendimiento.
- **Análisis de Errores y Visualización**: Interpretación de los resultados a través de métricas de clasificación, matrices de confusión y mapas de coropletas.

📍 *Ejemplo de visualización generada: Mapa de coropletas mostrando la densidad promedio de estaciones por comuna.*

---

## 2. Metodología y Desarrollo

### Paso 1: Definición de la Variable Objetivo

El dataset no incluía una variable explícita de "densidad". Para resolverlo se definió una métrica:

- **Distancia Promedio a 3 Vecinos Cercanos** (`avg_dist_km_3nn`): Se utilizó la distancia Haversine.
- **Discretización por Cuartiles**:
  - `alta`: Estaciones en el primer cuartil (más próximas).
  - `media`: Entre primer y tercer cuartil.
  - `baja`: Cuarto cuartil (más aisladas).

> ✅ Esto permitió convertir un problema espacial continuo en una clasificación multiclase.

---

### Paso 2: Entrenamiento y Comparación de Modelos

Se entrenaron tres modelos utilizando un pipeline con preprocesamiento y validación cruzada:

| Modelo                | Accuracy Promedio |
|-----------------------|-------------------|
| Random Forest         | 60.9%             |
| K-Nearest Neighbors   | 59.6%             |
| Regresión Logística   | 55.7%             |

🔍 El modelo Random Forest fue seleccionado para la optimización.

---

### Paso 3: Optimización y Evaluación Final

- Se usó **GridSearchCV** con **StratifiedKFold**.
- **Hiperparámetros optimizados**: `n_estimators`, `max_depth`, `min_samples_split`, `max_features`.
- **Resultado final**: Precisión promedio del **64.8%**, con buen desempeño general y errores comunes en zonas de transición geográfica.

---

## 3. Herramientas y Librerías Utilizadas

- **Lenguaje**: Python 3
- **Análisis de Datos**: Pandas, NumPy
- **Machine Learning**: Scikit-learn
  - `NearestNeighbors` (densidad)
  - `RandomForestClassifier`, `LogisticRegression`, `KNeighborsClassifier`
  - `Pipeline`, `ColumnTransformer`, `OneHotEncoder`
  - `GridSearchCV`, `StratifiedKFold`
- **Visualización**: Matplotlib, Seaborn
- **Geoespacial (opcional)**: GeoPandas

---

## 4. Estructura del Repositorio

- `Tercera_pre_entrega (1).ipynb`: Jupyter Notebook con el proceso completo.
- `estaciones_servicio_caba.csv`: Dataset principal.
- `comunas.geojson.txt`: Geometrías de las comunas para visualización.
- `README.md`: Este archivo.

---

## 5. Conclusiones y Próximos Pasos

El modelo Random Forest optimizado predice con éxito la densidad de estaciones de servicio en CABA. El análisis revela patrones geográficos significativos que podrían ser útiles para planificación urbana.



💡 *Este proyecto combina Machine Learning y análisis espacial, ofreciendo una visión práctica sobre la distribución urbana de infraestructura crítica.*
