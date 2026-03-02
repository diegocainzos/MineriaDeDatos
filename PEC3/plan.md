# Plan de Trabajo - PEC3: Deep Learning (Clasificación de Polen)

Basado en las especificaciones del enunciado, este es el plan paso a paso para resolver la PEC3 utilizando PyTorch (dado que ya hemos configurado el entorno con esta librería).

## Fase 1: Preparación de Datos y Data Augmentation (Valor: 1 punto)
1. **Carga de Datos:**
   - Utilizar `torchvision.datasets.ImageFolder` para cargar las imágenes desde `dataset/anuka1200`.
   - Dividir el dataset en conjuntos de Entrenamiento (Train), Validación (Validation) y Prueba (Test).
2. **Data Augmentation:**
   - Definir transformaciones básicas (redimensionar, convertir a tensor, normalizar).
   - Definir transformaciones de *Data Augmentation* (rotaciones, volteos horizontales/verticales, cambios de brillo, etc.) para el conjunto de entrenamiento.
3. **Análisis:**
   - Evaluar teórica y empíricamente cómo el *Data Augmentation* impacta en la generalización del modelo (evitar overfitting).

## Fase 2: Implementación de Modelos (Valor: 5 puntos)
Se deben construir, entrenar y evaluar 5 modelos de complejidad creciente. Para cada uno, se debe registrar la pérdida (loss) y precisión (accuracy) tanto en entrenamiento como en validación.

*   **Paso 2.1: Modelos Estándar (1 punto)**
    *   **NET-1 (Regresión Logística):** Red neuronal sin capas ocultas. Un modelo lineal simple (`nn.Linear(input_size, 2)`).
    *   **NET-2 (Perceptrón Multicapa - MLP):** Red neuronal con al menos una capa oculta (ej. `nn.Linear` -> `ReLU` -> `nn.Linear`).
*   **Paso 2.2: Red Neuronal Convolucional Base (2 puntos)**
    *   **CNN (Modelo 3):** Una CNN sencilla con 2 o 3 capas de convolución (`nn.Conv2d`) y agrupamiento (`nn.MaxPool2d`), seguidas de capas lineales.
*   **Paso 2.3: Variantes y Optimización de la CNN (2 puntos)**
    *   **CNN Variante A (Modelo 4):** Modificar la CNN base (ej. añadir más capas, cambiar el tamaño del kernel, añadir *Dropout* o *BatchNorm*). Justificar por qué se espera una mejora.
    *   **CNN Variante B (Modelo 5):** Probar otra configuración distinta buscando optimizar el rendimiento y comparar.

## Fase 3: Análisis de Pesos y Mapas de Características (Valor: 3 puntos)
Utilizando la CNN base (Modelo 3), se debe "abrir la caja negra" para entender qué está aprendiendo la red.

1. **Visualización de Pesos (1 punto):**
   - Extraer los tensores de pesos de las capas convolucionales (`model.conv1.weight.data`).
   - Usar `matplotlib` para visualizar estos filtros como imágenes.
   - *Análisis:* ¿Qué patrones básicos (bordes, colores, texturas) parecen estar detectando estos filtros?
2. **Visualización de Mapas de Características (1 punto):**
   - Pasar una imagen (o varias) por la red y capturar la salida *después* de cada capa convolucional/pooling (se pueden usar *hooks* en PyTorch o crear un modelo truncado).
   - Visualizar estas activaciones.
3. **Análisis Crítico (1 punto):**
   - Discutir cómo evolucionan las características desde las primeras capas (detectores de bajo nivel) hasta las últimas (conceptos más abstractos).
   - Evaluar cómo la red aprende a distinguir entre *Kunzea* y *Lepto*.

## Fase 4: Resultados y Conclusiones (Valor: 1 punto + Entregables)
1. **Gráficas de Evolución:**
   - Generar gráficas superpuestas comparando la evolución del aprendizaje (Loss y Accuracy vs. Epochs) en el conjunto de validación para **los 5 modelos**.
2. **Conclusiones:**
   - Sintetizar los hallazgos: ¿Cuál modelo funcionó mejor y por qué? ¿Valió la pena la complejidad extra de las CNNs?
3. **Preparación de Entregables:**
   - **Notebook (`main.ipynb`):** Limpiar el código, asegurar que se ejecuta correctamente de principio a fin, y añadir comentarios explicativos breves en cada celda.
   - **Memoria (PDF):** Redactar un documento de máximo 10 páginas (fuente 12pt). Centrarse en la *discusión técnica*, *justificación de resultados* y *análisis visual*, evitando definiciones teóricas genéricas.

---
### Próximos Pasos Sugeridos:
Podemos empezar inmediatamente con la **Fase 1**. ¿Quieres que escriba el código en `main.ipynb` para cargar el dataset, dividirlo en train/val/test y aplicar las técnicas de Data Augmentation?