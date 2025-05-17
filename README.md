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
5. [Conclusiones](#-conclusiones)  
6. [Recomendaciones](#-recomendaciones)  
7. [Estructura del Proyecto](#-estructura-del-proyecto)  
8. [Tecnologías Utilizadas](#-tecnologias-utilizadas)  
9. [Autor](#-autor)  
10. [Entorno de Trabajo](#6️⃣-entorno-de-trabajo)

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

**Segmentación clara de clientes:**

- El uso de KMeans permitió identificar 3 clusters bien diferenciados de clientes, basados en su comportamiento financiero.
- Estas agrupaciones fueron validadas visualmente mediante PCA y t-SNE, mostrando separación adecuada.
  
**Patrones diferenciados por grupo:**

- Un grupo mostraba bajo uso de la tarjeta, bajos pagos y poco saldo.
- Otro grupo tenía uso moderado, con pagos regulares y saldos manejables.
- El tercer grupo representaba clientes con alto nivel de gasto, mayores compras, pagos y balances altos.

**Transformación logarítmica efectiva:**

- Las variables financieras, al tener una distribución sesgada, se beneficiaron significativamente de la transformación logarítmica.
- Esto mejoró la visualización y la calidad del agrupamiento.

**DBSCAN no fue ideal:**

- Aunque se probó DBSCAN como método alternativo, no generó una segmentación útil en este caso, posiblemente por la dispersión de los datos y la falta de densidad homogénea.

**Relación entre antigüedad y gasto:**

- Se observó que clientes con mayor antigüedad (tenure) tienden a tener mayores niveles de compras promedio, aunque esto depende del cluster.

---

## ✅ Recomendaciones

- Complementar **t-SNE** con otras técnicas visuales en presentaciones ejecutivas o para validar agrupaciones.
  
**Diseñar estrategias personalizadas por cluster:**

- Cluster de usuarios inactivos o de bajo gasto: enviar promociones, aumentar límites o fomentar el uso mediante recompensas.
- Cluster de usuarios intermedios: ofrecer upgrades o productos complementarios.
- Cluster de alto gasto y saldo alto: monitorear riesgo crediticio y ofrecer planes premium o exclusivos.

**Implementar monitoreo continuo:**

- Estos clusters deben actualizarse periódicamente. Los hábitos de los clientes pueden cambiar por contexto económico, cambios personales o por incentivos.

**Integrar este análisis con sistemas CRM:**

- Usar los resultados para alimentar sistemas de marketing, fidelización y gestión de riesgo.

**Ampliar el modelo con nuevas variables:**

- Incluir variables sociodemográficas, canal de contacto, historial de mora, etc., puede enriquecer aún más el análisis.

**Optimizar la asignación de recursos:**

- Al conocer los perfiles de clientes, las campañas de marketing, soporte y cobranza pueden focalizarse y ser más rentables.

---

## 📂 Estructura del Proyecto

- `Archivos de datos/` - Dataset de clientes
- `Codigo Fuente (ipynb)/` - Análisis exploratorio y clustering
- `Visualizaciones exportadas/` - Gráficos generados con PCA y t-SNE
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
