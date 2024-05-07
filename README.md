# Guia de creacion de estacion ambiental
Esta guia esta dirijida a toda aquella persona que tenga la necesidad de implementar una estacion de monitoreo ambientral con el motro de raspian en una raspberry pi zero w , con el modulolo LoRaWan y su red, ademas de la plataforma de chirpstack y the thingsboard. Se establecen enlaces y graficos para su mejor entendimeineto de los sensores. 
# Configuracion de controlador raspberry pi zero w
Esta guia describe 2 formas de configurar la respberry pi, la cual se explica como se llego desde la descarga de la imagen del software de raspian hasta el desarrollo y puesta en marcha de los programas funcionales de python y la segunda forma explica como agregar y modificar una archivo quemado prevamiente en una micro-usb el cual contiene todos los archivos del paso 1.
   - https://learn.pi-supply.com/make/getting-started-with-the-raspberry-pi-lora-node-phat/
     # Descargar-e-instalar-imagen-del-sistema-raspian
     La imagen "Raspberry Pi OS (Legacy) Lite" 
     # Instalar la biblioteca RAK811 Python
Paso 1 : descargue y actualice la imagen más reciente del sistema operativo Raspbian en su tarjeta micro SD. Puede descargar la imagen más reciente desde aquí:  https://www.raspberrypi.org/downloads/raspbian/

Nota: Recomendamos descargar la versión Raspbian Lite

Paso 2 : En primer lugar, deberás conectar tu Raspberry Pi al Wi-Fi. En la terminal escriba el siguiente comando:

sudo raspi-config
Seleccione la opción 2 " Opciones de red ", luego N2 " Wi-Fi ", luego siga las instrucciones para ingresar sus credenciales de Wi-Fi y conectarse a Wi-Fi para acceder a Inter     
