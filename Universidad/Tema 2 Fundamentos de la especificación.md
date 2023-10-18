o l <u>Objetivo</u>: Repasar y entender qué es la lógica.

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

### Maude
Una implementación de la lógica de reescritura muy eficiente
- Sintaxis basada en ecuaciones y reglas de reescritura (estilo Haskell)
- Semántica basada en la lógica de reescritura

3 tipos de módulos:
- Módulos funcionales
- Módulos de sistema
- Módulos orientados a objetos

### Teorías ecuacionales
Las teorías ecuaciones en [[Lógica ecuacional]] se denominan teorías ecuacionales o especificaciones algebraicas. 
- Definen operaciones confluentes y terminantes.
- Se definen en módulos funcionales.
- E se compone de ecuaciones y axiomas algebraicos (Ax), de forma que normalmente escribimos
- Ax incluye los axiomas con los que el motor de reescritura es capaz de operar módulo, en el caso de Maude: *assoc, comm, id*
- Representan la parte estática del sistema
Una teoría ecuacional es un par ((sigma), E) donde:
- Sigma es la signatura, que describe la sintaxis de la teoría, es decir, los tipos de datos y los símbolos de operación (o de función) sobre ellos que define, y
- E es un conjunto de ecuaciones entre expresiones (denominados términos) en la sintaxis de sigma.


#### Teorías de reescritura
- Definen operaciones que pueden ser no concluyentes o no terminales
- Se definen en módulos de sistema
- Especifican la parte dinámica de los sistemas, es decir, las acciones que pueden producir transiciones o cambios.


# Signaturas
## Sin tipos
Tienen un único tipo, y símbolos de operación sobre él. Las operaciones indican el número de parámetros que toma
## De múltiples tipos
Permiten tener múltiples tipos y símbolos de operación
<u>Ejemplos:</u>
 -Integer
 -Bool
 -List
## De tipos ordenados
Signaturas de múltiples tipos que permiten relaciones de inclusión entre tipos
<u>Ejemplos:</u>
	-Natural < Integer < Rational

## De pertenencia
Permiten cambiar el tipo que tienen los términos
<u>Ejemplos:</u>
	-1 2 3 4 5: SortedList

<u>Ejercicios</u>:
- Ejemplo de una signatura sin sentido
sorts A, B, C, D:
	op f: A -> B       NO SE SI ESTA BIEN
- Ejemplo de una especificación que tenga sentido y que no sea pre-regular
sorts A B C D
subsorts A < BC < D
	op a: -> A
	op f: B -> B
	op f: C -> C
	
- Buscar en el manual de MAUDE como funciona el AND (parece esto: n), decir qué significa _ : _ y qué significa _ :=_
- Reescribir s0 + s(ss0 * s0), qué es el lr, r0, etc (no se, proceso de reescritura hasta que no se pueda reescribir más)

TE(X)s' = Álgebra de términos de la signatura x en algo de s


### La lógica de reescritura (LR)
Objetivo: Eliminar la simetría y con ella la interpretación ecuacional de las reglas
- Una signatura LR es una especificación ecuacional que hace explícito el conjunto de axiomas E para enfatizar el hecho de que la reescritura ocurrirá sobre clases de equivalencia módulo E.
#### Los conejitos saltarines
Podemos modelar el problema formalmente y hacer que Maude lo resuelva por nosotros

```C
//declaracion de variables
sorts Rabbit Board
subsort Rabbit < Board
ValidBoard < Board
op _ _ : Board Board -> Board [assoc]
ops x o f : -> Rabbit

//comprueba que una tabla sea valida
rmb B : ValidBoard
	if whites(B) = 3
	and blacks(B) = 3
	and frees(B) = 3

//operaciones para el movimiento
rl [xAdvances] : x free => free x
rl [xJumps] : x o free => free o x
rl [oAdvances] : free o => o free
rl [oJumps] : free x o => o x free

//constructor del tablero
protecting NAT
op initial : Nat -> Board
var N : Nat
eq initial(0) = free
eq initial(s N) = x initial(N) o

```


#### El juego de las jarras
```C
sort Basin .
op basin : Nat Nat -> Basin [ctor] .

sort BasinSet .
subsort Basin < BasinSet .
op _ _ : BasinSet BasinSet -> BasinSet [assoc comm] .
...
```
___ 
# Ejercicio
- comprobar que sea terminante el BOOLEAN de las diapositivas. Si es creciente, confluente, determinante, regular...

![[Pasted image 20231003161146.png]]

Terminante: 




___
# Palabras Clave
Signatura, pre-regular, con sentido, ambiguo, especificación, terminante, confluente, semántica laxa, semántica inicial

<u>Pre-Regular</u>: Cuando no hay duda del resultado, es decir, no haya "ambigüedad". En caso de ambigüedad el resultado será el tipo más pequeño. Es no pre-regular cuando los dos posibles resultados están al mismo nivel.

<u>Confluente</u>: Todo término t, si se puede reescribir de dos formas distintas, tarde o temprano llegamos al mismo sitio.
![[Pasted image 20230927162751.png]]

<u>Terminante</u>: Cuando no hay secuencia infinita de pasos de reescritura.

<u>Semántica inicial</u>: Nos permite construir otra álgebra.

<u>Semántica laxa</u>: Todas las álgebras que satisfacen todas las ecuaciones en E.