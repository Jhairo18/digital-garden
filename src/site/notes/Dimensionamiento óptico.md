---
{"dg-publish":true,"permalink":"/dimensionamiento-optico/","dgPassFrontmatter":true}
---


1. Defines la precisión requerida de medición, por ejemplo si quieres medir una burbuja de 1mm, el GSD (resolución espacial) debe ser por criterio de diseño la quinta parte de esto, el cual sería en nuestro caso particular 0.2mm
2. Luego identificas cual es la resolución por ejemplo 1920x1080. Te quedas con el más largo que sería 1920, y calculas tu FOV el cual seria 1920x0.2mm = 384mm
3. A partir de eso calculas la distancia focal de tu cámara el cual sería $f=\dfrac{senswidth\cdot distancia}{FOV}$
4. Tener en cuenta que la lente debe ser igual o mayor al sensor de la camara
