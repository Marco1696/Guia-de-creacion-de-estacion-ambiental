# Guia de creacion de estacion ambiental
Esta guia esta dirijida a toda aquella persona que tenga la necesidad de implementar una estacion de monitoreo ambientral con el motro de raspian en una raspberry pi zero w , con el modulolo LoRaWan y su red, ademas de la plataforma de chirpstack y the thingsboard. Se establecen enlaces y graficos para su mejor entendimeineto de los sensores. 
   # Configuracion de controlador raspberry pi zero w
Esta guia describe 2 formas de configurar la respberry pi, la cual se explica como se llego desde la descarga de la imagen del software de raspian hasta el desarrollo y puesta en marcha de los programas funcionales de python y la segunda forma explica como agregar y modificar una archivo quemado prevamiente en una micro-usb el cual contiene todos los archivos del paso 1.
   - https://learn.pi-supply.com/make/getting-started-with-the-raspberry-pi-lora-node-phat/
     # Descargar-e-instalar-imagen-del-sistema-raspian
     [Descargar](https://downloads.raspberrypi.com/raspios_oldstable_lite_arm64/images/raspios_oldstable_lite_arm64-2024-03-12/2024-03-12-raspios-bullseye-arm64-lite.img.xz?_gl=1*sv35ox*_ga*MzQ2MTQ5NjU2LjE3MDc4NDI4Nzg.*_ga_22FD70LWDS*MTcxNTEwNzQ2OC40LjEuMTcxNTEwNzUwMi4wLjAuMA..) la imagen **Raspberry Pi OS (Legacy) Lite ver.6.1** ultilizada como software de la estacion ambiental la cual estara en un formato **.zip**, se recomienda la utilizacion de la 
     aplicacion [WinRAR](https://www.win-rar.com/open-zip-file.html?&L=0) para extraer los datos de la imagen. 
     Tome en cuenta que esta version es la 6.1 y pueden existir actualizaciones, para obtener mas información sobre los sistemas operativos disponibles para Raspberry Pi, visita [El sitio oficial 
     de Raspberry Pi](https://www.raspberrypi.com/software/operating-systems/).
     Inserte uan micro-usb de almenos 8 GB de espacio en almacenamiento, para su posterior formateo con la aplicacion [SD Card Formatter](https://www.sdcard.org/downloads/formatter/), como recomendacion. Una vez formateada la tarjeta de memoria y extraida la imagen del software de descargara [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/)
     # Instalar la biblioteca RAK811 Python
     Paso 1 : En primer lugar, deberás conectar tu Raspberry Pi al Wi-Fi. En la terminal escriba el siguiente comando:

sudo raspi-config
Seleccione la opción 2 " Opciones de red ", luego N2 " Wi-Fi ", luego siga las instrucciones para ingresar sus credenciales de Wi-Fi y conectarse a Wi-Fi para acceder a Inter     
