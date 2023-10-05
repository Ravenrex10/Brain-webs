# Implementación software
### Emulación
El emulador simula la ejecución una a una las instrucciones de la CPU virtual -> Software

### Virtualización nativa
- Traducción binaria: Se analizan las instrucciones virtuales y se traducen a un código seguro para la CPU real sin instrucciones privilegiadas -> Hardware y software
- Trap & Emulate: Se deja ejecutar a la CPU real el código de la CPU virtual pero en modo no privilegiado -> Hardware
+Hardware = +Rendimiento

# Implementación hipervisor

(...)