# DS18B20-Sensor-de-Temperatura
## ¿Qué es?
El DS18B20 es un sensor digital de temperatura con encapsulado de tipo TO-92 similar al empleado en transistores pequeños.
Con este sensor puedes medir temperatura desde los -55°C hasta los 125°C y con una resolución programable desde 9 bits hasta 12 bits.

## ¿Para qué sirve?
El DS18B20 sirve para la medición de temperatura, tanto en ambientes domésticos como industriales. 
Sus características permiten crear redes con gran número de sensores para controlar, por ejemplo, 
la climatización o el sistema HVAC de un edificio comercial.

## DataSheet
![images](https://uelectronics.com/wp-content/uploads/2018/02/AR0333-Sensor-de-temperatura-Digital-DS18B20-V1.jpg)
## Circuito
![images](https://imgur.com/rHJZG0A.jpg)

### Codigo

import machine, onewire, ds18x20, time
 
ds_pin = machine.Pin(16)
ds_sensor = ds18x20.DS18X20(onewire.OneWire(ds_pin))
 
roms = ds_sensor.scan()
print('Found a ds18x20 device')
 
while True:
  ds_sensor.convert_temp()
  time.sleep_ms(750)
  for rom in roms:
    print(ds_sensor.read_temp(rom))
  time.sleep(2)

## ¿Que Hace? 

Debe ejecutar la función convert_temp() para iniciar una lectura de temperatura, luego esperar al menos 750 ms antes de leer el valor.
Utiliza la función read_temp para devolver un valor y luego hacemos una pausa de 2 segundos y lo ejecutamos de nuevo

