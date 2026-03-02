# Minería de Datos
## Práctica 3 - Deep Learning

**Autores:** Manuel Castillo-Cara / Luis Sarro  
**Curso académico:** 2024/2025  
**Fecha:** Octubre 2024

---

## Introducción
En este documento se propone la tercera actividad de la asignatura Minería de Datos, del Máster en Investigación en Inteligencia Artificial. Esta actividad corresponde a los temas 4 y 5 del contenido de la asignatura. Se asume que el alumnado ha leído el material propuesto en la guía, en concreto los epígrafes 11.1, 11.3 a 11.5 y 11.9.1 de [6] y el capítulo 9 de [5].

El objetivo es poner en práctica los contenidos teóricos relativos a las redes neuronales y el aprendizaje profundo. Lo importante no es tanto resolver el problema como demostrar que se han comprendido e interiorizado los diversos aspectos clave de las técnicas, su implementación y el impacto en los resultados.

## Aprendizaje profundo con Keras
El equipo docente recomienda el uso de **Keras** (sobre Python o R) por su facilidad de uso, aunque no es obligatorio. Se recomienda encarecidamente realizar las prácticas de programación en Python.

Para quienes no tengan experiencia previa, se sugiere seguir el tutorial de clasificación básica con Keras y repetir los pasos con los datos proporcionados. Si se opta por otro software, se sugiere abrir un hilo en el foro para exponer los motivos y ventajas.

## Identificación de granos de polen
La clasificación visual de granos de polen es una tarea difícil que tradicionalmente requiere expertos con microscopio. La automatización de esta tarea ahorraría recursos en campos como:
* Sistemas de información de afecciones alérgicas.
* Reconstrucción paleoclimática.
* Control de calidad en productos de miel.
* Investigaciones forenses y arqueología.

### El problema
Consiste en identificar granos de polen de dos especies de Nueva Zelanda que son morfológicamente muy similares (monádicos, isopolares, angulaperturados, etc.). Existe una leve diferencia en el tamaño promedio y en la forma en vista ecuatorial, pero el solape es considerable, lo que dificulta la distinción humana.

Las imágenes fueron obtenidas con un microscopio especial **Classifynder** (Veritaxa), que recompone una imagen enfocada a partir de múltiples enfoques verticales.

## Especificación de la tarea
Se propone construir un sistema de clasificación automática realizando una serie de experimentos con modelos de complejidad creciente:

1. **NET-1:** Red neuronal sin capa oculta (equivalente a una regresión binomial logística).
2. **NET-2:** Red con una o más capas ocultas.
3. **CNN:** Red Neuronal Convolucional (según el capítulo 9 de [5]).
4. **CNN Variante A:** Modificación del modelo anterior (más capas, tipos de convolución, etc.) justificando la mejora.
5. **CNN Variante B:** Otra modificación diferente para buscar optimización.

Se debe analizar y discutir los resultados y conclusiones de cada modelo.

## Pesos y mapas de características
Utilizando la CNN más sencilla (2 o 3 capas de convolución/pooling), se debe realizar un análisis para entender cómo la red extrae características:

1. **Visualización de pesos:** Usar Matplotlib para visualizar los pesos de las capas de convolución como imágenes.
2. **Visualización de mapas de características:** Extraer y visualizar los mapas generados por las capas de convolución para una o más imágenes de entrada.
3. **Análisis crítico:**
    * ¿Qué patrones se observan en los pesos?
    * ¿Qué características destacan en los mapas y cómo evolucionan a través de las capas?
    * ¿Cómo aprende la red a extraer información relevante?

## Entregable
1. **Memoria (PDF):** Máximo 10 páginas, fuente 12pt. Debe incluir experimentos, conclusiones y figuras clave. Se deben evitar definiciones teóricas genéricas y centrarse en la discusión técnica y justificación de los resultados. Debe incluir una gráfica de la evolución del aprendizaje para todos los modelos con el conjunto de validación.
2. **Notebook (.ipynb):** Con el código fuente y descripciones breves de cada celda.

## Evaluación (Rúbrica)

| Concepto | Puntos |
| :--- | :---: |
| 1. Técnicas de Data Augmentation y su impacto | 1 |
| 2. Descripción y obtención de resultados de los modelos | 5 |
| *2.1. Modelos estándar 1 y 2* | *(1)* |
| *2.2. Modelos 3: CNN (convolución, pooling...)* | *(2)* |
| *2.3. Modelos 4 y 5: CNN con variantes/configuraciones* | *(2)* |
| 3. Análisis crítico de los resultados | 3 |
| *3.1. Análisis general y gráfica* | *(1)* |
| *3.2. Análisis de los pesos* | *(1)* |
| *3.3. Análisis de los mapas de características* | *(1)* |
| 4. Conclusiones | 1 |
| **Total** | **10** |

**Nota mínima para aprobar:** 5 puntos. Se valorará el análisis crítico, el hilo argumental y la corrección orto-tipográfica.

## Referencias
[1] Keras Documentation: https://keras.io/  
[2] How to visualize filters and feature maps: https://machinelearningmastery.com/how-to-visualize-filters-and-feature-maps-in-convolutional-neural-networks/  
[3] TensorFlow Basic Classification: https://www.tensorflow.org/tutorials/keras/classification  
[4] Tutorial Basic Classification (R): https://tensorflow.rstudio.com/tutorials/keras/classification.html  
[5] Ian Goodfellow et al. *Deep Learning*. MIT Press, 2016.  
[6] Trevor Hastie et al. *The Elements of Statistical Learning*. Springer, 2001.
