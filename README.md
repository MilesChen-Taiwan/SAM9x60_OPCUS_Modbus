# Microchip
developing some project from Microchip 


git clone https://github.com/MilesChen-Taiwan/SAM9x60_OPCUS_Modbus.git

cd SAM9x60_OPCUS_Modbus

git clone https://github.com/open62541/open62541.git -b v1.3.4

cd open62541

git submodule update --init --recursive
 
sudo mkdir build

cd build

sudo cmake .. -DUA_ENABLE_AMALGAMATION=ON -DBUILD_SHARED_LIBS=ON -

DCMAKE_C_COMPILER=/home/miles/sam9x/linux4microchip23.10/buildroot-at91/output/host/bin/arm-buildroot-

linux-gnueabi-gcc 

make

cd .

cd.

mkdir bin

camke .

make

ls ./bin

