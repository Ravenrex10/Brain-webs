# Implementación software
### Emulación
El emulador simula la ejecución una a una las instrucciones de la CPU virtual -> Software

### Virtualización nativa
- Traducción binaria: Se analizan las instrucciones virtuales y se traducen a un código seguro para la CPU real sin instrucciones privilegiadas -> Hardware y software
- Trap & Emulate: Se deja ejecutar a la CPU real el código de la CPU virtual pero en modo no privilegiado -> Hardware
+Hardware = +Rendimiento

# Implementación hipervisor

(...)


# Virtualización de Discos

### Checkpoint
Contienen la:
- Configuración
- Imagen del disco (Snapshot)
- RAM (si está encendida la máquina)
- ROM (bios)
Se usa para preservar un estado de la máquina para poder volver atrás si fuera necesario.

Para ello se puede copiar todo el disco, pero es ineficiente.
Lo que haremos será guardar las diferencias. Tendremos una tabla de los bloques de memoria que han sido modificados con su contenido.

Al leer primero comprueba si el bloque se encuentra en la tabla diferencial, si no lo está se busca en el disco base.

#### Eliminar Snapshots
- Rollback -> Directamente borrarla.
- Commit -> Meter los cambios de la snapshot al disco base y luego borrar la snapshot.

Esto se hace porque es más rápido el acceso a memoria desde el disco base porque está indexado.
Si una snapshot tiene ramas y se ha convertido en un árbol tendremos conflictos al hacer commit de una hoja.

### Clones
Tipos:
- Full-clones: Copia todo
- Linked-clones: Estado almacenado con técnicas diferenciales. Se guardan solo los cambios.

# Virtualización de la red
Se crea una LAN virtual, hay varias formas:
- Host-only: Simula un switch virtual para conectar MVs. No hay salida al exterior.
- Bridged: Simula un bridge que conecta la LAN virtual con la LAN externa. Se pone la tarjeta red en modo promiscuo para poder enviar cualquier paquete. En tarjetas WiFi se llama modo monitor.
- NAT: Hay un router ficticio que aplica la traducción NAT a los paquetes de la máquina virtual y envía esos paquetes traducidos por la tarjeta red. Pero no me puede llegar cosas de fuera porque no se puede "destraducir".

