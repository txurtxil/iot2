Modificaciones realizadas en base al trabajo de Yoheee

https://github.com/0xYoshee/iot2

## IoT 2,Qt5+ Telegram+Oled SD1306 + MqTT + DHT22 + Switches ...

![Iot Mqtt ](https://github.com/txurtxil/iot2/blob/master/gpio2.jpg "Iot Mqtt")

## 1. Instalar dependencias:

###     1.1 Compilar e instalar librerias wiringpi:
         http://wiringpi.com/download-and-install/

###     1.2 Paquetes Qt:
          apt-get install build-essential
          apt-get install qtcreator
          apt-get install qt5-default
          apt-get install qt4-demos qt4-doc qt4-doc-html qt5-doc qt5-doc-html
          apt-get install libqt5serialport5
          apt-get install libqt5serialport5-dev
###      1.3 Paquetes Opencv y corregir path opencv::
          apt-get install libopencv-dev python-opencv
          cd /usr/include/opencv2
          ln -s imgproc/imgproc.hpp imgproc.hpp
###      1.4 Compilar e instalar QtDropbox2
         git clone https://github.com/b0bh00d/QtDropbox2
         cd QtDropbox2
         qmake && make
         cp libQtDropbox2.so* /usr/lib/
###      1.5 Compilar librerias qmq
         git clone https://github.com/emqtt/qmqtt
         cd qmqtt
         qmake && make
         make install        

## 3. Compilar iot2

          git clone https://github.com/txurtxil/iot2
          qmake && make
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
         relayX=Y  - establezca el estado X para el relé X (0-apagado. 1-encendido. 2-invertido. desde el intervalo deconmutación de 30 minutos encendido-apagado-encendido ...)        
         relayZ    - estado de retorno para el relé X
         relay=Y   -establezca el estado de todos los relés (0-apagado. 1-encendido. 2-invertido. desde el intervalo deconmutación de 30 minutos encendido-apagado-encendido ...)
         reboot    - reiniciar el hardware
         halt      - apagar dispositivo hardware         

         ### MQTT

         cam: solicite la foto en la respuesta image1: el campo contiene png de la cámara
         relayX=Y solicitud para cambiar el estado del relé X a Y (0-off. 1-on, etc ...) responde relayXState = Y estado del relé
         tempState - temperatura
         HumiState - Humedad



# 2 Codigo fuente iot2:

 ## 1.Definir dispositivos (hardware) defines.h:
          Definimos los dispositivos que usaremos y sus PIN GPIO wiringpi que usaran(DHT22, Switches, etc..):
              
                  #define RELAY1 "relay1"
                  .....
                  #define DEV_CAM1 "/dev/video1"
                  ......
                  #define PIN_DHT       1  // Pin fisico 12, wiring pi GIPio numero 1
                  .....
        Salida i2c de la pantalla Oled SD1306:
        En raspberry existe /dev/i2c-1, si tenemos problemas con el bus i2c, 
         editamos main.cpp

## 2. Telegram bot  body.cpp:
       Podemos definir comandos a ejecutar en nuestro bot (crear bot: 
       http://surfero.blogspot.com/2019/04/telegram-iot-crear-un-bot-telegram.html )
        
       editamos body.cpp y buscar las lineas del comando reboot:
       ..............
       //este es el comando reboot, que rinicia el sistema operativo
        }
        else if(m.string.toLower() == "reboot") {
            if(enableDisplay){
                timer->stop();
                ssd1306ClearScreen(LAYER0 | LAYER1) ;
                ssd1306DrawXBM(50, 15, start_width, start_height, start_bits, WHITE);
                ssd1306Refresh();
            }
           QProcess::startDetached("reboot");
         }
        //fin del comanod reboot 
        //Este comando ejecuta touch y crea un fichero /opt/ok vacio
        else if(m.string.toLower() == "comando") {
            if(enableDisplay){
                timer->stop();
                ssd1306ClearScreen(LAYER0 | LAYER1) ;
                ssd1306DrawXBM(50, 15, start_width, start_height, start_bits, WHITE);
                ssd1306Refresh();
            }
           // un comando que no hace mas que crear un fichero vacio en /opt/ok
           QProcess::startDetached("touch /opt/ok");
        }
         // Fin pruebas comandos Telegram Txurtxil
     .......................
 


