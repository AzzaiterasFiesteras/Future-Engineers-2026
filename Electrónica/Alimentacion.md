# Alimentación del robot

## Conexionado 
Para el conexionado de todos los componentes hemos necesitado tanto la placa de control Arduino, como una protoboard y un escudo. La placa junto a la protoboard han servido para la conexión de todos los compenentes menos los motores, los cuales hemos conectado al escudo.

### Conexionado del Escudo L298N
Lo primero fue conectar el motor al escudo. La alimentación, la consigue mediante los OUT1 y OUT2. Y para el control y la posterior programación de este; necesitamos establecer el pin IN1, IN2, y ENA. Los cuales controlan la dirección a la que gira el motor (para alante o para atrás) y la velocidad. En nuestro caso, así hemos establecido estos pines:
1. ENA: pin 5
2. IN1: pin 6
3. IN2: pin 7
   
### Conexionado de los sensores de ultrasonidos
Para el correcto funcionamento de nuestro robot, necesitábamos al menos 3 sensores de ultrasonidos que midieran las distancias entre las paredes. Estos sensores tienen 4 pines a los que conectarse. Uno de 5V y otro de GND los cuales le proporcionan la energía que necesita para funcionar. Y después, tiene otros dos pines más de control, el TRIGGER y el ECHO; que uno emite la señal y el otro la recibe. Así es cómo lo hemos conectado:
1. VCC: 5V
2. TRIGGER: pin 2
3. ECHO: pin 1
4. GND: GND

### Conexionado del servomotor

