# Autonomous Obstacle Avoiding Robot


---

## Abstract

This project documents the design and implementation of an **obstacle-avoiding robot car** capable of autonomous navigation through a predefined path. The robot uses an ultrasonic sensor to detect obstacles in its vicinity, halting forward motion upon detection. It then analyses its surroundings to identify alternative paths and selects the one with the least resistance to resume movement.

---

## Introduction

The goal of this project is to design and construct a robot car that can autonomously navigate through a path, detecting and avoiding obstacles along the way. When an obstacle is detected directly ahead, the robot halts its forward motion, scans its surroundings to evaluate the obstruction level of each potential path, and resumes movement along the route with the least resistance. This obstacle avoidance and path-selection mechanism demonstrates a practical application of robotics to real-world challenges such as autonomous navigation and dynamic obstacle avoidance.

---

## Working Principle

The ultrasonic sensor (HC-SR04) operates by emitting ultrasonic waves from its transmitter, which bounce off nearby objects and are captured by the receiver. Using the formula:

```
speed = distance / time
```

the distance to the object directly ahead of the car is calculated. If this distance falls below a predetermined threshold:

1. The motor driver halts forward motion and initiates a slight reverse movement.
2. The servo motor (carrying the ultrasonic sensor) rotates from **-90° to +90°**, scanning the full range to detect potential obstacles in all directions.
3. Once the least obstructed path is identified, the car advances along that route.
4. If further obstacles are encountered, the process repeats.

Through this iterative scan → decide → move cycle, the car autonomously navigates a path free of obstacles.

---

## Components Used

| # | Component |
|---|---|
| 1 | Ultrasonic Sensor (HC-SR04) |
| 2 | Arduino UNO |
| 3 | Servo Motor |
| 4 | Breadboard |
| 5 | L293D Motor Driver IC |
| 6 | Switch |
| 7 | Four DC Motors |
| 8 | Battery / Power Adaptor |

---

## Procedure

1. The vehicle moves forward in a straight line until the ultrasonic sensor detects an obstacle.
2. Upon detection, the vehicle reverses direction — this is coordinated by the L293D motor driver interfaced with the Arduino. Arduino pin connections were secured via soldering for stable communication, and the L293D regulates the gear motors through its output ports.
3. While reversing, the servo-mounted ultrasonic sensor sweeps a full 180°, measuring distances in all directions to identify the path of least resistance.
4. The vehicle then reorients (using its three-wheel configuration) and resumes movement along the chosen path.
5. This cycle repeats continuously, enabling autonomous operation.

---

## Circuit Diagram

The Arduino UNO interfaces with:
- The **HC-SR04** ultrasonic sensor (Trig/Echo pins) mounted on the servo
- The **servo motor** for sensor sweeping
- The **L293D motor driver**, which in turn drives the **four DC motors**
- A dedicated **power adaptor** supplying the Arduino

<img width="1107" height="575" alt="image" src="https://github.com/user-attachments/assets/2b410871-030f-4918-a5ed-0073a497994e" />


---

## Results

The car successfully navigated a predefined path, detecting obstacles, reversing, scanning for the least-obstructed direction, and resuming motion — achieving fully autonomous obstacle avoidance.

---

## Challenges & Discussion

1. **Power Supply:** The initial 9V battery drained quickly and could not sustain the circuit. Series/parallel battery configurations were tried but did not resolve the issue. The final solution was to power the Arduino directly via a power adaptor.
2. **Sensor Height Limitation:** The ultrasonic sensor could not reliably detect objects significantly shorter than its own mounted height, since the HC-SR04 relies on direct line-of-sight transmission and reflection of ultrasonic waves.

---

