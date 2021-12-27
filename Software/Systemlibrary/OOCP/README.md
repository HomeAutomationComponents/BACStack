# Object oriented communication protocol

This defines the internal communication between the modules.\
Currently there are two physical modes of transmission.
* CAN-Bus (systembus ESP32 with external hardware, for DIN rail)
* ESP-Now (wireless ESP32, ESP8266)


The message structure depends on the function\
Function 4 Bits (0-15)\
Moduleindex 6 Bits (1-63)\
Applicationindex 6 Bits (1-63)\
Inputoutputindex 5 Bits (1-31)\
Propertietype 6 Bits (1-63)\

* NMT-frame (Networkmanagement)\
Function = Function_NMT\
Moduleindex\
NMTCode 4 Bits (1-15)
NMTState 4 Bits (1-15) Optional

* Data-frame\
Function = Function_Read/Write\
Moduleindex\
Applicationindex\
Inputoutputindex\
Propertietype\
Priority 1 Bit (yes/no) Yes -> first byte of data will be priority

* Releasepriority-frame\
Function = Function_ReleasePriority\
Moduleindex\
Applicationindex\
Inputoutputindex\
Priority 4 Bits (0-15)

* OMT-frame (Objectmanagement)\
Function = Functio_OMT\
Moduleindex\
Applicationindex\
Inputoutputindex\
OMTCode 4 Bits (1-15)
first byte of data will be the object or propertytype

* Import-frame\
Function = Function_Import\
Moduleindex\
Applicationindex\
Inputoutputindex\
ImportCode 4 Bits (1-15)
first byte of data will be the object or propertytype

* Sync-frame (Synchronization)\
Function = Function_Sync\
Moduleindex\
Applicationindex\
Inputoutputindex\
SyncCode 4 Bits (1-15)
first byte of data will be the object or propertytype


