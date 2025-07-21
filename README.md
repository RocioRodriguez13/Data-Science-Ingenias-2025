# Análisis de Distribución y Densidad de Estaciones de Servicio en CABA  

**Proyecto Final – Data Science | Fundación YPF (2025)**  

---

## 📖 Descripción del proyecto  

Este proyecto analiza la **distribución geográfica y la accesibilidad** de las estaciones de servicio en la **Ciudad Autónoma de Buenos Aires (CABA)**.  

El objetivo principal es:  
- Identificar **patrones de concentración**  
- Detectar **zonas con baja cobertura**  
- Evaluar **oportunidades estratégicas** para la expansión comercial  

Comprender la **densidad y distribución espacial** de estos servicios es clave para la **planificación urbana** y el **análisis de mercado**.  

---

## 🗂 Fuente del dataset  

El dataset **`estaciones_servicio_caba.csv`** fue obtenido del portal de **Datos Abiertos de la Ciudad de Buenos Aires**.  
Contiene información geográfica, administrativa y comercial de **230 estaciones de servicio**.  

---

## 🎯 Objetivos del análisis  

1. **Evaluar la distribución y concentración** de estaciones para detectar zonas con alta o baja densidad de cobertura.  
2. **Transformar el problema espacial** en dos enfoques complementarios:  
   - **Aprendizaje supervisado:** Clasificar la densidad de una zona.  
   - **Aprendizaje no supervisado:** Identificar clústeres geográficos para validar y enriquecer los hallazgos.  

---

## 🔍 Metodología  

Se aplicaron técnicas de **Data Science** para obtener una visión integral del problema:  

- **Análisis exploratorio de datos (EDA)**  
- **Ingeniería de variables** para definir indicadores de densidad  
- **Modelado predictivo supervisado** (Random Forest para clasificación)  
- **Clustering no supervisado** (DBSCAN para detectar agrupamientos geográficos)  

---

## 📊 Principales descubrimientos del análisis exploratorio  

- **Dominio de mercado:** YPF y Shell concentran la mayoría de las estaciones, dominando el panorama comercial de la ciudad.  
- **Concentración geográfica:** Alta densidad en comunas del centro y corredor norte (Comunas 1, 3, 5, 6 y 13) y en nodos de alta circulación.  
- **Tipo de servicio:** Predominan las estaciones de combustibles líquidos, seguidas por las duales (líquidos + GNC).  
- **Estaciones sin marca:** Se identificaron 13 estaciones sin bandera comercial definida, analizadas por separado para evitar ruido en los análisis de marca.  

---

## 🤖 Resumen de los modelos aplicados  

### 1. Modelo Supervisado – Clasificación de Densidad  

- **Variable objetivo:** `clase_densidad` (alta, media, baja), calculada a partir de la **distancia promedio a los 3 vecinos más cercanos** usando NearestNeighbors y la métrica Haversine.  
- **Modelos comparados:** Random Forest, Regresión Logística y k-NN.  
- **Selección:** Random Forest por su mejor rendimiento y estabilidad.  
- **Optimización:** GridSearchCV + variables contextuales como comuna, barrio y distancia al centro (`dist_centro_km`).  
- **Resultado clave:** Precisión promedio **64.3%** en validación cruzada, demostrando capacidad para predecir la densidad con datos geográficos y contextuales.  

### 2. Modelo No Supervisado – Clustering Geográfico  

- **Algoritmo:** DBSCAN, ideal para datos espaciales.  
- **Parámetros:** `eps = 0.5 km` y `min_samples = 3`.  
- **Resultados:**  
  - 28 **clústeres de estaciones** identificados  
  - 107 **estaciones aisladas** (ruido)  
- **Conclusión:** Confirmó visualmente las zonas de alta demanda (microcentro) y validó las áreas de baja densidad a través de puntos de ruido.  

---

## ✅ Resultados esperados  

- Visualización de **patrones espaciales** de cobertura  
- Mapas interactivos con zonas de mayor y menor densidad  
- Insights estratégicos para optimizar la ubicación de nuevas estaciones

## 💛 Presentación
- https://gamma.app/docs/Analisis-de-Densidad-y-Clustering-de-Estaciones-de-Servicio-en-CA-yywvfaincusl4c3
