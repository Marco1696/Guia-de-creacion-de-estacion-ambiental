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
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/19063068-f180-40cb-ab88-d89edae9d770"/></td>
</tr>
</table>
</body>
</html>

**Paso 5 :** Plotear la red lora para comprovar su funcionalidad: Dirigirse a al apartado **Traffic** y presionar el recuadro **Poll Traffic**, se debera de empezar a visualizar informacion sobre mensajes que recibe el gateway sin que esten registrados en el mismo. (Ejemplo)
![WhatsApp Image 2024-05-16 at 3 27 48 PM (2)](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/580e379d-92ae-4fc7-9819-52e06b10e272)

# Configuracion de la plataforma de Chirpctack.
Acceder a la pagina de **Chirpstack** con la direccion [ip](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#L715) de la pc en conjunto con el puerto que se accino a chirpstack en el [scritp](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#L885) o el que se haya accinado en tu caso. (Ejemplo) **192.000.00.999:80**
Una vez en la pagina nos aparecera la siguiente imagen:
![Captura desde 2024-06-04 14-57-41](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/4bb5f169-7b1e-4d70-b8e9-a8e1984aa4d2)

El usuario y la contraseña por defaul el **admin**.
Una vez dentro de la plataforma aparecesala siguiente imagen 
![Captura desde 2024-06-04 15-22-06](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/35816c20-fc9a-418d-83a9-fa7a4a1f9b2f)

Para configurar la platafroma se seguiran los siguientes pasos:
**Paso 1 :** Crear un Tenanst o cliente del Network server. Dirijete a la parte de Tenants, consecutivamente da clic en Add Tenant. Dentro del recuadro que aparece podras colocara el nombre de cliente de tu preferecia, ademas de poner una breve descripcion y configurar el perfil del gateway, ya sea publico, privado o aceptar muchos gateways. (Ejemplo).
![Captura desde 2024-06-05 10-45-18](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/ac91aea2-22be-426c-8d9f-fcb6e2bff7ac)
Una vez configurado de clic en Sumit para gusrdar y cargar los cambios realizados.
**Paso 2 :** Crear un **Device Profiles**, para eso tenemos que ubicarnos en la pestaña del mismo nombre, una vez ahi nos dirijiramos a add device profile. La configuracion dependera de la reguion, el nombre que se le quiera otorgar al device profile, la cadena de reglas, version de mac y algoritmos a utilizar. (Ejemplo).
![Captura desde 2024-06-05 10-48-38](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/27915ca3-3b91-476d-9465-a298d1ec1382)
Hecho lo anterior dirigete a la pestaña de de Join (OTA/ABP), para esta configuracion existen 2 formas de conectra con la aplicacion los dispocitivos, ya sea por OTA o por ABP. 

*Conexion por OTA :* solo se dejara encendido sin hacer ningun cambio a la configuracion. (Ejemplo).
![Captura desde 2024-06-05 10-53-14](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/e1a03956-4d54-47b2-a8cb-59066f17093e)

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
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/f88abb5f-6cc8-4210-9930-34c3780cf6f2"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/936e8b51-0e93-42e0-ac95-8514f8198712"/></td>
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
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/3ddd1695-1cf8-4069-b269-f6831a947fe3"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/25ccdd68-5332-47af-b4e8-6723bacd99ab"/></td>
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
![Captura desde 2024-06-05 11-36-08](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/8f1fb8b0-3290-4b54-9ff3-351cef7ab332)
Delas demas pestañas que aparecen se dejan por defaul, almenos que se tenga que interactuar con esas opciones, se solicitaria rebizar la documentacion ofical de [Chirpstack](https://www.chirpstack.io/docs/).
Una vez configurado de clic en Sumit para gusrdar y cargar los cambios realizados.
**Paso 3 :** Dirigete a la pestaña de gateways y presiona **Add Gateway**, coloca el nombre de tu preferencia al gateway y una pequeña descripcion, ademas de escribir el Dev EUI del gateway que se encuenntra en [En la informacion de gateway](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/blob/main/README.md#configuracion-del-gateway-laird-sentrius). (Ejemplo).
![Captura desde 2024-06-05 11-49-17](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/a5fddb00-65fc-4ce5-be4b-5588ee792009)
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
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/ecd3a721-6669-49e9-ad23-ec7bcb442abf"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/3f66ce93-efe6-44ee-a0c6-8bcd2abfb17c"/></td>
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
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/7e54947a-5e43-4d2c-a68a-d4f1b282d2b6"/></td>
   <td><img src="https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/4a529d19-7618-4656-9ea0-60c4bd3fda89"/></td>
</tr>
</table>
</body>
</html>

# Configuracion de la plataforma de The Thingsboard.
Para acceder a la plataforma de Thingsboard es necesario escribir en tu navegaror la direccion de la ip en donde se instalo la aplicacion mas el puerto, que en este caso fue **9090**. Como es la primera vez en que accedes a la plataforma las credenciales por defaul son:
- **System Administrator**: sysadmin@thingsboard.org / sysadmin
- **Tenant Administrator**: tenant@thingsboard.org / tenant
- **Customer User**: customer@thingsboard.org / customer
Cualquier de esas te otorga acceso a la pagina principal de la aplicacion. (Ejemplo)
![Captura desde 2024-06-05 12-27-57](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/5effefae-7e0f-4a9e-9e4d-0b694874bed8)

Una vez dentro de la aplicacion sigue los paso que se te decriben ahi ![Captura desde 2024-06-05 12-38-04](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/d990dd20-ed40-4dae-86d6-b03679dec774).
No olvides tambien configurar en el apartado de configuraciones el **Device connectivity**. Activa la opcion de HTTP, coloca la direccion de la ip de tu pc, junto con el puesto de thingsboard **9090**. Guarda los cambios y sigue los paso para activar tu administrador de propietarios.

**Configuracion del administrador de propietarios :** Inicia tu secion de propietario segun los pasos del primer contacto con the thingsboard y suigue las indicaciones que te maraca este recuadro en la aplicacion ![Captura desde 2024-06-05 12-47-46](https://github.com/Marco1696/Guia-de-creacion-de-estacion-ambiental/assets/168860607/033ef2ff-1936-413b-9eb3-654cd4ca7d6f).
En el primer punto se abarcara la creacion y la conexcion del dispositivo con la integracion de chirpstack. Inicia la creacion del **Dispositivo** segun el cuadro antes mencionado, cuando llegues a la Prueba de conectividad del dispositivo, copia solo la direccion URL en este caso como ejemplo **http://192.000.00.9999:9090/api/v1/d3v6z0vE3OIHOSz4dN6g/telemetry** en vez de todo el comando que se muesta ahi. Ahora pegue este url en la parte de Chipstack de applications y en la pestaña de integrations 





     

     

             
   
