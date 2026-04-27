# Future-Engineers-2026
## Introduction 
Here you can see all our robot´s documentation.[For more information click here](Introduccion)
### Presentation 
Our team´s robot is called WALLE. WALLE was designed for the Future Engineers challenge of the World Robot Olympiad. In this challenge we must complete 2 rounds. The first one, called Open Challenge, consists of completing 3 full laps around a board whose internal walls are placed randomly. The second, called Obstacle Challenge, also requires three laps on a board changing, but with the added difficulty of avoiding obstacles. Depending on the obstacles´colors (red or green) it must be avoided from the right side or the left side.[For more information click here](Introduccion/Objetivo.md)

### Initial Conditions
To properly carry out this project, this robot has been previously designed according to some specific rules and conditions. We had complete freedom to use any material, such as plastic, wood or even Lego pieces. However, we had an limitation in the robot´s size. The robot can not exceed 30cm x 30cm. We adapted its design in all these conditions, with special care in the front steering gear, since it was not allow to make turns with the independent motors´control as they had to be conected in the same pin. This force us to design a front steering gear with a servomotor. [For more information click here](Condiciones_Previas/Condiciones_Previas.md)

## Materials and hardware - software relation
1. 3D printed chassis and pins: allows the placement of all the components with the enough space for the front steering gear not to interference with the rest of the components.
2. Arduino Uno board: controls all the robot´s components, such as the motors, the servomotor or the sensors. These are connected to the Arduino board
3. MG996R servo motor:  main responsible for the front steering gear. This is controlled by a servos library in the Arduino Ide program.
4. TT model motor with 1:40 speed reduction: provide robot movement. These are connected to the L298N motor driver shield for control.
5. Wheels with a diameter of [cm]: connected to the rear motors for their control.
6. Three HC-SR04 ultrasonic sensors for measuring distances: must measure and calculate the distance between the walls and the obstacles.
7. Electronic wiring: breadboard, male-to-male jumper wires, female-to-male jumper wires, and L298N shield for motor control: wires, protoboard and motor driver shield. Allows the comunication between the Arduino board and the rest of the components.
8. Power supply: two 3.7V 9900mAh 18650 batteries connected in series within their battery holder that provide enough energy for the correct running of the robot.
10. BNO055 gyroscope: allows the robot to make turns much more precisely by setting itself to specific degrees at the program.
11. Front wheel mechanism: made by 3D printed pieces that hold the mechanism for the robot to make turns correctly.
[For more information click here](Condiciones_Previas/Materiales_acabado.md)

## Mechanics 
### Chassis 
For the chassis design, we opted for a smaller one than in previous years to facilitate turns on the board We also addressed the lack of space for all the components by adding an upper level where we would place the circuit board, breadboard, shield, and later, the camera. However, we also had to adjust the design to accommodate a single rear motor for the robot's drive. Therefore, we drilled two holes in the lower level of the chassis (where the ultrasonic sensors, servo motor, and front wheel mechanism are located) for the wheels. We also maintained the front wheel design from previous years. We created a small protrusion to house the servo motor and all the necessary steering mechanism components. One of the three ultrasonic sensors, in this case, the center one, would also be located on this same protrusion.

This forms the base of the robot, upon which the other platforms will be stacked using a series of pins screwed to the structure. These plates will be secured with screws and will serve as a support for the installation of the remaining necessary components.
[For more information click here](Mecánica/Chasis.md)

### Steering system
[For more information click here](Mecánica/Dirección.md)

## Electronics
### Power system
One of the the major problems was being able to prove the necessary energy to all the components. o solve this, we used two rechargeable 18650 batteries of 9900 mAh each, connected in series to a battery holder. Other options, such as AAA batteries in series, 9V batteries, or even rechargeable 9V batteries of 1300 mAh, were not efficient enough and caused voltage drops.
[For more information click here](Electrónica/Alimentacion.md)

## Components

### Servo Motor
For the front steering wheel was necessary the incorporation of a servo motor. We chose one that could make turns according to the turning angles to make it easier for us to program.

### Motors 
In order to WALLE to move, we used only two motors, which were installed in the back of our vehicle. To connect the motors, we used the L298N motor driver shield, which was used only as an output for controlling the motors.

### Motor driver shield
For the motor connections, we chose the L298N shield, because the previous shields were incompatible with the board. All we did was connect the shield's ena pin to pin 7 of the Arduino board to control the speed, and the motors to the in1 and in2 pins to turn them on and off.

### Sensors
To prevent the robot from crashing with walls, we used ultrasonic distance sensors. We also added a structure into the robot to hold the sensors. To program these, we created a distance measurer that allowed us to see the distance each sensor was measuring in real time on the serial monitor.

### Arduino board
We took the Arduino Uno board as we were already familiar with it. 

### Bateries
We used the 18650 batteries for our robot. Their maximum voltage is 4.2V, and the battery capacity is 9900mAh. These batteries are also rechargeable. We chose these over others due to the large number of components we had to power.

[For more information click here](Electrónica/Componentes.md)

## Compilation process
For programming, we use the Arduino IDE program. Once the program is complete, all we have to do is upload it to the board. The process of uploading the board is very simple; we just connect the board to the computer using a wire and download the program. This way, the robot is ready to work.



## Compilation process
For programming, we used the Arduino IDE program. Once the program is complete, all we have to do is upload it to the board. The process of uploading the board is very simple; we just connect the board to the computer using a wire and download the program. This way, the robot is ready to work.

