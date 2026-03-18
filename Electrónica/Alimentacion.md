# Alimentación del robot

## Conexionado 
Para el conexionado de todos los componentes hemos necesitado tanto la placa de control Arduino, como una protoboard y un escudo. La placa junto a la protoboard han servido para la conexión de todos los compenentes menos los motores, los cuales hemos conectado al escudo.

### Conexionado del Escudo L298N
Lo primero fue conectar el motor al escudo. La alimentación, la consigue mediante los OUT1 y OUT2. Y para el control y la posterior programación de este; necesitamos establecer el pin IN1, IN2, y ENA. Los cuales controlan la dirección a la que gira el motor (para alante o para atrás) y la velocidad. En nuestro caso, así hemos establecido estos pines:
1. ENA: pin 5
2. IN1: pin 6
3. IN2: pin 7
<p align="center">
<img src="fotos_electronica/IMG_1350.jpeg" width="800" height="800" />
</p>
   
### Conexionado de los sensores de ultrasonidos
Para el correcto funcionamento de nuestro robot, necesitábamos al menos 3 sensores de ultrasonidos que midieran las distancias entre las paredes. Estos sensores tienen 4 pines a los que conectarse. Uno de 5V y otro de GND los cuales le proporcionan la energía que necesita para funcionar. Y después, tiene otros dos pines más de control, el TRIGGER y el ECHO; que uno emite la señal y el otro la recibe. Así es cómo lo hemos conectado:
- Ultrasonidos de la izquierda
1. VCC: 5V
2. TRIGGER: pin 2
3. ECHO: pin 1
4. GND: GND
- Ultrasonidos del centro
1. VCC: 5V
2. TRIGGER: pin 3
3. ECHO: pin 4
4. GND: GND
- Ultrasonidos de la derecha
1. VCC: 5V
2. TRIGGER: pin 11
3. ECHO: pin 12
4. GND: GND
   
<p align="center">
<img src="fotos_electronica/IMG_1351.jpeg" width="800" height="800" />
</p>

### Conexionado del servomotor
Para los giros era necesario incorporar un mecanismo de dirección delantero. Para eso utilizamos un servomotor, el cual conectamos a 5V, a GND y al pin 9.


