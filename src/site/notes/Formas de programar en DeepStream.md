---
{"dg-publish":true,"permalink":"/formas-de-programar-en-deep-stream/","dgPassFrontmatter":true}
---


Hay diferentes formas de trabajar con DeepStream, como por ejemplo:
1. LowCode (NVIDIA Graph Composer)
Es una herramienta que genera archivos de configuración y contenedores.
	- **Cuándo usarlo:** Estás en la fase de **diseño de arquitectura**. Quieres ver cómo se conectan los elementos (fuente de video -> preprocesamiento -> inferencia -> salida) sin escribir una sola línea de código.
	- **Ventaja:** Te ayuda a entender la jerarquía de DeepStream y evita errores típicos de "pads" mal conectados.
	- - **Desventaje:** Personalizar comportamientos muy específicos (como una lógica de conteo compleja) sigue requiriendo meterse al código después.
2. DeepStream Python Bindings (PyDS)
	- **Cuándo usarlo:** Para **aplicaciones industriales estándar**. Si necesitas detectar objetos y enviar alertas, guardar logs o interactuar con una base de datos.
	- **Cuándo usarlo:** Para **aplicaciones industriales estándar**. Si necesitas detectar objetos (como burbujas o etiquetas) y enviar alertas, guardar logs o interactuar con una base de datos.
3. C++ (GStreamer Nativo)
	- **Cuándo usarlo:** Cuando el hardware está al límite. Por ejemplo, si tienes una Jetson Orin Nano y quieres procesar **12 o 16 hilos de video en tiempo real** al mismo tiempo.
	- **Por qué:** Eliminas el "overhead" (la carga extra) de Python. Tienes control total sobre la memoria compartida y los punteros de la GPU.
	- - **Recomendación:** Úsalo solo si después de probar en Python ves que la CPU se satura o la latencia es inaceptable para una línea de producción de alta velocidad.
