Modificaciones realizadas en base al trabajo de Yoheee

https://github.com/0xYoshee/iot2

# IoT 2, Oled SD1306 + MqTT + DHT22 + Switches ...

## Instalar dependencias:

apt-get install libopencv-dev python-opencv

## Corregir path opencv:

cd /usr/include/opencv

ln -d imgproc/imgproc.hpp imgproc.hpp

## Compilar iot2:

git clone https://github.com/txurtxil/iot2

cd iot2/lib/QtDropbox2/

qmake

make

cp libQtDropbox2.so* /usr/lib/

cd ../../

qmake

make



Modificaciones realizadas en base al trabajo de Yoheee

https://github.com/0xYoshee/iot2


