# Explicación del programa





# Funciones del código 

| Funciones |  Sintaxis  | Uso explicado | 
| :--- | :---: | ---:| 
| `setup()`|`void setup()`  |Se ejecuta una sola vez al encender la placa. Inicializa comunicación serial, configura pines, conecta el servo, inicia el sensor BNO055 y calibra el giroscopio| 
| `loop()`|`void loop()`  |Se ejecuta continuamente. Lee sensores ultrasónicos, detecta obstáculos, controla el movimiento, corrige dirección y cuenta los giros para completar las vueltas.| 
| `obtenerGrados()`|`float obtenerGrados() ` |Lee la orientación del sensor BNO055 y devuelve el ángulo en grados respecto al eje X `(orientation.x)`. Se usa para saber hacia dónde apunta el robot.| 
| `prepararSensor()`|`void prepararSensor() ` |Espera hasta que el giroscopio tenga máxima precisión `(gyro == 3)`. Después guarda el ángulo inicial como referencia en `anguloObjetivo.`| 
| `hacerGiro()`|`void hacerGiro(int grados) ` |Ajusta el objetivo angular y mueve el servo para girar el coche. El robot sigue girando hasta que el error sea menor a 5°.| 
| `terminarCarrera()`|`void terminarCarrera() ` |Hace que el coche avance un poco más para no seguir girando 8para que no llegue a chocarse con la pared interna) y luego apaga el motor.| 
## Funciones dentro del `void setup`
| Funciones |  Sintaxis  | Uso explicado | 
| :--- | :---: | ---:| 
| `setup()`|`void setup()`  |Se ejecuta una sola vez al encender la placa. Inicializa comunicación serial, configura pines, conecta el servo, inicia el sensor BNO055 y calibra el giroscopio| 
| `loop()`|`void loop()`  |Se ejecuta continuamente. Lee sensores ultrasónicos, detecta obstáculos, controla el movimiento, corrige dirección y cuenta los giros para completar las vueltas.| 
| `obtenerGrados()`|`float obtenerGrados() ` |Lee la orientación del sensor BNO055 y devuelve el ángulo en grados respecto al eje X `(orientation.x)`. Se usa para saber hacia dónde apunta el robot.| 
| `prepararSensor()`|`void prepararSensor() ` |Espera hasta que el giroscopio tenga máxima precisión `(gyro == 3)`. Después guarda el ángulo inicial como referencia en `anguloObjetivo.`| 
| `hacerGiro()`|`void hacerGiro(int grados) ` |Ajusta el objetivo angular y mueve el servo para girar el coche. El robot sigue girando hasta que el error sea menor a 5°.| 
| `terminarCarrera()`|`void terminarCarrera() ` |Hace que el coche avance un poco más para no seguir girando 8para que no llegue a chocarse con la pared interna) y luego apaga el motor.| 
