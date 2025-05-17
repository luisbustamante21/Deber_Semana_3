# Segmentación de Clientes de Tarjeta de Crédito

![Badge en Desarrollo](https://img.shields.io/badge/Estado-✔%20Activo-brightgreen) 
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0.2-orange)

Proyecto de análisis no supervisado para segmentar clientes de tarjetas de crédito mediante técnicas de clustering.

## 📌 Tabla de Contenidos
1. [Justificación y Análisis](#-1-justificación-y-análisis)
2. [Problema](#-2-introducción-del-problema)
3. [Metodología](#-3-metodología-y-técnicas-aplicadas)
4. [Resultados](#-4-análisis-comparativo-entre-modelos)
5. [Conclusiones](#-5-conclusiones-y-recomendaciones)
6. [Entorno](#-6-entorno-de-trabajo)

---

## 1️⃣ Justificación y Análisis
El objetivo principal es desarrollar un sistema de segmentación basado en el comportamiento de uso de tarjetas de crédito para:

- Identificar grupos homogéneos según:
  - Nivel de gasto
  - Frecuencia de compras 
  - Uso de adelantos en efectivo
- Optimizar estrategias de marketing
- Gestionar riesgos crediticios

**Dataset utilizado**:  
`Credit Card Dataset for Clustering` con ~9,000 titulares activos y 18 variables comportamentales.

---

## 2️⃣ Introducción del Problema
Los emisores de tarjetas necesitan segmentación para:

✅ Mejorar retención de clientes  
✅ Reducir costos de adquisición  
✅ Ajustar límites de crédito según riesgo  

**Retos principales**:
- Extraer segmentos accionables sin supervisión
- Manejar variables con distintas escalas

---

## 3️⃣ Metodología y Técnicas Aplicadas

### 🔧 Preprocesamiento
- Imputación de valores faltantes
- Tratamiento de outliers
- Escalado de variables (`StandardScaler`/`MinMaxScaler`)
- EDA y análisis de correlaciones

### 📉 Reducción de Dimensionalidad
- PCA para visualización y reducción de ruido

### 🧩 Modelos de Clustering
| Modelo  | Enfoque | Parámetros Clave |
|---------|---------|------------------|
| K-Means | Partición | k ∈ [2,8] (eval. por Inercia/Silhouette) |
| t-SNE   | Reducción no lineal | `perplexity=30`, `learning_rate=200` |
| DBSCAN  | Densidad | `eps=0.5`, `min_samples=5` |

### 📊 Validación
- **Silhouette Score**: Cohesión y separación de clusters
- **Davies-Bouldin Index**: Calidad de particionamiento

---

## 4️⃣ Análisis Comparativo entre Modelos

| Modelo  | Silhouette | DB Index | Ventajas | Desventajas |
|---------|------------|----------|----------|-------------|
| K-Means | 0.32       | 0.85     | Rápido e interpretable | Sensible a outliers |
| t-SNE*  | 0.30       | 0.88     | Captura no-linealidades | Requiere clustering adicional |
| DBSCAN  | 0.25       | 1.10     | Detecta ruido | Difícil calibrar `eps` |

*_t-SNE con clustering posterior_

---

## 5️⃣ Conclusiones y Recomendaciones

### 🎯 Segmentos Identificados
1. Alto gasto + pagos completos
2. Uso moderado + pagos mínimos
3. Alto uso de cash advance
4. Bajo uso + pagos irregulares

### 💡 Recomendaciones
- **Marketing**: Promociones segmentadas (ej: recompensas por cash advance)
- **Riesgo**: Revisar límites para segmento 3
- **Monitoreo**: Reevaluar trimestralmente con nuevos datos

---

## 6️⃣ Entorno de Trabajo
```yaml
Sistema Operativo: Ubuntu 20.04 LTS
Python: 3.8.12
Librerías Principales:
  - pandas 1.3.5
  - scikit-learn 1.0.2
  - matplotlib 3.4.3
Herramientas:
  - Jupyter Notebook 6.4.7
  - Git 2.25.1
