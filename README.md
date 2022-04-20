#!/usr/bin/python3

import RPi.GPIO as GPIO
import time
from w1thermsensor import W1ThermSensor
import os
import sys

GPIO.setmode(GPIO.BCM) #sets up pins
GPIO.setwarnings(False)

# Sam's idea: The motion detector starts the program and turns on a light as the program runs. The tempature must be 25C or higher to activate the buzzer. To turn off the program and light, touch the sensor.

GPIO.setup(23, GPIO.IN) #motion sensor takes input
GPIO.setup(26, GPIO.OUT) # pin light is on
GPIO.setup(6, GPIO.OUT) #buzzer pin
GPIO.setup(4, GPIO.OUT) #tempature sensor ! must be on this GPIO
GPIO.setup(23, GPIO.IN, pull_up_down=GPIO.PUD_UP) #touch sensor

global touchstatus
touchstatus = False
GPIO.input(22)==True
time.sleep(2)

global i
i = GPIO.input(23) = touch sensor

def LEDon():
  GPIO.output(26, GPIO.HIGH)
  time.sleep(0.5)
#   GPIO.output(26, GPIO.LOW) do not need this because the light will be on 

def LEDoff():
  time.sleep(0.5)
  GPIO.output(26, GPIO.LOW) 
  
def buzzerOFF():
    B_pin = 6
    GPIO.output(B_pin,GPIO.HIGH)

def buzzerON():
     B_pin = 6
     GPIO.output(B_pin,GPIO.LOW)  

if (i == 1): #high output from sensor
    LEDon()
    print("System activated...")
    time.sleep(0.5)      
      
while LEDon() == True:
    temperature = sensor.get_temperature()
    print("The temperature is %s celsius" % temperature)
    time.sleep(.1)
    if temperature >= 25:
        buzzerON()
    else:
        LEDoff()
        buzzerOFF()

if (GPIO.input(Trg)==True): #input from touch sensor turns off the program
    LEDoff() #turn the light off
    buzzerOFF() #turn buzzer off
    print("System shutting down...")
    time.sleep(1)
    sys.exit()
