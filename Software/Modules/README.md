# Modules

Modules represent the logical unit, which contains the devices application.
But there are also simple modules without an application object. 
In this modules the inputoutpotobjects are integrated into the module object. (e.g. SP111)

The software consists of 2 parts. 
Firstly the systemlibrary and secondly the library of the module it selfs.

Systemlibrary\
->Dictionary\
->OOCP\
->System

Available modulelibrarys:
* Gateway
* EnOcean
* Sensoring
* nRF24L01
* SP111

To bind in the Systemlibrary to platformio use

> lib_extra_dirs = Fullpath_to_Systemlibrary\Systemlibrary\
> lib_ldf_mode = deep+

You will find a full platfomio.ini in the modulelibrarys.
