Sensors
=======

DS18B20 Temperature Sensor
--------------------------

The DS18B20 is a thermoresistive temperature sensor and can be found in many of the sensor kits referenced in this book.  To set up the DS18B20 connect the jumper wires as shown in +@fig:ds18b20_setup.  If you have an individual sensor instead of a sensor module you will need to use a 4.7k ohm resistor as shown in the diagram.  The resistor allows the device to work properly and should be used to avoid damage to the component [@DS18B20_resistor].  If you have a DS18B20 module it may already include a resistor and you will not need to add another.  Be sure to check before setting up your sensor. 

![DS18B20 Setup](images/DS18B20_setup.png){#fig:ds18b20_setup}

Once you have set up the wiring of the DS18B20 you will need to set up the one wire interface.  This can be done with the following steps [@DS18B20_code_setup].  

1. In a terminal enter:  ``` sudo nano /boot/config.txt ```
2. Scroll to the bottom of this text file and enter ``` dtoverlay=w1–gpio ```

Once the set up is complete you can use the DS18B20 code provided to output the temperature to the terminal.

[DS18B20 Code](https://github.com/cloudmesh-community/fa18-523-84/blob/master/paper/code/ds18b20.py)

Temperature and Humidity Sensor Module
--------------------------------------

The temperature and humidity sensor used in this example is the DHT11 sensor which can be purchased as a part of the [Kookye Smart Home Sensor kit](https://www.amazon.com/gp/product/B01J9GD3DG/ref=oh_aui_detailpage_o03_s01?ie=UTF8&psc=1) or the [Elegoo Uno Kit.](https://www.amazon.com/ELEGOO-Project-Starter-Tutorial-Arduino/dp/B01D8KOZF4/ref=sr_1_6?s=electronics&ie=UTF8&qid=1542065611&sr=1-6&keywords=dht11+temperature+and+humidity+module).  The humidity compontent of the DHT11 works by measuring the conductivity between two electrodes. Between these electrodes there is a substrate that holds moisture and as the moisture changes the conductivity changes [@How_DHT11_Works]. The temperature sensor of the DHT11 works in the same way as the DS18B20.

To set up the DHT11 sensor connect jumper wires to the Raspberry Pi as shown in +@fig:dht11_setup.  Ensure that the ground wire of the DHT11 is connected to the ground rail of the breadboard or a ground pin on the Raspberry Pi.  The VCC wire of the DHT11 should be connected to 3.3v from the Raspberry Pi.  To recieve data the middle pin should be connected to one of the GPIO pins on the Raspberry Pi.  In this example and associated code we connect the data wire to GPIO 4 on the Raspberry Pi as shown in +@fig:dht11_setup.

![DHT11 Setup](images/DHT11_setup.png){#fig:dht11_setup}  

Once you have checked that the DHT11 is set up correctly you will need to set up the Adafruit_DHT module for python.  The sample python class utilizes the Adafruit_DHT module which can be set up by executing the following code in a terminal on your Raspberry Pi [@Adafruit_setup].  

```bash
git clone https://github.com/adafruit/Adafruit_Python_DHT.git
cd Adafruit_Python_DHT
sudo apt-get update
sudo apt-get install build-essential python-dev
sudo python setup.py install
```

Once you have set up the Adafruit_DHT module you can run the python code to display the temperature and humidity reading to the terminal.  

[Temperature & Humididy Sensor Code](https://github.com/cloudmesh-community/fa18-523-84/blob/master/paper/code/temp_humid.py)

Photosensetive Light Sensor Module
----------------------------------

![Light Sensor Setup](images/light_setup.png){#fig:light_setup}


Capacitive Touch Sensor Module
------------------------------

![Touch Sensor Setup](images/touch_setup.png){#fig:touch_setup}


2 Channel Relay Module
----------------------

![Relay Module Setup](images/relay_setup.png){#fig:relay_setup}


16 x 2 LCD Screen
-----------------

![LCD Setup](images/lcd_setup.png){#fig:lcd_setup}


Compass
-------

TODO: which compass sensor

The default pins are defined in variants/nodemcu/pins_arduino.h as GPIO

```
    SDA=4 
    SCL=5
    D1=5 
    D2=4.
```

You can also choose the pins yourself using the I2C constructor
Wire.begin(int sda, int scl);


## Sources for this section:

  * DS18B20_resistor: https://arduino.stackexchange.com/questions/30822/the-use-of-4-7kohm-resistor-with-ds18b20-temperature-sensor
  * DS18B20_code_setup: http://www.circuitbasics.com/raspberry-pi-ds18b20-temperature-sensor-tutorial/
  * Adafruit_setup: https://stackoverflow.com/questions/28913592/python-gpio-code-for-dht-11-temperature-sensor-fails-in-pi-2
  * How_DHT11_Works: https://howtomechatronics.com/tutorials/arduino/dht11-dht22-sensors-temperature-and-humidity-tutorial-using-arduino/

