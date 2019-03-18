**Wireless Sensor Networks**



**Introduction**

A sensor network is an infrastructure comprised of sensing (measuring), computing, and communication elements that gives an administrator the ability to instrument, observe, and react to events and phenomena in a specified environment. The administrator typically is a civil, governmental, commercial, or industrial entity.

The environment can be the physical world, a biological system, or an information technology (IT) framework. Network(ed) sensor systems are seen by observers as an important technology that will experience major deployment in the next few years for a plethora of applications, not the least being national security. Typical applications include, but are not limited to, data collection,monitoring, surveillance, and medical telemetry. In addition to sensing, one is often also interested in control and activation.

There are four basic components in a sensor network:

1. an assembly of distributed or localized sensors
2. an interconnecting network (usually, but not always,wireless-based)
3. a central point of information clustering; and
4. a set of computing resources at the central point (or beyond) to handle data correlation, event trending, status querying, and data mining. 

In this context, the sensing and computation nodes are considered part of the sensor network; in fact, some of the computing may be done in the network itself. Because of the potentially large quantity of data collected, algorithmic methods for data management play an important role in sensor networks. The computation and communication infrastructure associated with sensor networks is often specific to this environment and rooted in the device and application-based nature of these networks.

**Constraints and challenges.**

Individual sensor node in WSN is a resource constrained. They have limited processing capability, storage capacity, and communication bandwidth. It is necessary to consider the hardware constraints of the sensor nodes.

A. **Energy**
In WSN Energy is the biggest constraint. Energy consumption in sensor nodes can be divided into three parts:

1. Energy for the transducer.
2. Energy for communication among sensor nodes.
3. Energy for microprocessor computation.
   It was found that each bit transmitted in WSNs consumes about as much power as executing 800–1000 instructions. Thus, communication is more costly than computation in WSN's.

B. **Power Consumption**
The wireless sensor node are micro-electronic device that can be equipped with very limited power source (<0.5 Ah, 1.2 V). In some application, replenishment of power resources might be impossible. Sensor node lifetime, therefore, shows a strong dependence on battery lifetime.

C. **Memory**
Memory of sensor nodes usually consists of flash memory and RAM. Flash memory is used to store downloaded application code and RAM is used for storing application programs, sensor data, and intermediate computations. There is limited space to run complicated algorithms and functions after loading OS and application code [5].

D. **Transmission Range**
Range of communication in sensor nodes is very limited for both technically and by the need to conserve energy. The actual range achieved from a given transmission signal strength is dependent on various environmental factors such as weather, vibration, humidity, pressure and terrain etc.

E. **Communication**
A sensor node utilize maximum energy in data communication. This involves both data transmission and reception. It can be seen that for short-range communication with low radiation power, transmission and reception energy costs are nearly the same. Mixers, frequency synthesizers, phase locked loops (PLL), voltage control oscillators (VCO) and power amplifiers, all consume valuable power in the transceiver circuitry.

F. **Higher Latency In Communication**
Network congestion, Multi-hop routing and processing in the intermediate nodes of WSN may give rise to higher latency in packet transmission. So, it is very difficult to achieve synchronization. Such synchronization issues may sometimes be very critical in security as some security mechanisms may rely on critical event reports and cryptographic key distribution.

G. **Unattended Operation Of Networks**
Generally, the nodes in a WSN are deployed in remote regions like mountain, terrain and are left unattended. The likelihood that a sensor experiences a physical attack in such an environment is therefore, very high. Detection of physical tampering is virtually impossible due to remote management of a WSN.



**Applications of Sensor Networks.**

Wireless sensor network are deployed widely and they give an economical solution to many problems. In this section we give a survey on applications of Wireless Sensor Networks. Here are some typical and promising applications of WSNs are:
A. **Military Applications**
It can be used as commanders to monitor the status (position, quantity, availability) of their troops, equipment and battlefield
surveillance or reconnaissance of opposing forces and terrain to target the enemy, to detect attack etc.
B. **The Medical Application**
Sensors can be extremely useful in patient diagnosis and monitoring. Patients can wear small sensor devices that monitor their
physiological data such as heart rate or blood pressure [8].
C. **Commercial Applications**
It can be used to detect/track/monitor a vehicle, to support interactive devices, or to control environmental condition of a
building.
D. **Environmental Monitoring**
It can be used to monitor the condition/status of environment such as humidity, temperature, pressure, and pollution in soil, marine, and atmosphere. It also includes traffic, habitat, Wild fire etc.
E. **Infrastructure Protection Application**
It includes water distribution monitoring power grids monitoring, etc. [8].
F. Scientific Exploration
WSNs can be deployed under the water or on the land surface of a planet for scientific research purpose.
G. **Public Safety**
WSNs can be applied to monitor the chemical, biological or other environmental threats, it is important that the availability of the network is never threatened.



**Advantages of WSN**

1. Network setups can be carried out without fixed infrastructure.
2. Suitable for the non-reachable places such as over the sea, mountains, rural
    areas or deep forests.
3. Flexible if there is random situation when additional workstation is needed.
4. Implementation pricing is cheap.
5. It avoids plenty of wiring.
6. It might accommodate new devices at any time.
7. It's flexible to undergo physical partitions.
8. It can be accessed by using a centralized monitor.



**Mobile Ad hoc NETworks or MANET's**

An ad hoc network is a network that is setup, literally, for a specific purpose, to meet a quickly
appearing communication need. The simplest example of an ad hoc network is perhaps a set of
computers connected together via cables to form a small network, like a few laptops in a meeting
room. In this example, the aspect of self-configuration is crucial – the network is expected to work
without manual management or configuration.Usually, however, the notion of a MANET is associated with wireless communication and specifically wireless multihop communication; also, the name indicates the mobility of participating nodes as a typical ingredient. Examples for such networks are disaster relief operations – firefighters communicate with each other – or networks in difficult locations like large construction sites, where the deployment of wireless infrastructure (access points etc.), let alone cables, is not a feasible option. In such networks, the individual nodes together form a network that relays packets between nodes to extend the reach of a single node, allowing the network to span larger geographical areas than would be possible with direct sender – receiver communication.

|                            MANET                             |                             WSN                              |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| diversity, although present, is not quite as large in MANETs. | WSNs are conceivable with very different network densities, from very sparse to very dense deployments, which will require different or at least adaptive protocols. |
| MANETs, on the other hand, are used to support more conventional applications (Web, voice, and so on) with their comparably well understood traffic characteristics. | WSNs have to interact with the environment, their traffic charateristics can be expected to be very different from other, human-driven forms of networks. A typical consequence is that WSNs are likely to exhibit very low data rates over a large timescale, but can have very bursty traffic when something happens (a phenomenon known from real-time systems as event showers or alarm storms). Long periods (months) of inactivity can alternate with short periods (seconds or minutes) of very high activity in the network, pushing its capacity to the limits. |
| MANETs also have scarce energy but compared to WSN they have large resources. | WSNs have tighter requirements on network lifetime, and recharging or replacing WSN node batteries is much less an option than in MANETs |
|  In a MANET, each individual node should be fairly reliable  | in a WSN, an individual node is next to irrelevant.in a WSN, an individual node is next to irrelevant |


![img](https://i.imgur.com/3fnAmzH.jpg)



**Enabling technologies for wireless sensor networks.**



