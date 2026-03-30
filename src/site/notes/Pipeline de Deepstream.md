---
{"dg-publish":true,"permalink":"/pipeline-de-deepstream/","dgPassFrontmatter":true}
---


La siguiente imagen representa el flujo general del pipeline de Deepstream:
![Pasted image 20260327234614.png](/img/user/attachments/Pasted%20image%2020260327234614.png)
1. Source: La entrada de video. Puede ser un archivo MP4, una cámara IP por RTSP, una webcam USB, o incluso varios streams al mismo tiempo
2. Decoder: Descomprime el video (H.264, H.265) directamente en la memoria de la GPU, sin pasar por la CPU. Esto lo hace rápido.
3. StreamMux: Agrupa varios frames en un "batch" para procesarlos juntos de una sola vez. Aquí le defines el tamaño del batch.
4. Primary GIE: Es el corazón del pipeline. Aquí corre el modelo de IA, y detecta cada frame. Usa tu `config_infer_primary.txt` y tu `labels.txt`.
5. Tracker: Le da una identidad a cada objeto detectado (ID único) y lo sigue de frame en frame, aunque se mueva o se tape momentáneamente.
6. Secundary GIE (opcional): Toma los objetos que ya detectó el Primary GIE y los clasifica con más detalle. Por ejemplo: Primary detecta "auto", Secondary dice si es "sedán" o "camioneta".
7. OSD+Slink: OSD dibuja los cuadros y etiquetas sobre el video. Sink es la salida: puede ser la pantalla, un archivo, un stream RTSP, o una cola de mensajes.