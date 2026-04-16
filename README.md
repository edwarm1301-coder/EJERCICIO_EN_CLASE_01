# EJERCICIO_EN_CLASE_01 CONMUTACION Y TELETRAFICO
## Se realiza la creación de un nuevo Notebook: para ello se utlizo  Google Colab y crear un nuevo notebook.
<img width="1360" height="580" alt="image" src="https://github.com/user-attachments/assets/1303a6a4-70a5-4ee1-af3a-bb9afd42b8b9" />
descarga de la liberia y dependiencias:
<img width="1360" height="580" alt="image" src="https://github.com/user-attachments/assets/6e651906-80e8-42e8-9c13-5bc70d23a3a4" />

### PARTE 1:
Se  realiza la captura el tráfico de red mientras YOLOv8 descargado un modelo ya establecido. Este proceso utiliza el protocolo TCP. El protocolo TCP es  orientado a conexión y fiable en las redes de comunicaciones.
<img width="713" height="267" alt="image" src="https://github.com/user-attachments/assets/d8789a4b-a508-4617-8811-8489cb3554a6" />

### archivos que se descargaron:
<img width="307" height="282" alt="image" src="https://github.com/user-attachments/assets/c8f47c6c-4193-4a48-b2b9-7beae68167cf" />

### Luego se toma el archivo .pcap y se abre con el aplicativo wireshark para poder analisis los paquetes que nos suministro la captura de paquetes previamienta ejecutados:

<img width="1361" height="753" alt="image" src="https://github.com/user-attachments/assets/c0b8f2f6-cfe1-4ae5-92de-3d80ab0adacd" />

### Una vez generado el tráfico ahora se realizara la descargar el modelo YOLOv8 Nano. Para ello activará una conexión TCP, como se muestra en la siguiente imagen:


<img width="1788" height="384" alt="image" src="https://github.com/user-attachments/assets/bd33916d-88e3-4685-af48-42cbb2c2d86c" />

### Se procedera a detener la descarga y se descargara el archivo .pcap para poder validar el trafico que nos suministro dicha ejecución:

<img width="878" height="280" alt="image" src="https://github.com/user-attachments/assets/746fd546-801e-4292-be1b-a055c1e8673e" />

### Swe realiza un analisis del archivo .pcap en wireshark, como se puede apreciar protocolos de red como lo son: TCP y HTTP, con su respectivas direcciones de IP de origen y destino:

<img width="1919" height="1055" alt="image" src="https://github.com/user-attachments/assets/5b04f4d7-cafe-4dbe-b491-45804748d796" />

### PARTE 2:
 Se realizar el análisis de la Transmisión de Video (Tráfico UDP en Tiempo Real) con una solicitud de paquetes y la descarga de un archivo de tipo .pcap:

### ¡IMPORTANTE!: En esta fase, se simulará la transmisión de un video desde una cámara web. Para minimizar la latencia, se usará el protocolo UDP, que es más rápido pero no garantiza la entrega de todos los paquetes.
### A. Inicio de  la captura de paquetes: Se comienza una nueva captura, esta vez enfocada solo en el tráfico UDP.


<img width="744" height="131" alt="image" src="https://github.com/user-attachments/assets/251f8960-5cba-453b-a7a2-aabbb28be724" />

<img width="531" height="102" alt="image" src="https://github.com/user-attachments/assets/3af1299c-cf6b-4c66-bfb8-59732af2abad" />

### Luego de obtener el archivo .pcap se analizara con wireshark las tramas y paquetes:


<img width="1906" height="995" alt="image" src="https://github.com/user-attachments/assets/14fb73b4-3262-4b64-a760-83ef98e24c3e" />

 ### B. Se ejecutara el script de transmisión: Este código enviará 100 "fotogramas" en simultaneo para poder tener un carga de paquetes más pesada y poder validar más protocolos:

 <img width="1912" height="869" alt="image" src="https://github.com/user-attachments/assets/26db099e-1f9a-4a48-9513-6bc6824e2bac" />

### (Se evidencia algunos paquetes se que perdieron a la hora de realizara la trasmision).

 ### C. Detener y bajar archivo:
 
 <img width="320" height="45" alt="image" src="https://github.com/user-attachments/assets/af58077a-febc-4280-a276-2f01466371f9" />
 <img width="1871" height="939" alt="image" src="https://github.com/user-attachments/assets/337fe31f-4ffa-432e-ba78-24dcd480a38c" />

 ### PARTE 3: 
 ### Análisis Forense con Wireshark
 ## Se realizara la apertura de los dos archivos .pcap que  se descargaron previamente en el PC para ser analizados  con Wireshark:

<img width="1862" height="989" alt="image" src="https://github.com/user-attachments/assets/0d5bc87d-4f90-4b96-8f29-9ad677649cb4" />

#### (Se utiliza en la barra de filtros de wireshark el siguiente parametro para poder validar solo en trafico TCP del archivo)
### tcp.flags.syn == 1. Como se puede observar al ulitizar el parametro mencionado anteriormente, se puede determinar cuantos paquetes de tipo TCP fueron enviados por la origen (soucer) con el ACK=1 que en este caso fueron 3 paquetes.

### Con el parametro tcp.analysis.retransmission utlizado en la barra de busqueda de filtros, se hallo un paquete de trasminision perdido desde la IP de desde 172.28.1.0 a la IP de destino 172.28.1.12

<img width="1748" height="1000" alt="image" src="https://github.com/user-attachments/assets/92711b87-ea61-4444-bd29-fad681d05c99" />

### Lametablemte no se logro obtener paquetes con el parametro tcp.port == 443

<img width="1324" height="692" alt="image" src="https://github.com/user-attachments/assets/02723d3b-544c-45ff-be21-2a23a720d627" />

### PREGUNTAS A RESOLVER:
### 1. ¿Qué es YOLO, cuáles son sus características y su arquitectura?
RTA: YOLO  es un modelo de visión por computadora diseñado para la detección de objetos en tiempo real, gracias a este modelo de detencion logramos aprender más acerca de las trasmsión de paquetes en tipo real para luego ser analizados con wireshark.

### Arquitectura:
YOLOv8 utiliza una arquitectura de red neuronal convolucional (CNN) optimizada que divide la imagen en una rejilla y predice cuadros delimitadores (bounding boxes) y probabilidades de clase simultáneamente.

### Protocolo vs. Aplicación (TCP vs. UDP) Descarga del modelo (TCP):
Se usa TCP porque es un protocolo fiable y orientado a conexión. Es crucial que el archivo yolov8n.pt llegue completo y sin errores, ya que un solo bit corrupto inutilizaría el modelo.
### Para la Transmisión de video con el protocolo UDP:
 UDP se usa porque prioriza la velocidad y la baja latencia. En video en vivo, es mejor perder un fotograma (paquete) que retrasar toda la transmisión esperando una retransmisión.
 ### 3. Fiabilidad vs. Velocidad Retransmisiones en TCP:
 Al realizar una filtración  por tcp.analysis.retransmission, si aparecen resultados, significa que el protocolo detectó pérdida de datos y reenvió los paquetes automáticamente para asegurar la integridad.
 ### El impacto que se genero en video:
 Al utiliazr el  mecanismo de la trasmision de un video en vivo, causaría pausas o "lag", ya que el video se detendría para esperar los datos antiguos antes de mostrar los nuevos. 
 
 ### 4. Identificación del Origen 
 Para aislar el tráfico del servidor al momento de realizar  el modelo en el  archivo descarga_tcp.pcap, se puedeu usar los siguientes los siguientes parametros  en wireshark: ip.src == (IP DEL SERVIDOR): Para ver solo los paquetes que vienen del servidor hacia el  Colab.ip.dst == (IP DEL SERVIDOR): Para ver las peticiones que del  Colab que se va a utlizara se  enviara al servidor.tcp.port == 443: Para realizar un analsis más detallado  solo en el tráfico de descarga segura (HTTPS).















