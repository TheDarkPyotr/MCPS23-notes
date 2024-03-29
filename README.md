## Mobile and cyber-physical systems 
### A.Y. 22-2023 notes

The course is organized in two modules that run in parallel, and 4 hands-on classes   
The timetable can be found here: [https://www.di.unipi.it/it/didattica/wif-lm/orario](https://www.di.unipi.it/it/didattica/wif-lm/orario)  
See [[README#Contributing]] for submit lectures notes.

### Lectures 
- **Prof. Chessa**:
	- [[L1 - 21-02-2023]] : Introduction to IoT architecture
	- [[L2 - 22-02-2023]] : IoT issues and protocol families
	- [[L4 - 28-02-2023]] : Brief IoT Security and intro to MQTT
	- [[L6 - 03-03-2023]] : MQTT basic features, QoS, retained messages, last will and packet structure
	- [[L7 - 07-03-203]]: MQTT problems, brief CoAP, introduction to ZigBee
	- [[L9 - 10-03-2023]]: ZigBee network joining, management, formation; APO, APS
	- [[L10 - 14-03-2023]]: ZDO, ZCL #TODO **waiting update materials**
	- [[L11 - 15-03-2023]]: Greenhouse and DOREMI Use cases
	- [[L13 - 21-03-2023]]: Iot Design aspect intro
	- [[L15 - 24-03-2023]]: Energy efficiency, duty cycle
- **Prof.ssa Paganelli**:
	- [[L3 - 24-02-2023]] : Wireless Network (*CSMA/CD, MACA, Binary Exponential Backoff*)
	- [[L5 - 01-03-2023]]: IEEE 802.11 (Wireless Network)
	- [[L8 - 08-03-2023]]: Mobile Networks (4G, 5G and mobility topics)
	-  [[L12 - 17-03-2023]]: SDN Intro
	- [[L14 - 22-03-2023]]: SDN Architecture

##### Module 1, Prof. Stefano Chessa:

-   IoT & smart environments;
-   IoT case studies;
-   MQTT, IEEE 802.15.4, ZigBee and Bluetooth standards;  
-   design aspects of IoT; 
-   energy harvesting IoT;
-   introduction to embedded programming;
-   wireless sensor networks and ad hoc networks.
-   indoor localization (By Dr. Filippo Palumbo of ISTI-CNR)

##### Module 2, Prof. Federica Paganelli:

-   wireless networks;  
-   mobile networks;
-   software-defined networks;
-   network function virtualization;
-   introduction to signal processing.  

##### Hands-on classes:

the course also includes 4 (tentative) hands-on classes, that will require the students bring their own PC in class (the rest of the material will be provided by the instructors.). The classes are on:

-   SDN and network slicing;
-   Arduino and Tensorflow (by Dr. Michele Girolami of ISTI-CNR);
-   Arduino, Thingspeak and MQTT;
-   sampling and FFT.

### Material
Relevant sites:  

-   Arduino: [http://arduino.cc/en/Guide/HomePage](http://arduino.cc/en/Guide/HomePage "http://arduino.cc/en/Guide/HomePage")
    
-   TinyOS: [http://www.tinyos.net/](http://www.tinyos.net/ "http://www.tinyos.net/")
    
-   Contiki: [http://contiki-os.org/](http://contiki-os.org/)  
    
-   Zigbee alliance: [http://www.zigbee.org/](http://www.zigbee.org/)
    
-   Bluetooth standard: [https://www.bluetooth.com/](https://www.bluetooth.com/)
    
-   MQTT: [http://mqtt.org/](http://mqtt.org/)
    
-   COAP: [http://coap.technology/](http://coap.technology/)
    
-   IEEE 802.15.x standards: [https://standards.ieee.org/about/get/802/802.15.html](https://standards.ieee.org/about/get/802/802.15.html)
    
-   Particle: [https://docs.particle.io/  
    ](https://docs.particle.io/)
    
-   Raspberry: [https://www.raspberrypi.org/  
    ](https://www.raspberrypi.org/)
    
-   Sparkfun: [https://learn.sparkfun.com/](https://learn.sparkfun.com/)


### Contributing
For each lecture the `.md` file is named `L{N} - {DATE}` where `{N}` is the incremental number of the lecture and `{DATE}` is the calendar date of the lecture. Each lecture have the following schema:

```markdown
## Lecture main topic
### Paragraph 
#### Sub-paragraph
...
```

To save images in the `/images` folder: right click on folder and `Set as attachment folder`. 