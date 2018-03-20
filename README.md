# mitemp - Library for Xiaomi Mi Temperature and Humidity Sensor (v2) with Bleutooth LE and the LCD display



This library lets you read sensor data from a Xiaomi Mi BluetoothLE Temperature and Humidity sensor.



## Functionality 
It supports reading the different measurements from the sensor
- temperature
- humidity
- battery level

To use this library you will need a Bluetooth Low Energy dongle attached to your computer. You will also need a
Xiaomi Mi Temperature and Humidity sensor. 

## Backends
This sensor relies on the btlewrap library to provide a unified interface for various underlying btle implementations
* bluez tools (via a wrapper around gatttool)
* bluepy library

### bluez/gatttool wrapper
To use the bluez wrapper, you need to install the bluez tools on your machine. No additional python 
libraries are required. Some distrubutions moved the gatttool binary to a separate package. Make sure you have this 
binaray available on your machine.

Example to use the bluez/gatttool wrapper:
```python
from mitemp.mitemp_poller import MiTempPoller
from btlewrap.gatttool import GatttoolBackend

poller = MiTempPoller('some mac address', GatttoolBackend)
```

### bluepy
To use the [bluepy](https://github.com/IanHarvey/bluepy) library you have to install it on your machine, in most cases this can be done via: 
```pip3 install bluepy``` 

Example to use the bluepy backend:
```python
from mitemp.mitemp_poller import MiTempPoller
from btlewrap.bluepy import BluepyBackend

poller = MiTempPoller('some mac address', BluepyBackend)
```

### pygatt
If you have a Blue Giga based device that is supported by [pygatt](https://github.com/peplin/pygatt), you have to
install the bluepy library on your machine. In most cases this can be done via: 
```pip3 install pygatt``` 

Example to use the pygatt backend:
```python
from mitemp.mitemp_poller import MiTempPoller
from btlewrap.pygatt import PygattBackend

poller = MiTempPoller('some mac address', PygattBackend)
```

## Conttributing
please have a look at [CONTRIBUTING.md](CONTRIBUTING.md)

----

## Projects Depending on `mitemp`

The following shows a selected list of projects using this library:

* https://github.com/ThomDietrich/miflora-mqtt-daemon - An MQTT Client/Daemon for Smart Home solution integration
* https://home-assistant.io/components/sensor.miflora/ - Integration in Home Assistant 