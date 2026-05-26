# Explicación del programa





# Funciones del código 

| Funciones |  Sintaxis  | Uso explicado | 
| :--- | :---: | ---:| 
| `setup()`|`void setup()`  |Se ejecuta una sola vez al encender la placa. Inicializa comunicación serial, configura pines, conecta el servo, inicia el sensor BNO055 y calibra el giroscopio| 
| `loop()`|`void loop()`  |Se ejecuta continuamente. Lee sensores ultrasónicos, detecta obstáculos, controla el movimiento, corrige dirección y cuenta los giros para completar las vueltas.| 
