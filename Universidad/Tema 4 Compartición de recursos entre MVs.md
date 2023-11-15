# Indice
- Sobrecostes inherentes a la virtualización
- Influencia en el rendimiento de la compartición de recursos entra máquinas virtuales
- Paravirtualización y optimización
- Obtención de estadísticas
- Asignación de recursos
	-Estática
	-Dinámica

# Sobrecostes inherentes a la virtualización
### CPU
El problema son las instrucciones privilegiadas y E/S.
- Traducción binaria: 
	-Se traducen a un código seguro para la CPU real.
	-Incluye el código de emulación.
	-La traducción lleva tiempo extra.
- Trap & Emulate:
	-Se generan excepciones en la CPU real, que debe emular dichas operaciones.

Pérdida de eficiencia:
 ```
 Sv = fp x Ne + (1-fp)
 ```
fp = porcentaje de instrucciones privilegiadas
Ne = número medio de instrucciones que las reemplazan

### Excepciones
Invalidan todo el trabajo anticipado por el pipeline del procesador.

A mayor longitud del pipeline, mayor pérdida de rendimiento en cada excepción.

### Memoria
La virtualización requiere espacio físico de RAM y MMU del procesador.

### Discos duros
Dos formas de implementar:
- By pass: Directamente conectarlo a la máquina virtual.
- Ficheros: del sistema de archivos del hipervisor.
###### Físicos
- Menos retardo
- Uso: Aplicaciones críticas
###### Sobre ficheros
- Overhead por las estructuras de datos del sistema de ficheros
- Es posible no asignar el espacio libre del volumen. Ahorra espacio, pero puede provocar inanición por falta de disco real y fragmentación del fichero que simula el disco.

### Snapshots
Disminuyen la eficiencia del disco

### La red
Requiere simular
- Interfaces
- LANs virtuales
El paso de paquetes entre máquinas virtuales en el mismo switch virtual se hace mediante buffers de memoria del hipervisor.


# Eficiencia de la E/S
- Throughput: velocidad máxima de transferencia en butes/s.
- Latencia: Tiempo mínimo que tarda en transferirse el primer byte.
- tps: transacciones por segundo máximas (del mínimo tamaño).

tps = 1/(Linicial + Ttransferencia)
th = B * tps

La virtualización afecta al rendimiento:
- Aumenta la latencia
- Se puede reducir con el uso de buffering en el sistema real
- Respecto al throughput
		- Una buena simulación lo mantiene al 100% del original
		- Puede degradarse por las copias entre buffers reales y virtuales

Hay que intentar usar bloques grandes. Si no usar bloques pequeños con E/S asíncrona
¿Mejorar tps o throughput?
tps: muchos clientes con datos pequeños
througput: pocos clientes con datos grandes