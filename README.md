
# Arduino Ultrasonic Radar

An Arduino-based ultrasonic radar system built using an **Arduino Uno**, **HC-SR04 ultrasonic sensor**, and **servo motor**.

The system rotates the ultrasonic sensor across a 180° range and measures the distance to objects at different angles. The collected **angle and distance data** is transmitted to a computer and displayed on a **radar-style map**, allowing detected objects to be visualized in real time.

## Project Overview

This project was developed as part of a university Arduino class.

The project combines hardware and software components to create a simple radar system:

* **Arduino Uno** — controls the sensor and servo motor
* **HC-SR04 Ultrasonic Sensor** — measures the distance to objects
* **Servo Motor** — rotates the ultrasonic sensor
* **Breadboard & Jumper Wires** — connect the electronic components
* **Computer Radar Interface** — visualizes the measured objects on a radar-style map

The ultrasonic sensor is mounted on the servo motor. As the servo rotates, the Arduino takes distance measurements at different angles.

The Arduino then sends the angle and distance data through the serial connection to the computer. The computer uses this information to display the detected objects on a radar map.

## Features

* 180° ultrasonic scanning
* Automatic servo movement
* Real-time distance measurement
* Angle-based object detection
* Serial communication between Arduino and computer
* Radar-style graphical visualization
* Real-time object mapping
* Arduino Uno based
* Low-cost hardware

## Components

| Component                 | Quantity |
| ------------------------- | -------: |
| Arduino Uno               |        1 |
| HC-SR04 Ultrasonic Sensor |        1 |
| Servo Motor               |        1 |
| Breadboard                |        1 |
| Jumper Wires              |  Several |
| USB Cable                 |        1 |
| Computer                  |        1 |

## How It Works

The system consists of two main parts:

1. **Hardware**
2. **Radar visualization software**

### 1. Hardware Scanning

The servo motor rotates the HC-SR04 ultrasonic sensor through a defined angle range.

At each angle:

1. Arduino positions the servo.
2. The HC-SR04 sends an ultrasonic pulse.
3. The pulse travels toward an object.
4. The pulse reflects from the object.
5. The sensor receives the returning echo.
6. Arduino measures the echo time.
7. The distance is calculated.
8. The angle and distance are sent to the computer.

### 2. Radar Visualization

The computer receives the measurements through the Arduino's serial connection.

The data contains two important values:

```text
Angle + Distance
```

For example:

```text
30° → 45 cm
60° → 72 cm
90° → 35 cm
120° → 80 cm
```

The visualization software converts these measurements into positions on a radar-style map.

The polar coordinates can be represented using:

```text
X = Distance × cos(angle)
Y = Distance × sin(angle)
```

This allows the detected objects to be displayed according to their approximate position relative to the ultrasonic sensor.

## Radar Map

The radar visualization represents the area scanned by the ultrasonic sensor.

A typical visualization contains:

* A radar/grid background
* Angle indicators
* Distance markers
* Scanning line
* Detected objects
* Real-time object positions

As the servo rotates, the scanning line moves across the radar display. When an object is detected, its approximate position is shown according to its measured angle and distance.

## Data Communication

The Arduino communicates with the computer through a USB serial connection.

The Arduino sends measurements similar to:

```text
0,85
10,82
20,79
30,45
40,52
50,68
```

Where:

```text
angle,distance
```

For example:

```text
30,45
```

means that an object was detected approximately **45 cm away at an angle of 30°**.

The computer application reads this information and converts it into a graphical radar representation.

## Distance Calculation

The approximate distance is calculated using the speed of sound:

```text
Distance = (Echo Time × Speed of Sound) / 2
```

The division by two is necessary because the ultrasonic pulse travels from the sensor to the object and then returns to the sensor.

## Wiring

A typical connection is:

### HC-SR04 → Arduino Uno

| HC-SR04 Pin | Arduino Uno    |
| ----------- | -------------- |
| VCC         | 5V             |
| GND         | GND            |
| TRIG        | Digital Pin 10 |
| ECHO        | Digital Pin 11 |

### Servo Motor → Arduino Uno

| Servo Wire | Arduino Uno   |
| ---------- | ------------- |
| Signal     | Digital Pin 9 |
| VCC        | 5V            |
| GND        | GND           |

> **Note:** The exact pins may be different depending on the code used in the original project. Check the Arduino sketch before connecting the circuit.

## Software Requirements

### Arduino

* Arduino IDE
* Arduino Uno
* Arduino Servo library

### Radar Visualization

The radar visualization requires the computer-side program used to receive the serial data and draw the radar map.

Depending on the original implementation, this may have been created using software such as:

* Processing
* Python
* Java
* Another serial visualization application

> The original visualization source code should be included in the repository if it is available.

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/arduino-ultrasonic-radar.git
```

### 2. Upload the Arduino Code

Open the Arduino `.ino` file in Arduino IDE.

Select:

```text
Tools → Board → Arduino Uno
```

Select the correct USB/COM port and upload the program.

### 3. Connect the Arduino

Connect the Arduino Uno to the computer using a USB cable.

### 4. Start the Radar Visualization

Run the computer-side visualization program included in the repository.

The visualization application should connect to the Arduino's serial port and begin receiving angle and distance measurements.

### 5. Start Scanning

Once the Arduino and visualization program are connected, the servo will rotate the ultrasonic sensor and the radar map will update with the detected objects.


```

## Example Radar Data

The Arduino may send data in the following format:

```text
Angle: 0°   Distance: 85 cm
Angle: 10°  Distance: 82 cm
Angle: 20°  Distance: 79 cm
Angle: 30°  Distance: 45 cm
Angle: 40°  Distance: 52 cm
```

The visualization software converts this information into a graphical representation.

## Applications

This project demonstrates concepts that can be applied to:

* Object detection
* Robotics
* Obstacle detection
* Autonomous systems
* Distance measurement
* Embedded systems
* Sensor visualization
* Serial communication
* Real-time data visualization

## Limitations

The system has some practical limitations:

* Ultrasonic measurements can be affected by object shape and surface material.
* Small or angled objects may not be detected reliably.
* The HC-SR04 has a limited measurement range.
* Servo movement introduces a delay between measurements.
* The radar represents detected objects based on a single ultrasonic sensor.
* The visualization provides an approximate representation rather than a precise 2D map.
* Objects outside the sensor's scanning range cannot be detected.

## Future Improvements

Possible improvements include:

* Improving the radar graphical interface
* Adding distance filtering
* Improving object detection accuracy
* Tracking moving objects
* Adding multiple ultrasonic sensors
* Adding an LCD/OLED display
* Adding data logging
* Improving scanning speed
* Adding a custom PCB
* Creating a more advanced 2D mapping system
* Adding object labels and tracking

## Authors

- **Luka Tonia** — [GitHub Profile](https://github.com/LukaTonia)
- **Levan Japaridze** — [GitHub Profile](https://github.com/Japo8)

University Arduino  Project



You may modify and use the project for learning and academic purposes.
