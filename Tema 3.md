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
