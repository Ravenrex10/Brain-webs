1. Dado el siguiente conjunto de tareas:

![[Pasted image 20231115202459.png]]

a.- Realizando una asignación de prioridades óptima calcular los bloqueos siguiendo el protocolo de techo de prioridad.
<u>Prioridades:</u> -> Menor tiempo = Mayor prioridad
F -> 7
FT -> 6
D -> 5
A -> 4
E -> 3
C -> 2
B -> 1

<u>Techos de prioridad:</u> -> La mayor prioridad de entre las tareas que usan ese recurso.
R1: 6 
R2: 2
R3: 4
R4: 1

<u>Bloqueos:</u> Miramos todos los procesos con menor prioridad y miramos que recursos se usan en esos procesos  y sus techos. De los recursos que tienen un techo mayor o igual a la prioridad de la tarea X escogemos el recurso que tenga mayor tiempo. Su tiempo es el bloqueo de X. 
Bloqueo de B: 0
Bloqueo de C: 7 
Bloqueo de E: 7
Bloqueo de A: 7
Bloqueo de D: 2
Bloqueo de FT: 2
Bloqueo de F: 0

b.- Realizar el análisis de tiempo de respuesta en el caso peor con los bloques del apartado a.