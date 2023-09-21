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

