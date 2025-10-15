# 💧 Desafío de Análisis Hídrico: Equilibrio y Gestión del Consumo en Barcelona (Reto 3)

## 🚀 Objetivo del Proyecto

El objetivo principal de este proyecto es transformar datos agregados de consumo de agua en **Inteligencia Operacional**. Utilizamos técnicas avanzadas de **Data Science** y **Machine Learning (Feature Engineering)** para:

1.  **Cuantificar la Presión:** Determinar qué sectores y distritos ejercen la mayor presión (riesgo estructural e intensidad).
2.  **Identificar Anomalías:** Localizar los **focos de ineficiencia** (fugas y usos atípicos) en tiempo real y estacionalmente.
3.  **Proponer Estrategia ODS:** Desarrollar una estrategia de gestión dirigida y eficaz para cumplir con el **ODS 6 (Agua Limpia)** y el **ODS 13 (Acción por el Clima)**.

---

## 📊 Metodología y Técnicas Aplicadas

El análisis se estructuró en tres fases, priorizando la **Intensidad de Uso** sobre el volumen absoluto.

### 1. Indicadores de Riesgo Estructural y Geográfico

Se crearon métricas de negocio para transformar el consumo en riesgo accionable:

* **IIC (Índice de Intensidad de Consumo):** Mide la eficiencia por contador ($\text{L/día/contador}$). Clave para identificar la ineficiencia de las **grandes instalaciones**.
* **RCI (Ratio de Concentración Industrial):** Mide la **saturación** del distrito por consumo industrial (riesgo urbanístico).
* **ACM (Consumo Promedio Primavera):** Mide la intensidad del uso Doméstico/Comercial en el período de máximo estrés estacional.

### 2. Detección Avanzada de Anomalías (ML Indexing)

Se aplicó **Feature Engineering** para crear un "escáner" ML que contextualiza el consumo diario:

* **Indexación:** Se generaron **Ventanas Móviles (Media de 7 días)** y **Variables Retrasadas (Lag 1)**.
* **Validación:** Se calculó el **Z-Score Móvil** como métrica de anomalía, que fue la base para la clasificación final de días atípicos por el modelo **Isolation Forest**.

---

## 🚩 Hallazgos Clave (Insights para la Gestión)

Los resultados identifican los **focos precisos** de intervención:

| Foco de Riesgo | Dónde / Cuándo | Evidencia Cuantitativa | Acción Estratégica |
| :--- | :--- | :--- | :--- |
| **I. Ineficiencia Estructural** | Distritos **3 y 4** | $\text{IIC} > 14,000 \text{ L/día/contador}$ | **Auditoría obligatoria** en la industria de alta intensidad (FIG. 1). |
| **II. Estrés Estacional** | **Primavera** y **Distrito 1** | **ACM Máximo** ($\approx 311$ L/día/contador). | **Activar planes de gestión en Primavera**, dirigidos al Distrito 1. |
| **III. Fallo Sistémico de Red** | **Toda la red** | **55.920 alertas** de código `SALYNFPFMKJN5D2V`. | Investigación urgente para resolver el **fallo de infraestructura** (FIG. 5). |
| **IV. Anomalía Operacional** | **Martes - Jueves** | Picos de demanda confirmados por ML (Z-Score $\approx +1.90$ en días laborables). | Aplicar **tarifas dinámicas** en días pico operativos para aplanar la curva. |

---

## 🛠️ Archivos del Proyecto

* `consumo_agregado.parquet`: **(BASE)** Datos principales de consumo utilizados para todos los cálculos.
* `Fuites`: Datos de alertas de la red utilizados para la **Ineficiencia Directa** (FIG. 5).
* `notebook_final.ipynb`: Notebook de Google Colab con el código completo y las visualizaciones.
