---
title: DAQ Studio 
date: 2021-12-08 19:47:35
tags: diy, DAQ
---

# DAQ Studio (Proposing)

DAQ studio is tool to acquire data from test instruments through RS232 / RS485 / CANBUS or any user defined protocols. 

Industrial users constantly need to communicate with a instrument with predefined protocols, most of the time, they will have to look up the manual and manully query the device. 

DAQ studio speeds the process by:
- User predefined proctocol
- NLP enchanced automated data extraction
- Build up device database to avoid reinventing wheels

Examples:
Alicat Meter with command A\r for reading
A\r -> A 14.3512 23.45 0.001 0.003 AIR\r

User definied protocol:
```
[ADDRESS] [PRESSURE] [Temperature] [Vol Flow Rate] [Mass Flow Rate] [Gas Type]\r
```

NLP enhanced data extraction:
```
Array of six items: A,14.3512,23.45,0.001,0.003,AIR
Four values
14.3512 - match ambient pressure pattern
23.45 - match temperature pattern
0.001 - unknown
0.003 - unknown
```

User only need to define the unknowns.


The tool can also be used to analyse acquired data using charts, averaging tools, data will also be saved in the cloud for later analysis.
