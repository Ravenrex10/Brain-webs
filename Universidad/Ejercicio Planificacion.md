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

RA = 3 + 7 + IA
RB = 10 + 0 + IB
RC = 20 + 7 + IC
RD = 5 + 2 + ID
RE = 1 + 7 + IE
RFT = 1 + 2 + IF
RF = 2 + 0 + IG


# Examen 2018
![[Pasted image 20231116181600.png]]

<u>Prioridades</u>:
C -> 5
A -> 4
E -> 3
B -> 2
D -> 1

<u>Techos de prioridad</u>:
R1: 4
R2: 3
R3: 4
R4: 5
R5: 5

<u>Bloqueos</u>:
Bloqueo de D: 0
Bloqueo de B: 0.3
Bloqueo de E: 0.3
Bloqueo de A: 0.3
Bloqueo de C: 0.1

<u>Tiempos de respjuesta</u>:
RC = Cc + Ic + Bc + 2(cambio de contexto) + ...
RC = 4 + 0.1 + 2 * 0.1 + |Rc/TA| cola + |Rc/TB| cola + |Rc/TC| cola + |Rc/TD| cola + |Rc/Te| cola + |Rc/1| * 0.2
W0c = 4.3
W1c = 4.3 + |4.3/90| * 0.1 + |4.3/100| * 0.1 + |4.3/30| * 0.1 + |4.3/1000| * 0.1 + |4.3/150| * 0.1 +  |4.3/1| * 0.1
W2c = 6
W3c = 6 <= D = 30

Ra = Ca + Ba + 2Csw + ... + Ia
Ra = Ca + Ba + 2Csw + ... + |Ra/Tc| * (Cc + 2Csw)
Ra = 2 + 0.3 + 2 * 0.1 + ...
W0a = 2.5
W1a = 7.8
W2a = 8.8
W3a = 9
W4a = 9 < 70

Re = Ce + Be + Ie + 2Csw + Planif
Re = 12 + 0.3 + |Re/Tc|(Cc + 2Csw) + |Re/Ta|(Ca + 2Csw) + 