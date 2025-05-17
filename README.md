Segmentación de Clientes de Tarjeta de Crédito
1. Justificación y Análisis
Este proyecto desarrolla un sistema de segmentación de clientes basado en su comportamiento con tarjetas de crédito, para optimizar estrategias de marketing y personalizar ofertas. La segmentación permite:

Identificar grupos homogéneos según nivel de gasto, frecuencia y uso de adelantos.

Definir campañas focalizadas que aumenten la efectividad y reduzcan la tasa de abandono (churn).

Detectar patrones de pago y morosidad para gestionar riesgos crediticios.

Se emplea un Credit Card Dataset for Clustering con ~9,000 titulares activos y 18 variables recolectadas en 6 meses.

2. Introducción del Problema
Los emisores necesitan segmentar clientes para:

Mejorar retención.

Reducir costos de adquisición.

Ajustar límites y condiciones crediticias acorde al riesgo.

El reto: extraer segmentos claros sin supervisión, manejando variables heterogéneas (montos, frecuencias, transacciones).

3. Metodología y Técnicas Aplicadas
Preprocesamiento
Imputación y tratamiento de outliers.

Escalado con StandardScaler / MinMaxScaler.

Análisis exploratorio y correlaciones.

Reducción de Dimensionalidad
PCA para visualización y reducción de ruido.

Modelos de Clustering
K-Means: prueba k=2 a 8, evaluación con Inercia y Silhouette.

t-SNE: reducción no lineal para visualización; clustering sobre el espacio embebido.

DBSCAN: clusters de densidad variable, ajuste de eps y min_samples.

Validación
Silhouette Score.

Davies–Bouldin Index.

4. Resultados y Comparación de Modelos
Modelo	Parámetros Clave	Silhouette Score	DB Index	Ventajas	Desventajas
K-Means	k = 4	0.32	0.85	Rápido, fácil interpretación	Sensible a outliers, requiere k fijo
t-SNE + Clustering	perplexity=30, lr=200	0.30	0.88	Captura relaciones no lineales	No es clustering directo, requiere método adicional
DBSCAN	eps=0.5, min_samples=5	0.25	1.10	Detecta ruido y clusters libres	Difícil calibración en alta dimensión
Jerárquico	Ward, 4 clusters	0.29	0.90	No requiere k previo, dendrograma	Costoso computacionalmente

5. Conclusiones y Recomendaciones
K-Means (k=4) brinda el mejor balance entre cohesión y separación.

Identificación de cuatro segmentos clave:

Clientes con alto gasto y pagos completos.

Usuarios moderados con pagos mínimos frecuentes.

Clientes que utilizan adelantos en efectivo.

Bajo uso de tarjeta y pagos irregulares.

Recomendaciones:

Marketing personalizado para cada segmento (ej. incentivos para usuarios de adelantos).

Revisión de límites y condiciones para segmentos de mayor riesgo.

Reevaluar segmentos trimestralmente incorporando nuevos datos.
