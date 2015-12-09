# IoT enabled Smart Parking Meter with IBM Bluemix & PubNub

Smart Parking System based on IBM Buemix hosted Parking Meter & hardware controlled by an Arduino YUN along with PubNub as the communication middleware.

## OVERVIEW

This project demonstrates how we can build an application seever on IBM Bluemix for allowing users to reserve parking bays and automatically handle their parking bills as well. The Hardware for this is based on Arduino YUN which can control a set of HC-SR04 ultrasonic sensors, to detect the availability of a parking slot and update this information on a mobile app using the PubNub's realtime data stream network.  

## INTRODUCTION

This application is assumed to be installed in a public parking space where each parking bay is monitored using a HC-SR04 ultrsonic sensor connected to Arduino YUN board.

Refer [Circuit Diagram](schematic.png)

The application has three parts

1) Parking management Server - This is the application server written in Python which manages the parking reservations, billing and broadcasts parking status updates to all Apps. 

2) Hardware - This is the master controller module which runs on Arduino YUN. It periodically gets the status of parking slots within its jurisdiction, from the ultrasonic sensors.

3) Mobile App - This is a cordova based simple mobile app which displays a map of the entire parking lot with color coded status indicators. It provides an instant update to the driver about the current availablity of free parking slots. It also allows the user to reserve a vacant parking bay and additionally handles the parking billing. 

BUILD AND INSTALL

Refer [Build & Install](BUILD.md) Steps

## WORKING

1) Deploy the Parking management Server application on IBM Bluemix

2) Install the Mobile app in an android phone and ensure that the phone has access to internet.

1) Power up the hadrware setup and make sure that Arduino YUN has access to internet.

2) Make sure that the ultrasonic sensors are not obstructed 

3) Launch the mobile app. Upon launching, it will ask the user for entering his vehicle registration ( license plate ) number. Feed in a number and proceed. 


4) Check that the initial status of the parking slots is green to indicate that all parking bays are free.

4) Obstruct one or more ultrasonic sensors with a object to simulate the presence of a vehicle. 

5) Observe the display of mobile app. After a few seconds the color for the corrosponding slot numbers should turn red to indicate that the slots have been occupied.

6) If the mobile app indicates grey status for any of the parking slot then this means that the sensor has a fault or is malfunctioning and the slot is currently unavailable. This can simulated in ultrasonic sensor by blocking the trigger signal or blocking the reception of echo.

7) For reserving a parking bay, tap on a vacant parking bay. The app will display a message indicating that the parking bay has been reserved for you. Also the color of the bay will change to red.

8) Subsequently, obstruct the corrosponding sensor to simulate the parking of car. 

9) After sometime , remove the obstruction from the ultrasonic sensor to simulate pulling out of the carr from the bay.

10) The mobile app should automatically detect this  and display a message to user prividing the details of his parking session along with the bill.



