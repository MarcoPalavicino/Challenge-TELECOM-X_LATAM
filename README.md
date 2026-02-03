# Telecom X – Análisis de Evasión de Clientes (Churn)

## 📌 Descripción del proyecto

Este proyecto corresponde a un análisis exploratorio de datos (EDA) y proceso ETL enfocado en el estudio de la **evasión de clientes (Churn)** para la empresa ficticia *Telecom X*.  
El objetivo principal es comprender qué factores influyen en la cancelación del servicio por parte de los clientes, utilizando datos reales consumidos desde una API en formato JSON.

El análisis fue desarrollado como parte de un **challenge de Data Science**, siguiendo buenas prácticas de limpieza, transformación, análisis y comunicación de resultados.

---

## 🎯 Objetivo del análisis

- Analizar el comportamiento de los clientes que **cancelan** vs. los que **permanecen**.
- Identificar patrones asociados a:
  - Antigüedad del cliente (tenure)
  - Cargos mensuales y totales
  - Tipo de contrato y servicios
- Generar **insights accionables** que puedan apoyar decisiones de retención.
- Preparar el dataset para futuros **modelos predictivos de churn**.

---

## 🗂️ Estructura del proyecto

El proyecto se encuentra contenido en un único notebook:


Dentro del notebook se desarrollan las siguientes etapas:

1. Contexto del proyecto  
2. Extracción de datos desde API  
3. Inspección inicial del dataset  
4. Limpieza y transformación de datos (ETL)  
5. Análisis Exploratorio de Datos (EDA)  
6. Conclusiones e insights  
7. Recomendaciones estratégicas  

---

## 🔌 Fuente de datos

- **Origen:** API pública en GitHub  
- **Formato:** JSON  
- **Contenido:** Información demográfica, contractual, servicios y estado de evasión de clientes.

Los datos se cargan directamente desde la API utilizando `requests` y se transforman a un `DataFrame` de Pandas mediante `json_normalize`.

---

## 🧹 Limpieza y tratamiento de datos (ETL)

Durante el proceso ETL se realizaron las siguientes acciones:

- Copia de seguridad del dataset original.
- Normalización de columnas de texto (lowercase, eliminación de espacios).
- Identificación y corrección de categorías especiales (ej. *no phone service*).
- Eliminación de registros con **Churn vacío**.
- Conversión de variables numéricas mal tipadas.
- Creación de una columna derivada:
  - **cuentas_diarias** = cargo mensual / 30
- Estandarización de la variable objetivo:
  - `Churn` → `churn_binario` (1 = evasión, 0 = permanencia)

---

## 📊 Análisis Exploratorio de Datos (EDA)

El análisis exploratorio incluye:

- Distribución base de churn.
- Comparación de variables numéricas entre clientes que evaden y los que no:
  - Antigüedad del cliente
  - Cargos mensuales
  - Cargos totales
  - Cuenta diaria
- Estadísticas descriptivas por grupo (media, mediana, percentiles).

Este análisis permitió identificar diferencias claras entre ambos grupos y sentar bases para modelos predictivos futuros.

---

## ⚠️ Complicaciones encontradas durante el desarrollo

Durante el desarrollo del challenge se presentaron algunas dificultades técnicas relevantes:

- Columnas numéricas almacenadas inicialmente como `object`, lo que provocó errores al calcular estadísticas agregadas.
- Advertencias de tipo `SettingWithCopyWarning` al modificar subconjuntos del DataFrame.
- Inconsistencias semánticas en categorías como *no phone service* y *no internet service*.
- Registros con valores vacíos en la variable objetivo `Churn`, que requirieron tratamiento explícito.

Estas situaciones fueron abordadas mediante validación de tipos, uso correcto de `.loc`, estandarización de strings y limpieza controlada de datos.

---

## 📌 Principales conclusiones

- Los clientes que cancelan presentan, en promedio:
  - **Menor antigüedad** en la empresa.
  - **Cargos mensuales más altos**.
- Los contratos de corto plazo y menor vinculación están más asociados al churn.
- La cuenta diaria resulta una métrica útil para comparar el costo percibido del servicio.

---

## 💡 Recomendaciones estratégicas

- Implementar estrategias de retención temprana para clientes con baja antigüedad.
- Evaluar planes con cargos elevados y ofrecer alternativas personalizadas.
- Incentivar contratos de mayor duración.
- Usar las variables analizadas como base para un **modelo predictivo de churn**.

---

## 🛠️ Tecnologías utilizadas

- Python 3
- Pandas
- Requests
- Matplotlib
- Seaborn
- Google Colab
- GitHub

---




