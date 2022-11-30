# ESP32CAM-DHT11-G7
Este repositorio contiene los archivos para el ejercicio en clase que envia la informacion de DHT11 por MQTT a NodeRed

## Introducción
Este ejercicio consiste en realizar una estación de clima que realice lo siguiente:
- Obtener información de temperatura y humedad relativa del sensor DHT11 con el micro controlador ESP32CAM
- Enviar los valores del sensor por MQTT de forma local en JSON, con el objetivo de enviar varias variables en el mismo mensaje
- Generar un Flow que obtenga por MQTT los valores enviados por el sensor y realice una gráfica del historico y muestre indicadores de valores instantaneos
- Generar un flow, el cual realice lo siguiente:
    - Obtener valor de temperatura, humedad relativa, Calidad del Aire, Indice Ultra Violeta por API de openweathermap.org
    - Graficar valores instantaneos e historicos del la ubicación actual en un dashboard
    - Suscribirse a un Broker MQTT público para poder obtener la información de datos climáticos de todos los alumnos del grupo 7
    - Reportar por MQTT los datos obtenidos por API para que puedan ser visualizados por el resto de los alumnos
    - Enviar una señal de encendido/apagado del LED Flash soldado en el ESP32CAM para indicar sobre temperatura (arriba de 28°C)

### Material Necesario

Para realizar este ejercicio necesitarás contar con lo siguiente:

- Micro controlador ESP32CAM
- Convertidor de niveles FTDI
- Cable USB-A a USB-mini
- Jumpers
- Protoboard
- Sensor DHT11

### Software necesario

Para poder hacer funcionar este proyecto, es necesario contar con el siguiente software:
- [Ubuntu 20.04](https://releases.ubuntu.com/20.04/)
- [Arduino IDE](https://www.arduino.cc/en/software)
    - [Gestor de tarjetas ESP32](https://github.com/iotechbugs/esp32-arduino/blob/master/docs/arduino-ide/boards_manager.md)
    - [Configuración de la IDE de Arduino para trabajar con el ESP32CAM](https://github.com/iotechbugs/esp32-arduino)
    - [Biblioteca PubSubClient](https://github.com/knolleary/pubsubclient)
- [Mosquitto MQTT Broker](https://mosquitto.org/download/)
    - [Listener en puerto 1883 para 0.0.0.0 y conexiones no autentificadas activadas](https://mosquitto.org/man/mosquitto-conf-5.html)
- [NodeJS](https://nodejs.org/es/)
    - [NPM](https://www.npmjs.com/)
    - [NodeRed](https://nodered.org/docs/getting-started/local)
    - [Nodos Dashboard](https://flows.nodered.org/node/node-red-dashboard)

### Material de referencia

En los siguientes enlaces puedes encontrar cursos en la plataforma de edu.codigoiot.com que te permitirán realiar las configuraciones necesarias

- [Instalación de Virutal Box y Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=812)
- [Configuración de Arduino IDE para ESP32CAM](https://edu.codigoiot.com/course/view.php?id=850)
- [Instalación de NodeRed](https://edu.codigoiot.com/course/view.php?id=817)
- [Introducción a NodeRed](https://edu.codigoiot.com/course/view.php?id=278)
- [Instalación de Mosquitto MQTT](https://edu.codigoiot.com/course/view.php?id=818)

### Servicios

Para que este ejercicio funcione, necesitas los siguientes servicios
- [HiveMQ](http://www.mqtt-dashboard.com/). Es un broker publico y no se necesita cuenta
- [OpenWeatherMap](https://openweathermap.org). Servicio meteorológico gratuito. Se requiere cuenta, pero no se requiere ningun pago


## Instrucciones

### Requisitos previos
Para realizar este ejercicio necesitas cumplir con los siguientes requisitos previos

1. Tener configurado en entorno de desarrollo. Para esto es necesario contar con la IDE de Arduino configurada para poder cargar programas al ESP32CAM
2. Entorno de NodeJS configurado para trabajar con NodeRed. Deberás tener agregados los nodos Dashboard.
3. Entorno de Mosquitto MQTT configurado. Deberás tener modificado el archivo mosquitto.conf para que acepte conexiones externas y no autentificadas. Deberás tener el firewall de Ubuntu abierto para permitir conexiones en el puerto 1883.

### Instrucciones de preparación de entorno
Para poder configurar tu entorno y realizar este ejercicio, encesitas lo siguiente

1. Realiza el circuito. Las instrucciones se encuentran en el encabezado del código para el ESP32CAM. Deberás cambiar lo siguiente:
    - El tema de publicación y suscripción
    - Nombre de red y contraseña al que deseas conectarte
    - Tiempo de espera entre envío de datos en milisegundos
2. Arrancar NodeRed y cargar el Flow. Deberás modificar lo siquiente:
    - Temas MQTT a reportar. Deberás ajustarlos de acuerdo a tus fines
    - Coordenadas. Deberás actualizar las coordenadas geográficas usadas para hacer la petición por API a OpenWheatherMap
    - API Key. Deberás generar tus propias API Keys para hacer uso del servicio de OpenWeatherMap
    - Temperatura umbral para envíar señal de encendido del LED Flash para indicar sobre temperatura
3. Energiza el circuito. Asegurate de energizar el circuito realizado y de que este se encuentre en rango de la red de WiFi seleccionada

### Instrucciones de operación

Para observar el funcionamiento de este ejercicio, es necesario que abras el dashboard. Generalmente puedes encontrarlo en http://localhost:1880/ui desde la computadora que ejecuta NodeRed.

## Resultado

![Vista previa](https://github.com/joseomarojeda/ESP32CAM-DHT11-G7/blob/main/Resultados/DASHBOARD.png?raw=true)
![Vista previa](https://github.com/joseomarojeda/ESP32CAM-DHT11-G7/blob/main/Resultados/ARMADO%20DE%20CICUITO.jpeg?raw=true)
![Vista previa](https://github.com/joseomarojeda/ESP32CAM-DHT11-G7/blob/main/Resultados/SENSOR%20FUNCIONANDO.jpeg?raw=true)
![Vista previa](https://github.com/joseomarojeda/ESP32CAM-DHT11-G7/blob/main/Resultados/LED%20ENCENDIDO%2028%20%C2%B0C.jpeg)

# Evidencias
A continuación puedes ver enlaces a las evidencias de este proyecto

- [Repositorio](https://github.com/joseomarojeda)



# Créditos

Desarrollado por Hugo Escalpelo
- [GitHub](https://github.com/joseomarojeda)