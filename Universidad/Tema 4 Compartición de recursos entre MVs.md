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
##### Físicos
- Menos retardo
- Uso: Aplicaciones críticas
##### Sobre ficheros
- Overhead por las estructuras de datos del sistema de ficheros
- Es posible no asignar el espacio libre del volumen. Ahorra espacio, pero puede provocar inanición por falta de disco real y fragmentación del fichero que simula el disco.