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

## 1 Configuración
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




