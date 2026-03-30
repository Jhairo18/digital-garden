---
{"dg-publish":true,"permalink":"/consideraciones-para-la-captura-de-datos/","dgPassFrontmatter":true}
---


Se debe tener encuenta lo siguiente para la captura de datos
1. Representatividad del entorno real (crítico): El modelo debe representar condiciones reales de operación para que no tenga una degradación de domain gap. 
	- Para esto se captura los datos de entrenamiento con la misma cámara desde el mismo ángulo donde el modelo estará en producción.
	- Utilizar la cámara final de despliegue para grabar secuencias de entrenamiento
	- Considerar variaciones iluminación luz diurna, artificial nocturna, contraluz y sombras parciales.
	- Documentar especificaciones técnicas de la cámara para poder ser factible la reproducibilidad.
2. Calidad del etiquetado (crítico)
	- Definir bien el criterio de anotación, como por ejemplo ¿Qué constituye una caída? ¿Una persona sentada en el suelo se clasifica como caída? ¿Se incluyen caidas parciales?
3. Negativos duros (muy alta): Los negativos duros son imágenes que contienen escenas visualmente similares en una caída, pero que no lo son. El objetivo es reducir los falsos positivos, algunos ejemplos para personas caídas sería:
	- Persona agachándose a recoger un objeto del suelo
	- Persona acostada voluntariamente en un sofá, cama o superfice.
	- Persona inclinada sobre un escritorio o mesa.
4. Diversidad de imágenes (muy alta): El dataset debe cubrir la máxima variabilidad posible en las características de las personas y condiciones de captura.
	- Considerar carcterísticas físicas, vestimenta, superficie, iluminación, contexto (interior hogar, hospital, fábrica), exterior (calle,parque).
5. Objetos pequeños y oclusiones (alta): Detección de objetos pequeños es un problema para YOLO, asegurar que el dataset incluya ejemplos con distintos tamaños de objetos relativo al frame
	- Persona caída 
6. Data agumentation (media-alta)
7. Balance de clases (media): Se tiende a tener problemas cuando no se tiene suficientes datos de la clase minoritaria, si el mAP de una clase es significativamente inferior se deben aplicar técnicas de balanceo como data agumentation, sobremuestro, ajustar funciones de perdida como focal loss.
8. Resolución y formato de imágenes: YOLO redimensiona las imágenes de entrada a un tamaño fijo durante el entrenamiento mas o menos 640 x 640 pixeles, se debe asegurar que tipicamente se tenga al menos 30-50 pixeles del lado en la imagen redimensionada en los objetos, también se puede calcular de la siguiente forma: `tamaño_final = tamaño_objeto × (640 / resolución_imagen)` 
9. División del dataset
10. Cantidad de imágenes: Tener en cuenta que la calidad y representatividad siempre superan la calidad bruta.

[[Yolo\|Yolo]]