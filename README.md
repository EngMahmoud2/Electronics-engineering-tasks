# Servo motor


## Engine operation algorithm Servo motor type To shape the robot's walking motion


To design a servo motor operating algorithm to form the robot's walking motion, we need to implement a set of programming steps that control the movement of the servo motors to form the walking motion. I will give you a simple example using the Python programming language.

Prerequisites:

Servo library to control servo motors.

Time library to manage timings.

Numpy library if you want to deal with arrays easily.
Programming steps:
Importing the basic libraries:

import time
import numpy as np
from Servo import Servo

### Define the servo motors and their location:
```
servo_pins = [2, 3, 4, 5, 6, 7] # List of the pin numbers connected to the servo
servos = [Servo(pin) for pin in servo_pins]
```
### Define the start and end angles:
```
Start and end angles for each servo
initial_angles = [90, 90, 90, 90, 90, 90] # Default start angles
walking_angles = [
[60, 120], # Forward and backward step angles for each servo
[70, 110],
[80, 100],
[60, 120],
[70, 110],
[80, 100]
]
```
### Function to move the servo to a certain angle:
```
def move_servo(servo, angle):
servo.write(angle)
time.sleep(0.02) # Wait a little while to let the servo move
```
### Function to form the walking motion:
```
def walk_cycle():
for i in range(len(servos)):
move_servo(servos[i], walking_angles[i][0])   # Step forward
time.sleep(0.5) # Wait for equilibrium

for i in range(len(servos)):
move_servo(servos[i], walking_angles[i][1])   # Step back
time.sleep(0.5) # Wait for equilibrium
```

### Run the walking motion repeatedly:
```
def start_walking():
try:
while True:
walk_cycle()
except KeyboardInterrupt:
print("Stop walking.")
for i in range(len(servos)):
move_servo(servos[i], initial_angles[i])     # Return to default angles
```
### Run:To start the robot, call the start_walking() function:
```
if name == "main":
start_walking()
```
