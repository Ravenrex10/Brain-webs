### Ejercicio 3
```C
int tiempoAnterior;
int tiempo;
bool encendido;
void setup()
{
  pinMode(2, OUTPUT);
  tiempoAnterior = 0;
  Serial.begin(10);
  encendido = false;
}

void loop()
{
  if (encendido){
  	digitalWrite(2, HIGH);
  }else{
    digitalWrite(2, LOW);
  }
  if (millis() - tiempoAnterior>=500){
    encendido = !encendido;
    tiempoAnterior += 500;
  }
}
```
![[Pasted image 20230921174337.png]]

