## Guía para la creación de una estación ambiental
Esta guía esta dirigida a toda aquella persona que tenga la necesidad de implementar una estación de monitoreo ambiental con los siguientes elementos **motor de raspian** de una raspberry pi zero w , **modulo LoRaWan**, además de la plataforma de **chirpstack y the thingsboard**. Se establecen enlaces y gráficos para análisis de datos y un mejorar la comprensión  de las condiciones ambientales. 
   ## Configuración del controlador raspberry pi zero w
Se describe con detalle los pasos a seguir para configura el controlador que desarrollara las funciones de otorgar órdenes a los sensores conectados y se enlazara al protocolo de red LoRa WAN para el envió de la información recolectada. Para las configuraciones iniciales se consultó la siguiente página:
   - https://learn.pi-supply.com/make/getting-started-with-the-raspberry-pi-lora-node-phat/

     ## Descargar e instalar imagen del sistema raspian
     [Descargar](https://downloads.raspberrypi.com/raspios_oldstable_lite_arm64/images/raspios_oldstable_lite_arm64-2024-03-12/2024-03-12-raspios-bullseye-arm64-lite.img.xz?_gl=1*sv35ox*_ga*MzQ2MTQ5NjU2LjE3MDc4NDI4Nzg.*_ga_22FD70LWDS*MTcxNTEwNzQ2OC40LjEuMTcxNTEwNzUwMi4wLjAuMA..) la imagen **Raspberry Pi OS (Legacy) Lite ver.6.1** utilizada como software de la estación ambiental, la cual estará en un formato **.zip**, se recomienda la utilización de la aplicación [WinRAR](https://www.win-rar.com/open-zip-file.html?&L=0) para extraer los datos de la imagen. 
     Tomar en cuenta que esta versión es la 6.1 y pueden existir actualizaciones, para obtener más información sobre los sistemas operativos disponibles para Raspberry Pi, visita [El sitio oficial de Raspberry Pi](https://www.raspberrypi.com/software/operating-systems/).
     Inserte una micro-usb de al menos 8 GB de espacio en almacenamiento, para su posterior formateo con la aplicación [SD Card Formatter](https://www.sdcard.org/downloads/formatter/), como recomendación. Una vez formateada la tarjeta de memoria y extraída la imagen del software, descarga el **Install Raspberry Pi OS using Raspberry Pi Imager** contenido en [el sitio oficial de Raspberry Pi](https://www.raspberrypi.com/software/). la cual nos servirá para instalar la imagen del sistema operativo raspian en la miro-usb.
     
     ## Instalar la biblioteca RAK811 Python
     **Paso 1 :** En primer lugar, deberás conectar tu Raspberry Pi al Wi-Fi. En la terminal escriba el siguiente comando:
      </body>
             </html>
                      
         sudo raspi-config
    
     Seleccione la opción **System Options**, consecutivamente **Wireless LAN**, posteriormente siga las instrucciones para ingresar las credenciales de la red Wi-Fi comenzando por el usuario y consecutivamente la contraseña para acceder que la raspberry pi zero w se conecte a la red de internet.
  
     <!DOCTYPE html>
     <html>
        <head>
           <meta charset="UTF-8">
           
        </head>
        <body>
        
     <table>
     </thead>
     <tr>
        <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp%20Image%202024-05-16%20at%2012.31.55%20PM.jpeg"/></td>
        <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-07 at 3.13.44 PM.jpeg"/></td>
     </tr>
        <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-07 at 3.13.44 PM (1).jpeg"/></td>
        <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 12.18.30 PM.jpeg"/></td>
     </tr>
     </table>
     </body>
     </html>
     En las anteriores imágenes se visualizan los pasos a seguir para conseguir la conexión a internet de manera inalámbrica desde las opciones a acceder hasta la conexión exitosa del dispositivo.
     
     **Paso 2 :** Antes de reiniciar la raspberry pi, habilite el hardware serial en Raspberry Pi y deshabilite la consola serial. Vuelva al inicio de las configuraciones y seleccione **Interface Options**, posteriormente **Serial Port** consecutivamente **No** y por ultimo **Yes** como se muestra en las siguientes imágenes. 
     <!DOCTYPE html>
     <html>
        <head>
           <meta charset="UTF-8">
        </head>
        <body>
     <table>
     </thead>
     <tr>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 12.37.48 PM.jpeg"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 12.41.38 PM.jpeg"/></td>
     </tr>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 12.41.38 PM (1).jpeg"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 12.41.39 PM.jpeg"/></td>
     </tr>
     </table>
     </body>
     </html>
     
     Una vez hecho esto selecciona **SSH** y actívalo, esto con la finalidad de lograr una conexión inalámbrica a la raspberry, del mismo modo activa el **SPI** y **I2C**.
     <!DOCTYPE html>
     <html>
        <head>
           <meta charset="UTF-8">
        </head>
        <body>
     <table>
     </thead>
     <tr> 
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 12.41.39 PM (1).jpeg"/></td>
        <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 12.41.40 PM.jpeg"/></td>
     </tr>
     </table>
     </body>
     </html>

     **Paso 3 :** Escriba el siguiente comando en la raspberry pi zero:
     </body>
             </html>
             
         sudo nano /boot/config.txt
     
     Desplácese hacia abajo del código y agregue la siguiente línea:
      </body>
             </html>
             
         dtoverlay=pi3-miniuart-bt
        
     <!DOCTYPE html>
     <html>
        <head>
           <meta charset="UTF-8">
           
        </head>
        <body>
        
     <table>
     </thead>
     <tr>
        <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 1.06.10 PM.jpeg"/></td>
     </tr>
     </table>
     </body>
     </html>
     
     Guardar y salir con **CTRL+O** y **CTRL+X**. Reinicie la Raspberry Pi para que todos los cambios surtan efecto.
     
     **Paso 4 :** Instalación el programa de Python 3. Escriba el sigiente comando:
     </body>
             </html>
             
         sudo apt update

     </body>
             </html>
             
         sudo apt upgrade

     </body>
             </html>
             
         sudo apt install python3-pip
     
      </body>
             </html>
             
         sudo pip3 install --upgrade pip
     </body>
             </html>
             
         sudo pip3 install adafruit-blinka 

     **Paso 5 :** Instala la biblioteca Python RAK811. Escriba el siguiente comando:

     </body>
             </html>
             
         sudo pip3 install rak811
    
   ## Creación de credenciales de seguridad y conexión de ABP.
**Paso 1 :** Escriba el siguiente comando:
</body>
         </html>
             
    sudo nano Dev_Addr.py
    
La parte de **Dev_Addr** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahí se desplegara una consola, escriba el siguiente código:
</body>
         </html>

    import secrets
         
    def generate_deveui():
        manufacturer_prefix = "00FF"  # Prefijo del fabricante (ejemplo se puende modificar las 2 ultimas letras)
        random_suffix = secrets.token_hex(3) 
        deveui = manufacturer_prefix + random_suffix
        return deveui.upper()

    # Genera un DevEUI
    deveui = generate_deveui()
    print("DevEUI:", deveui)
    
Guardar y salir con **CTRL+O** y **CTRL+X**. Este programa de Python se ejecutará para conocer el Device address que se asignará a el dispositivo, 
 ademas de servir para la conexión ABP con el Gateway y la aplicación de Chirpstack. 
El código consta de *import secrets* el cual importa el módulo *secrets*, que proporciona formas de generar números aleatorios de manera segura para criptografía, posteriormente se define la función *generate_deveui():* la cual su mecanismo de acción es devolver el **DevEui**, esta función consta de *manufacturer_prefix = "00FF"* que asigna el prefijo del fabricante que se  puede modificar para la identificación del dispositivo según sean las necesidades del usuario, posteriormente *random_suffix = secrets.token_hex(3)* este genera un numero aleatorio de 6 caracteres hexadecimales contenido en 3 bytes utilizando la función *token_hex* y el módulo *secrets* para  garantizar que la respuesta final sea única y se genere de manera segura, consecutivamente *deveui = manufacturer_prefix + random_suffix*  combina el numero aleatorio creado y el prefijo del fabricante para formar el DevEUI, por ultimo *return deveui.upper()* devuelve el DevEUI en mayúsculas.
La última parte del código contiene la orden *deveui = generate_deveui()* que llama la función *generate_deveui* y almacena la información en la variable *deveui* para que posteriormente se imprima en la consola con la orden *print("DevEUI:", deveui)*. 
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
   
Guardar y salir con **CTRL+O** y **CTRL+X**. Este código contiene la indicación de *import secrets* la cual importa el módulo *secrets*, que proporciona formas de generar números aleatorios de manera segura para criptografía y *import binascii* que importa el módulo *binascii*, el cual contiene funciones para convertir entre binarios y ASCII, posteriormente se define la función *def generate_network_key(length)* que toma el argumento *length* que especifica la longitud de la clave en bytes, además esta función la componen las líneas de código *network_key_bytes = secrets.token_bytes(length)*  la cual genera una cadena de bytes aleatoria especificada por la función *token_bytes* del modulo *secrets*, consecutivamente la línea *return binascii.hexlify(network_key_bytes).decode('utf-8').upper()* convierte la cadena de bytes aleatorios a una hexadecimal con *binascii.hexlify* posteriormente se decodifica la cadena hexadecimal a una cadena de texto con *decode('utf-8')* y la convierte en mayúscula con *upper()*.
Por último el código contiene la línea *network_key = generate_network_key(16)* la cual llama a la función de *generate_network_key* con un argumento **16** que genera una clave de 16 bytes y posteriormente se imprime el valor obtenido en la consola con el comando *print("Network Key",network_key). Posteriormente a la configuración y guardado del código escriba el siguiente comando. 
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
   
Guardar y salir con **CTRL+O** y **CTRL+X**. Este código es particularmente similar al anterior solo con pequeñas diferencias en cuestión de la variable *application_key*. Una vez culminado este último código se ejecutan los progaramas anteriormente creados de Python, procurando copiar los datos que arrojen estos.
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
    DEV_ADDR = '0x26011BDA'  # Reemplaza con la dirección real del dispositivo
         
    """Network Session Key.
    The device address must be in big-endian format, so most-significant-byte
    first.
    """
    NWKS_KEY = '00112233445566778899AABBCCDDEEFF'  # Reemplaza con el app_key obtenido
         
    """App Session Key.
    The device address must be in big-endian format, so most-significant-byte
    first.
    """
    APPS_KEY = 'FFEEDDCCBBAA99887766554433221100'  # Reemplaza con el app_key obtenido
    
Reemplazo los datos obtenidos en el **paso 2**. Guardar y salir con **CTRL+O** y **CTRL+X**. El código anterior contiene las llaves de conexión para el network server y el aplication server, además del identificador que se le otorgará al dispositivo a conectar, esto con la finalidad simplificar los códigos de muestreo y envió de datos. 
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
    
Guardar y salir con **CTRL+O** y **CTRL+X**. Este código contiene la indicación de *import secrets* la cual importa el módulo *secrets*, que proporciona formas de generar números aleatorios de manera segura para criptografía y *import binascii* que importa el módulo *binascii*, el cual contiene funciones para convertir entre binarios y ASCII, posteriormente se define la función *def generate_random_hex(length)* la cual contiene el parámetro *length* el cual define la longitud de la cadena hexadecimal deseada, consecutivamente la línea del código *random_bytes = secrets.token_bytes(length // 2)*, genera una cadena de bytes aleatorias con la mitad de longitud que la cadena de *length*, posteriormente la linea *random_hex = binascii.hexlify(random_bytes).decode('utf-8')* convierte la cadena de bytes a una cadena hexadecimal y después decodifica a una cadena de caracteres para que *return random_hex.upper()* devuelva la cadena hexadecimal en mayúsculas.
Por último el *eui16 = generate_random_hex(16)* hace el llamado a la funcion para generar la cadena hexadecimal de 16 caracteres y finaliza con la impresión del valor en la consola con *print("EUI de 16 dígitos:", eui16)*. Ejecuta el código y guarda el Dev_EUI el cual será el identificador del dispositivo en la red LoRaWAN y se conectara a la plataforma de Chirpstack.
## Creación de códigos de sensores utilizados en la estación de monitoreo.

   ## Sensores Alphasense.
   Escriba en el siguiente comando:
   </body>
         </html>
             
    sudo nano loraysensores.py
    
  En el comando la parte **loraysensores** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
   </body>
         </html>

    from random import randint
    from sys import exit
    from time import sleep
    import board
    import busio
    import adafruit_ads1x15.ads1115 as ADS
    from adafruit_ads1x15.analog_in import AnalogIn
    from rak811.rak811 import Mode, Rak811
    from ttn_secrets import APPS_KEY, DEV_ADDR, NWKS_KEY
    
    # Initialize the I2C interface
    i2c = busio.I2C(board.SCL, board.SDA)
    # Create an ADS1115 object
    ads1 = ADS.ADS1115(i2c, address=0x48)
    ads2 = ADS.ADS1115(i2c, address=0x49)
    
    # Define the analog input channels
    ads1_channel0 = AnalogIn(ads1, ADS.P0)
    ads1_channel1 = AnalogIn(ads1, ADS.P1)
    ads1_channel2 = AnalogIn(ads1, ADS.P2)
    ads1_channel3 = AnalogIn(ads1, ADS.P3)
    
    ads2_channel0 = AnalogIn(ads2, ADS.P0)
    ads2_channel1 = AnalogIn(ads2, ADS.P1)
    ads2_channel2 = AnalogIn(ads2, ADS.P2)
    ads2_channel3 = AnalogIn(ads2, ADS.P3)
    
    lora = Rak811()
    
    # Most of the setup should happen only once...
    
    lora.hard_reset()
    lora.mode = Mode.LoRaWan
    lora.band = 'US915'
    lora.set_config(dev_addr=DEV_ADDR,
                    apps_key=APPS_KEY,
                    nwks_key=NWKS_KEY)

                    
    lora.join_abp()
    # Note that DR is different from SF and depends on the region
    # See: https://docs.exploratory.engineering/lora/dr_sf/
    # Set Data Rate to 5 which is SF7/125kHz for EU868
    lora.dr = 2
    
    # Read analog inputs
    ads1_values = [ads1_channel0.value, ads1_channel1.value, ads1_channel2.value, ads1_channel3.value]
    ads2_values = [ads2_channel0.value, ads2_channel1.value, ads2_channel2.value, ads2_channel3.value]
    
    # Convert values to strings
    ads1_str = " ".join(map(str, ads1_values))
    ads2_str = " ".join(map(str, ads2_values))
    
    print('Paquete enviado')
    lora.send('1.1' + 'ADS1: ' + ads1_str + '| ADS2: ' + ads2_str, confirm=False)
    lora.close()
    exit(0)
    
   El código anterior se compone de 8 pasos para su funcionamiento: 
   **Paso 1 :** Se importan los módulos y archivos a utilizar dentro del código en este caso *random, sys y time*, son módulos de Python para el control del sistema y control del tiempo, por otra parte *board, busio, adafruit_ads1x15.ads1115 y AnalogIn*  son módulos de las librerías de Adafruit para manejar interfaces de hardware, conversores ADC y entradas analogicas. Para la conexión de LoRaWAN se establece *rak811.rak811* el cual es el módulo para controlar *LoRa RAK811*, por último el archivo *ttn_secrets* o el nombre del archivo que contenga las credenciales de conexión a LoRaWAN como la Aplication Key, Network key y el Device address, esto con la finalidad de una conexión cifrada entre sensor, red LoRa y el servidor de red.
   **Paso 2 :** La inicialización del I2C con la instrucción *i2c = busio.I2C(board.SCL, board.SDA)* en la cual se utiliza los pines de la raspberry SCL y SDA.
   **Paso 3 :** Creación de objetos ADS1115 en donde se crean 2 instancias *ads1 = ADS.ADS1115(i2c, address=0x48) y ads2 = ADS.ADS1115(i2c, address=0x49)*, por la utilización de 2 dispositivos convertidores de señal análoga a digital utilizando el I2C para la conexión con direcciones diferentes.
   **Paso 4 :** Definición de canales para entrada de datos analógicos de los sensores de gas por lectura principal y de corrección, otorgando un total de 8 lecturas diferentes y por consiguiente 8 definiciones de canales en los pines o, 1, 2 y 3 de los ADS1115.
   **Paso 5 :** Definición e inicialización del módulo LoRa RAK811, en donde se define que *lora* ocupara el Rak811, con una configuración de operación en modo LoRaWAN en la reguion US915, ademas de configurar las claves de seguridad (dev_addr=DEV_ADDR, apps_key=APPS_KEY, nwks_key=NWKS_KEY) y se realiza la conexion atravez del modo **ABP**, por último de establece la tasa de datos *lora.dr = 2* que es para US915_1.
   **Paso 6 :** Lectura de entradas analogicas las cuales se identificaran con la orden *ads1_values y ads2_values*, consecutivamente en las lineas de codigo *[ads1_str = " ".join(map(str, ads1_values))] y [ads2_str = " ".join(map(str, ads2_values))]* convierten los valores de entrada en cadenas de texto separadas poe espacios.
   **Paso 7 :** Envio de datos atraves de LoRa, en donde se encuentra la leyenda de *paquete enviado* cuando se hayan enviado correctamente los datos atravez de lora, ademas de expecificar el formato de envio del mensaje con la linea *lora.send('1.1' + 'ADS1: ' + ads1_str + '| ADS2: ' + ads2_str, confirm=False)*, en la cual se implementa un identificador para que en posteriores procesos del analisis de datos sea mas eficiente identifiacar y procesar la informacion, este identificador va acompañado de los valores de los *ADS1115*, por último se cierra la conexion y finaliza el programa. 
Para poder ejecutar el codigo anterior es necesario descargar las librerias de **Adafruit circuitpython ads1x15**. Escriba el siguiente comando:
   </body>
         </html>
              
    sudo pip3 install adafruit-circuitpython-ads1x15
    
   ## Sensor BME 280.
   Escriba en el siguiente comando:
   </body>
         </html>
             
    sudo nano lorabme.py
    
   La parte de **lorabme** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
   </body>
         </html>
    import board
    import time
    from adafruit_bme280 import basic as adafruit_bme280
    from random import randint
    from sys import exit
    from time import sleep
    
    from rak811.rak811 import Mode, Rak811
    from ttn_secrets import APPS_KEY, DEV_ADDR, NWKS_KEY
    
    # Setup LoRa
    lora = Rak811()
    lora.hard_reset()
    lora.mode = Mode.LoRaWan
    lora.band = 'US915'
    lora.set_config(dev_addr=DEV_ADDR,
                    apps_key=APPS_KEY,
                    nwks_key=NWKS_KEY)
    lora.join_abp() 
    lora.dr = 2
    
    # Setup BME280 sensor
    i2c = board.I2C()   # uses board.SCL and board.SDA
    bme280 = adafruit_bme280.Adafruit_BME280_I2C(i2c, address=0x76)
    bme280.sea_level_pressure = 1013.25
    
    
    
    # Read BME280 sensor data
    identifier = "1.2"
    temperature = "{:.2f}".format(bme280.temperature)
    humidity = "{:.2f}".format(bme280.relative_humidity)
    pressure = "{:.2f}".format(bme280.pressure)
    altitude = "{:.2f}".format(bme280.altitude)
    
    # Format data as bytes
    data_to_send = ','.join([identifier, temperature, humidity, pressure, altitude])
    data_bytes = bytes(data_to_send, 'utf-8')
    
    # Send data via LoRaWAN
    print('Paquete enviado:', data_to_send)
    lora.send(data_bytes, confirm=False)
    
    lora.close()
    exit(0)
    
   Para poder ejecutar el codigo es necesario descargar las librerias de **Adafruit circuitpython bme280**. Escriba el siguiente comando:
   </body>
         </html>
              
    sudo pip3 install adafruit-circuitpython-bme280
    
   ## Sensor SCD 40.
   Escriba en el siguiente comando:
   </body>
         </html>
             
    sudo nano lorascd40.py
    
   La parte de **lorascd40** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
   </body>
         </html>
         
    import time
    import board
    import adafruit_scd4x
    from datetime import datetime
    
    from rak811.rak811 import Mode, Rak811
    from ttn_secrets import APPS_KEY, DEV_ADDR, NWKS_KEY
    
    # Configurar LoRaWAN
    lora = Rak811()
    lora.hard_reset()
    lora.mode = Mode.LoRaWan
    lora.band = 'US915'
    lora.set_config(dev_addr=DEV_ADDR, 
                    apps_key=APPS_KEY, 
                    nwks_key=NWKS_KEY)
    lora.join_abp()
    lora.dr = 2
    
    # Configurar sensor SCD4X
    i2c = board.I2C()
    scd4x = adafruit_scd4x.SCD4X(i2c)
    scd4x.start_periodic_measurement()
    
    #Identificador del sensor
    identifier = "1.3"
    
    # Función para enviar datos a través de LoRaWAN
    def enviar_datos_lorawan(identifier, co2, temperatura, humedad):
        datos_csv = "{},{},{},{}".format(identifier, co2, temperatura, humedad)
        lora.send(datos_csv, confirm=False)
        print("Datos enviados exitosamente por LoRaWAN:", datos_csv)
        
    try:
        muestras_realizadas = 1
        while muestras_realizadas < 2:
            if scd4x.data_ready:
                co2 = round(scd4x.CO2, 2)
                temperatura = round(scd4x.temperature, 2)
                humedad = round(scd4x.relative_humidity, 2)
                
                # Imprimir los valores de las mediciones del sensor
                print("CO2:", co2, "ppm")
                print("Temperatura:", temperatura, "*C")
                print("Humedad:", humedad, "%")
                
                # Enviar solo los valores de las mediciones a través de LoRaWAN
                enviar_datos_lorawan(identifier, co2, temperatura, humedad)
                
                muestras_realizadas += 1
                if muestras_realizadas == 2:
                    break
                    
            time.sleep(1)
    except KeyboardInterrupt:
        print('Interrupción de teclado, finalizando...')
    finally:
        scd4x.stop_periodic_measurement()
        lora.close()

   Para poder ejecutar el codigo es necesario descargar las librerias de **Adafruit circuitpython scd4x**. Escriba el siguiente comando:
   </body>
         </html>
              
    sudo pip3 install adafruit-circuitpython-scd4x
    
   ## Sensor SEN 55.
   Escriba en el siguiente comando:
   </body>
         </html>
             
    sudo nano lorasen55.py
    
   La parte de **lorasen55** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
   </body>
         </html>

    import time
    from sensirion_i2c_driver import I2cConnection, LinuxI2cTransceiver
    from sensirion_i2c_sen5x import Sen5xI2cDevice
    from rak811.rak811 import Mode, Rak811
    from ttn_secrets import APPS_KEY, DEV_ADDR, NWKS_KEY

    
    def initialize_lora():
        lora = Rak811()
        lora.hard_reset()
        while True:
            try:
                lora.mode = Mode.LoRaWan
                lora.band = 'US915'
                lora.set_config(dev_addr=DEV_ADDR,
                                apps_key=APPS_KEY,
                                nwks_key=NWKS_KEY)
                lora.join_abp()
                lora.dr = 2
                return lora
            except Exception as e:
                print("Error iniciando LoRaWAN:", e)
                print("Reintentando...")
                time.sleep(10)  # Retry after 10 seconds
                
    def send_data_lorawan(lora, data):
        try:
            lora.send(data, confirm=False)
            print("Paquete enviado")
        except Exception as e:
            print("Error enviando datos por LoRaWAN:", e)
            
    def read_sensor_values(device):
        # Start measurement
        device.start_measurement()
        
        # Lists to store measured values
        pm1_0_values = []
        pm2_5_values = []
        pm4_0_values = []
        pm10_0_values = []
        humidity_values = []
        temperature_values = []
        
        for _ in range(10):
            # Wait until next result is available
            print("\nEsperando nuevos datos...")
            while device.read_data_ready() is False:
                time.sleep(0.1)
                 
            # Read measured values -> clears the "data ready" flag
            values = device.read_measured_values()
             
            # Store measured values
            pm1_0_values.append(values.mass_concentration_1p0.physical)
            pm2_5_values.append(values.mass_concentration_2p5.physical)
            pm4_0_values.append(values.mass_concentration_4p0.physical)
            pm10_0_values.append(values.mass_concentration_10p0.physical)
            humidity_values.append(values.ambient_humidity.percent_rh)
            temperature_values.append(values.ambient_temperature.degrees_celsius)
            
            # Print current measured values
            print("Concentración de masa PM 1.0:   {:.1f} µg/m^3".format(values.mass_concentration_1p0.physical))
            print("Concentración de masa PM 2.5:   {:.1f} µg/m^3".format(values.mass_concentration_2p5.physical))
            print("Concentración de masa PM 4.0:   {:.1f} µg/m^3".format(values.mass_concentration_4p0.physical))
            print("Concentración de masa PM 10.0:  {:.1f} µg/m^3".format(values.mass_concentration_10p0.physical))
            print("Humedad Ambiental:           {:.2f} %RH".format(values.ambient_humidity.percent_rh))
            print("Temperatura Ambiental:        {:.2f} °C".format(values.ambient_temperature.degrees_celsius))
            
            # Read device status
            status = device.read_device_status()
            print("Estatus del dispositivo: {}\n".format(status))
            
        # Stop measurement
        device.stop_measurement()
        print("Medición detenida.")
        
        # Calculate average values
        avg_pm1_0 = sum(pm1_0_values) / len(pm1_0_values)
        avg_pm2_5 = sum(pm2_5_values) / len(pm2_5_values)
        avg_pm4_0 = sum(pm4_0_values) / len(pm4_0_values)
        avg_pm10_0 = sum(pm10_0_values) / len(pm10_0_values)
        avg_humidity = sum(humidity_values) / len(humidity_values)
        avg_temperature = sum(temperature_values) / len(temperature_values)
        
        # Format the data as CSV string
        csv_data = "{:.2f},{:.2f},{:.2f},{:.2f},{:.2f},{:.2f}".format(
            avg_pm1_0, avg_pm2_5, avg_pm4_0, avg_pm10_0, avg_humidity, avg_temperature
        )
        
        return csv_data
        
    try:
        lora = initialize_lora()
        
        # Initialize I2C transceiver
        i2c_transceiver = LinuxI2cTransceiver('/dev/i2c-1')
        device = Sen5xI2cDevice(I2cConnection(i2c_transceiver))
        
        # Read sensor values
        csv_data = read_sensor_values(device)
        # Print and send data via LoRaWAN
        print("Mandando datos vía LoRaWAN...")
        print("Datos (CSV format):", csv_data)
        send_data_lorawan(lora, '1.4, ' + csv_data)
        
    finally:
        lora.close()
        i2c_transceiver.close()
   Para poder ejecutar el codigo es necesario descargar las librerias de **Sensirion i2c driver y Sensirion i2c sen5x**. Escriba el siguiente comando:
   </body>
      </html>
              
    sudo pip3 install sensirion-i2c-driver
   </body>
      </html>
              
    sudo pip3 install sensirion-i2c-sen5x
   
   ## Codigo de para mandar datos a Chirpstack.
   La funcion basica del siguiente codigo es enviar datos recabados por los sensores a la plataforma de chirpstack atraves de LoRaWan. Escriba en el siguiente comando:
   </body>
         </html>
             
    sudo nano Conjuto_de_sensores.py
    
   La parte de **Conjuto_de_sensores** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo: 
   </body>
         </html>
    import subprocess
    import time
    import sys
    
    try:
        while True:
            try:
                print('Iniciando nuevo ciclo de mediciones')
                print('            ')
                print('            ')
                print('            ')
                print('---------------------------------------------')
                # Ejecutar ADS1115
                print('Iniciando sensores Alphasense')
                subprocess.run(["python3", "loraysensores.py"])
                print('Alphasense, muestra exitosa')
                print('______________________________________________')
                print('  ')
                # Ejecutar bme280
                print('Iniciando sensor bme280')
                subprocess.run(["python3", "lorabme.py"])
                print('bme280, muestra exitosa')
                print('______________________________________________')
                print('  ')
                # Ejecutar scd40
                print('Iniciando sensor scd40')
                subprocess.run(["python3", "lorascd40.py"])
                print('scd40, muestra exitosa')
                print('______________________________________________')
                print('  ')
                # Ejecutar sen55
                print('Iniciando sensor sen55')
                subprocess.run(["python3", "lorasen55.py"])
                print('sen55, muestra exitosa')
                print('______________________________________________')
                print('  ')
                print('            ')
                print('            ')
                print('            ')
                print('---------------------------------------------')
                print('Terminando ciclo de mediciones')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
                print('            ')
            except Exception as e:
                print("Error durante la ejecución del script:", e)
                
            #time.sleep(60)
            
    except KeyboardInterrupt:
        print("Programa interrumpido por el usuario.")
        sys.exit(0)     

   ## Crear un servicio de pytho3 en la raspberry pi zero w para que se ejcute automaticamente el codigo pra mandar datos a Chirpstack
   Escriba en el siguiente comando:
   </body>
         </html>
             
    sudo nano /etc/systemd/system/mi_script.service
   La parte de **Conjuto_de_sensores** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo: 
   </body>
         </html>
    [Unit]
    Description=Mi script de inicio
    After=network.target
    
    [Service]
    ExecStart=python3 /home/modulolorapizerow/Conjuto_de_sensores.py
    WorkingDirectory=/home/modulolorapizerow/
    StandardOutput=inherit
    StandardError=inherit
    Restart=always
    User=modulolorapizerow
    
    [Install]
    WantedBy=multi-user.target
    
   Modificar la **Description** si se requiere, ademas de **/home/modulolorapizerow/Conjuto_de_sensores.py** por la ubicacion del codigo que envia los datos de los sensores, en **WorkingDirectory** modifica **/modulolorapizerow/** por tu usuario de raspberry pi zero w que hayas colocado ademas de **User**. Guarda y cierra la consola con **CTRL+O** y **CTRL+X**.
   Para que el servicio pueda ejecutarse es necesario escribir los siguientes comandos:
   </body>
         </html>
             
    sudo systemctl daemon-reload
   </body>
         </html>
             
    sudo systemctl enable mi_script
   </body>
         </html>
             
    sudo systemctl start mi_script
   </body>
         </html>
             
    sudo systemctl status mi_script
   Cierra la consola con **CTRL+Z y Enter** 
    
## Instalar chirpstack y The Thingsboard en docker o cualquier otro sistema operativo.
En la pagina oficial de [Chirpstack](https://www.chirpstack.io/docs/getting-started/docker.html) se describen los pasos para instalar el chirpstack en tu servidor segun el software que maneje. Una vez instalado se tiene que abrir una terminal de programacion o coloquialmente conocida como cmd. Para la instalacion es necesario un sistema operativo que soporte el contenerdor de docker y temer conocimiento del puerto IP del equipo en donde se instalara el docker.
Escriba el siguiente comando para tener la IP del dispositivo linux o en su defecto de windows:

**Linux :**
</body>
         </html>
         
    ifconfig
Se deplegara informacion sobre las ip registradas, la direccion que se tiene que buscar es **eno1: inet *192.000.00.999***.

**Windows :**
</body>
         </html>
         
    ipconfig
Se deplegara informacion sobre las ip registradas, la direccion que se tiene que buscar es **Direccion IPv4 *192.000.00.999***.

**Instalar la libreria de chirpstack docker en linux**
Escriba el siguiente comando en la consola de linux:
</body>
         </html>
         
    git clone https://github.com/chirpstack/chirpstack-docker.git
    
Una vez instalada la libreria en la consola escriba el siguiente comando:    
</body>
         </html>
             
    cd chirpstack-docker
   
Posteriormente escriba en siguiente comando:
</body>
         </html>
             
    sudo nano docker-compose.yml
      
Se desplegara un scritp que se tiene que modificar para su mejor funcionalidad. Ejemplo del scrip modificado. 
**Script de docker original**
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
      - 8080:8080
      
    chirpstack-gateway-bridge:
    image: chirpstack/chirpstack-gateway-bridge:4
    restart: unless-stopped
    ports:
      - 1700:1700/udp
    volumes:
      - ./configuration/chirpstack-gateway-bridge:/etc/chirpstack-gateway-bridge
    environment:
      - INTEGRATION__MQTT__EVENT_TOPIC_TEMPLATE=eu868/gateway/{{ .GatewayID }}/event/{{ .EventType }}
      - INTEGRATION__MQTT__STATE_TOPIC_TEMPLATE=eu868/gateway/{{ .GatewayID }}/state/{{ .StateType }}
      - INTEGRATION__MQTT__COMMAND_TOPIC_TEMPLATE=eu868/gateway/{{ .GatewayID }}/command/#
    depends_on:https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#L715
      - mosquitto
      
    chirpstack-gateway-bridge-basicstation:
    image: chirpstack/chirpstack-gateway-bridge:4
    restart: unless-stopped
    command: -c /etc/chirpstack-gateway-bridge/chirpstack-gateway-bridge-basicstation-eu868.toml
    ports:
      - 3001:3001
    volumes:
      - ./configuration/chirpstack-gateway-bridge:/etc/chirpstack-gateway-bridge
    depends_on:
      - mosquitto
      
    chirpstack-rest-api:
    image: chirpstack/chirpstack-rest-api:4
    restart: unless-stopped
    command: --server chirpstack:8080 --bind 0.0.0.0:8090 --insecure
    ports:
      - 8090:8090
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
      - 1883:1883
    volumes: 
      - ./configuration/mosquitto/config/:/mosquitto/config/
      
    volumes:
    postgresqldata:
    redisdata:

    
**Paso 1 :** Modifica el codigo segun los siguientes parrafos. Escribe el siguiente parrafo debajo de **ports: - 8080:8080**.
</body>
         </html>
         
    thingsboard:
    image: thingsboard/tb-postgres
    volumes:
      - thingsboarddata:/data
    ports:
      - 9090:9090
Este parrafo instalara the thingsboard en el docker y otrogara un puerto de acceso a la pagina principal de la aplicacion.

**Paso 2 :** Identifica a **chirpstack-gateway-bridge:** en el cual en su estructura contiene a * environment:*, modifica los 3 parrafos que incluyen **eu868** por las siglas de la region en la que se este trabajando, en este caso se trabajo con **us915**. Esto servira para identificar la reguin en la que estas trabajando y poder conectar el gateway segun la reguion de trabajo.

**Paso 3 :** En el script identidica la siguiente linea **c /etc/chirpstack-gateway-bridge/chirpstack-gateway-bridge-basicstation-eu868.toml**, modificar **eu868** or las siglas de la region en la que se este trabajando, en este caso se trabajo con **us915_1**. Esto servira para identificar la reguin en la que estas trabajando y poder conectar el gateway segun la reguion de trabajo.

**Paso 4 :** Desplazate al finale del script y abajo de **redisdata:** escribe **thingsboarddata:**, esto con la dinalidad de crear una carpata de guardado de datos y configuraciones que realizen el la aplicacion de the thingsboard.

**Paso 5 :** Identifica el los **ports:** en el sript, en el primer **ports: - 8080:8080**, modifica el primer *8080* por **80** debera de quedar haci **ports: - 80:8080**. Para el segundo **ports: - 1700:1700/udp** modifica *1700* por **1699** debera visualizarse de la siguiente manera **ports: - 1699:1700/udp**. Como tercer **ports: - 1883:1883** modifica el primer *1883* por **1884** debera visualizarse de la siguiente manera **ports: - 1884:1883**. Tenga en cuenta los puertos dispibles a utilizar en su dispositivo, en caso de lo contrario que no esten disponibles modifique los puertos segun su criterio.
Concluidas las modificaciones guarde y salga con **CTRL+O** y **CTRL+X**. Ejemplo del script modificado y ajustado a la region us915.

**Version modificada**
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
    command: --server chirpstack:8080 --bind 0.0.0.0:8090 --insecure
    ports:
      - 8090:8090
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
 
Ejecute el anterior script con este comando en la consola:
</body>
         </html>
             
    sudo docker-compose up
    
Una vez ejecutado se podra acceder a la aplicacion web,con la IP que tenga su dispositivo con los puertos que coresponden a cada aplicacion. Para thingsboar el puerto es 9090 y para chirpstack el puerto es 80. Ejemplo **192.000.00.999:9090**
## Configuracion del gateway Laird Sentrius.
La configuaracion del gateway Laird Sentrius fue obtenida de la pagina oficial de [ezurio](https://www.ezurio.com/iot-devices/lorawan-iot-devices/sentrius-rg1xx-lorawan-gateway-wi-fi-ethernet-optional-lte-us-only), en donde se encontrara la documentacion del gateway [laird sentrius](https://www.ezurio.com/documentation/quick-start-guide-sentrius-rg1xx-v30),misma que sirve para configurar el gateway. En caso de que nose pueda configurar el gateway de la siguiente manera consutal la guia del gateway [laird sentrius](https://www.ezurio.com/documentation/quick-start-guide-sentrius-rg1xx-v30).   
**Paso 1 :** Conectar el gateway a la corriente y a un puerto de internat estable. Consecutivamente obtener la informacion de las direcciones contenidad de que se encuentran en el reverso del gateway o la caja del mismo. (Ejemplo)

<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 10-31-04.png"/></td>
</tr>
</table>
</body>
</html>

**Paso 2 :** Resetear el gataway de fabrica, presionanod primero el biton marcado como numero 2 en la imagen y consequitivamente el boton 3 durante 5 segundo una vez hecho esto se encenderan todas las luces del gateway y se ressteara. 
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 10-30-14.png"/></td>
</tr>
</table>
</body>
</html>

**Paso 3 :** Acceder al gateway por wifi o conexion fisica de cable ethernet.
   
   **Opcion 1 :** Acceder por wifi: Dejar presionado el boton de **User botton** en gateway durante 7 segundos, posteriormente conectarse desde su pc a la red WiFi: rg1xx2945D0. Para poder acceder a la pagina principar de gateway es necesario verificar los ultimos 6 digitos del Ethernet MAC ID los cuales tendras que modificar en el URL https://rg1xx**2945D0**.local. Modificado el URL copialo y pegalo en el buscador de tu preferencia. Para acceder 
   El usiario es :
   </body>
            </html>

    sentrius

   La contraseña es :
   </body>
            </html>
   
    RG1xx   

   **Opcion 2 :** Acceder por conexion fisica de cable ethernet:  conectar un cable ethernet al gateway en el espacio 5 **Ethernet conector**, posteriormente conectarlo aun router a que tambien estara concetada la pc mediante conexon fisica. Para poder acceder a la pagina principar de gateway es necesario verificar los ultimos 6 digitos del Ethernet MAC ID los cuales tendras que modificar en el URL https://rg1xx**2945D0**.local. Modificado el URL copialo y pegalo en el buscador de tu preferencia. Para acceder 
   El usiario es :
   </body>
            </html>

    sentrius

   La contraseña es :
   </body>
            </html>
   
    RG1xx   
**Paso 3 :** Una vez dentro del gateway configura la conexion wifi a la red de tu preferencia, no olvides que tendras que conectar tu pc a esa red para acceder al gateway con la misma URL. (Ejemplo) 
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 3.28.34 PM.jpeg"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 3.28.34 PM (1).jpeg"/></td>
</tr>
</table>
</body>
</html>

**Paso 4 :** Configura la red loRAWAN, en donde nos ubicaremos en la parte de **lora**, en esa seccion nos dirigiremos a **Forwarder** y ahi seleccionaremos el modo **semtech UDP Forwarder**, dentro del de este modo modificaremos el **Network server address** con la [direccion ip](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#Instalar-chirpstack-y-The-Thingsboard-en-docker-o-cualquier-otro-sistema-operativo)
de la pc en que instalamos el docker, chirptack y the thingsboard y modificaremos los **Port Up** y **Port Down** con los puertos que se registraron en esta la [linea 898](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md?plain=1#898), en la parte de port Up el primer numero que aparece y en la parte de port down el segundo numero. (Ejemplo)
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 3.27.48 PM.jpeg"/></td>
</tr>
</table>
</body>
</html>

**Paso 5 :** Plotear la red lora para comprovar su funcionalidad: Dirigirse a al apartado **Traffic** y presionar el recuadro **Poll Traffic**, se debera de empezar a visualizar informacion sobre mensajes que recibe el gateway sin que esten registrados en el mismo. (Ejemplo)
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-05-16 at 3.27.48 PM (1).jpeg"/></td>
</tr>
</table>
</body>
</html>

## Configuracion de la plataforma de Chirpctack.
Acceder a la pagina de **Chirpstack** con la direccion [ip](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#L715) de la pc en conjunto con el puerto que se accino a chirpstack en el [scritp](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#L885) o el que se haya accinado en tu caso. (Ejemplo) **192.000.00.999:80**
Una vez en la pagina nos aparecera la siguiente imagen:
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 10-32-31.png"/></td>
</tr>
</table>
</body>
</html>

El usuario y la contraseña por defaul el **admin**.
Una vez dentro de la plataforma aparecesala siguiente imagen 
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 10-33-42.png"/></td>
</tr>
</table>
</body>
</html>

Para configurar la platafroma se seguiran los siguientes pasos:
**Paso 1 :** Crear un Tenanst o cliente del Network server. Dirijete a la parte de Tenants, consecutivamente da clic en Add Tenant. Dentro del recuadro que aparece podras colocara el nombre de cliente de tu preferecia, ademas de poner una breve descripcion y configurar el perfil del gateway, ya sea publico, privado o aceptar muchos gateways. (Ejemplo).
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 10-34-37.png"/></td>
</tr>
</table>
</body>
</html>

Una vez configurado de clic en Sumit para gusrdar y cargar los cambios realizados.
**Paso 2 :** Crear un **Device Profiles**, para eso tenemos que ubicarnos en la pestaña del mismo nombre, una vez ahi nos dirijiramos a add device profile. La configuracion dependera de la reguion, el nombre que se le quiera otorgar al device profile, la cadena de reglas, version de mac y algoritmos a utilizar. (Ejemplo).
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 10-35-28.png"/></td>
</tr>
</table>
</body>
</html>

Hecho lo anterior dirigete a la pestaña de de Join (OTA/ABP), para esta configuracion existen 2 formas de conectra con la aplicacion los dispocitivos, ya sea por OTA o por ABP. 

*Conexion por OTA :* solo se dejara encendido sin hacer ningun cambio a la configuracion. (Ejemplo).
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 10-36-26.png"/></td>
</tr>
</table>
</body>
</html>

*Configuracion ABP :* Dependiendo de la reguion en que se encuentre, la configuracion de los radios variara, consulte la cartpeta de [Chirstack](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/tree/main/chirpstack), donde se pueden visualizar las reguiones por abreviatura y obtener esta configuraciones. (Ejemplo).
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 10-39-29.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-06 13-41-40.png"/></td>
</tr>
</table>
</body>
</html>

Consecutivamente despues de culminado esta configuracion, pasamos a la pestaña de Class-B, deja por defaul esa pestaña y dirigete a Class-C, enciende esta clase y en el recuadro de **Class-C confirmed downlink timeout (seconds)** colocamos 5 para que cada 5 segundos de descarge los datos del dispositivo. (Ejemplo) 
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 11-10-40.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 11-10-46.png"/></td>
</tr>
</table>
</body>
</html>

Ahora dirigete a la pestaña de Codec, aqui es importante conocer el cifrado de mensaje que se etsa manejando, ademas de los bytes por mensaje que llegan y muy importante que estos datos no varen en cifras numerias, en palabras mas sencillas si el tipo de digito que maneja todo el mensaje es 29.98, asegurate que no la configuracion del cofigo este configurada solamente para eso y no no vare en numeros de 3 cifras, te presento un ejemplo del codigo urilizado en lenguaje de javaScript para descifrar los mensajes enviados por los sensores utilizados.
</body>
         </html>
         
    function decodeUplink(input) {
    // Parse bytes from the input
    const bytes = input.bytes;
    
    // Decode the identifier (assuming it's already in text format)
    const identifier = String.fromCharCode(bytes[0], bytes[1], bytes[2]);
    
    // Variable para almacenar los datos decodificados
    let decodedData;
    
    // Variable para almacenar la fuente de los datos
    let dataSource;
    
    // Verificar el identificador y aplicar el proceso correspondiente
    if (identifier === "1.2") {
      // Proceso para el identificador BME
      const temperature = parseFloat(String.fromCharCode(bytes[4], bytes[5], bytes[6], bytes[7], bytes[8]));
      const humidity = parseFloat(String.fromCharCode(bytes[10], bytes[11], bytes[12], bytes[13], bytes[14]));
      const pressure = parseFloat(String.fromCharCode(bytes[16], bytes[17], bytes[18], bytes[19], bytes[20], bytes[21]));
      const altitude = parseFloat(String.fromCharCode(bytes[23], bytes[24], bytes[25], bytes[26], bytes[27], bytes[28], bytes[29]));
      
    decodedData = {
      identifier: identifier + " BME", 
      temperatureBME: temperature,
      humidityBME: humidity,
      pressure: pressure,
      altitude: altitude
    };
    dataSource = "Sensor BME";
    } else if (identifier === "1.1") {
      // Proceso para el identificador de sensores alphasense
      const SO2 = parseFloat(String.fromCharCode(bytes[9], bytes[10], bytes[11], bytes[12]));
      const O3 = parseFloat(String.fromCharCode(bytes[14], bytes[15], bytes[16], bytes[17]));
      const NO2 = parseFloat(String.fromCharCode(bytes[19], bytes[20], bytes[21], bytes[22]));
      const CO = parseFloat(String.fromCharCode(bytes[24], bytes[25], bytes[26], bytes[27]));
      const SO2_2 = parseFloat(String.fromCharCode(bytes[36], bytes[37], bytes[38], bytes[39]));
      const O3_2 = parseFloat(String.fromCharCode(bytes[41], bytes[42], bytes[43], bytes[44]));
      const NO2_2 = parseFloat(String.fromCharCode(bytes[46], bytes[47], bytes[48], bytes[49]));
      const CO_2 = parseFloat(String.fromCharCode(bytes[51], bytes[52], bytes[53], bytes[54]));
      
    decodedData = {
      identifier: identifier + " Alphasense",
      SO2: SO2,
      O3: O3,
      NO2: NO2,
      CO: CO,
      SO2_2: SO2_2,
      O3_2: O3_2,
      NO2_2: NO2_2,
      CO_2: CO_2
    };
    dataSource = "Sensor Alphasense";
    } else if (identifier === "1.4") {
      // Proceso para el identificador de sensor de particulas PM 2.5 y PM 10
      const PM1_0 = parseFloat(String.fromCharCode(bytes[5], bytes[6], bytes[7], bytes[8], bytes[9]));
      const PM2_5 = parseFloat(String.fromCharCode(bytes[11], bytes[12], bytes[13], bytes[14], bytes[15]));
      const PM4_0 = parseFloat(String.fromCharCode(bytes[17], bytes[18], bytes[19], bytes[20], bytes[21]));
      const PM10_0 = parseFloat(String.fromCharCode(bytes[23], bytes[24], bytes[25], bytes[26], bytes[27]));
      const humidity = parseFloat(String.fromCharCode(bytes[29], bytes[30], bytes[31], bytes[32], bytes[33]));
      const temperature = parseFloat(String.fromCharCode(bytes[35], bytes[36], bytes[37], bytes[38], bytes[39]));

    decodedData = {
      identifier: identifier + " SEN55",
      PM1_0: PM1_0,
      PM2_5: PM2_5,
      PM4_0: PM4_0,
      PM10_0: PM10_0,
      humidityALPHA: humidity,
      temperatureALPHA: temperature
    };
    dataSource = "Sensor de Particulas PM";
    } else if (identifier === "1.3") {
      // Proceso para el identificador de sensor de dioxido de carbono CO2
      const CO2 = parseFloat(String.fromCharCode(bytes[4], bytes[5], bytes[6]));
      const temperature = parseFloat(String.fromCharCode(bytes[8], bytes[9], bytes[10], bytes[11], bytes[12]));
      const humidity = parseFloat(String.fromCharCode(bytes[14], bytes[15], bytes[16], bytes[17], bytes[18]))
      
    decodedData = {
      identifier: identifier + " SCD40",
      CO2: CO2,
      temperaturePM: temperature,
      humidityPM: humidity
    };
    dataSource = "Sensor de CO2";
    } else {
    // Si el identificador no coincide con ninguno de los esperados, se establecen valores predeterminados
    decodedData = {
      identifier: "Desconocido",
      message: "Identificador no reconocido"
    };
    dataSource = "Desconocido";
    }

    // Devolver un objeto con la clave 'data'
    return { data: decodedData };
    }
    
    function encodeDownlink(input) {
    return {
    bytes: [225, 230, 255, 0]
    };
    }

Este codigo solo es una manera de decifrar los datos del mensaje lora que mando un dispositivo atravez de una red lora y que fue recibido por esa plataforma. El codigo comprende la utilizacion de un identificador para resalizar un decifrado en especifico segun el tipo de sensor y el payload que se este decifrando, en este caso si no conoces aun la infomacion de estos se recomienda que lo dejes por defaul y continues a la pestraña de Mesurements en la cual de daran de alta los identificadores para cada valor a analizar, esta parte tiene distintos distintivos para analizar y graficar, en el siguiente ejemplo se tomo a concideracion el Gauge debido que sirve para graficar elementos como temperatura y unidades de ese estilo.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 11-36-08.png"/></td>
</tr>
</table>
</body>
</html>

Delas demas pestañas que aparecen se dejan por defaul, almenos que se tenga que interactuar con esas opciones, se solicitaria rebizar la documentacion ofical de [Chirpstack](https://www.chirpstack.io/docs/).
Una vez configurado de clic en Sumit para gusrdar y cargar los cambios realizados.
**Paso 3 :** Dirigete a la pestaña de gateways y presiona **Add Gateway**, coloca el nombre de tu preferencia al gateway y una pequeña descripcion, ademas de escribir el Dev EUI del gateway que se encuenntra en [En la informacion de gateway](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#configuracion-del-gateway-laird-sentrius). (Ejemplo).
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 11-49-17.png"/></td>
</tr>
</table>
</body>
</html>

Una vez configurado de clic en Sumit para guardar y cargar los cambios realizados.
**Paso 4 :** Dirigete a la pestaña de applications y presiona **Add Application**, configura con el nombre de tu preferecia y añade una descripcion, da clic en **Sumit** para guardar y cargar los cambios, se deplegara otra pagina, presiona **Add Device**, configura con el nombre de tu preferecia, añade una descripcion, escribe tu Device EUI (EUI64) del [dispositivo a conectar](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#Creacion-de-credenciales-de-seguridad-y-coneccion-de-ABP.) al igual que tu Join EUI (EUI64) si cuentas con el, en caso de no tenerlo deja en blanco el espacio. Seleciona el *Device profile* que creaste con anterioridad y activa el *Disable frame-counter validation* esto con la finalidad de poder recibir mensajes de diferentes sensores a la vez. (Ejemplo).
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 11-52-46.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 12-08-26.png"/></td>
</tr>
</table>
</body>
</html>

**Paso 5 :** Dentro de **Devices** dirigete a la pestaña de **Activation** ahi agraga el **Device address**, **Network session key** y **Application session key** que obtuviste de tu [raspberry](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#Creacion-de-credenciales-de-seguridad-y-coneccion-de-ABP.), ademas agrega un 1 en **Uplink frame-counter** esto para que al momento de reactivar el device descarge solo una lectura de la informacion del dispositivo, por ultimo preciona **(Re)active Device** para guardar y cargar las configuraciones. Si fue correcta la activacion en la parate de event te aparecera el payload del sensor conectado. (Ejemplo).
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 11-56-00.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 12-21-50.png"/></td>
</tr>
</table>
</body>
</html>

## Configuracion de la plataforma de The Thingsboard.
Para acceder a la plataforma de Thingsboard es necesario escribir en tu navegaror la direccion de la ip en donde se instalo la aplicacion mas el puerto, que en este caso fue **9090**. Como es la primera vez en que accedes a la plataforma las credenciales por defaul son:
- **System Administrator**: sysadmin@thingsboard.org / sysadmin
- **Tenant Administrator**: tenant@thingsboard.org / tenant
- **Customer User**: customer@thingsboard.org / customer
Cualquier de esas te otorga acceso a la pagina principal de la aplicacion. (Ejemplo)
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 12-27-57.png"/></td>
</tr>
</table>
</body>
</html>

Una vez dentro de la aplicacion sigue los paso que se te decriben ahi 
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 12-38-04.png"/></td>
</tr>
</table>
</body>
</html>

No olvides tambien configurar en el apartado de configuraciones el **Device connectivity**. Activa la opcion de HTTP, coloca la direccion de la ip de tu pc, junto con el puesto de thingsboard **9090**. Guarda los cambios y sigue los paso para activar tu administrador de propietarios.

**Configuracion del administrador de propietarios :** Inicia tu secion de propietario segun los pasos del primer contacto con the thingsboard y suigue las indicaciones que te maraca este recuadro en la aplicacion 
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-05 12-47-46.png"/></td>
</tr>
</table>
</body>
</html>

En el primer punto se abarcara la creacion y la conexcion del dispositivo con la integracion de chirpstack. Inicia la creacion del **Dispositivo** segun el cuadro antes mencionado, cuando llegues a la Prueba de conectividad del dispositivo, copia solo la direccion URL en este caso como ejemplo **http://192.000.00.9999:9090/api/v1/d3v6z0vE3OIHOSz4dN6g/telemetry** en vez de todo el comando que se muesta ahi. Ahora pegue este url en la parte de Chipstack de applications, pestaña de integrations y recuadro de HTTP como se muestra en al imagen.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-10 14-06-57.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-10 14-04-27.png"/></td>
</tr>
</table>
</body>
</html>

Una vez configurado de clic en Sumit para guardar y cargar los cambios realizados.
Ahora actualiza la pagina de the thingsboard y se debe de observar el cambio der estado del dispositivos de inactivo a encendido, presionar doble clic en el dispositivo e ubicarse en la pestaña de telemetry, si se realizo bien el proceso de integracion se podra visualizar datos de lso sensores como la direccion eui, un object adonde se contendra nuestros datos y una data que estara incriptada.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-10 14-08-31.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-10 14-19-33.png"/></td>
</tr>
</table>
</body>
</html>

## Configuracion del Motor de reglas de ThingsBoard
Este paso es importante debido a que la telemetria enviada desde chirpstack solo se puede observar en una cadena de datos separada por comas como este ejemplo **Object:{"humidityBME":27.6,"temperatureBME":23.65,"altitude":2182.29,"identifier":"1.2 BME","pressure":777.16}**, esto representa una problematica al momento de querer graficar solamente una cosa. Para que en el The Thingsboard se muestre cada valor por separado es necesario editir la cadena de reglas que esta por defaul, crear una nueva o importar alguna ya hecha que nos pueda servir para esta problematica.
  Si es que se esta terabajndo en el mismo proyecto o un similar se recomienda descargar e importar el archivo de tipo JSON [Separador de telemetria](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/separador_de_telemetria.json) el cual brindara la funcionalidad de separar la telemetria para su graficacion correspondiente.
  En caso de que tengas los mismos problemas pero tus datos son difernetes los siguientes pasos de como configurar la cadena de reglas te serviran para el mejor entendimiento de Thingsboard.

**Paso 1 :** Crear una nueva cadena de reglas, otorgarle nombre y enceder el debug, lo ultimo te servira para ver la actividad y la informacion que va ingresando a la cadena de reglas.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-10 14-47-22.png"/></td>
</tr>
</table>
</body>
</html>

**Paso 2 :** Ingresa a la cadena de reglas que creaste y seleciona el filtro de message type filter, agregale un nombre, en la parte de *Select message types* solo deja a **Post Telemetry**, enciende el modo debug, una vez hecho esto da clic en agregar y arrastra el mouse desde el ultimo punto de input hasta el primer punto del filtro para unirlos. Estes filtro ademas de ver la actividad de los mensajes que llegas a la aplicacion puede solo visualizar los mansajes de la telemetria ya interpretada por the Thingsboard.    
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-10 14-54-56.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 10-33-22.png"/></td>
</tr>
</table>
</body>
</html>

**Paso 3 :** Agrega al esquema el filto de script, agregale nobre y activa la funcion de debug, en la parte de agregar algun codigo en TBEL o Javascript, seleciona javascript y copia y modifica el siuiente codigo segun tus requerimientos 
 </body>
            </html>

    return msg.object && msg.object.identifier && msg.object.identifier === '1.3 SCD40';

Por la configuracion de los mensajes y para ser mas practica la identificacion de los sensores y sus respectivos datos que arrojan los identificadores son fundamentales desde el codigo del sensor, haci en este momento el codigo hace refenrencia a tomar el msg.object del mensaje original, analizar solo el msg.object.identifier y buscar coincidencias para encontrar el msg.object.identifier === '1.3 SCD40', ahora si utilizas los identificadores o sensores con distinta informacion te recomiendo que utilices este filtro, en caso de que solamente se un sensor descarta este filtro de tu esquema final.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-10 15-10-21.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 10-33-51.png"/></td>
</tr>
</table>
</body>
</html>

**Paso 4 :** Dirigete a los nodos de tranformacion y agrega el nodo llamado script, dale un nombre y activa el modo debug, agrega algun codigo en TBEL o Javascript en el recuadro ubicado en la parte inferior, seleciona javascript, copia y modifica el codigo segun las necesidades que presentes, a continuacion se muestran los codigos utilizados para el presente proyecto divididos por sensor.

**Codigo de JavaScript para sensor de temperatura y humedad BME280.**

</body>
            </html>

    // Extraer los valores del mensaje original
    var temperatureBME = msg.object.temperatureBME;
    var humidityBME = msg.object.humidityBME;
    var pressure = msg.object.pressure;
    
    // Obtener la fecha y hora actuales
    var currentDateTime = new Date();
    
    // Ajustar la hora a zona Horaria de Mexico
    currentDateTime.setHours(currentDateTime.getHours() - 6);
    
    // Crear un nuevo mensaje con las claves y valores extraídos
    var newMsg = {
        processingDateTime: currentDateTime, 
        temperatureBME_ºC: temperatureBME,
        humidityBME_porciento: humidityBME,
        pressure: pressure
    };
    
    // Retornar el nuevo mensaje en el formato correcto
    return { msg: newMsg, metadata: metadata, msgType: msgType };

El codigo anterior muestra la definicion de valores como temperatura, humedad y presion que serian extraidos de la posttelemetria en el codigo compuestos por  var temperatureBME el cual es el nombre de identificacion del valor el cual es igual a msg.object.temperatureBME; que contiene la informacion de ese valor, esa misma logica se aplica para los siguientes valores con los que se esta trabajando. A continiacion el codigo define la fecha y la hora en que se estan extrayendo los datos y se realiza un ajuste en la hora para que coincida con la hora centro de Mexico, por ultimo se crea una nueva varible que contendra los valores utilizados y los retornara de nuevo a la posttelemetria para que los valoras aparezcan de manera unitaria en la visualizacion de telemetria.

**Codigo de JavaScript para los sensores de gasde Alphasense.**

</body>
            </html>

    // Extraer los valores del mensaje original
    var NO2 = msg.object.NO2;
    var NO2_2 = msg.object.NO2_2;
    var O3 = msg.object.O3;
    var O3_2 = msg.object.O3_2;
    var CO = msg.object.CO;
    var CO_2 = msg.object.CO_2;
    var SO2 = msg.object.SO2;
    var SO2_2 = msg.object.SO2_2;
    
    // Definir la calibracion NO2
    var Sensitivity_NO2 = 0.281;
    var Gain_NO2 = 0.73;
    var Electr_Zero_WE_NO2 = 233;
    var WE_Sensor_NO2 = -385;
    var WE_zero_NO2 = 228; 
    var Peso_molecular_NO2 = 46.0055;
    var Volumen_molar_NO2 = 24.45;
    
    // Sustitucion en la formula
    var Concentracion_gas_NO2 = (((((NO2 + NO2_2) / 2) - WE_zero_NO2 - Electr_Zero_WE_NO2) * Gain_NO2 + WE_Sensor_NO2) / Sensitivity_NO2) / 1000;
    
    // Converir de ppm a μg/m3
    var Valor_real_NO2 = (Concentracion_gas_NO2 * Peso_molecular_NO2) / Volumen_molar_NO2;
    
    // Definir la calibracion O3
    var Sensitivity_O3 = 0.342;
    var Gain_O3 = 0.73;
    var Electr_Zero_WE_O3 = 234;
    var WE_Sensor_O3 = -469;
    var WE_zero_O3 = 241; 
    var Peso_molecular_O3 = 48.0;
    var Volumen_molar_O3 = 24.45;
    var Sensitivity_NO2_O3 = 0.342;
    
    // Sustitucion en la formula
    var Concentracion_gas_O3 = ((((((O3 + O3_2) / 2) - WE_zero_O3 - Electr_Zero_WE_O3) * Gain_O3 + WE_Sensor_O3) / Sensitivity_O3) / Sensitivity_NO2_O3) / 1000;
    
    // Converir de ppm a μg/m3
    var Valor_real_O3 = (Concentracion_gas_O3 * Peso_molecular_O3) / Volumen_molar_O3;
    
    // Definir la calibracion de CO
    var Sensitivity_CO = 0.412;
    var Gain_CO = 0.8;
    var Electr_Zero_WE_CO = 354;
    var WE_Sensor_CO = 515;
    var WE_zero_CO = 443; 
    var Peso_molecular_CO = 28.01;
    var Volumen_molar_CO = 24.45;
    
    // Sustitucion en la formula
    var Concentracion_gas_CO = (((((CO + CO_2) / 2) - WE_zero_CO - Electr_Zero_WE_CO) * Gain_CO + WE_Sensor_CO) / Sensitivity_CO) / 1000;
    
    // Converir de ppm a μg/m3
    var Valor_real_CO = (Concentracion_gas_CO * Peso_molecular_CO) / Volumen_molar_CO;
    
    // Definir la calibracion de SO2
    var Sensitivity_SO2 = 0.302;
    var Gain_SO2 = 0.8;
    var Electr_Zero_WE_SO2 = 361;
    var WE_Sensor_SO2 = 377;
    var WE_zero_SO2 = 361; 
    var Peso_molecular_SO2 = 64.066;
    var Volumen_molar_SO2 = 24.45;
    
    // Sustitucion en la formula
    var Concentracion_gas_SO2 = (((((SO2 + SO2_2) / 2) - WE_zero_SO2 - Electr_Zero_WE_SO2) * Gain_SO2 + WE_Sensor_SO2) / Sensitivity_SO2) / 1000;
    
    // Converir de ppm a μg/m3
    var Valor_real_SO2 = (Concentracion_gas_SO2 * Peso_molecular_SO2) / Volumen_molar_SO2;
    
    // Obtener la fecha y hora actuales
    var currentDateTime = new Date();
    
    // Ajustar la hora a zona Horaria de Mexico
    currentDateTime.setHours(currentDateTime.getHours() - 6);
    
    // Crear un nuevo mensaje con las claves y valores extraídos
    var newMsg = {
        processingDateTime: currentDateTime, 
        NO2_μg_m3: Valor_real_NO2,
        O3_μg_m3: Valor_real_O3,
        CO_μg_m3: Valor_real_CO,
        SO2_μg_m3: Valor_real_SO2
    };
    
    // Retornar el nuevo mensaje en el formato correcto
    return { msg: newMsg, metadata: metadata, msgType: msgType };

Las modificaciones a los valores de la postelemetria en cuestion de los sensores de gas alphasense se definen por las variables que se extraen de la telemetria y los valores, posteriormente de definen los valores de calibracion segun las graficas de calibracion de los sensores, concecutivamente se establece la ecuacion correspondiente para determinar el valor real de concentracion de gases y las formulas de conversion, ademas de integrar la fecha y su respectiva correccion. Por ultimo solo se define una nueva variable para contener el nuevo valor de los gases y retornarlos a la telemetria para su posterior visualizacion.**NOTA :** El codigo anterior es un conjunto de codigos unidos para el envio de datos mas amigable con la plataforma,  sin embargo sepueden establecer unitariariamente con la finalidad de visualizar con mayor rapidez los eventos que se esten ejecutando.

**Codigo de JavaScript para sensor de partuculas PM Sen55.**

</body>
            </html>

    // Extraer los valores del mensaje original
    var PM1_0 = msg.object.PM1_0;
    var PM2_5 = msg.object.PM2_5;
    var PM4_0 = msg.object.PM4_0;
    var PM10_0 = msg.object.PM10_0;
    var temperatureALPHA = msg.object.temperatureALPHA;
    var humidityALPHA = msg.object.humidityALPHA;
    
    // Obtener la fecha y hora actuales
    var currentDateTime = new Date();
    
    // Ajustar la hora a zona Horaria de Mexico
    currentDateTime.setHours(currentDateTime.getHours() - 6);
    
    // Crear un nuevo mensaje con las claves y valores extraídos
    var newMsg = {
        processingDateTime: currentDateTime, 
        PM1_0_μg_m3: PM1_0,
        PM2_5_μg_m3: PM2_5,
        PM4_0_μg_m3: PM4_0,
        PM10_0_μg_m3: PM10_0,
        temperatureALPHA_ºC: temperatureALPHA,
        humidityALPHA_porciento: humidityALPHA
    };
   
    // Retornar el nuevo mensaje en el formato correcto
    return { msg: newMsg, metadata: metadata, msgType: msgType };

**Codigo de JavaScript para sensor de Dioxido de carbono SCD40.**

</body>
            </html>

    // Extraer los valores del mensaje original
    var temperaturePM = msg.object.temperaturePM;
    var humidityPM = msg.object.humidityPM;
    var CO2 = msg.object.CO2;
    
    // Obtener la fecha y hora actuales
    var currentDateTime = new Date();
    
    // Ajustar la hora a zona Horaria de Mexico
    currentDateTime.setHours(currentDateTime.getHours() - 6);
    
    // Crear un nuevo mensaje con las claves y valores extraídos
    var newMsg = {
        processingDateTime: currentDateTime, 
        temperaturePM_ºC: temperaturePM,
        humidityPM_Porciento: humidityPM,
        CO2_ppm: CO2
    };
    
    // Retornar el nuevo mensaje en el formato correcto
    return { msg: newMsg, metadata: metadata, msgType: msgType };

Para los datos del sensor de particulas y el de dioxido de carbono las configuraciones son las mismas que para el sensor BME280, en las cuales solamente se tranforma el dato de una cadena de valores separados por comas y puntos por un datos individual segun el identificador proporcionado por el sensor y haci al momento de retornar a la telemetria,poder visualizar en el panel una lectura unitaria de las variables definidas al final de cada codigo.
Acontinuacion se muestran imagenes de ejemplo de los nodos a agragar y el esquema de visualizacion.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 10-27-03.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 10-34-16.png"/></td>
</tr>
</table>
</body>
</html>

**Paso 5 :** Selecciona el nodo de accion llamado *Save timeseries*, coloca el nombre de tu preferencia y activa el modo debug. En la configuracion del mismo dejar en defaul, posteriormente agrega el nodo como se muestra en las imagenes siguientes. Este nodo cumple la funcion de guardar la telemetria en la base da datos que se este utilizando. 
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 10-41-52.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 10-34-35.png"/></td>
</tr>
</table>
</body>
</html>
     
**Paso 6 :** Agrega el nodo *res api call*, este tiene la principal funcion de obtener los datos procesados de la posttelemetria y enviarlos a un serevidor local con una URL del mismos servidor. Para su configuracion es necesario contra con un servidor locar y una URL para recibir los datos procesados, como primer punto tienen que nombrar al nodo con el nombre de tu prefencia,posteriormente coloca la URL del servido a enviar, en el metodo requerido existen varias opciones para la extracion de datos, en este caso se selecciono la de POST la cual es la que contiene la informacion a utilizar y el cuadro del cliente de HTTP por la cual se recibira la informacion, en casode tener alguno otro formato de salida que no sea JSON modificar el apartado que marca dicho archivo, si no existe alguna otra modificacion a realizar que se observe necesaria agregar el nodo, y conectarlo con el nodo de *Save timeseries* y colocar *success*. Las siguientes imagenes muestran un ejemplo de lo desctrito con anterioridad.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/WhatsApp Image 2024-07-23 at 10.55.21 AM (1).jpeg"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-07-16 19-00-39.png"/></td>
</tr>
</table>
</body>
</html>

 ## Configuracion del perfiles de dispositivo.
 La configuracion y creacion de un perfil de dispositivo simplifica pasos cuando se quieren agregar varios dispositivos con que otorgan informacion similar o que tienen la misma estructura en su configuracion. En este segmento se describira la configuracion de los perfiles y como es que se conectan a un dispositivo, cadena de reglas, panel de dispositivo, ademas de la importancia que se le puede otorgar aun mensaje para que sea leido y agrupado.
 
 **Paso 1 :** Dirijete a la seccione de paneles, agrega un nuevo panel, coloca el nombre de tu preferencia, una pequeña descripcion y si ya tienes algun cliente registrado coloca ese cliente para que pueda visualizar la informacion de solo ese panel, al final solo dale en agragar y posteriormente despues de que se despliegue la pagina dale en guardar.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-11-03.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-24-49.png"/></td>
</tr>
</table>
</body>
</html>
      
**Paso 2 :** Una vez creado el panel dirijete a perfiles de dispositivo y ahi crea un nuevo perfil, agrega el nombre de tu agrado, posteriormente en el siguiente recuadro agrega la cadena de reglas que creaste con anterioridad, selecional el recuadro del panle y busca el nombre del panel creado, para el recuador de cola, seleciona que tan prioritario es el mensaje para que el perfil lo maneje segun sus 3 opciones, en este caso se utilizo *HighPriority*, por ultimo la cadena de reglas de egde es utilizada para enviar informacion de los paneles a aplicaciones exteriores, esta cadena se deja por defecto en caso de que se tenga que configurar una nueva cadena, se buscara el nombre de la cadena creada y se accionara al recuadro.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-10-06.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-11-47.png"/></td>
</tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-12-04.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-12-12.png"/></td>
</tr>
</table>
</body>
</html>

**Paso 3 :** Para los siguentes 3 puntos de configuracion se pueden dejar por defaul, en caso de que se tengan que configurar por el tipo de comunicacion a establecer el punto 2 tiene las opciones de configuracion, segun el tipo de conexion, seleccionar la que se este usando. Si se requiere la configuracion de una alarma con la finalidad de alertar sobre la llegada de telemtria o que algun dato a exedido los limites que se marquen y para el punto 4 la opcion que da este espacio es para la creacion de dispocitivos de aprovisionamiento los cuales tienen la funcion de establecerse con la configuracion de los parametros selecionados en el perfil del dispositivo, solo se solicita crear claves desde el dispositivo o adicionar las claves creadas por defaul en el perfil.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-12-26.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-12-38.png"/></td>
</tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 11-12-47.png"/></td>
</tr>
</table>
</body>
</html>

## Configuracion del panel del dispositivo.
Diriguete a dispositivos y seleciona el dispositivo que creaste con anterioridad, estando ahi ve a modo edicion representado por un lapiz o pluma en su defecto, estando en el recuadro, elimina el prefir de dispositivo registardo y seleciona el perfil creado anteriormente, esto con la finalidad de que se complete la conexion de todas las variables necesarias para visualizar la informacion graficamente en thingsboard. Posteriormente a esto sigua los pasos de la configuracion del panel.

**Paso 1 :** Diriguete a la pestaña de paneles y selecciona el panel que creaste con anterioridad, agrega un widget, en este ejemplo se mostrara solamente la configuracion de la temperatura, pero en general es una configuracion similar con los los demas datos, solo en casos especiales como la indormacion de particulas de monocido de carbono y algunas otras particulas en el ambiente se aplicaran algunos otras operaciones.

Para la configuracion de la temperatura solamete se buscara un widget que muestre la temperatura de forma numeriaca y grafica por ejemplo el widget de la seccion de *Indoor Environment*  llamado *Indoor temperature chart card with background* :
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 12-13-55.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 13-04-10.png"/></td>
</tr>
</table>
</body>
</html>

Ahora seleciona el dispositivo que continen los datos a graficar y elimina la temperatura que se muestra por defaul, posteriormente a eso se te desplegara el panel de informacion de los datos que se pueden selecionar para graficar, y tendras que buscar el nombre de temperatura en el panel y seleccionarlo, una vez hecho eso dirigete al recuadro de grafico y posiscionate en decimales, ahi agrega 2, esto para que se muestre el valor real de la temperatura y no se redonde por defecto, por ultimo en el recuadro de valores, al igual coloca 2 en los decimales, esto para que la recta que se dibuje con el historico de la temperatura coresponda a las cifras registradas por el valor numerico de la temperatura.   
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 12-54-18.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 12-54-30.png"/></td>
</tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 12-54-40.png"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 12-54-50.png"/></td>
</tr>
</table>
</body>
</html>

Los paneles finales se visdualizaran de esta manera segun su configuracion y los datos a graficar.
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src= "https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/raw/main/images/Captura desde 2024-06-14 13-09-24.png"/></td>
</tr>
</table>
</body>
</html>
