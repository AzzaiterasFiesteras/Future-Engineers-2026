
# Funciones del código 

| **Funciones** |  **Sintaxis** | **Uso explicado** | 
| :--- | :---: | ---:| 
| `setup()`|`void setup()`  |Se ejecuta una sola vez al encender la placa. Inicializa comunicación del puerto serie, configura pines, conecta el servo, inicia el sensor BNO055 y calibra el giroscopio| 
| `loop()`|`void loop()`  |Se ejecuta continuamente. Lee sensores ultrasónicos, detecta obstáculos, controla el movimiento, corrige dirección y cuenta los giros para completar las vueltas.| 
| `obtenerGrados()`|`float obtenerGrados() ` |Lee la orientación del sensor BNO055 y devuelve el ángulo en grados respecto al eje X `(orientation.x)`. Se usa para saber hacia dónde apunta el robot.| 
| `prepararSensor()`|`void prepararSensor() ` |Espera hasta que el giroscopio tenga máxima precisión `(gyro == 3)`. Después guarda el ángulo inicial como referencia en `anguloObjetivo.`| 
| `hacerGiro()`|`void hacerGiro(int grados) ` |Ajusta el objetivo angular y mueve el servo para girar el coche. El robot sigue girando hasta que el error sea menor a 5°.| 
| `terminarCarrera()`|`void terminarCarrera() ` |Hace que el coche avance un poco más para no seguir girando 8para que no llegue a chocarse con la pared interna) y luego apaga el motor.| 

## Funciones dentro del `void setup`

| **Funciones** | **Uso explicado** | 
| :--- | ---: |
| `Serial.begin(9600)`| Inicia comunicación del puerto serie. |
| `pinMode()`| Configura pines como entrada o salida |
| `cochino.attach(pinservo)`| Conecta el servo |
| `cochino.write(centroServo)`|`Coloca el servo centrado ` |
| `bno.begin()`|Inicializa el sensor BNO055 |
| `prepararSensor()`|Calibra el giroscopio |

## Funciones dentro del `void loop`

| **Funciones** | **Uso explicado** | 
| :--- | ---: |
| `Serial.begin(9600)`| Inicia comunicación del puerto serie. |
| `pinMode()`| Configura pines como entrada o salida |
| `cochino.attach(pinservo)`| Conecta el servo |
| `cochino.write(centroServo)`|`Coloca el servo centrado ` |
| `bno.begin()`|Inicializa el sensor BNO055 |
| `prepararSensor()`|Calibra el giroscopio |


## Funciones de librerías

| **Función** |**Librería** | **Uso explicado** | 
| :--- | :---: | ---:| 
| `Serial.begin()`|Arduino  |Comunicación con el puerto serie| 
| `Serial.print()`|Arduino  |Mostrar texto en el puerto serie.| 
| `Serial.println()`|Arduino |Mostrar texto con salto en el puerto serie.| 
| `pinMode()`| Arduino|Configura pines| 
| `digitalWrite()`|Arduino |Encender/apagar pin.| 
| `digitalRead()` |Arduino |Leer pin digital.| 
| `analogWrite()`|Arduino  |PWM para velocidad| 
| `delay()`|Arduino  |Pausa del programa.| 
| `abs()`|Arduino/C++ |Valor absoluto.| 
| `attach()` | Servo | Conectar servo|
| `write()`  | Servo | Mover servo |
| `begin()`| BNO055 | Iniciar sensor  |


# Explicación del programa
## Variables y librerías
```C++
#include <Wire.h>
#include <Adafruit_Sensor.h>
#include <Adafruit_BNO055.h>
#include <Servo.h>
#include <Ultrasonic.h>

int ENA = 5;
int IN1 = 6;
int IN2 = 7;

Servo cochino;
Adafruit_BNO055 bno = Adafruit_BNO055(55);

const int pinservo = 9;
const int pinPulsador=13;

float anguloObjetivo;  
int centroServo = 35;  // Posición recta
int sentido = 0;       // 1 para derecha, 2 para izquierda
int contadorGiros = 0; // Control de esquinas para las 3 vueltas
int contador1=0;
int contador2=0;
bool start = false; 
```
Antes de desarrollar la lógica de la programación, lo primero fue instalar las librerías tanto de los motores como del servomotor, de los sensores de ultrasonidos y del giroscopio para facilitar la programación mediante `#include <nombre de la librería>`Y además, nombrar el servo y el giroscopio. Los sensores de ultrasonidos los nombramos posteriormente. Y por último, antes de nombrar a los sensores, definimos todas las variables:
- `int ENA = 5`; `int IN1 = 6`; `int IN2 = 7`; establecemos los pines a los que van conectados los motores en el escudo L298N.
- `const int pinservo = 9;` establecemos el pin al que está conectado el servo. 
- `float anguloObjetivo:` que es el ángulo al que queremos ir.
- `int centroServo = 35; ` que es la posición del servomotor en la cual el sistema de dirección del robot está orientado para ir recto.
- `int sentido = 0; ` el robot identificará el sentido al que debe girar en el primer giro. Para esto era necesario crear una variable para la cual el valor 1 sea girar hacia la derecha y el valor 2 para la izquierda. Es por esto, que desde el principio del código establecemos que sea 0.
- `int contadorGiros = 0;` gracias a esta variable que cuenta giros, el robot es capaz de pararse al completar las 3 vueltas (12 giros en total).
- `contador1` y `contador2`:
- `bool start = false`: Este tipo de variable solo puede tener dos valores: true (verdadero) o false (falso). En este caso empieza en false, lo que significa que el sistema está apagado. Lo usaremos para iniciar el programa desde el pulsador.
  
```C++
#define TRIG_IZQ 8
#define ECHO_IZQ 10
Ultrasonic ultraIZQ(TRIG_IZQ, ECHO_IZQ, 60000);
#define TRIG_CENTRO 3
#define ECHO_CENTRO 4
Ultrasonic ultraCENTRO(TRIG_CENTRO, ECHO_CENTRO, 60000);
#define TRIG_DERECH 11
#define ECHO_DERECH 12
Ultrasonic ultraDERECH(TRIG_DERECH, ECHO_DERECH, 60000);
```

Como ya sabemos, los sensores de ultrasonidos están compuestos por un `trigger` (que emite una señal) y un `echo` (que recibe esa señal). Según el tiempo que tarda en rebotar esa señal podemos calcular la distancia. Para esto, tuvimos que indicar en la programación los pines a los que estaban conectados cada trigger y cada echo de cada sensor, de tal manera que:
- **Trigger** (pin 8) y **echo** (pin 10) = sensor ultrasonidos izquierda
- **Trigger** (pin 3) y **echo** (pin 4) = sensor ultrasonidos centro
- **Trigger** (pin 11) y **echo** (pin 12) = sensor ultrasonidos derecha
  
## Void setup

```C++
void setup() {
  Serial.begin(9600);
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(ENA, OUTPUT);
  pinMode(pinPulsador, INPUT_PULLUP);

  cochino.attach(pinservo);
  cochino.write(centroServo);
  
  Serial.println("Hola, iniciando sistema...");

  if (!bno.begin()) {
    Serial.println("No se encuentra el sensor BNO");
    while (1); // Bloqueo si no hay sensor
  }
  prepararSensor(); 
  
}
```
El` void setup` es una función que se crea al principio del programa y sólo se ejecuta una única vez al comienzo del programa. Su propósito principal es iniciar todos los componentes que se necesitan para comenzar a funcionar correctamente. En nuestro caso, activamos el puerto serie para poder calibrar las lecturas de los sensores de ultrasonido, y configuramos el pin del servomotor para que pueda empezar a funcionar desde el inicio. Además iniciamos los motores y el pulsador. A parte, añadimos un condicional para que en el caso de que no se detecte el giroscopio que lo imprima en el puerto serie y también bloquee el sistema. Además, llamamos a la función que calibra el giroscopio para que el robot sepa dónde está el "norte".  

## Void loop

```C++
  if (digitalRead(pinPulsador) == LOW) {
    start = true;
    Serial.print(2);
  }
  if (start == true) {
  // Lógica de fin de carrera: tras 12 giros (3 vueltas), el robot para
    if (contadorGiros >= 12) {
      terminarCarrera();
      while(1); 
    }
```
En la primera parte del void loop hemos establecido la programación del pulsador de tal manera que al pulsarlo empiece todo el programa y además, imprima en el puerto serie el número 2 para comprobar que el pulsador está funcionando. Además, añadimos la lógica del final: tras 12 giros, es decir, tres vueltas el robot se detiene. 
