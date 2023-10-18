<u>Sistema empotrado</u>: Dispositivo que incluye un computador programable pero que no es un computador de propósito general.

### Características de un SOE
- Cambio de contexto rápido
- Política de planificación es de tiempo real y el dispatcher forma parte del planificador
- Tamaño pequeño
- Respuesta a interrupciones externas rápidas
- Minimizar el intervalo de deshabilitación de interrupciones

### POSIX
##### Crear hebra
```C
#include <pthread.h>
int pthread_create(pthread_t *thread, const pthread_attr_t *attr, void *(*start_routine) (void*), void *arg); //Primer parametro es un id, el segundo los atributos (nosotros los dejaremos en null), el tercero contiene el nombre de la funcion que he implementado y hará de hebra.
//EJEMPLO
rc = pthread_create(&threads[t], NULL, PrintHello, & id[t]);

int pthread_attr_destroy(ptread_attr_t *attr);

int pthread_attr_init(pthread_attr_t * attr);
```
##### Sincronización
##### Manejo de evento
##### Mecanismos para sistemas de tiempo 
