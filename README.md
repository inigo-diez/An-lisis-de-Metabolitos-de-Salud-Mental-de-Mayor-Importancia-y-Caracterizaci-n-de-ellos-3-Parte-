# Análisis Metabolómico GC-MS para la Identificación de Biomarcadores Volátiles en Salud Mental

## Introducción

Los trastornos mentales representan una de las principales causas de discapacidad a nivel mundial, y su diagnóstico sigue dependiendo casi exclusivamente de criterios clínicos subjetivos. La ausencia de biomarcadores objetivos y reproducibles limita tanto la capacidad diagnóstica como el seguimiento terapéutico en condiciones como la depresión, la esquizofrenia, el trastorno bipolar o el autismo.

En este contexto, la metabolómica volátil emerge como una aproximación prometedora. Los compuestos orgánicos volátiles son metabolitos de bajo peso molecular que reflejan el estado metabólico del organismo en tiempo real y pueden detectarse de forma no invasiva en matrices biológicas como el aliento, el plasma o las heces. Muchos de estos compuestos tienen origen microbiano o son producto del metabolismo intermediario, lo que los conecta directamente con el eje microbiota-intestino-cerebro, una de las vías de investigación más activas en psiquiatría translacional.

La cromatografía de gases acoplada a espectrometría de masas (GC-MS) es la técnica de referencia para la detección e identificación de COVs, gracias a su alta sensibilidad, resolución y capacidad de anotación mediante comparación espectral con bases de datos. Sin embargo, el análisis de los datos generados por GC-MS presenta retos considerables: alta dimensionalidad, presencia de contaminantes instrumentales, valores ausentes con significado biológico y heterogeneidad entre muestras que puede enmascarar señales reales.

Identificar **qué metabolitos son más sensibles al cambio entre condiciones experimentales** es el núcleo de este trabajo. Un metabolito sensible es aquel cuya abundancia varía de forma consistente y discriminante entre grupos, independientemente de que esa variación sea de gran magnitud o alcance significación estadística convencional. Priorizar estos compuestos permite focalizar los recursos de validación en las señales con mayor potencial biomarcador, evitando tanto la pérdida de candidatos relevantes por criterios estadísticos demasiado rígidos como la inclusión de señales espurias por criterios demasiado laxos.

## Qué hace este proyecto

A partir de datos crudos de GC-MS obtenidos en 17 experimentos, el proyecto implementa un pipeline completo de análisis metabolómico que cubre desde la limpieza de datos hasta la priorización de candidatos y su contraste con la literatura en salud mental:

1. **Limpieza y control de calidad**: eliminación de contaminantes instrumentales comunes (silanos, siloxanos, derivados TMS, oximas) y selección de los 279 picos con calidad espectral suficiente (Match Factor ≥ 700).

2. **Preprocesamiento**: transformación logarítmica (log₂), detección de muestras atípicas con Isolation Forest y escalado robusto.

3. **Clustering no supervisado** (K-Means y jerárquico) para descubrir la estructura natural de los grupos experimentales, incluyendo un análisis refinado tras la exclusión de outliers.

4. **Análisis estadístico diferencial** con pruebas no paramétricas (Mann-Whitney U, Kruskal-Wallis) y corrección FDR, junto con el cálculo de fold change entre condiciones.

5. **Modelado supervisado** con Random Forest y XGBoost (validación LOO-CV) y análisis de importancia de características con SHAP para identificar los metabolitos más discriminantes.

6. **Ranking integrado de sensibilidad**: cada metabolito recibe una puntuación combinada a partir de cuatro criterios independientes — varianza entre condiciones (40%), magnitud del cambio (30%), importancia SHAP (20%) y significación estadística (10%) — produciendo una lista ordenada de candidatos de mayor a menor relevancia.

7. **Enriquecimiento con base de datos de referencia**: los candidatos se contrastan contra una base de datos curada de ~39.000 compuestos asociados a condiciones de salud mental, incorporando para cada coincidencia la información disponible sobre condiciones asociadas, matriz biológica, método de detección, tipo de evidencia y vínculo microbiano.

---

> **Nota metodológica:** Los metabolitos identificados son **candidatos priorizados**, no biomarcadores confirmados. Su validación requiere estudios con mayor tamaño muestral y métodos cuantitativos dirigidos.
