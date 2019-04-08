iot2 for Orange pi iot-2g

## Instalar dependencias:

apt-get install libopencv-dev python-opencv

##corregir path opencv:

cd /usr/include/opencv
ln -d imgproc/imgproc.hpp imgproc.hpp

## Compliar iot2:

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


