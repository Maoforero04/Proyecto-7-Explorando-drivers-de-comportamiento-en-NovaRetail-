# Proyecto-7-Explorando-drivers-de-comportamiento-en-NovaRetail-

🎯 Objetivo del proyecto

NovaRetail+ es una plataforma de comercio electrónico en Latinoamérica con millones de usuarios. Para el cierre de 2024, el equipo de Crecimiento y Retención buscó responder la siguiente pregunta de negocio:

¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado (ingreso_anual)?

Este proyecto desarrolla un análisis exploratorio de datos (EDA) de tipo correlacional, no causal, con el fin de:

Diagnosticar la calidad, distribución y consistencia de las variables numéricas, binarias y categóricas del dataset.
Identificar y cuantificar relaciones entre variables de comportamiento del cliente (visitas, compras, publicidad dirigida, satisfacción, membresía premium, dispositivo, región) y el ingreso_anual que generan para la empresa.
Traducir los hallazgos estadísticos en implicaciones de negocio accionables, documentando explícitamente qué se puede y qué no se puede afirmar con este tipo de análisis (correlación ≠ causalidad).

📊 Dataset utilizado

Archivo: novaretail_comportamiento_clientes_2024.csv
Registros: 15,000 clientes, sin valores nulos.
Columnas (12):
Columna	Descripción
id_cliente	Identificador único del cliente
edad	Edad del cliente
nivel_ingreso	Ingreso anual estimado del cliente (personal)
visitas_mes	Número de visitas a la app/sitio web en el mes
compras_mes	Número de compras realizadas en el mes
gasto_publicidad_dirigida	Gasto en anuncios asignado al usuario
satisfaccion	Calificación de satisfacción (escala 1-5)
miembro_premium	Suscripción premium (1 = sí, 0 = no)
abandono	Abandono de la plataforma / churn (1 = sí, 0 = no)
tipo_dispositivo	Dispositivo utilizado (móvil, escritorio, tablet)
region	Región geográfica del cliente (norte, sur, este, oeste)
ingreso_anual	Métrica principal — ingreso (revenue) generado por el cliente para la empresa

🔍 Etapas del análisis

El notebook S8_Student_Version-Project-NovaRetail.ipynb está organizado en 6 secciones:

Sección 1 — Cargar y explorar el dataset: carga del CSV, revisión de tipos de datos, valores faltantes y rangos generales.

Sección 2 — Preparar datos y documentar supuestos: limpieza y corrección de tipos de datos; diagnóstico de variables numéricas, binarias y categóricas; documentación de supuestos del análisis.

Sección 3 — Visualización de relaciones:
Heatmap de correlación entre variables numéricas.
Evaluación razonada de la necesidad (o no) de un scatterplot general.
Scatterplots específicos para los pares de variables con relaciones moderadas o fuertes (ingreso_anual vs compras_mes, ingreso_anual vs visitas_mes).

Sección 4 — Coeficientes de correlación y evidencia numérica:
Correlación de Pearson entre variables numéricas relevantes.
Correlación punto-biserial entre ingreso_anual y variables binarias (miembro_premium, abandono).
V de Cramér entre variables categóricas (tipo_dispositivo vs region).

Sección 5 — Interpretación de resultados para el negocio: hallazgos documentados con evidencia visual, evidencia numérica, interpretación no causal, qué no se puede afirmar, e implicación de negocio para cada relación relevante (p. ej. compras_mes como impulsor directo de ingreso_anual, visitas_mes como relación mediada, independencia entre tipo_dispositivo y region).

Sección 6 — Limitaciones y próximos pasos: reconocimiento honesto de las limitaciones del análisis (correlación vs. causalidad, variables externas no consideradas, naturaleza transversal del dataset) y propuesta de siguientes pasos (segmentación adicional, experimentos A/B, nuevas variables a recolectar).

Librerías utilizadas: pandas, numpy, seaborn, matplotlib, scipy.stats (pointbiserialr, chi2_contingency).

▶️ Cómo ejecutar el notebook

Opción recomendada: Google Colab

Abre Google Colab.
Ve a Archivo > Abrir cuaderno > GitHub, pega la URL de este repositorio y selecciona S8_Student_Version-Project-NovaRetail.ipynb (o usa Archivo > Subir cuaderno si lo tienes descargado localmente).
Sube el archivo novaretail_comportamiento_clientes_2024.csv a la sesión de Colab (panel izquierdo → ícono de carpeta → subir), o móntalo desde Google Drive para persistencia entre sesiones.
Ajusta la ruta de carga del CSV en la celda correspondiente si es necesario (por ejemplo, pd.read_csv("novaretail_comportamiento_clientes_2024.csv")).
Ejecuta las celdas en orden: Entorno de ejecución > Ejecutar todas.

⚠️ Nota metodológica

Este es un análisis correlacional, no causal. Salvo en el caso de compras_mes → ingreso_anual (donde la relación es causal por definición de negocio, ya que el revenue se genera a partir de las compras), el resto de asociaciones encontradas no deben interpretarse como relaciones de causa-efecto sin validación adicional (por ejemplo, mediante experimentos controlados A/B).
