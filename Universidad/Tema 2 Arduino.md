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
