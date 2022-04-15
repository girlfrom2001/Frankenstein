#!/usr/bin/python3

import RPi.GPIO as GPIO
import time
from w1thermsensor import W1ThermSensor
import os
import sys

# Sam's idea: The motion detector starts the program and turns on a light as the program runs. The tempature must be 25C or higher to activate the buzzer. To turn off the program and light, touch the sensor.
