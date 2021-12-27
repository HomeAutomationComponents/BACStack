# OOCP
The OOCP "Object orientatet communication protocol" is a smart home project,
which I started during my studies to integrate various devices into my smart home.
\
\
It is based, similar to the BACnet protocol, on objects which can maintain a large number of properties. The modules communicate externally via a gateway,
which is connected to the network via etherent.
The internal communication between the modules takes place via the system bus (CAN bus) and for the wireless modules via ESP-NOW.
Currently only the ESP8266 and ESP32 are supported.
\
\
The HTTP and UDP are currently available as external interfaces.
The UDP works with broadcast messages.

The hole internal communication takes place via identifiers, which are structured as follows:
> uint32_t Identifier = Siteindex  |  Moduleindex | Applicationindex  | Inputoutputindex 

Because UDP send Broadcast messages it is necessary to take care of a unique siteindex, which identifies the gateway.
To define which propertie you want to access, there is a global definition of the propertie types.
There are two variants to set a value of a propertie.

* via UDP [Identifier][Propertietype]=Value(Priority)
* via HTTP /dev/id/[Identifier][Propertietype]=Value(Priority)

You can find a full list of commands in the readme of the Gateway
