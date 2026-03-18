# Componentes del robot

| Componente |  Modelo |
| :--- | :---: |
| Servomotor| MG996R |
| Escudo | L298N |
| Sensores de ultrasonidos|  HC-SR04  |
| Placa | Arduino Uno |
| Motor | Modelo TT con reducción de velocidad 1:40. |
| Baterías | 2 x 18650 de 9900 mAh cada una |

## Servomotor
Basándonos en experiencias anteriores, directamente hemos optado por el servomotor MG996R ya que funciona controlando ángulos de giro en lugar de controlar la velocidad del propio servomotor. Esto facilita bastante todo ya que ahora podemos mover las ruedas delanteras con más precisión y requiriendo mucho menos esfuerzo. El modelo que elegimos fue el MG996R, como ya he dicho, ya que es conocido por ser más potente y por tener un buen rango de movimiento para este tipo de proyectos.

<p align="center">
<img src="fotos_electronica/IMG_1356.jpeg" width="700" height="700" />
</p>

## Escudo
El escudo que hemos utilizado ha sido el modelo L298N, y lo usamos principalmente para hacer las conexiones de los motores. Este escudo nos ha permitido controlar el movimiento de los motores de una forma más sencilla, ya que se encarga de enviar la energía necesaria para que funcionen correctamente. Además ya eramos conscientes de la incompatibilidad del escudo DRV8835 de Pololu con nuestros motores. Por lo tanto, seleccionamos directamente el modelo L298N.
<p align="center">
<img src="fotos_electronica/IMG_1355.jpeg" width="700" height="700" />
</p>

## Sensores de ultrasonidos 
Para la correcta programación de nuestro robot necesitábamos disponer de tres sensores ultrasónicos de distancia para conseguir que el robot no impactara ni tocara ninguna pared. Para la implementación de estos en el chasis utilizamos una estructura diseñada previamente en la interfaz de TinkerCad y la imprimimos en 3D. Esto nos permitió sujetar bien los tres sensores de ultrasonidos. De tal modo que nos aseguramos que los sensores se mantienen en su sitio sin caerse mientras hacíamos pruebas.

<p align="center">
<img src="fotos_electronica/IMG_1357.jpeg" width="700" height="700" />
</p>

## Placa 






