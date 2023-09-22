# Introducción al Modelado Web
Especifica abstracciones sobre el mundo real
Facilita el desarrollo
##### Papel del modelo en el desarrollo
- borrador (comunicar ideas)
- guía (planos)
- programa (Model-Drive-Engineering)

#### Dimensiones del modelado web
- Fases: En las que se divide el proceso de desarrollo
- Niveles: Puntos de vista para estudiar el sistema
- Aspectos: Perspectivas de carácter estático y dinámico
- Adaptación: Considera el contexto del usuario

# Modelado Web con IFML
Interaction Flow Modeling Language
https://editor.ifmledit.org
#### Objetivos
Representación explícita del front-end:
- Con un único tipo de diagrama: [[Flujo de interacción]]
- Muestra diferentes aspectos
- Sin entrar en detalles técnicos de implementación
- Especificando composición, contenido, órdenes, acciones y efectos
![[Pasted image 20230919202434.png]]
![[Pasted image 20230919202610.png]]
# Arquitectura Web
Describe los componentes software, las relaciones entre ellos y sus propiedades. Ignora la implementación interna de los componentes.
### Patrones de Arquitectura
- Esquemas de organización general de un sistema
- Especifican una serie de subsistemas o componentes
- (...)
### Puntos de vista arquitectónicos
##### Arquitectura física o niveles (tiers)
- Elementos físicos (Hardware, software de terceros, otros elementos externos)
##### Arquitectura lógica o capas (layers)
- Componentes software

### Escalabilidad
Cómo afecta al rendimiento el incremento del uso y de los datos
Es importante:
- El correcto dimensionamiento de la aplicación
- La adaptabilidad del sistema
##### Tipos
- Escalabilidad vertical (añadir más potencia)
- Escalabilidad horizontal (crear clones, equilibrado hardware, equilibrado software)
# Modelado Arquitectónico en UML
### Diagrama de Componentes 
Un componente es una unidad de composición con todas sus interfaces y dependencias de contexto explícitamente definidas.
Propiedades:
- Unidades de software orientadas a ala composición
- Definen un serie de puertos
- Implementan y requieren interfaces
- Reutilizables a partir de su especificación
##### Puertos
Puntos de interacción entre un componente y su entorno
![[Pasted image 20230922184929.png]]
- Representan partes de la funcionalidad ofrecida o requerida
- Ocultan un mecanismo interno que ofrece o precisa la funcionalidad

##### Interfaces
Se utilizan en los diagramas de componentes
Evitan la dependencia entre componentes
Un componente presenta un conjunto de interfaces
![[Pasted image 20230922185046.png]]

##### Componentes VS Clases
<u>Semejanzas</u>:
- Ambos tienen nombre y definen una serie de propiedades
- Pueden realizar un conjunto de interfaces
- Pueden participar en relaciones e interacciones
<u>Diferencias</u>:
- Las clases representan abstracciones lógicas
- Los componentes representan el empaquetamiento físico de esos elementos lógicos
- Al implementar un componente se usarán varias clases
- Los componentes solo son accesibles a través de sus interfaces

##### Componentes
Pueden anidarse
La especificación de un componente indica:
- Puertos
- Interfaces ofrecidas y requeridas
- Realizaciones
- Artefactos
![[Pasted image 20230922185416.png]]
### Diagrama de Despliegue
##### Nodos
Modelan un recurso computacional del sistema en tiempo de ejecución
- Pueden ser hardware of software
- Se pueden estereotipar para representar dispositivos específicos
![[Pasted image 20230922185656.png]]

##### Aplicaciones Web
Muestran la topología de comunicación de un sistema distribuido
- Representan los nodos o dispositivos del sistema
- Las conexiones entre nodos
- La asignación de artefactos y componentes software
![[Pasted image 20230922185753.png]]