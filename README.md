Modificaciones realizadas en base al trabajo de Yoheee

https://github.com/0xYoshee/iot2

# IoT 2, Oled SD1306 + MqTT + DHT22 + Switches ...

## 1. Instalar dependencias:

### Compilar e instalar librerias wiringpi:

http://wiringpi.com/download-and-install/

### Paquetes Qt:

apt-get install libopencv-dev python-opencv

apt-get install libqt5serialport5

apt-get install libqt5serialport5-dev

### Compilar e instalar QtDropbox2

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






