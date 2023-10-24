## Lógica Temporal Lineal
- o f -> Es cierto si f se cumple en el siguiente momento
- diamante f -> Es cierto si eventualmente se cumple f
- [] f -> Es cierto si f se cumple en todos los momentos a partir de ese momento
- f1 U f2 -> f1 se satisface si f2 se satisface en algún momento en el futuro y, hasta entonces, f1 se satisface en todos los estados intermedios.

## Estructuras de Kripke
Estructura de kripke = (A, ->a, L) donde:
- A es un conjunto de estados
- ->a es una relación de transición
- L:A ->P(AP) es una función de etiquetado, que asocia a cada estado a perteneciente a A el conjunto L(a) de proposiciones atómicas en AP que se satisfacen en a.

## Lectores y escritores
```c
mod READERS-WRITERS is 
	pr NAT .
	sort System .
	op <_,_> : Nat Nat -> System [ctor] . ---//Readers/Writers
	vars R W : Nat .
	rl < 0, 0 > => < 0, s(0) > .
	rl < R, s(W) > => < R, W > .
	rl < R, 0 > => < s(R), 0 > .
	rl < s(R), W > => < R, W > .	
	```

No es terminante y tiene infinitos estados alcanzables.

Para probarlo se le puede acotar la búsqueda escribiendo ``search [1, 1000000]`` por ejemplo.

### Abstracción
Podemos abstraer una parte del sistema para resumirlo.
Por ejemplo, da lo mismo tener 15 lectores que 16, por lo que puedo agrupar esos estados en un estado "tengo escritores" de la siguiente forma:
```c
< s N, 0 > = < N, 0 >
```

