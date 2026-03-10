# Análisis Metabolómico GC-MS para la Identificación de Biomarcadores Volátiles en Salud Mental

## Introducción

Identificación de los metabolitos son más sensibles al cambio entre condiciones experimentales es el núcleo de este trabajo. Un metabolito sensible es aquel cuya abundancia varía de forma consistente y discriminante entre grupos, independientemente de que esa variación sea de gran magnitud o alcance significación estadística convencional, priorizar estos compuestos permite focalizarnos en ellos de tal manera que se pueda lograr evitar la perdida de aquellos que sean candidatos relevantes para el estudio.

## Qué hace este proyecto

A partir de los resultados del proyecto Analisis-Metabol-mico-Estad-stico-con-Python(https://github.com/inigo-diez/Analisis-Metabol-mico-Estad-stico-con-Python) el proyecto prioriza los metabolitos con alta variabilidad, aquellos que cambian significativamente entre las condiciones experimentales, revelando cómo las condiciones influyen en los perfiles metabólicos. Son estos cambios los que permiten comprobar que compuestos deben ser tratados con mayor cuidado para evitar su pérdida en caso de que sean de importancia y estén relacionados con los trastornos mentales. Por otra parte, también se identifica sus características relacionadas con la salud mental y con la microbiota, información obtenida a partir de la base de datos del proyecto Mental-Health-Biomarkers-Database(https://github.com/inigo-diez/Mental-Health-Biomarkers-Database). 

1. **Ranking integrado de sensibilidad**: cada metabolito recibe una puntuación combinada a partir de cuatro criterios independientes — varianza entre condiciones (40%), magnitud del cambio (30%), importancia SHAP (20%) y significación estadística (10%) — produciendo una lista ordenada de candidatos de mayor a menor relevancia.

2. **Enriquecimiento con base de datos de referencia**: los candidatos se contrastan contra una base de datos curada de ~39.000 compuestos asociados a condiciones de salud mental, incorporando para cada coincidencia la información disponible sobre condiciones asociadas, matriz biológica, método de detección, tipo de evidencia y vínculo microbiano.

---

> Los metabolitos identificados son **candidatos priorizados**, no biomarcadores confirmados. Su validación requiere estudios con mayor tamaño muestral y métodos cuantitativos dirigidos.
