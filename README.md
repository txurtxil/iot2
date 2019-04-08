Modificaciones realizadas en base al trabajo de Yoheee

https://github.com/0xYoshee/iot2

# IoT 2, Oled SD1306 + MqTT + DHT22 + Switches ...

## Instalar dependencias:

apt-get install libopencv-dev python-opencv

apt-get install libqt5serialport5

apt-get install libqt5serialport5-dev

git clone https://github.com/b0bh00d/QtDropbox2

cd QtDropbox2

qmake

make

cp libQtDropbox2.so* /usr/lib/

## Corregir path opencv:

cd /usr/include/opencv2

ln -s imgproc/imgproc.hpp imgproc.hpp
## Compilar iot2

git clone https://github.com/txurtxil/iot2

qmake

make



Modificaciones realizadas en base al trabajo de Yoheee

https://github.com/0xYoshee/iot2


