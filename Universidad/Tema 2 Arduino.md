[[Ejercicios Arduino]]
## Creación de bibliotecas
``` C
# ifndef Morse_h
# define Morse_h    //Evita incluirla dos veces

Morse::Morse(int pin)
{
	pinMode(pin, OUTPUT);
	_pin = pin;_
}

class Morse {
public:
	Morse(int pin);
	void dot();
	void dash();
private:
	int _pin;
};
#endif
```

### Incluir bibliotecas
```C
#include <Morse.h>
```


## Interrupciones
Para acceder al hardware. Lo hacemos a través del polling.
Se pueden definir interrupciones para:
- Temporizadores
- Hardware

Detectan:
- RISING
- FALLING
- CHANGING
- LOW

#### Variables globales en la ISR (servicio de interrupción) en Arduino
Deben ser declaradas *volatile* para que no se pierda actualizaciones de esa variable.


Durante la ejecución de la interrupción Arduino no actualiza el valor de la función millis(), por lo que debe ser lo más rápido posible.

#### Funciones

```C
attachInterrupt (digitalPinToInterrupt(pin), ISR, mode);
DetachInterrupt(interrupt); //Anula la interrupción
NoInterrupts(); //Desactiva las interrupciones
Interrupts(); //Reactiva las interrupciones
````


## Temporizadores
Para manejar funciones de tiempo, servos y generar señales periódicas.
Arduino tiene tres módulos times: *timer0, timer1, timer2*

- Timer0 altera micros(), millis(), delay()
- Timer-1 no pudo usar funciones de servos
- Timer-2 no puedo usar tone()

### Cómo usarlos
1. Deshabilitar interrupciones
2. Limpiar el contenido del registro que guarda la cuenta
3. Habilitar la interrupción por desbordamiento del Timer-2
4. Configurar la frecuencia a la que el timer comenzará a contar.
5. Habilitar interrupciones

# FreeRTOS
Sistema operativo para microcontroladores
En FreeRTOSConfig.h podemos cambiar algunas propiedades

### Gestión de Tareas
- Tiene un planificador apropiativo con round-robin.
- Funciona con un proceso formado por varias hebras ("Tasks")
- La prioridad va de 0 a configMaxPriorities -1. En arduino hay 4

Las tareas no deben hacer return y deben borrarse al terminar.
Ejemplo de una tarea:
```C
void ATaskFunction( void *pvParameters ) 
{ 
	int iVariableExample = 0;
	 for( ;; ){
	  }
	vTaskDelete( NULL );
}
```

#### Crear tarea
Hay que usar xTaskCreate para crear una tarea:
```C
xTaskCreate(vTask1, /* Pointer to the function that implements the task. */ "Task 1",/* Text name for the task. This is to facilitate debugging only. */ configMINIMAL_STACK_SIZE, /* Stack depth – MEDIDO en palabras. */ NULL, /* We are not using the task parameter. */ 1, /* This task will run at priority 1. */ NULL); /* We are not going to use the task handle. *
```

#### Retrasos
```C
void vTaskDelay(TickType_t xTicksToDelay );
```
podemos usar la función portTICK_PERIOD_MS para averiguar el tiempo real en ticks haciendo 250/portTICK_PERIOD_MS

Otra forma sería usar el siguiente:
```C
void vTaskDelayUntil(TickType_t *pxPreviousWakeTime, TickType_t xTimeIncrement );
```


#### Colas
Tiene colas que se les puede asignar prioridad

#### Variable compartida
Se puede crear un mutex. Para trabajar con ello también tenemos semáforos.

```C
SemaphoreHandle_t xSemaphoreCreateMutex( void );
```
