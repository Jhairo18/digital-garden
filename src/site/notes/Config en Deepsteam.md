---
{"dg-publish":true,"permalink":"/config-en-deepsteam/","dgPassFrontmatter":true}
---


Es el manual de instrucciones que dice al sistema cómo armar y ejecutar partes de tu pipeline o en general del análisis de video con IA.
# nvinfer
Es el archivo config que se encarga de realizar la inferencia de IA (detección de objetos, clasificación y segmentación) dentro del pipeline de video
```
# Ruta a tu ONNX 
onnx-file=yolo26sJhairov2.onnx 

# Ruta donde se creará el motor rápido (se genera solo la primera vez) model-engine-file=yolo26sJhairov2.onnx_b1_gpu0_fp16.engine 

# Carpeta de los archivos de texto de las clases 
labelfile-path=labels.txt 
batch-size=1 

# 0:FP32, 1:INT8, 2:FP16 (usa 2 para Jetson) 
network-mode=2 

# Número de clases del modelo (caida=0, persona=1)
num-detected-classes=2 

# Inferir cada 4 frames (el tracker interpola el resto) 
interval=0 

# Dimensiones de inferencia, define las dimensiones de entrada del modelo, debe ser igual que el entrenamiento (reducido de 1280 para Orin NX 8GB) 
infer-dims=3;640;640
 
# Define ID único del motor de inferencia del pipeline, es importante si tienes múltiples modelos
gie-unique-id=1 

# Define la función de sobre qué le das al MODELO para procesar, si es 1 el modelo recibe todo el frame, si es 2 solo recibe cajas detectadas
process-mode=1 

# Define el tipo de red 0 detector, 1 clasificador y 2 segmentación
network-type=0 

# Método para agrupar bounding boxes 0 sin clustering, 1 DBSCAN, 2 NMS 
cluster-mode=2 

# Achica la imagen sin deformar para que pueda ser procesado mediante Yolo, para que después la caja vuelvan al tamaño original
maintain-aspect-ratio=1 

# Función que interpreta la salida del modelo, traduce la matriz de yolo, es necesario que coincida con el MODELO. Define la función que se buscará dentro del archivo 
parse-bbox-func-name=NvDsInferParseYolo 

# Es un archivo compilado (.so) el cual contiene código C/C++ el cual sirve para que use ese traductor especial, se recomienda hacer esto cuando es probable que tengas un parser complicado como modelos antiguos y actualizados de YOLO (v3,v4,v5,v8,v26)
custom-lib-path=DeepStream-Yolo/nvdsinfer_custom_impl_Yolo/libnvdsinfer_custom_impl_Yolo.so 

# Filtro de confianza
[class-attrs-all] 
re-cluster-threshold=0.7
```
