
## IOT-Sensor-Network
![mod](https://user-images.githubusercontent.com/25153383/33517256-ddc5fd74-d7a6-11e7-967a-d347e390c9a9.jpg)

![mod1](https://user-images.githubusercontent.com/25153383/33517278-1fd29af6-d7a7-11e7-9559-40edc8c1e48e.jpg)

##Raspberry Pi Weather Station

Measures:

- Temperature
- Humidity
- Atmospheric Pressure
- Lux



##Parts you'll need:

[AM2302](http://www.adafruit.com/products/393) Temperature / Humidity Sensor  
[BMP180](http://www.adafruit.com/products/1603) Temperature / Barometric Pressure Sensor  
[DS18B20](http://www.adafruit.com/products/374) Waterproof Temperature Sensor  
[TSL2561](http://www.adafruit.com/products/439) Digital Lumosity Sensor  

##Installation Instructions:

These instructions have been tested with the latest version of Raspian, however they should run in most distributions of Linux fairly easily.

Wire up the sensors as shown here: 
![img](https://user-images.githubusercontent.com/25153383/33514127-e24c1640-d773-11e7-9947-feb35a3e86dc.png)

### Setup the AM302

Here we set up the AM2302 Humidity Sensor.

Clone the Adafruit Python DHT Library

git clone https://github.com/adafruit/Adafruit_Python_DHT.git  

Build some tools  

sudo apt-get update  

sudo apt-get install build-essential python-dev python-openssl  

sudo python setup.py install    
### Setup the DSB18B20    

You will need to add One Wire Support:    

sudo nano /boot/config.txt  

Add the following line:      

dtoverlay=w1-gpio      
Reboot the Pi:    

sudo reboot  
Add smbus and i2c tools:  

sudo apt-get install python-smbus  
sudo apt-get install i2c-tools  

You may get "already installed" Messages from this  

sudo nano /etc/modules

Add the following:  

i2c-bcm2708   
i2c-dev  
Modify boot config:  

sudo nano /boot/config.txt  

Add the following lines:  

dtparam=i2c1=on  
dtparam=i2c_arm=on  

Reboot the Pi:  

sudo reboot  

### Setup the TSL2561  

cd ~/sources  

wget https://raw.githubusercontent.com/adafruit/Adafruit-Raspberry-Pi-Python-Code/master/Adafruit_I2C/Adafruit_I2C.py 
wget https://raw.githubusercontent.com/seanbechhofer/raspberrypi/master/python/TSL2561.py  


### Setup the BMP 180 

git clone https://github.com/adafruit/Adafruit_Python_BMP.git  
cd Adafruit_Python_BMP  
sudo python setup.py install  

### Test the sensors  

git clone https://github.com/Morjatt/IOT-Sensor-Network.git  
cd reader  
sudo python readings.py dryrun
