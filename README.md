<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<p><a href="https://github.com/antonimodev/network-sniffing/blob/main/README_EN.md"><strong>ENGLISH VERSION 🇬🇧</strong></a></p>

<h1>🌐Network Sniffer</h1>

<p>Los Sniffers, también conocidos como rastreadores de red, son herramientas empleadas para <strong><em>monitorizar, capturar y analizar en tiempo real los paquetes de datos que se transmiten en una red</em></strong>. Cuando los datos viajan a través de internet, se fragmentan en pequeños paquetes que pasan por diferentes nodos de la red, y los sniffers permiten interceptar y analizar estos paquetes.</p>

<ul>
  <li>Analizar y mejorar el rendimiento de una red.</li>
  <li>Supervisar la actividad de los empleados en una red corporativa.</li>
  <li>Detectar y prevenir ataques cibernéticos.</li>
  <li>Monitorear paquetes de datos para gestión y resolución de problemas.</li>
</ul>

<h2>🦈Wireshark</h2>
<div align="center"><img src="https://static-00.iconduck.com/assets.00/wireshark-alt-icon-2048x2048-4ex8a9zk.png" width="250px" alt="Wireshark Icon"></div>

<br>

<strong>Wireshark</strong> es una herramienta gratuita y de código abierto para el análisis de tráfico de red. Permite capturar y examinar los datos en tránsito, desglosando los paquetes para ver su contenido detalladamente. Esto es especialmente útil para la resolución de problemas de red y la seguridad.

<p>Para empezar a utilizar Wireshark, puedes <a href="https://www.wireshark.org/download.html">Descargarlo aquí</p>

## 📖Índice

1. [Abrir Wireshark - Menú inicial e interfaces de red.](#1---abrir-wireshark---menú-inicial-e-interfaces-de-red)
2. [Interfaz básica - Botones y paquetes de red.](#2---interfaz-básica---botones-y-paquetes-de-red)
3. [Filtro de búsqueda.](#3---filtro-de-búsqueda)
4. [Organización de paneles.](#4---organización-de-paneles)
5. [Reglas de color.](#5---reglas-de-color)

    5.1 [Clasificación de colores.](#51---clasificación-de-colores)
   
6. [Login en web HTTP.](#6---login-en-web-http)
7. [Filtro por protocolo.](#7---filtro-por-protocolo)
   
    7.1 [Seguimiento de sesión HTTP.](#71---seguimiento-de-sesión-http)

8. [Credenciales obtenidas.](#8---credenciales-obtenidas)
9. [Conclusión.](#9---conclusión)

## 🔎Análisis y captura de paquetes HTTP con Wireshark

### 1 - Abrir Wireshark - Menú Inicial e interfaces de red.

Una vez descargado Wireshark en nuestro entorno de trabajo, podremos abrirlo para familiarizarnos con los elementos básicos necesarios para completar la práctica. Podemos iniciar el programa desde la terminal con el comando <code>wireshark</code> o haciendo doble clic en el icono desde la interfaz gráfica. Al abrirlo, veremos la ventana principal del programa con una lista de las interfaces de red disponibles.

<dl>
    <dt>Interfaz de red.</dt>
    <dd><em>Es un componente que permite a un dispositivo conectarse a una red ya sea a través de cables, Wi-Fi o de forma virtual.</em></dd>
</dl>

En nuestro caso, estamos utilizando una máquina virtual (<em>VirtualBox</em>), y la interfaz de red que muestra señal es <strong>eth0</strong>. La señal variará en función del tráfico de red que esté ocurriendo en ese momento.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/0%20START%20WIRESHARK.png" alt="Start Wireshark">

<br>

### 2 - Interfaz básica - Botones y paquetes de red.

Una vez que seleccionemos la interfaz de red que queremos monitorizar, accederemos al panel principal, donde podremos observar diversos elementos de la interfaz. Es fundamental entender algunos conceptos básicos antes de profundizar en más detalles. En este contexto, es importante saber: ¿Qué son los paquetes de red?

<dl>
    <dt>Paquetes de red</dt>
    <dd><em>Son unidades de datos que se envían a través de una red. Cada paquete contiene información sobre su origen, destino y otras instrucciones para asegurar que la información llegue correctamente.</em></dd>
</dl>

A continuación, encontrarás algunas funciones básicas en Wireshark:
<ul>
    <li><strong>Iniciar captura de paquetes:</strong> Comienza a capturar el tráfico de datos en la interfaz de red seleccionada. Esto permite observar y analizar los paquetes en tiempo real.</li>
    <li><strong>Detener captura de paquetes:</strong> Detiene la captura de datos. Esto es útil cuando se ha recopilado suficiente información o se desea analizar los datos ya capturados.</li>
    <li><strong>Reiniciar captura de paquetes:</strong> Detiene la captura actual y comienza una nueva sesión de captura. Es útil para empezar a capturar datos desde un punto limpio, sin los datos anteriores.</li>
</ul>

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/1%20INIT%20ICONS.png?raw=true" alt="Wireshark Menu">

<br>

### 3 - Filtro de búsqueda.

Además de los botones básicos, Wireshark permite filtrar paquetes según diversos criterios en la barra de filtro de búsqueda. Puedes usar filtros para protocolos, direcciones IP, puertos, direcciones MAC, entre otros, dependiendo de lo que estés buscando.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/2%20SEARCH%20FILTER.png?raw=true" alt="Filter">

<br>

### 4 - Organización de paneles.
Una vez familiarizados con la interfaz básica, presionaremos el botón para iniciar la captura de paquetes. A continuación, veremos la ventana de captura, donde Wireshark comenzará a mostrar los paquetes de red en tiempo real, organizados en tres paneles distintos:

<ul>
    <li><strong>Panel Central:</strong> Muestra la lista de paquetes capturados en tiempo real. Aquí puedes ver un resumen de cada paquete, incluyendo información como el número de paquete, la hora de captura, la dirección IP de origen y destino, y el protocolo utilizado.</li>
    <li><strong>Panel Inferior Izquierdo:</strong> Proporciona un desglose detallado del paquete seleccionado en el panel central. Muestra los datos del paquete desglosados en diferentes niveles, como la capa de red, capa de transporte y capa de aplicación.</li>
    <li><strong>Panel Inferior Derecho:</strong> Muestra el contenido en bruto del paquete seleccionado en formato hexadecimal y ASCII. Aquí puedes examinar los datos exactos que componen el paquete.</li>
</ul>

Esta organización en paneles te permite analizar en detalle cada paquete capturado y entender mejor la información que fluye a través de la red.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/3%20CAPTURED%20PACKETS.png?raw=true" alt="Packet info">

<br>

### 5 - Reglas de color.

Puede que en lugar de aparecerte como a mí, te aparezcan paquetes de colores distintos, estos colores tienen un significado que nos ayuda a clasificar cada paquete según sus parámetros. Para poder ver a qué corresponde cada paquete y familiarizarnos visualmente podemos ir al apartado: <pre>View > Coloring Rules</pre>

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/4%20VIEW-COLORING%20RULES.png?raw=true" alt="View Coloring rules">

### 5.1 - Clasificación de colores.

En esta sección, podrás ver cómo se clasifica la naturaleza de los paquetes según su color. Aunque para esta práctica no profundizaremos demasiado en las reglas de color, es útil conocerlas para mantener cierto nivel de organización en el análisis de paquetes.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/5%20COLORING%20RULES.png?raw=true" alt="Coloring rules">

<br>

### 6 - Login en web HTTP.

Para el proyecto actual, vamos a explorar la seguridad de los protocolos de red HTTP. Navegaremos a una página web que use el protocolo "http" y que ofrezca un formulario de inicio de sesión. Introduciremos credenciales aleatorias para observar cómo se transmiten los datos. En la actualidad, la mayoría de los sitios web utilizan el protocolo HTTPS, que cifra los paquetes y dificulta el acceso a su contenido.

<dl>
    <dt>Protocolo de red</dt>
    <dd>Conjunto de reglas y estándares que definen cómo se debe comunicar el dispositivo en una red.</dd>
    <dt>Protocolo HTTP</dt>
    <dd><em>Protocolo de transferencia de hipertexto, utilizado para la transmisión de datos sin cifrar entre el navegador y el servidor web. Los datos se envían en texto plano, lo que hace que sea vulnerable a la interceptación y al análisis.</em></dd>
    <dt>Protocolo HTTPS</dt>
    <dd><em>Protocolo de transferencia de hipertexto seguro, que utiliza cifrado SSL/TLS para proteger los datos durante la transmisión. Garantiza que la comunicación entre el navegador y el servidor web esté cifrada y sea más segura frente a ataques.</em></dd>
</dl>

En palabras menos técnicas, podríamos decir que un protocolo HTTP dicta las reglas que deben seguir los paquetes de datos para transmitirse de manera eficiente. La principal diferencia con HTTPS es que HTTPS añade cifrado a esos datos, asegurando que la comunicación sea mucho más segura y difícil de interceptar.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/6%20LOGIN%20PAGE.png?raw=true" alt="login page">

<br>

### 7 - Filtro por protocolo.

Una vez que hemos identificado los protocolos de red que vamos a utilizar, podemos filtrar los paquetes por HTTP en la barra de búsqueda de Wireshark. Esto nos permitirá centrarnos únicamente en los paquetes que contienen información relacionada con el proceso de inicio de sesión en el dominio HTTP.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/7%20HTTP%20PROTOCOL%20FILTERED.png?raw=true" alt="HTTP Protocol Filtered">

### 7.1 - Seguimiento de sesión HTTP.

Una vez localizado el paquete que contiene el login, deberemos hacer lo siguiente: <pre>Click derecho > Follow > HTTP Stream</pre>
Esta acción nos permitirá ver toda la información para una sesión HTTP específica, facilitando la identificación de problemas y la revisión de los datos.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/8%20FOLLOWING%20HTTP%20STREAM.png?raw=true" alt="HTTP STREAM">

<br>

### 8 - Credenciales obtenidas.

Se abrirá una ventana con toda la información de la sesión HTTP. Aquí, podremos observar las respuestas del cliente (nosotros) y del servidor, diferenciadas por colores:

- Cliente: Rojo 🔴
- Servidor: Azul 🔵

¡Eureka! Hemos capturado las credenciales, en este caso tenemos de username <strong><em>antonimodev</em></strong> y de password <strong><em>github42</em></strong>.

<img src="https://github.com/antonimodev/network-sniffing/blob/main/Wireshark%20-%20Capturas%20Castellano%20Github/9%20EUREKA!.png?raw=true" alt="Credentials">

<br>

### 9 - Conclusión
<p>En esta práctica con Wireshark, he aprendido a utilizar esta herramienta para capturar y analizar el tráfico de red, con un enfoque específico en el protocolo HTTP. Además he podido curiosear sobre diferentes tipos de protocolos y afianzar aún más la concepción sobre la seguridad en redes. Estos pasos me han permitido:</p>

- <strong>Familiarizarme con Wireshark</strong>: He iniciado el programa, seleccionado la interfaz de red adecuada y explorado la interfaz básica, comprendiendo su organización en paneles para la visualización de datos.
- <strong>Aplicar Filtros de Búsqueda</strong>: He aprendido a usar la barra de filtros para centrarnos en los paquetes HTTP específicos, lo que facilita el análisis de datos relevantes y mejora la eficiencia en la captura de información.
- <strong>Analizar Paquetes HTTP</strong>: Al seguir una sesión HTTP específica, he visto cómo se transmiten los datos entre el cliente y el servidor, identificando las respuestas del servidor y del cliente mediante colores y filtros.
- <strong>Entender la Seguridad en la Transmisión de Datos</strong>: He explorado la diferencia entre los protocolos HTTP y HTTPS, comprendiendo cómo el cifrado en HTTPS protege la comunicación frente a posibles interceptaciones y ataques.
- <strong>Captura y Análisis de Datos Sensibles</strong>: Finalmente, he observado cómo las credenciales se transmiten en texto plano a través del protocolo HTTP, destacando la importancia de utilizar HTTPS para proteger información sensible en la web.

En definitiva, esta práctica me ha dado una visión más clara de cómo funciona el tráfico de red y por qué es crucial mantener la seguridad en comunicaciones.

</body>
</html>
