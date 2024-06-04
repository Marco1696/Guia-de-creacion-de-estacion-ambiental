# Guia de creacion de estacion ambiental
Esta guia esta dirijida a toda aquella persona que tenga la necesidad de implementar una estacion de monitoreo ambiental con los siguientes elementos **motor de raspian** de una raspberry pi zero w , **modulo LoRaWan**, ademas de la plataforma de **chirpstack y the thingsboard**. Se establecen enlaces y graficos para su el analisis de datos y un mejor entendimeineto de las condiciones ambientales. 
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
     
      </body>
             </html>
             
         sudo pip3 install --upgrade pip
     </body>
             </html>
             
         sudo pip3 install adafruit-blinka 

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
   
Guardar y salir con **CTRL+O** y **CTRL+X**. Una vez culminado este ultimo codigo ejecutamos los codigos de Python, procurando copiar los datos que arrojaran estos codigos.
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
    
Reemplazo los datos obtenidos en el **paso 2**. Guardar y salir con **CTRL+O** y **CTRL+X**.
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
    
Guardar y salir con **CTRL+O** y **CTRL+X**. Ejecuta este codigo y guarda el Dev_EUI el cual sera el identificador del dispositivo en la red LoRaWAN el cual se conectara el con la plataforma de Chirpstack.
# Creacion de codigos de sensores utilizados en la estacion de monitoreo.

   # Sensores Alphasense.
   Escriba en el siguiente comando:
   </body>
         </html>
             
    sudo nano loraysensores.py
    
   La parte de **loraysensores** se puede modificar por cualquier nombre, esto es solo un ejemplo. Una vez ahi se desplegara una consola y debera escribir el siguiente codigo:
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
    
   Para poder ejecutar el codigo es necesario descargar las librerias de **Adafruit circuitpython ads1x15**. Escriba el siguiente comando:
   </body>
         </html>
              
    sudo pip3 install adafruit-circuitpython-ads1x15
    
   # Sensor BME 280.
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
    
   # Sensor SCD 40.
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
    
   # Sensor SEN 55.
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
   
   # Codigo de para mandar datos a Chirpstack.
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

   # Crear un servicio de pytho3 en la raspberry pi zero w para que se ejcute automaticamente el codigo pra mandar datos a Chirpstack
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
    
# Instalar chirpstack y The Thingsboard en docker o cualquier otro sistema operativo.
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
    depends_on:
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
# Configuracion del gateway Laird Sentrius.
La configuaracion del gateway Laird Sentrius fue obtenida de la pagina oficial de [ezurio](https://www.ezurio.com/iot-devices/lorawan-iot-devices/sentrius-rg1xx-lorawan-gateway-wi-fi-ethernet-optional-lte-us-only), en donde se encontrara la documentacion del gateway [laird sentrius](https://www.ezurio.com/documentation/quick-start-guide-sentrius-rg1xx-v30),misma que sirve para configurar el gateway. En caso de que nose pueda configurar el gateway de la siguiente manera consutal la guia del gateway [laird sentrius](https://www.ezurio.com/documentation/quick-start-guide-sentrius-rg1xx-v30).   
**Paso 1 :** Conectar el gateway a la corriente y a un puerto de internat estable. Consecutivamente obtener la informacion de las direcciones contenidad de que se encuentran en el reverso del gateway o la caja del mismo. (Ejemplo)
![sentrius direccion](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/24c2694b-67a5-4397-9999-be4b9d1b2983) 
**Paso 2 :** Resetear el gataway de fabrica, presionanod primero el biton marcado como numero 2 en la imagen y consequitivamente el boton 3 durante 5 segundo una vez hecho esto se encenderan todas las luces del gateway y se ressteara. 
![Captura desde 2024-06-04 12-29-22](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/bbfa84ca-eedf-4aea-9fad-ab48b8bffc85)
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
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/c4dde515-826f-431a-b458-fdf5f764d852"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/1112e33a-5869-4296-9812-7fc42db1e490"/></td>
</tr>
</table>
</body>
</html>

**Paso 4 :** Configura la red loRAWAN, en donde nos ubicaremos en la parte de **lora**, en esa seccion nos dirigiremos a **Forwarder** y ahi seleccionaremos el modo **semtech UDP Forwarder**, dentro del de este modo modificaremos el **Network server address** con la [direccion ip](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#L715)
de la pc en que instalamos el docker, chirptack y the thingsboard y modificaremos los **Port Up** y **Port Down** con los puertos que se registraron en esta la [linea 898](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#L898), en la parte de port Up el primer numero que aparece y en la parte de port down el segundo numero. (Ejemplo)
<!DOCTYPE html>
<html>
   <head>
      <meta charset="UTF-8">
           
   </head>
   <body>
        
<table>
</thead>
<tr>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/c4dde515-826f-431a-b458-fdf5f764d852"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/1112e33a-5869-4296-9812-7fc42db1e490"/></td>
</tr>
</table>
</body>
</html>

**Paso 5 :** Plotear la red lora para comprovar su funcionalidad: Dirigirse a al apartado **Traffic** y presionar el recuadro **Poll Traffic**, se debera de empezar a visualizar informacion sobre mensajes que recibe el gateway sin que esten registrados en el mismo. (Ejemplo)

# Configuracion de la plataforma de Chirpctack.








         

     

     

             
   
