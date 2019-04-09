Modificaciones realizadas en base al trabajo de Yoheee

https://github.com/0xYoshee/iot2

# IoT 2,Qt5+Oled SD1306 + MqTT + DHT22 + Switches ...

## 1. Instalar dependencias:

###     1.1 Compilar e instalar librerias wiringpi:
         http://wiringpi.com/download-and-install/

###     1.2 Paquetes Qt:

          apt-get install libopencv-dev python-opencv
          apt-get install libqt5serialport5
          apt-get install libqt5serialport5-dev

###      1.3 Compilar e instalar QtDropbox2
         git clone https://github.com/b0bh00d/QtDropbox2
         cd QtDropbox2
         qmake
         make
         cp libQtDropbox2.so* /usr/lib/
## 2. Corregir path opencv:
          cd /usr/include/opencv2
          ln -s imgproc/imgproc.hpp imgproc.hpp

## 3. Compilar iot2

          git clone https://github.com/txurtxil/iot2
          qmake
          make
          ./iot2


# Trabajar con iot2:

## 1.1 Configuración aplicación iot2
    Editar fichero nuevo de configuración /etc/iot.conf:
    
         [telegram]
         enable = true
         token = bot token

         [mqtt]
         enable = true
         host = servidor por ejemplo m10.cloudmqtt.com
         puerto = puerto, por ejemplo, 11420
         cid = iot-2g
         usuario = usuario
         pass = contraseña
         
## 1.2 Configuración comandos Telegram y MQtt:
         ### Comandos de TELEGRAM
         cam       - foto de camara
         temp      - temperatura del sensor
         reboot    - reiniciar el hardware
         relayX=Y  - establezca el estado X para el relé X (0-apagado. 1-encendido. 2-invertido. desde el intervalo deconmutación de 30 minutos encendido-apagado-encendido ...)        
         relayZ    - estado de retorno para el relé X
         relay=Y   -establezca el estado de todos los relés (0-apagado. 1-encendido. 2-invertido. desde el intervalo deconmutación de 30 minutos encendido-apagado-encendido ...)

         ### MQTT

         cam: solicite la foto en la respuesta image1: el campo contiene png de la cámara
         relayX=Y solicitud para cambiar el estado del relé X a Y (0-off. 1-on, etc ...) responde relayXState = Y estado del relé
         tempState - temperatura
         HumiState - Humedad



# 2 Codigo fuente iot2:

 ## 1.defines.h:
          Definimos los dispositivos que usaremos y sus PIN GPIO wiringpi que usaran(DHT22, Switches, etc..):
              
                  #define RELAY1 "relay1"
                  .....
                  #define DEV_CAM1 "/dev/video1"
                  ......
                  #define PIN_DHT       1  // Pin fisico 12, wiring pi GIPio numero 1
                  .....
        


