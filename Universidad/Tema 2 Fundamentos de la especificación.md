<u>Objetivo</u>: Repasar y entender qué es la lógica.

# Lenguajes y Lógica
### Ventaja de los lenguajes declarativos
- Basados en lógica computacionalmente interpretable.
- Un programa declarativo basado en una lógica determinada es típicamente una teoría  lógica en dicha lógica.
- Las propiedades que queremos verificar sobre un programa declarativo pueden ser especificadas por otra teoría Q.
- La relación de satisfacción P |= Q establece que la propiedad Q es satisfecha por el programa P, y que los modelos de P son también modelos de Q.

### La verificación de lenguajes imperativos (C, C++, Java...)
- Primero debemos definir la semántica matemática.
- Si queremos automatizar la verificación debemos definir la semántica como una teoría lógica TL en una lógica.

### Lógicas para aplicaciones software
Restricciones de la lógica
- [[Lógica ecuacional]]
Extensiones de la lógica
- Lógica difusa
- Lógica lineal
- Lógicas modales

### Lógica de reescritura (RWL)
-  Lógica del cambio que permite especificar la dinámica de sistemas
- Integración de distintas características: 
	– Funciones y tipos 
	– Indeterminismo 
	– Concurrencia 
	– Reflexión 
	– Genericidad 
	– ... 
- Marco unificado en el que se pueden definir distintas lógicas: 
	– Lógica ecuacional 
	– Lógica clausal 
	– Lógica lineal 
	– … 
-  Existe una lógica temporal, asociada a la RWL, que es estrictamente más potente que CTL/LTL: la temporal logic of rewriting (TLR)

# Maude
Una implementación de la lógica de reescritura muy eficiente
- Sintaxis basada en ecuaciones y reglas de reescritura (estilo Haskell)
- Semántica basada en la lógica de reescritura

#### 3 tipos de módulos:
- Módulos funcionales
- Módulos de sistema
- Módulos orientados a objetos

