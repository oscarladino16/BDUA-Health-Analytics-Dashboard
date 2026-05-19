# BDUA-Health-Analytics-Dashboard
Métodos Cuantitativos y Cualitativos para los Negocios.
# Inteligencia de Negocios en Salud Pública: Predicción y Cobertura (BDUA)

## Descripción del Proyecto
Este proyecto desarrolla un flujo de trabajo analítico que integra métodos estadísticos, Machine Learning y minería de texto (NLP) para fundamentar la toma de decisiones estratégicas en el sector salud. El objetivo principal es predecir el comportamiento y la volatilidad del estado de afiliación de poblaciones vulnerables utilizando la Base de Datos Única de Afiliados (BDUA) de Colombia, respaldado por un análisis contextual del estado del arte científico.

## Arquitectura del Proyecto (Doble Eje)
1. **Eje de Realidad Operativa (BDUA):** Modelado predictivo de series de tiempo mediante Machine Learning para pronosticar volúmenes de afiliados por grupo etario y condición de vulnerabilidad (`Condición del beneficiario`).
2. **Eje de Contexto Científico (Scopus):** Análisis bibliométrico y de sentimiento (NLP) sobre las tendencias globales en la adopción de analítica de datos para la gestión y aseguramiento en salud pública.

## Cuadro de Mando Integral (Balanced Scorecard - Bottom-Up)
* **Aprendizaje y Crecimiento:** Análisis bibliométrico (Bibliometrix) y de sentimiento (NLP) de la literatura científica en Scopus.
* **Procesos Internos:** Despliegue de modelos de Machine Learning para el forecast de estados de afiliación en la BDUA.
* **Perspectiva del Cliente:** Estabilidad en la cobertura de salud y protección activa de poblaciones en condiciones de riesgo.
* **Perspectiva Financiera:** Proyección y optimización de ingresos por Unidad de Pago por Capitación (UPC) indexada por edad y género.

## Tecnologías Utilizadas
* **Entorno:** Jupyter Notebook (Google Colab / GitHub)
* **Procesamiento de Datos:** Pandas, NumPy
* **NLP & Sentimiento:** Hugging Face (Transformers), Qwen/LLMs
* **Machine Learning & Estadística:** Scikit-Learn, Statsmodels, SciPy (PDF)
* **Bibliometría:** Bibliometrix
* **Visualización:** Matplotlib, Seaborn (Salidas listas para Dashboard)
