# **PRÁCTICA 4 Secuencia de Leds con sensor**

## Para está práctica se utilizó 

* Módulo ESP32
* sensor Ultrasónico de distancia 
* 4 Led
* 4 Resistencias 

## Para la simulación nos dirigimos a la página  

woki : https://wokwi.com

#### Dashboard de página a utilizar 
![](https://github.com/AxelMld/Practica-3-Sensor-Ultrasonico-/blob/main/dash.png?raw=true)

## Pasos a Seguir 

1. Seleccionar el módulo ESP32 
2. Escoger los dispositivos a utilizar (Leds y resistencias )
3. Realizar las conexiones como se muestra en el apartado "conexión"




## Conexión 

![](https://github.com/AxelMld/Practica4/blob/main/Conexion.png?raw=true)


## Código utilizado 


```

// defines pins numbers
const int trigPin = 27;
const int echoPin = 26;
const int led1 = 23;
const int led2 = 22;
const int led3 = 21;
const int led4 = 19;


// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=3 && safetyDistance<=100)
{
  digitalWrite(led1, 1);
  digitalWrite(led2, 0);
  digitalWrite(led3, 0);
  digitalWrite(led4, 0);
 
}
else if(safetyDistance>=100 && safetyDistance<=200 ) 
{
   digitalWrite(led1, 1);
  digitalWrite(led2, 1);
  digitalWrite(led3, 0);
  digitalWrite(led4, 0);
}

else if(safetyDistance>=200 && safetyDistance<=300 ) 
{
   digitalWrite(led1, 1);
  digitalWrite(led2, 1);
  digitalWrite(led3, 1);
  digitalWrite(led4, 0);
}
else if(safetyDistance>=300 ) 
{
  digitalWrite(led1, 1);
  digitalWrite(led2, 1);
  digitalWrite(led3, 1);
  digitalWrite(led4, 1);
}

else 
{
  digitalWrite(led1, 0);
  digitalWrite(led2, 0);
  digitalWrite(led3, 0);
  digitalWrite(led4, 0);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
}

```


# Resultados

## 1. Resultado con un rango de distancia de 3 a 100 

![](https://github.com/AxelMld/Practica4/blob/main/resultado%201.png?raw=true)

## 2. Resultado con un rango de distancia de 100 a 200 

![](https://github.com/AxelMld/Practica4/blob/main/resultado%202.png?raw=true)

## 3. Resultado con un rango de distancia de 200 a 300 

![](https://github.com/AxelMld/Practica4/blob/main/resultado%203.png?raw=true)

## 4. Resultado con un rango de distancia mayor a 300 

![](https://github.com/AxelMld/Practica4/blob/main/resultado%204.png?raw=true)


## 4. Resultado con un rango de distancia mayor  a 400 o menor a 3 

![](https://github.com/AxelMld/Practica4/blob/main/resultado%205.png?raw=true)


# Creditos 

**Axel Miranda.**

