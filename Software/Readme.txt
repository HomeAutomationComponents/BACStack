# Software

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
