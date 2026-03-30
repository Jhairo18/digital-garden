---
{"dg-publish":true,"permalink":"/jetpack/","dgPassFrontmatter":true}
---


Jetpack es una versión personalizada de Ubuntu optimizada específicamente para los procesadores de NVIDIA. Incluye el kernel de Linux, cargadores de arranque y controladores de hardware. Además de utilizar DeepStream SDK el cual es un framework sobre JetPack diseñado para la construcción de pipelines, permitiendo múltiples flujos de cámara simultáneamente con una latencia mínima.
Ademas de tener bibliotecas de aceleración como:
- CUDA: Arquitectura de computación paralela en NVIDIA. Permite tareas matemáticas se ejecuten en la GPU en vez de la CPU
- TensorRT: Tiene un optimizador de inferencia. Toma un modelo entrenado y lo optimiza para que corra a la máxima velocidad posible.
- cuDNN: Biblioteca para redes neuronales profundas. Optimiza operaciones como las convolucionales.
- VPI:  Biblioteca que permite delegar tareas de procesamiento de imágenes a diferentes aceleradores de hardware (GPU, PVA o VIC)