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
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/4d702a48-e214-4d85-bbd4-e71a74a255b9"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/1f56131c-8b4e-403d-a593-da4980ac102f"/></td>
     </tr>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/1cea8f29-9151-44ef-aa92-d2b1b4c07757"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/62076d59-8e6b-44a5-8a2a-07a76aa58e51"/></td>
     </tr>
     </table>
     </body>
     </html>
     La imagen muestra el recuadro en donde se escribira el nombre de la red wifi a conectarse, una vez realizado se dezplegara un segundo cuadro en donde se colocara la contraseña de esa red.
     
     **Paso 2 :** Antes de reiniciar la raspberry pi, debemos habilitar el hardware serial en Raspberry Pi y deshabilitar la consola serial. Entonces puedes volver al inicio de las configuraciones y seleccionar **Interface Options**, 
     posteriormente seleccionar **Serial Port** y luego seleccionar **No** y luego **Yes** como se muestra en las iguientes imagenes. 
     <!DOCTYPE html>
     <html>
        <head>
           <meta charset="UTF-8">
        </head>
        <body>
     <table>
     </thead>
     <tr>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/1c74d453-083c-4438-81f5-25b7acc888a0"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/dfe8da6e-a15a-4c30-99f7-e8d060e3b312"/></td>
     </tr>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/9ff7ad69-9749-4374-b6c5-ebaa5991cce2"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/2cc4c211-b01f-4d3a-8c0c-6c40f6e1909d"/></td>
     </tr>
     </table>
     </body>
     </html>
     
     Una vez hecho esto seleccionar **SSH** y activarlo para poder conectarte inalambricamente, del mismo modo activar el **SPI** y **I2C**.
     <!DOCTYPE html>
     <html>
        <head>
           <meta charset="UTF-8">
        </head>
        <body>
     <table>
     </thead>
     <tr> 
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/978f5aea-cd27-462c-99a3-78354a53c1d8"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/711cf1bf-784d-49a5-bdbd-5d244eca8c8c"/></td>
     </tr>
     </table>
     </body>
     </html>

     **Paso 3 :** Escriba el siguiente comando en la raspberry pi zero:
     </body>
             </html>
             
        sudo nano /boot/config.txt
     
     Desplácese hacia abajo del codigo y agregue la siguiente línea:
      </body>
             </html>
             
         dtoverlay=pi3-miniuart-bt
        
     ![WhatsApp Image 2024-05-16 at 1 06 10 PM](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/cc18955f-f3c9-4b33-b03a-6d1be35ef3f4)
     Guardar y salir con **CTRL+O** y **CTRL+X**. Reinicie su Raspberry Pi para que todos los cambios surtan efecto.
     
     **Paso 4 :** Se instalara el programa de Python 3. Escriba el sigiente comando:
     </body>
             </html>
             
         sudo apt update

     </body>
             </html>
             
         sudo apt upgrade

     </body>
             </html>
             
         sudo apt install python3-pip

     **Paso 5 :** Ahora instalemos la biblioteca Python RAK811. Escriba los siguientes comandos:

     </body>
             </html>
             
         sudo pip3 install rak811
    
   # Creacion de credenciales de seguridad y coneccion de ABP.
**Paso 1 :** Escriba el siguiente comando:
</body>
         </html>
             
    sudo nano Dev_Addr.py
    
La parte de **Dev_Addr** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
</body>
         </html>

    import secrets
    import binascii
         
    def generate_deveui():
    manufacturer_prefix = "00FF"  # Prefijo del fabricante (ejemplo se puende modificar las 2 ultimas letras)
    random_suffix = secrets.token_hex(3) 
    deveui = manufacturer_prefix + random_suffix
    return deveui.upper()

    # Genera un DevEUI
    deveui = generate_deveui()
    print("DevEUI:", deveui)
    
Guardar y salir con **CTRL+O** y **CTRL+X**. Este programa de Python se ejecutara para conocer el Device address que se accinara a nuestro dispositivo y sevira para la conexion ABP con el gateway y la aplicacion de Chirpstack.
**Paso 2 :** Escriba el siguiente comando:
</body>
         </html>
             
    sudo nano nwkey.py
   
La parte de **nwkey** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
</body>
         </html>
             
    import secrets
    import binascii
         
    def generate_network_key(length):
    # Genera una cadena de bytes aleatorios para la clave de red
    network_key_bytes = secrets.token_bytes(length)
    return binascii.hexlify(network_key_bytes).decode('utf-8').upper()
         
    # Genera una clave de red de 128 bits (16 bytes)
    network_key = generate_network_key(16)
    print("Network Key:", network_key)
   
Guardar y salir con **CTRL+O** y **CTRL+X**. Consecutivamente escriba el siguiente comando:
</body>
         </html>
             
    sudo nano applkey.py
    
La parte de **applkey** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
</body>
         </html>
             
    import secrets
    import binascii

    def generate_application_key(length):
    # Genera una cadena de bytes aleatorios para la clave de aplicación
    app_key_bytes = secrets.token_bytes(length)
    return binascii.hexlify(app_key_bytes).decode('utf-8').upper()
         
    # Genera una clave de aplicación de 128 bits (16 bytes)
    application_key = generate_application_key(16)
    print("Application Key:", application_key) 
   
Guardar y salir con **CTRL+O** y **CTRL+X**. Una vez culminado este ultimoc codigo ejecutamos los codigos de Python, procurando copiar los datos que arrojaran estos codigos.
**Paso 3 :** Escribimos el siguiente comando:
</body>
         </html>
             
    sudo nano ttn_secrets.py 
   
La parte de **ttn_secrets** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
</body>
         </html>
         
    """ABP Template."""
    """Device address.
    The device address must be in big-endian format, so most-significant-byte 
    first.
    For Chirpsatck issued addresses the first byte should be 0x26
    """
    DEV_ADDR = '0x0'
         
    """Network Session Key.
    The device address must be in big-endian format, so most-significant-byte
    first.
    """
    NWKS_KEY = ''
         
    """App Session Key.
    The device address must be in big-endian format, so most-significant-byte
    first.
    """
    APPS_KEY = ''
    
Los datos obtenidos en el **paso 2** se agregaran entre las comillas '' (ejemplo: en la parte de DEV_ADDR ='0X0ff9def0e'). Guardar y salir con **CTRL+O** y **CTRL+X**.
**Paso 4 :** Obtener el el Device EUI. Escriba en el siguiente comando:
</body>
         </html>
             
    sudo nano Dev_EUI.py
   
La parte de **Dev_EUI** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
</body>
         </html>

    import secrets
    import binascii
         
    def generate_random_hex(length):
    # Genera una cadena de bytes aleatorios y luego la convierte a hexadecimal
    random_bytes = secrets.token_bytes(length // 2)
    random_hex = binascii.hexlify(random_bytes).decode('utf-8')
    return random_hex.upper()
         
    # Genera un identificador único de 16 caracteres hexadecimales
    eui16 = generate_random_hex(16)
    print("EUI de 16 dígitos:", eui16)
    
Guardar y salir con **CTRL+O** y **CTRL+X**. Ejecuta este codigo y guarda el Dev_EUI el cual sera necesario para conectar el dispositivo en la plataforma de Chirpstack.
# Creacion de codigos de sensores utilizados en la estacion de monitoreo.
   # Sensor BME 280.
   # Sensor SCD 40.
   # Sensor SEN 55.
   # Sensores Alphasense.
   # Codigo de para mandar datos a Chirpstack.
# Instalar chirpstack y The Thingsboard en docker o cualquier otro sistema operativo.
En la pagina oficial de [Chirpstack](https://www.chirpstack.io/docs/getting-started/docker.html) se describen los pasos para instalar el chirpstack en tu servidor segun el software que maneje. Una vez instalado se tiene que abrir una terminal de programacion o coloquialmente conocida como cmd. Escriba el siguiente comando:
</body>
         </html>
             
    cd chirpstack-docker
   
Si se encuentra instalado en Docker, posteriormente escriba en siguiente comando:
</body>
         </html>
             
    sudo nano docker-compose.yml
      
En ese codigo se tiene que modificar los siguientes acpectos 
</body>
         </html>
         
    version: "3"
         
    services:
    chirpstack:
    image: chirpstack/chirpstack:4
    command: -c /etc/chirpstack
    restart: unless-stopped
    volumes:
      - ./configuration/chirpstack:/etc/chirpstack
      - ./lorawan-devices:/opt/lorawan-devices
    depends_on:
      - postgres
      - mosquitto
      - redis
    environment:
      - MQTT_BROKER_HOST=mosquitto
      - REDIS_HOST=redis
      - POSTGRESQL_HOST=postgres
    ports:
      - 80:8080
         
    thingsboard:
    image: thingsboard/tb-postgres
    volumes:
      - thingsboarddata:/data
    ports:
      - 9090:9090
         
    chirpstack-gateway-bridge:
    image: chirpstack/chirpstack-gateway-bridge:4
    restart: unless-stopped
    ports:
      - 1699:1700/udp
    volumes:
      - ./configuration/chirpstack-gateway-bridge:/etc/chirpstack-gateway-bridge
    environment:
      - INTEGRATION__MQTT__EVENT_TOPIC_TEMPLATE=us915_1/gateway/{{ .GatewayID }}/event/{{ .EventType }}
      - INTEGRATION__MQTT__STATE_TOPIC_TEMPLATE=us915_1/gateway/{{ .GatewayID }}/state/{{ .StateType }}
      - INTEGRATION__MQTT__COMMAND_TOPIC_TEMPLATE=us915_1/gateway/{{ .GatewayID }}/command/#
    depends_on:
      - mosquitto
         
    chirpstack-gateway-bridge-basicstation:
    image: chirpstack/chirpstack-gateway-bridge:4
    restart: unless-stopped
    command: -c /etc/chirpstack-gateway-bridge/chirpstack-gateway-bridge-basicstation-us915_1.toml
    ports:
      - 3001:3001
    volumes: 
      - ./configuration/chirpstack-gateway-bridge:/etc/chirpstack-gateway-bridge
    depends_on:
      - mosquitto
           
    chirpstack-rest-api:
    image: chirpstack/chirpstack-rest-api:4
    restart: unless-stopped
    command: --server chirpstack:80 --bind 0.0.0.0:81 --insecure
    ports:
      - 8000:8001
    depends_on:
      - chirpstack
         
    postgres:
    image: postgres:14-alpine
    restart: unless-stopped
    volumes:
      - ./configuration/postgresql/initdb:/docker-entrypoint-initdb.d
      - postgresqldata:/var/lib/postgresql/data
    environment:
      - POSTGRES_PASSWORD=root
           
    redis:
    image: redis:7-alpine 
    restart: unless-stopped
    command: redis-server --save 300 1 --save 60 100 --appendonly no
    volumes:
      - redisdata:/data
         
    mosquitto:
    image: eclipse-mosquitto:2
    restart: unless-stopped
    ports:
      - 1884:1883
    volumes: 
      - ./configuration/mosquitto/config/:/mosquitto/config/

    volumes:
    postgresqldata:
    redisdata:
    thingsboarddata:
    
Posteriormente de los ajustes al codigo guarde y salga con **CTRL+O** y **CTRL+X**. Ejecute el anterior codigo con este comando en la consola:
</body>
         </html>
             
    sudo docker-compose up
    
Una vez ejecutado se podra acceder a la aplicacion web,con la IP que se acciona al servidor o donde se tenga instalado el docker.
# Configuracion del gateway Laird Sentrius.





         

     

     

             
   
