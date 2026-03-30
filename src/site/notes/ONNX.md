---
{"dg-publish":true,"permalink":"/onnx/","dgPassFrontmatter":true}
---


Es un formato estandar abierto, cuyo problema que resuelve es que si entrenas un modelo en pytorch, normalmente solo lo puedes usar con PyTorch. El modelo ONNX te permite exportar tu modelo a un formato que no dependa del framework.

De por si ONNX lo que aplica algunas optimizaciones al modelo como eliminación de operaciones redundantes o función de capas, asi que generalmente funciona mejor que un .pt por ejemplo. Luego lo optimizas aún más en TensorRT para desplegarlo también.
# Enlaces
[[Yolo\|Yolo]]