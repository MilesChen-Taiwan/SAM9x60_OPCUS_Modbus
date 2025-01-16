cmake_minimum_required(VERSION 3.5)

project(OPCUSWithModbus)

SET(CMAKE_C_COMPILER   /home/miles/sam9x/24.04/buildroot-at91/output/host/bin/arm-buildroot-linux-gnueabi-gcc)
SET(CMAKE_CXX_COMPILER /home/miles/sam9x/24.04/buildroot-at91/output/host/bin/arm-buildroot-linux-gnueabi-g++)

#SET(CMAKE_C_COMPILER   /home/user/WorkArea/buildroot_9x60_curiosity-2023.10/buildroot-at91/output/host/bin/arm-buildroot-linux-gnueabi-gcc)
#SET(CMAKE_CXX_COMPILER /home/user/WorkArea/buildroot_9x60_curiosity-2023.10/buildroot-at91/output/host/bin/arm-buildroot-linux-gnueabi-g++)

#SET(CMAKE_C_COMPILER	gcc)
#SET(CMAKE_CXX_COMPILER	g++)

set (EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

#add_definitions(-std=c99)

include_directories(${PROJECT_SOURCE_DIR}/../open62541)

add_executable(gpio_control ${PROJECT_SOURCE_DIR}/src/gpio_control.cpp)
target_link_libraries(gpio_control pthread)

add_executable(button_control_I2C_setting_Fan ${PROJECT_SOURCE_DIR}/src/button_control_I2C_setting_Fan.cpp)
target_link_libraries(button_control_I2C_setting_Fan pthread libi2c.so)

add_executable(server_MODBUS_TCP_with_Fan_control ${PROJECT_SOURCE_DIR}/src/server_MODBUS_TCP_with_Fan_control.cpp)
target_link_libraries(server_MODBUS_TCP_with_Fan_control libmodbus.so pthread libi2c.so)

add_executable(client_MODBUS_TCP ${PROJECT_SOURCE_DIR}/src/client_MODBUS_TCP.cpp)
target_link_libraries(client_MODBUS_TCP libmodbus.so pthread libi2c.so)

add_executable(OPC_Server_MODBUS_Client ${PROJECT_SOURCE_DIR}/src/OPC_Server_MODBUS_Client.cpp ${PROJECT_SOURCE_DIR}/open62541/build/open62541.c)
target_link_libraries(OPC_Server_MODBUS_Client libmodbus.so pthread libi2c.so)

add_executable(modbus_slaveWithEMC2305 ${PROJECT_SOURCE_DIR}/src/modbus_slaveWithEMC2305.c)
target_link_libraries(modbus_slaveWithEMC2305 libmodbus.so pthread libi2c.so)

add_executable(modbus_masterWithEMC2305 ${PROJECT_SOURCE_DIR}/src/modbus_masterWithEMC2305.c )
target_link_libraries(modbus_masterWithEMC2305 libmodbus.so pthread libi2c.so)

add_executable(tutorial_server_object ${PROJECT_SOURCE_DIR}/src/tutorial_server_object.c ${PROJECT_SOURCE_DIR}/open62541/build/open62541.c)
target_link_libraries(tutorial_server_object libmodbus.so pthread libi2c.so)

add_executable(OPCUA_gateway ${PROJECT_SOURCE_DIR}/src/OPCUA_gateway.cpp ${PROJECT_SOURCE_DIR}/open62541/build/open62541.c)
target_link_libraries(OPCUA_gateway libmodbus.so libmodbus.so.5 libmodbus.so.5.1.0 pthread libi2c.so)

