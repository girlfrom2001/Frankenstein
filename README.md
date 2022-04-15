#!/usr/bin/python3

import RPi.GPIO as GPIO
import time
from w1thermsensor import W1ThermSensor
import os
import sys

GPIO.setmode(GPIO.BCM) #sets up pins
GPIO.setwarnings(False)

# Sam's idea: The motion detector starts the program and turns on a light as the program runs. The tempature must be 25C or higher to activate the buzzer. To turn off the program and light, touch the sensor.

Trg = 22 #touch sensor pin number
GPIO.setup(Trg,GPIO.IN,pull_up_down=GPIO.PUD_UP) #touch sensor









if (GPIO.input(Trg)==True): #input from touch sensor turns off the program
  GPIO.output (B_pin,GPIO.LOW) #turn the light off
  print("System shutting down...")
  time.sleep(1)
  sys.exit()
