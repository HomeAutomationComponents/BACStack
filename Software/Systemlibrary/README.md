# Systemlibrary

The systemlibrary contains all the necessary functions for operating the internal communication and defining all object types, property types, etc.\
More detailed explanations can be found in the respective readme`s.

## Overview

### Objects

The dictionary is used to store the object structure.
The structure begins with an object of type module.\
|->module\
This can contain objects of the type application or inputoutput.\
|->module|->inputoutput\
|->module|->application\
An applications object contains objects of the type input output.\
|->module|->inputoutput\
|->module|->application|->Inputoutput

A module works without applications and contains all the information required to operate the module itself.
An application object represents the function of the module. For example a BME280 sensor or an EnOcean device.
The strict distinction between modules and devices is very important. 
Modules can contain several applications. e.g. like the EnOcean module or the Sensoring module with its variable applikationtypes.
Therefore, a device would be more like the application object.

Basically, the applications are loaded from templates, which contain the definition and available properties and inputoutput objects.
There are several types of inputoutput objects.
* Binaryinput (e.g. button)
* Binaryoutput (e.g. switch)
* Binaryvalue (e.g. enable inverting of a binaryinput state)
* Analoginput
* Analogoutput
* Analogvalue
* Multistateinput
* Multistateoutput
* Multistatevalue (e.g. for the temperature oversampling of BME680)

### Data
Data will be saved in a vector<uint8_t> with fixed or variable length.
To access the data and have a secure data structure for the various core tasks (esp32 only), a Class_Data was introduced.
In this class the data are buffered and can than passed in to the functions which reads or write the data of the propertie.
Several basic functions such as Float_to_Bytes, Bytes_to_Uint etc. convert the most common data types.

### Priorities
Outputobjects contain a property called priority matrix. It contains all active priorities with their values for the propertie present value.
A priority-dependent setting of the present values will of course generate overhead. But a small illustration will show the importance of this.
We have a smart home which controls a socket. You also have the option of changing the value via various interfaces or manually at the device.
The question is what the socket should do.\
For example, the smart home changes the value every 15 minutes. But you want a permanent value via a web interface, or someone wants to switch the socket manually.
This is extra ordinary i know.
But i think this would be helpfull and i did not find this in other smart home open source projects.

For this case there are several priorities.
* Critical (human security higest)
* Safty (equipment security)
* 02
* Application (e.g. push button at the socket)
* Manual (web interface)
* 06
* Programm (smart home demand)
* Default

A priority is as long as active until it will be released.
> [Identifier][Propertietype_Presentvalue]=Null

