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
     Inserte uan micro-usb de almenos 8 GB de espacio en almacenamiento, para su posterior formateo con la aplicacion [SD Card Formatter](https://www.sdcard.org/downloads/formatter/), como recomendacion. Una vez formateada la tarjeta de memoria y extraida la imagen del software de descargara el **Install Raspberry Pi OS using Raspberry Pi Imager** contenido en [el sitio oficial 
     de Raspberry Pi](https://www.raspberrypi.com/software/). la cual nos serivira para intalar la imagen en la miro-usb.
     # Instalar la biblioteca RAK811 Python
     **Paso 1 :** En primer lugar, deberás conectar tu Raspberry Pi al Wi-Fi. En la terminal escriba el siguiente comando:
             </body>
             </html>
             
             sudo raspi-config
     Seleccione la opción **System Options**, luego **Wireless LAN**, luego siga las instrucciones para ingresar sus credenciales de Wi-Fi y conectarse a Wi-Fi para acceder a Internet.
     <!DOCTYPE html>
     <html>
        <head>
           <meta charset="UTF-8">
           
        </head>
        <body>
        
     <table>
     </thead>
     <tr>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/1cea8f29-9151-44ef-aa92-d2b1b4c07757"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/1f56131c-8b4e-403d-a593-da4980ac102f"/></td>
     </tr>
     <tr> 
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/60445c5c-113b-4a44-a221-eff2285dbe8d"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/62076d59-8e6b-44a5-8a2a-07a76aa58e51"/></td>
     </tr>
     </table>
     </body>
     </html>
     La imagen muestra el recuadro en donde se escribira el nombre de la red wifi a conectarse, una vez realizado se dezplegara un segundo cuadro en donde se colocara la contraseña de esa red.
   **Paso 2 :** Antes de reiniciar la raspberry pi, debemos habilitar el hardware serial en Raspberry Pi y deshabilitar la consola serial. Entonces puede volver al inicio de las configuraciones y selacionar interfaz options, una vez dentro del cuadro seleccionar serial port y luego seleccionar " No " y luego " Sí ". Una vez hecho esto seleccionar SSH para poder conectarte inalambricamente, ademas de activar el SPI y I2C corespondientemente en la raspberry pi zero, una vez hecho esto reinicia la raspberry pi para p
