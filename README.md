 # Project-Unit-2

![giphy](https://user-images.githubusercontent.com/111941990/202969030-338b256b-aff1-4e3c-bd06-5f7e37bd59da.gif)


# Unit 2: A Distributed Weather Station for ISAK


# Criteria A: Planning


## Problem definition
Emile and Ainne are two resource-limited roommates at UWC ISAK Japan worried about their health, as they’ve seen on a tiktok that the the temperature and humidity in their room can cause health issues. They’ve started leaving a thermometer so that they can see the temperature of the room and check it once a day before going to sleep, but the task has become tedious and inaccurate since they often forget to check it and it's very restricted to their room, which means they don’t know the value of this data relative to the temperature and humidity of the campus. It is also difficult to compare the data they get from the thermometer, and they have no way to measure humidity. Ainne and Emile are in need of a cost effective, more efficient way to get and visualize both the humidity and temperature of their room and the campus along with other useful measures of the data such as mean, standard deviation, minimum, maximum, and median.



## Proposed Solution
Considering the client requirements an adequate solution includes a low cost sensing device for humidity and temperature and a custom data script that process and anaysis the samples acquired. For a low cost sensing device an adequate alternative is the DHT11 sensor[^1] which is offered online for less than 5 USD and provides adequare precision and range for the client requirements (Temperature Range: 0°C to 50°C, Humidity Range: 20% to 90%). Similar devices such as the DHT22, AHT20 or the AM2301B [^2] have higher specifications, however the DHT11 uses a simple serial communication (SPI) rather than more eleborated protocols such as the I2C used by the alternatives. For the range, precision and accuracy required in this applicaiton the DHT11 provides the best compromise. Connecting the DHT11 sensor to a computer requires a device that provides a Serial Port communication. A cheap and often used alternative for prototyping is the Arduino UNO microcontroller [^3]. "Arduino is an open-source electronics platform based on easy-to-use hardware and software"[^4]. In additon to the low cost of the Arduino (< 6USD), this devide is programable and expandable[^1]. Other alternatives include diffeerent versions of the original Arduino but their size and price make them a less adequate solution.


**Design statement**

I will design and make a program that checks temperature and humidity for two clients who are roommates and students at UWC ISAK Japan. The program will consist on a tool called DHT11 sensor for being able to keep track of humidity and temperature of their rooms, plus getting useful measures such as mean, standard deviaton, minimum, maximum, and median. It is constructed using the softwares Python, Arduino, and DHT11. It will take 3 weeks to make and will be evaluated according to the criteria A, B, and C.


[^1]: Industries, Adafruit. “DHT11 Basic Temperature-Humidity Sensor + Extras.” Adafruit Industries Blog RSS, https://www.adafruit.com/product/386. 
[^2]: Nelson, Carter. “Modern Replacements for DHT11 and dht22 Sensors.” Adafruit Learning System, https://learn.adafruit.com/modern-replacements-for-dht11-dht22-sensors/what-are-better-alternatives.   
[^3]:“How to Connect dht11 Sensor with Arduino Uno.” Arduino Project Hub, https://create.arduino.cc/projecthub/pibots555/how-to-connect-dht11-sensor-with-arduino-uno-f4d239.  
[^4]:Team, The Arduino. “What Is Arduino?: Arduino Documentation.” Arduino Documentation | Arduino Documentation, https://docs.arduino.cc/learn/starting-guide/whats-arduino.  

## Success Criteria

1. The solution provides a visual representation of the Humidity and Temperature values inside a dormitory (Local) and outside the house (Remote) for a period of minimum 48 hours. 
2. ```[HL]``` The local variables will be measure using a set of 4 sensors around the dormitory.
3. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote locations. ```(SL: linear model)```, ```(HL: non-lineal model)```
4. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.
5. ```(SL)```The Local samples are stored in a csv file and ```(HL)``` posted to the remote server.
6. Create a prediction the subsequent 12 hours for both temperature and humidity.
7. A poster summarizing the visual representations, model and analysis is created and communicated. (Should include a study of health levels)

# Criteria B: Design

## System Diagram **SL**
![](sysdim_sl.png)

**Fig.1** shows the system diagram for the proposed solution (**SL**). The indoor variables will be measured using an Arduino microprocessor and the sensor DHT11 conencted to the local computer (Laptop) located inside a room. The outdoor variables will be requested to the remote server using a GET request to the API of the server at ```192.168.6.147/readings```. The local values are stored in a CSV database locally.

![](sysdim_hl.png)

**Fig.2** shows the system diagram for the proposed solution (**HL**). The indoor variables will be measured using a Raspberry PI and four DHT11 sensors located inside a room. Four sensors are used to determine more precisely the physical values and include measurement uncertainty. The outdoor variables will be requested to the remote server using a GET request to the API of the server at ```192.168.6.147/readings```. The local values are stored in a CSV database locally and POST to the server using the API and TOKEN authentication. A laptop computer is used for remotely controlling the local Rasberry Pi using a Dekptop sharing application (VNC Viewer). (Optional) Data from the local raspberry is downloaded to the laptop for analysis and processing.


## Record of Tasks
**Task No**|**Planned Action**|**Planned Outcome**|**Time estimate**|**Target completion date**|**Criterion**
:-----:|:-----:|:-----:|:-----:|:-----:|:-----:
1|Write the Problem context|Problem definition|10min|Nov 21|A
2|Read proposed solution|Have a better understanding of what we have to do and write our design statement|10min|Nov 21|A
3|Get materials|Have usb cable, adaptor, arduino and DHT11|2min|Nov 21|A
4|Set up DHT11 to Arduino|The DHT11 connected to the GND, ports 12 and 13 to get 5v  |1min|Nov 21|C
5|Edit and load Learning Log program to our Arduino|Fully set up Arduino and DHT11|10min|Nov 24|C
6|Begin coding to fullfill the needs of our clients|A code that will read the data collected by the arduino and the DHT11|15min|Nov 26|C
7|Make the code create and then append the data into two sepparate csv files|Two files titled "temperature.csv" and "humidity.csv" that store data in new lines|20min|Nov 26|C
8|Create an mvp (minimal viable product "prototype")/ Could be part of criteria C|Approval from clients to continue|10min|Nov 26| 
9|Run our program inside our room to collect data|At least 48 hrs of data, both temperature and humidity|50hr|Nov 26 to 27|C
10|Revise our data and consult to Dr Ruben in order to make improvements to our program and data collection|Feedback on better practices on how to store our data|10min|Nov 29| 
11|Format the data collection so that its saved in a new line everytime|A better way on how to stroe our data along with the exact date and time when it was taken|10min|Nov 29|C
12|Creat a prodgram to grapn our data|Tow different graphs of temperature and humidity|20mi|Dec 2| 
13|Re-run our program |Collect at least another 48hrs of data with new format|50hr|Dec 7 to 8| 

## Test Plan

## Flow diagrams

# Criteria C: Development

## List of techniques used

## Development


# Criteria D: Functionality

A 7 min video demonstrating the proposed solution with narration
