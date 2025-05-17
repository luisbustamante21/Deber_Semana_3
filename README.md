# Segmentación de Clientes de Tarjeta de Crédito

![Badge en Desarrollo](https://img.shields.io/badge/Estado-✔%20Activo-brightgreen) 
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0.2-orange)

Proyecto de análisis no supervisado para segmentar clientes de tarjetas de crédito mediante técnicas de clustering.

## 📌 Tabla de Contenidos
1. [Justificación y Análisis](#1-justificación-y-análisis)  
2. [Introducción del Problema](#2-introducción-del-problema)  
3. [Metodología y Técnicas Aplicadas](#3-metodología-y-técnicas-aplicadas)  
4. [Análisis Comparativo entre Modelos](#4-análisis-comparativo-entre-modelos)  
5. [Conclusiones](#conclusiones)  
6. [Recomendaciones](#recomendaciones)  
7. [Estructura del Proyecto](#estructura-del-proyecto)  
8. [Tecnologías Utilizadas](#tecnologías-utilizadas)  
9. [Autor](#autor)  
10. [Entorno de Trabajo](#entorno-de-trabajo)

---

# 📊 Segmentación de Clientes de Tarjeta de Crédito

## 1. Justificación y Análisis

Este proyecto aplica técnicas de **aprendizaje no supervisado** para segmentar clientes de tarjetas de crédito, con el objetivo de:

- Diseñar estrategias de marketing personalizadas.
- Identificar perfiles de riesgo.
- Optimizar la asignación de límites de crédito y promociones.

Se utilizó un dataset con información de aproximadamente **9,000 clientes activos** durante los últimos seis meses, incluyendo 18 variables que describen su comportamiento financiero: saldo promedio, frecuencia de compras, adelantos en efectivo, pagos mínimos y totales, entre otros.

---

## 2. Introducción del Problema

Las instituciones financieras necesitan segmentar su base de clientes para:

- Enfocar estrategias de **retención y fidelización**.
- **Reducir el riesgo crediticio** adaptando condiciones según perfiles.
- **Mejorar la eficiencia** comercial y operativa.

Dado que no se cuenta con etiquetas previas, se aplican técnicas de **clustering** para identificar grupos de clientes con comportamientos similares.

---

## 3. Metodología y Técnicas Aplicadas

### 📌 1. Preprocesamiento de Datos
- Eliminación de valores nulos y variables irrelevantes.
- Escalado de variables con `StandardScaler`.
- Análisis exploratorio de distribuciones y correlaciones.

### 📌 2. Reducción de Dimensionalidad
- **PCA (Principal Component Analysis)**: Reducción a dos componentes principales para facilitar visualización y uso de DBSCAN.
- **t-SNE (t-distributed Stochastic Neighbor Embedding)**: Técnica no lineal para mejorar la visualización de agrupaciones de K-Means.

### 📌 3. Modelos de Clustering Aplicados
- **K-Means**: Se evaluaron valores de *k* entre 2 y 4. Se seleccionó **k = 3** como óptimo utilizando el Silhouette Score.
- **DBSCAN**: Aplicado sobre los datos reducidos por PCA. Detecta grupos de forma libre y puntos de ruido sin necesidad de fijar *k*.

---

## 4. Análisis Comparativo entre Modelos

| Modelo   | Reducción Dimensional | Parámetros Clave                  | N° Clusters     | Silhouette Score | Observaciones Clave                                                      |
|----------|------------------------|-----------------------------------|------------------|------------------|--------------------------------------------------------------------------|
| K-Means  | PCA                    | `k = 3`                           | 3                | ~0.32            | Clusters bien separados. Requiere definir número de clusters.           |
| DBSCAN   | PCA                    | `eps = 0.25`, `min_samples = 5`   | 2 + ruido        | ~0.23*           | Capta ruido y formas no convexas. Sensible a los parámetros.            |
| t-SNE    | No aplica              | `perplexity = 30`, `learning_rate = 200` | n/a       | n/a              | No realiza clustering, pero mejora la visualización de agrupaciones.    |

> *Silhouette Score aproximado calculado solo para puntos no etiquetados como ruido.

---

## 🧾 Conclusiones

- **K-Means (k=3)** fue el modelo más efectivo y fácil de interpretar para segmentación general.
- **DBSCAN** mostró potencial para detectar **outliers** y grupos no lineales, pero fue más sensible a la elección de parámetros.
- **t-SNE** no se utilizó para clustering directamente, pero fue muy útil para validar visualmente los grupos generados.

---

## ✅ Recomendaciones

- Usar **DBSCAN** en análisis enfocados en detección de anomalías o cuando no se desea definir el número de clusters.
- Complementar **t-SNE** con otras técnicas visuales en presentaciones ejecutivas o para validar agrupaciones.
- Considerar aplicar esta metodología a otras líneas de productos financieros o campañas de marketing.

---

## 📂 Estructura del Proyecto

- `Archivos de datos/` - Dataset de clientes
- `Codigo Fuente (ipynb)/` - Análisis exploratorio y clustering
- `visualizations/` - Gráficos generados con PCA y t-SNE
- `README.md` - Documentación del proyecto


---

## 📌 Tecnologías Utilizadas

- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

---

## ✍️ Autor

**Luis Bustamante**  

---


## 6️⃣ Entorno de Trabajo
```yaml
Sistema Operativo: Windows 11
Python: 3.8.12
Librerías Principales:
  - pandas 1.3.5
  - scikit-learn 1.0.2
  - matplotlib 3.4.3
Herramientas:
  - Jupyter Notebook 6.4.7
  - Git 2.25.1
