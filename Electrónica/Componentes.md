# Componentes del robot

| Componentes |  Modelo |
| :--- | :---: |
| Servomotor| MG996R |
| Escudo | L298N |
| Sensores de ultrasonidos|  HC-SR04  |
| Placa | Arduino Uno |
| Motor| Modelo TT con reducción de velocidad 1:40. |
| Baterías | 2 x 18650 of 9900 mAh cada una |

## Servomotor
Basándonos en experiencias anteriores, directamente hemos optado por el servomotor MG996R ya que funciona controlando ángulos de giro en lugar de controlar la velocidad del propio servomotor. Esto facilita bastante todo ya que ahora podemos mover las ruedas delanteras con más precisión y requiriendo mucho menos esfuerzo. El modelo que elegimos fue el MG996R, como ya he dicho, ya que es conocido por ser más potente y por tener un buen rango de movimiento para este tipo de proyectos.

| <img src="fotos_electronica/MG996R.jpg"> | **Specifications** |
|------------------------------|------------------------------|
| **Model:** MG996R | **Operating Voltage:** 4.8V – 7.2V |
| **Logic Voltage:** 3.3V / 5V compatible | **PWM Frequency:** 50 Hz (20 ms period) |
| **Stall Torque:** 9.4 kg·cm @ 4.8V / 11 kg·cm @ 6.0V | **Features:** Digital servo, metal gears, dual ball bearings, approximately 180° rotation|
| **Control Interface:** PWM (3-wire: Signal, VCC, GND) | **Operating speed:** 0.17 s/60° @ 4.8V, 0.14 s/60° @ 6.0V |
| 🔗 **[Buy Here](https://www.lcsc.com/product-image/C112633.html)** | **Function:** Controls the steering system |

<p align="center">
<img src="fotos_electronica/IMG_1356.jpeg" width="700" height="700" />
</p>

## Escudo
El escudo que hemos utilizado ha sido el modelo L298N, y lo usamos principalmente para hacer las conexiones de los motores. Este escudo nos ha permitido controlar el movimiento de los motores de una forma más sencilla, ya que se encarga de enviar la energía necesaria para que funcionen correctamente. Además ya eramos conscientes de la incompatibilidad del escudo DRV8835 de Pololu con nuestros motores. Por lo tanto, seleccionamos directamente el modelo L298N.

| <img src="fotos_electronica/escudofoto.jpg"> | **Specifications** |
|------------------------------|------------------------------|
| **Model:** L298N Dual H-Bridge Motor Driver Module | **Operating Voltage:** 5V – 35V (motor supply) |
| **Logic Voltage:** 5V TTL compatible | **PWM Frequency:** Up to 25–30 kHz |
| **Max Continuous Current:** 2A per channel  |**Max Peak Current:** 3A per channel (short duration)|
| **Control Interface:** PWM + Direction pins (IN1–IN4, ENA, ENB) |**Built-in Features:** Dual H-Bridge, 5V regulator (78M05), thermal protection, flyback diodes |
| 🔗 **[Buy Here](https://www.lcsc.com/product-image/C112633.html)** | **Function:** Controls the speed and direction of DC motors and stepper motors using PWM and H-Bridge switching |

<p align="center">
<img src="fotos_electronica/IMG_1355.jpeg" width="700" height="700" />
</p>

## Sensores de ultrasonidos 
Para la correcta programación de nuestro robot necesitábamos disponer de tres sensores ultrasónicos de distancia para conseguir que el robot no impactara ni tocara ninguna pared. Para la implementación de estos en el chasis utilizamos una estructura diseñada previamente en la interfaz de TinkerCad y la imprimimos en 3D. Esto nos permitió sujetar bien los tres sensores de ultrasonidos. De tal modo que nos aseguramos que los sensores se mantienen en su sitio sin caerse mientras hacíamos pruebas.

| <img src="fotos_electronica/escudofoto.jpg"> | **Specifications** |
|------------------------------|------------------------------|
| **Model:** HC-SRO4 | **Operating Voltage:** 5V DC |
| **Logic Voltage:** 5V TTL compatible | **PWM Frequency:** 40 kHz |
| **Measuring Range:** 2 cm – 400 cm |**Measurement Accuracy:** ±3 mm|
| **Control Interface:** Trigger (TRIG) + Echo (ECHO) digital pins |**Built-in Features:** Non-contact distance measurement, low power consumption, automatic echo detection |
| 🔗 **[Buy Here](https://www.lcsc.com/product-image/C112633.html)** | **Function:** Measures the distance to objects by transmitting and receiving ultrasonic waves|

<p align="center">
<img src="fotos_electronica/IMG_1357.jpeg" width="700" height="700" />
</p>

## Placa 
La placa que hemos utilizado para nuestro robot ha sido la Arduino Uno R3. Decidimos usar esta placa porque ya habíamos trabajado con Arduino en otras ocasiones y nos parecía más fácil de entender. Además, es muy útil para conectar sensores, cables y otros componentes debido a su multitud de pines, y luego programarla para que funcione como queremos. Gracias a esto, pudimos hacer la programación del robot de forma más sencilla y aprender mejor cómo funciona la programación y la electrónica.

| <img src="fotos_electronica/escudofoto.jpg"> | **Specifications** |
|------------------------------|------------------------------|
| **Model:** Arduino Uno R3 | **Operating Voltage:** 5V  |
| **Input Voltage:** 7–12V recommended (6–20V limit) | **Clock Frequency:** 16 MHz |
|**Microcontroller:** ATmega328P|**Memory:** 32 KB Flash, 2 KB SRAM, 1 KB EEPROM|
| **Digital I/O Pins:** 14 (6 PWM outputs) |**Analog Inputs:** 6 (10-bit ADC) |
| **Communication Interfaces:** UART, I²C, SPI, USB|**Features:** USB Type-B, ICSP header, reset button, onboard voltage regulator, replaceable ATmega328P |
| 🔗 **[Buy Here](https://www.lcsc.com/product-image/C112633.html)** | **Function:** Programmable microcontroller board for controlling sensors, actuators, and embedded electronic systems. |

<p align="center">
<img src="fotos_electronica/IMG_2478.jpeg" width="700" height="700" />
</p>

## Motor
Para conseguir que el robot se pueda mover, hemos utilizado solo un motor que van conectados a las ruedas traseras. No pusimos motores en las ruedas delanteras porque no eran necesarios. En vez de eso, decidimos controlar la dirección del robot usando dos ruedas delanteras que están conectadas a un servomotor. De tal manera que el servomotor permite que el robot se mueva hacia la izquierda o hacia la derecha, encargándose de su dirección.

| <img src="fotos_electronica/escudofoto.jpg"> | **Specifications** |
|------------------------------|------------------------------|
| **Model:** TT DC Gear Motor| **Operating Voltage:** 3V – 6V DC  |
|**Rated Voltage:** 6V DC | **No-Load Speed:** ≈200 RPM @ 6V (varies by gear ratio) |
|**Stall Current:** ≈1.2 A|**No-Load Current:** ≈150–250 mA|
|**Output Shaft:** Double D Shaft |**Gearbox Type:** Plastic reduction gearbox|
|**Motor Type:** Brushed DC Motor|**Features:** High torque, low cost, lightweight, suitable for robot cars |
| 🔗 **[Buy Here](https://www.lcsc.com/product-image/C112633.html)** | **Function:** Provides rotational motion to drive robot wheels and other small mechanical systems. |

<p align="center">
<img src="fotos_electronica/IMG_2477.jpeg" width="700" height="700" />
</p>

## Baterías
Las baterías 18650 que son de ion de litio son ampliamente usadas en robótica y electrónica, y es por esto que son las que hemos usado. Su voltaje máximo son 4.2 V cargadas completamente. Y la capacidad de la batería en este caso, 9900 mAh (aunque muchas veces las baterías baratas "de 9900 mAh" no entregan realmente esa capacidad; suelen estar sobreestimadas). Con las dos baterías apiladas en serie tendríamos para 4 cargas enteras de un móvil, por ejemplo. Además, un beneficio de estas baterías es que son recargables. 
<p align="center">
<img src="fotos_electronica/IMG_2476.jpeg" width="700" height="700" />
</p>


