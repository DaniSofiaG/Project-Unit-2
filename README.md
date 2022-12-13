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
![systemdiagram-project2 drawio](https://user-images.githubusercontent.com/89135778/207327393-314b295f-e8ba-446f-aebc-027906263f98.png)
**Fig.1** shows the system diagram for the proposed solution (**SL**). The indoor variables will be measured using an Arduino microprocessor and the sensor DHT11 conencted to the local computer (Laptop) located inside a room. The outdoor variables will be requested to the remote server using a GET request to the API of the server at ```192.168.6.147/readings```. The local values are stored in a CSV database locally.


## Record of Tasks
**Task No**|**Planned Action**|**Planned Outcome**|**Time estimate**|**Target completion date**|**Criterion**
:-----:|:-----:|:-----:|:-----:|:-----:|:-----:
1|Write the Problem context|Problem definition|10min|Nov 21|A
2|Read proposed solution|Have a better understanding of what we have to do and write our design statement|10min|Nov 21|A
3|Get materials|Have usb cable, adaptor, arduino and DHT11|2min|Nov 21|A
4|Create a way to arrange our tasks and schedule our work for the project|A github project spreadsheet where we can write tasks for the project|2min|Nov 21|B
5|Arrange our tasks according ot the format of the project|A table where we record and schedule our estiate tasks|15min|Nov 21|B
6|Set up DHT11 to Arduino|The DHT11 connected to the GND, ports 12 and 13 to get 5v  |1min|Nov 21|C
7|Edit and load Learning Log program to our Arduino|Fully set up Arduino and DHT11|10min|Nov 24|C
8|Begin coding to fullfill the needs of our clients|A code that will read the data collected by the arduino and the DHT11|15min|Nov 26|C
9|Make the code create and then append the data into two sepparate csv files|Two files titled "temperature.csv" and "humidity.csv" that store data in new lines|20min|Nov 26|C
10|Create an mvp (minimal viable product "prototype")/ Could be part of criteria C|Approval from clients to continue|10min|Nov 26|C
11|Run our program inside our room to collect data|At least 48 hrs of data, both temperature and humidity|50hr|Nov 26 to 27|C
12|Revise our data and consult to Dr Ruben in order to make improvements to our program and data collection|Feedback on better practices on how to store our data|10min|Nov 29|C
13|Format the data collection so that its saved in a new line everytime|A better way on how to stroe our data along with the exact date and time when it was taken|10min|Nov 29|C
14|Creat a program to grapn our data|Tow different graphs of temperature and humidity|20min|Dec 2|C
15|Re-run our program |Collect at least another 48hrs of data with new format|50hr|Dec 7 to 8|C
16|Create a program to visualize our data |Two graphs, temperature and humidity using matplotlib |40min|Dec 8|C
17|Get relevant values for the clients |A comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.|40min|Dec 10|C
18|Create a program that gets the mathimatical models of our data and and the sensor data |Four graphs with a linear and quadratic model that goes through the scatter plot |1hr|Dec 10|C
19|A way for our clients to visualize our code without having to know python|Create flowcharts on relevant parts of our code|1hr|Dec 11|B
20|Another way to support the visualization of our solution|A system diagram|10min|Dec11|B

## Test Plan

## Flow diagrams
![flowcharts-project2](https://user-images.githubusercontent.com/89135778/207318982-60e019bc-4c61-4c6f-a2c5-53cf6b5f5405.png)
![flowcharts2-project2-Page-2 drawio](https://user-images.githubusercontent.com/89135778/207319231-c944f7cb-27ac-4e5d-bc52-b2dd29e05469.png)


# Criteria C: Development

## List of techniques used

## Development


# Criteria D: Functionality

A 7 min video demonstrating the proposed solution with narration


# Poster
![1](https://user-images.githubusercontent.com/111941990/207320927-b9de2b15-014b-4c90-a76c-3e5d0a80fdc1.png)
![2](https://user-images.githubusercontent.com/111941990/207320969-7d28bc18-c125-4693-9c17-21ddb3493c3d.png)
