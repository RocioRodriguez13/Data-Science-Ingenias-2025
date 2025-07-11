
Análisis de Clustering de Estaciones de Servicio en CABA

Este proyecto realiza un análisis de clustering no supervisado para identificar agrupaciones naturales de estaciones de servicio en el mapa de la Ciudad Autónoma de Buenos Aires (CABA).
El objetivo es aplicar el algoritmo DBSCAN para segmentar geográficamente las estaciones, partiendo de la hipótesis de que no se distribuyen de manera uniforme, sino que forman conglomerados en áreas de alta demanda o con características geográficas específicas.

Visualización Clave

El resultado principal del análisis es un mapa de CABA que muestra las estaciones de servicio agrupadas en clusters, cada uno con un color diferente.
Las estaciones que no pertenecen a ningún cluster (puntos de ruido u outliers) se marcan en negro.


Metodología
1. Datos

Se utilizaron los siguientes conjuntos de datos:
Coordenadas geográficas (lat, long) de cada estación de servicio, extraídas de estaciones_servicio_caba.csv.
Datos geoespaciales de las comunas de CABA para la visualización del mapa base, extraídos de comunas.geojson.txt.

2. Algoritmo de Clustering

Se seleccionó el algoritmo DBSCAN (Density-Based Spatial Clustering of Applications with Noise) por sus ventajas para trabajar con datos espaciales:
No asume que los clusters tienen formas esféricas. Es capaz de identificar puntos aislados como ruido, lo cual se alinea con la distribución real de las estaciones.
Su funcionamiento se basa en la densidad, lo que es ideal para encontrar concentraciones en un mapa.

3. Hiperparámetros

Se definieron los siguientes hiperparámetros clave para el modelo:
eps (epsilon): 0.5 km. La distancia máxima entre dos estaciones para que se consideren vecinas. Se eligió un radio de 500 metros como un umbral razonable de "cercanía" en un contexto urbano.

min_samples: 3. El número mínimo de estaciones necesarias para formar un cluster denso. Se decidió que un grupo de al menos 3 estaciones es suficiente para ser considerado un polo de servicio relevante.

metric: 'haversine'. Métrica de distancia optimizada para coordenadas geográficas (latitud/longitud), que calcula la distancia sobre una esfera.

Resultados y Análisis

La aplicación del modelo DBSCAN arrojó los siguientes resultados:
Número de clusters encontrados: 28
Número de puntos de ruido (outliers): 107

El análisis de los clusters revela patrones de distribución interesantes:
Cluster 0 (el más grande): Corresponde a la zona de mayor densidad de estaciones, abarcando principalmente los barrios de Balvanera (7 estaciones) y Almagro (3 estaciones), lo que confirma la alta concentración en el macrocentro de la ciudad.
Clusters más pequeños: Se observan agrupaciones lineales a lo largo de avenidas importantes como Av. Rivadavia o Av. Juan B. Justo, lo que sugiere una estrategia de ubicación a lo largo de corredores de alto tránsito.
Puntos de Ruido: Las estaciones clasificadas como ruido (-1) tienden a ubicarse en zonas de menor densidad poblacional o en los límites de la ciudad, validando los hallazgos de análisis exploratorios previos.

Archivos del Repositorio

Cuarta_entrega.ipynb: Notebook de Jupyter con todo el código del análisis, desde la carga de datos hasta la visualización final.

estaciones_servicio_caba.csv: Dataset con la información de las estaciones de servicio.

comunas.geojson.txt: Archivo GeoJSON con los polígonos de las comunas de CABA.

README.md: Este archivo.
