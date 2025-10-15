#  Desafío de Análisis Hídrico: Equilibrio y Gestión del Consumo en Barcelona (Reto 3)

##  Objetivo del Proyecto

El objetivo principal de este proyecto es transformar datos agregados de consumo de agua en **Inteligencia Operacional** para la gestión sostenible. Se utilizaron técnicas de análisis avanzado y creación de métricas de negocio para:

1.  **Cuantificar la Presión:** Determinar qué sectores y distritos ejercen la mayor presión (riesgo estructural e intensidad).
2.  **Identificar Ineficiencia:** Localizar los **focos de pérdida** y **usos atípicos** en tiempo y geografía.
3.  **Proponer Estrategia ODS:** Desarrollar una estrategia de gestión dirigida y eficaz para cumplir con el **ODS 6 (Agua Limpia)** y el **ODS 13 (Acción por el Clima)**.

---

##  Metodología y Técnicas Aplicadas

La gestión de datos se centró en la creación de **Indicadores de Intensidad (IIC/ACM)**, que permiten dirigir los recursos de auditoría a las zonas de mayor riesgo por unidad de consumo, superando el análisis tradicional basado en volumen.

### 1. Indicadores de Riesgo Estructural (Presión y Concentración)

* **IIC (Índice de Intensidad de Consumo):** Mide la eficiencia por contador ($\text{L/día/contador}$). Clave para identificar la **ineficiencia de las grandes instalaciones** (Foco: Distritos 3 y 4).
* **RCI (Ratio de Concentración Industrial):** Mide la **saturación urbanística** del distrito por consumo industrial (Foco: Distritos 3 y 4).
* **ACM (Consumo Promedio Primavera):** Mide la **intensidad del uso Doméstico/Comercial** durante el período de máximo estrés estacional (Foco: Distrito 1).

### 2. Análisis Temporal y de Eficiencia Directa

Se desglosó la serie temporal para entender el "cuándo" de la crisis:

* **Pico Estacional:** Identificación de la **Primavera** como el periodo de máximo estrés total.
* **Pico Operativo:** Localización del pico de demanda industrial/comercial en los días **Martes a Jueves**.
* **Fugas Sistémicas:** Cuantificación de las alertas de fallo de red (`Fuites`) como la fuente principal de ineficiencia.

---

##  Hallazgos Clave y Estrategia Final

El análisis valida una estrategia de intervención quirúrgica basada en la intensidad de uso.

| Foco de Riesgo | Dónde / Cuándo | Evidencia Cuantitativa | Acción Estratégica |
| :--- | :--- | :--- | :--- |
| **I. Ineficiencia Estructural** | Distritos **3 y 4** | $\text{IIC Industrial} \approx 16,200 \text{ L/día/contador}$ | **Auditoría obligatoria** en la industria de alta intensidad (FIG. 1). |
| **II. Estrés Estacional** | **Primavera** y **Distrito 1** | **ACM Máximo** ($\approx 311$ L/día/contador). | **Activar planes de gestión en Primavera**, dirigidos al Distrito 1. |
| **III. Fallo Sistémico de Red** | **Toda la red** | **55.920 alertas** de código `SALYNFPFMKJN5D2V`. | Investigación urgente para resolver el **fallo de infraestructura** (FIG. 5). |
| **IV. Picos Operacionales** | **Martes - Jueves** | Picos de demanda máxima entre Martes y Jueves (FIG. 4). | Aplicar **tarifas dinámicas** a grandes usuarios en días pico. |

---

##  Archivos del Proyecto

* `consumo_agregado.parquet`: **(BASE)** Datos principales de consumo.
* `Fuites`: Datos de alertas de la red utilizados para la **Ineficiencia Directa** (FIG. 5).
* `[...].ipynb`: Notebook de Google Colab con el código completo y las visualizaciones.
