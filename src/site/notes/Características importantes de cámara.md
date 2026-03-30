---
{"dg-publish":true,"permalink":"/caracteristicas-importantes-de-camara/","dgPassFrontmatter":true}
---


Se presentan las características de la cámara basada en orden de importancia
##  Tamaño de pixel (Pixel Pitch)
Medida en micrometros de cada pixel individual. A mayor tamaño, más luz captura cada pixel y mejor es la imagen.
- Rango de excelencia: $\ge 3.45 \mu m$ (Sensores FSI como Sony Pregius Gen2: IMX250,IMX264). Son ideales para muy poca luz
- Rango Industrial Estándar: $\ge 2.74 \mu m$  (Sensores BSI como Sony Pregius IMX540, IMX541)
- Zona prohibida (Consumo) $< 2.0 \mu m$ (Cámaras de seguridad baratas o webcams).
# SNR
Mide que tan limpia es la imagen frente al ruido electrónico. Un SNR bajo hace que YOLO vea cosas que no existen o pierda detecciones reales.
- $\ge 40 dB$: Excelente para inspección de precisión.
- $< 35 dB$: El ruido electrónico empezará a confundir al modelo de IA, especialmente en texturas sutiles.
# FPS
Debe ser al menos el doble de velocidad de paso de los objetos para tener un margen de errror.
- Si pasa 1 objeto cada segundo, con 15-30 está cuvierto.
# Interfaz de comunicación - Estabilidad en Planta
- **GigE Vision con PoE (Power over Ethernet):** La mejor opción. Un solo cable de red lleva datos y energía hasta a 100 metros. Muy estable frente a interferencias de motores.
- **USB 3.0:** Excelente para distancias cortas ($< 5m$). Muy rápido pero el cable es delicado.
- **Wi-Fi (PROHIBIDO):** Las fábricas tienen demasiado ruido electromagnético. El Wi-Fi causa pérdida de frames y latencia inaceptable para inspección en tiempo real.
# Tipo de obturador (shutter)
- Global shutter → Captura todos los píxeles al mismo tiempo. Evita la deformación geométrica. Es obligatorio para objetos en movimiento o líneas de producción
- Rolling shutter → Captura linea por linea, lo cual genera distorsión por movimiento "efecto gelatina", haciendo que las mediciones fallen.
# Tamaño del sensor físico
Más grande = mejor captura de luz general
- 1/2" o mayor → recomendado para visión por computadora
- 2/3" o 1" → ideal para aplicaciones exigentes
- 1/4" o menor → Evitar en condiciones variables de luz
# Rango dinámico WDR
Capacidad de ver zonas muy oscuras y muy brillantes al mismo tiempo, importante en entornos de luz solar directa, sombras profundas o iluminación mixta
- **≥ 60 dB** → Bueno para entornos con luz variable
- **<40 dB**  → Perderá detalle en sombras o zonas sobre iluminadas
