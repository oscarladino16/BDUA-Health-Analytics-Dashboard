# Dashboard de Inteligencia de Negocios: Analítica en Salud Pública

**Universidad Nacional Abierta y a Distancia (UNAD)**

**Curso:** Métodos Cuantitativos y Cualitativos para los Negocios (107071)

**Fase 4:** Diseño y construcción de dashboard de inteligencia de negocios

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/oscarladino16/BDUA-Health-Analytics-Dashboard/blob/main/BDAU_Analytics.ipynb)

### 📊 Cuadro de Mando Integral (Balanced Scorecard) - KPIs y Metas

| Nivel Estratégico | KPI | Descripción | Meta (Target) |
| :--- | :--- | :--- | :--- |
| **Aprendizaje y Crecimiento** | **KPI 1: Sentimiento de Innovación** | Índice de favorabilidad NLP en literatura científica sobre analítica en salud. | **> 70%** (Sentimiento Positivo) |
| **Aprendizaje y Crecimiento** | **KPI 2: Focos de Atención Demográfica** | Identificación algorítmica de los grupos poblacionales más estudiados. | **Top 2** (Mapeo estricto de Género y Edad) |
| **Procesos Internos** | **KPI 3: Precisión del Forecast Demográfico** | Tasa de asertividad del modelo de Machine Learning al pronosticar estados de afiliación. | **> 85%** (Accuracy algorítmico) |
| **Procesos Internos** | **KPI 4: Eficiencia en Depuración** | Identificación automatizada de registros atípicos (fallecidos/retirados) en la BDUA. | **100%** (Detección previa a auditoría) |
| **Perspectiva del Cliente** | **KPI 5: Estabilidad de Cobertura** | Tasa de usuarios con cobertura activa garantizada frente al riesgo de inestabilidad. | **> 95%** (Afiliados en estado ACTIVO) |
| **Perspectiva del Cliente** | **KPI 6: Garantía de Afiliación Vulnerable** | Identificación de población asegurada bajo categorías prioritarias de protección especial. | **100%** (Aislamiento algorítmico del clúster) |
| **Perspectiva Financiera** | **KPI 7: Proyección de Ingresos UPC** | Consolidación de la base capitable clasificada por grupos etarios y género. | **100%** (Conciliación de datos a reportar) |
| **Perspectiva Financiera** | **KPI 8: Mitigación de Pagos Indebidos** | Prevención de glosas financieras cuantificando registros inactivos y el valor proxy de la UPC. | **Reducción a $0 COP** (Exposición a glosas por lote analizado) |


### Nivel 1: Perspectiva de Aprendizaje y Crecimiento (La Base Analítica)
* **Estrategia:** Comprender, mediante la revisión científica global, el impacto de las variables demográficas en los sistemas de aseguramiento y validar el uso de algoritmos predictivos para la gestión de salud pública.
* **KPI 1 (Sentimiento de Innovación en Salud Pública):** Índice de favorabilidad obtenido mediante NLP en los resúmenes científicos (*abstracts*) respecto a la adopción de análisis de datos. 
    * *Resultado del Proyecto:* **70.77% de sentimiento Positivo/Innovador**, demostrando un consenso científico absoluto sobre la viabilidad de estas tecnologías.
* **KPI 2 (Focos de Atención Demográfica):** Identificación de los grupos demográficos más estudiados globalmente, extraídos a través del mapeo de redes de co-ocurrencia con Bibliometrix en R. Las variables clave validadas son: *Female, Male, Adult, Middle Aged, Aged*.

### Nivel 2: Perspectiva de Procesos Internos (La Operación del Modelo)
* **Estrategia:** Desplegar un modelo de Machine Learning de series de tiempo sobre la BDUA para automatizar el pronóstico de transiciones en la variable *Estado del afiliado* (ej. de Activo a Retirado o Suspendido).
* **KPI 3 (Precisión del Forecast Demográfico):** Tasa de asertividad (minimización del error mediante métricas como el MAPE) del modelo predictivo al pronosticar el volumen de afiliados a corto y mediano plazo.
* **KPI 4 (Eficiencia en Depuración de Datos):** Volumen de registros atípicos o inconsistentes (ej. afiliados marcados como fallecidos pero aún activos) identificados proactivamente por el algoritmo antes de los ciclos de auditoría tradicionales.

### Nivel 3: Perspectiva del Cliente (El Afiliado al Régimen Subsidiado)
* **Estrategia:** Traducir la precisión de los datos en estabilidad real para el usuario. Utilizar las predicciones del modelo para evitar que los afiliados en condiciones críticas pierdan su cobertura por fricciones administrativas.
* **KPI 5 (Estabilidad de Cobertura):** Tasa de precisión en la predicción de usuarios que caerán del estado "Activo" a estados inactivos ("Retirado", "Suspendido"), permitiendo acciones preventivas de retención.
* **KPI 6 (Garantía de Afiliación Vulnerable):** Diferencia entre el volumen pronosticado (output del modelo de ML) y el volumen real de personas aseguradas bajo categorías prioritarias en la columna *Condición del beneficiario* (ej. "MADRES COMUNITARIAS", "POBLACIÓN INFANTIL A CARGO DEL ICBF").

### Nivel 4: Perspectiva Financiera (Sostenibilidad y Capitación)
* **Estrategia:** Dado que los ingresos de las EPS en Colombia dependen de la Unidad de Pago por Capitación (UPC) —la cual varía según la edad y el género—, se usa el modelo predictivo de la BDUA para proyectar y proteger los ingresos operacionales futuros.
* **KPI 7 (Precisión en Proyección de Ingresos UPC):** Desviación porcentual entre los afiliados "Activos" proyectados por el modelo de ML (agrupados por Grupo etario y Género) y los afiliados "Activos" reales que efectivamente generarán un pago de capitación para la entidad.
* **KPI 8 (Mitigación de Pagos Indebidos):** Volumen de afiliados predichos correctamente por el modelo en estado "Fallecido" o "Retirado", lo que permite a la entidad depurar la base de datos a tiempo y evitar sanciones o devoluciones financieras al sistema general de seguridad social.

---

## 3. Arquitectura del Flujo Analítico y Estructura del Código

El proyecto está diseñado para ejecutarse de forma políglota dentro de un único Jupyter Notebook (`Dashboard_Fase4.ipynb`), orquestando entornos de **Python 3.12** y **R** de manera coordinada.

### Estructura de Componentes en el Notebook:
1.  **Ingesta Automatizada de Datos (API SODA - Colombia):** Conexión directa al endpoint JSON (`https://www.datos.gov.co/resource/d7a5-cnra.json`) utilizando la librería `requests` de Python, parametrizando la carga para superar las restricciones de paginación por defecto.
2.  **Análisis Bibliométrico Avanzado (Motor de R):** Configuración del entorno del sistema operativo Linux (instalación de dependencias críticas como `libpoppler-cpp-dev` y `libcurl4-openssl-dev`) para permitir la compilación nativa del paquete científico `bibliometrix` de R directamente desde una celda empleando el comando mágico `%%R`.
3.  **Procesamiento de Lenguaje Natural (NLP - Python):** Implementación del algoritmo VADER a través de `nltk` para analizar de manera automatizada el corpus de resúmenes científicos de Scopus, calculando la métrica normalizada de score *Compound* para categorizar la favorabilidad de la innovación.
4.  **Modelado Predictivo de Series de Tiempo (ML - Scikit-Learn):** Extracción de la serie histórica de producción, transformación mediante `PolynomialFeatures` (Grado 2) para capturar tendencias no lineales, y ajuste de una `LinearRegression` para proyectar el volumen de investigación hacia el año 2030.
5.  **Validación Estadística (Scipy):** Cálculo de la Función de Densidad de Probabilidad (PDF) normal de los datos históricos para contrastar las proyecciones algorítmicas con la distribución de probabilidad matemática real.

---

## 4. Instrucciones de Reproducibilidad

Para garantizar que este flujo de trabajo sea completamente reproducible por el docente o cualquier científico de datos, siga los siguientes pasos:

1.  **Clonar el Repositorio:**
    ```bash
    git clone [https://github.com/oscarladino16/BDUA-Health-Analytics-Dashboard.git](https://github.com/oscarladino16/BDUA-Health-Analytics-Dashboard.git)
    cd BDUA-Health-Analytics-Dashboard
    ```
2.  **Preparación de Archivos:** Asegúrese de colocar los archivos `scopus.csv` y `AnnualSciProd.csv` en la misma raíz del directorio de ejecución (o súbalos a la ruta `/content/` si está ejecutando en Google Colab).
3.  **Ejecutar el Notebook:** Abra el archivo `Dashboard_Fase4.ipynb` en su entorno interactivo y ejecute las celdas secuencialmente. El mismo script se encargará de configurar las librerías del sistema Linux y descargar los lexicones de NLP de forma automatizada.


### Visualizaciones de Bibliometrix

A continuación, se presentan los hallazgos visuales de la literatura científica global extraídos de Scopus. Puedes hacer clic en los enlaces para acceder a los archivos interactivos o revisarlos directamente abajo:

* 🔗 **[Ver Producción Científica Anual](./AnnualSciProd.png)**AnnualSciProd.png
* 🔗 **[Ver Mapa Temático](./ThematicMap.png)** 
* 🔗 **[Ver Nube de Palabras (Word Cloud)](./WordCloud.png)** 

---

#### 1. Producción Científica Anual
*(Evidencia del crecimiento exponencial en la adopción algorítmica dentro del sector salud)*
![Producción Científica Anual](./img/annualsciprod.png)

#### 2. Mapa Temático
*(Análisis de densidad y centralidad de los focos demográficos de investigación)*
![Mapa Temático](./img/ThematicMap.png)

#### 3. Nube de Palabras Clave
*(Visualización de las frecuencias de segmentación basadas en género y edad)*
![Nube de Palabras Clave](./img/WordCloud.png)


## Cuadro de Interpretación Estratégica AI
El cuadro de texto interactivo embebido en el dashboard concluye lo siguiente:
> *"El análisis de procesamiento de lenguaje natural sobre la literatura reciente revela un **70.77% de sentimiento Positivo/Innovador**. Esto indica una sólida confianza académica global en el uso de analítica avanzada para resolver problemas de salud pública. Cruzando esto con los modelos de Machine Learning entrenados, se proyecta un crecimiento exponencial que superará las **900 publicaciones anuales para el 2030**, teniendo como focos analíticos principales las variables de género y rango etario. Esta fundamentación teórica y matemática valida la urgencia estratégica de implementar modelos predictivos sobre la BDUA local para salvaguardar la sostenibilidad financiera de las EPS y mitigar la desprotección de los afiliados vulnerables."*
"""

