
# --- English ---
## InmuneGo-IsingModel
A simulation that utilizes Ising modelling to study the dynamics of the inmune system response to cancer metastasis

Cancer metastasis, the spread of cancer cells from one part of the body to another, is a complex process that involves interactions between cancer cells and the immune system. ImmuneGO simulates this process by representing cancer cells and the response of the inmune system as stones on a GO board and modeling their interactions using Ising modeling principles. On the other hand, changing the parameters could be useful to analyse the response of the inmune system to another type of diseases or illnesses. This is a proyect that I did in July 2021 for a course of Modelling of Processes and Properties, based on two publications of Matias Alvarado [1][2].

The project is completely in Spanish, but about to coming out in English. 

Lastest changes: 07th July 2021


# --- Español ---
## InmuneGo-IsingModel
últimos cambios: 07 Julio 2021

Este projecto es una simulación para estudiar el dinamismo de la respuesta del sistema inmune a la metástasis, mediante modelo de Ising.

La metastasis, la dispersión de células cansesoras de una parte del cuerpo a otra, es un proceso complejo que involucra interacciones entre estas células y el sistema inmune. InmuneGO simula este proceso mediante la representación de las distintas células como fichas en un tablero del juego de mesa GO y modela las interacciones con los principios del modelo de Ising. Por otro lado, cambiando los parámetros elegidos, podría ser útil para analizar la respuesta del sistema inmune para con otro tipo de enfermedades. Este projecto lo realicé durante Julio 2021 como parte del curso de Modelado de Procesos y Propiedades, basado en dos publicaciones de Matias Alvarado [1][2]. 

### ¿Qué es el Go?

El Go es un juego de mesa por turnos, de estrategia, originario de China, datando de hace más de 4000 años. Basicamente, en un tablero de 19 x 19 (Figura 1), cada jugador (siendo blanco o negro), coloca una pieza por turno, en las intersecciones de las líneas, tratando de ocupar todas las libertades del contrincante (Figura 2) para “capturar” y quitar poder al mismo.

<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main//images/Fig1-TableroTipico.png?raw=true" height="300" width="400" alt="Tablero típico del juego Go de 19 x 19"/>  
</p>
<p align="center">Figura 1. Tablero típico del juego Go de 19 x 19. </p>

<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/images/Fig2-Libertades.png?raw=true" alt="Libertades de una pieza, siendo las libertades de una pieza negra los números 1, 2, 3 y 4."/>  
</p>
<p align="center">Figura 2. Libertades de una pieza, siendo las libertades de una pieza negra los números 1, 2, 3 y 4. </p>

### ¿Por qué la metáfora?

Dadas las diferentes tácticas que se pueden emplear y la cantidad enorme de variantes que se obtiene de una partida de Go, se puede considerar semejante y modelizar la competencia que existe entre el sistema inmune y el cáncer, donde ambos intentan rodear las células o moléculas enemigas, para destruirlas. Esto puede verse en la figura 3, donde se muestra cómo se pasa de un tablero de Go, a un grafo del modelo de Ising y finalmente a la competencia real que existen entre el cáncer y el sistema inmune.

![Análisis del juego Go como competencia entre el sistema inmune y el cáncer.](https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/blob/main/images/Fig3-Analisis.png?raw=true)
Figura 3. Análisis del juego Go como competencia entre el sistema inmune y el cáncer.



### Modelo matemático

Como modelo matemático, los papers consultados utilizan las siguientes ecuaciones:


***
#### Ecuaciones consideradas
***
<p style="text-align:center;"><img src="https://latex.codecogs.com/png.image?\inline&space;\dpi{110}\bg{white}H=-\frac{1}{2}\sum\limits&space;_{i,j}^{n}w_{i,j}x_i&space;x_j-\sum\limits&space;_{i}^{n}h_{i}|x_{i}|" title="H=-\frac{1}{2}\sum\limits _{i,j}^{n}w_{i,j}x_i x_j-\sum\limits _{i}^{n}h_{i}|x_{i}|" /></p>


<p style="text-align:center;"><img src="https://latex.codecogs.com/png.image?\inline&space;\dpi{110}\bg{white}x_i=c_i(n_i&plus;r_{0}^{k_i})" title="x_i=c_i(n_i+r_{0}^{k_i})" /></p>

<p style="text-align:center;"><img src="https://latex.codecogs.com/png.image?\inline&space;\dpi{110}\bg{white}w_{i,j}=\sum\limits&space;_{k}^{m}r_{t}x_{t}^{ij}" title="w_{i,j}=\sum\limits _{k}^{m}r_{t}x_{t}^{ij}" /></p>


$H$ : Hamiltoniano de Ising para ferromagnetismo en el cual se incluyen parámetros bioquimicos y biofísicos.<br>
&emsp;$x_i$ : Descripción de la molécula.<br>
&emsp;$c_i$ : Tipo de molécula. <br>&emsp;&emsp;Si $c_i = 1$ es una molécula del sistema inmune.<br> &emsp;&emsp;Si $c_i = -1$ es una molécula cancerosa. <br>
&emsp;$n_i$ : Cantidad de celulas que tiene la molécula.<br>
&emsp;$r_0$ : Rate of TGF beta <br>
&emsp;$k_i$ : El ratio de crecimiento de la molécula <br>
&emsp;$w_{i,j}$ : Energía de intercambio entre $x_i$ y $x_j$<br>
&emsp;&emsp;$r_t$ : El coeficiente de peso según la fuerza de la táctica empleada <br>
***

Dada la complejidad que presentaba el problema, y el poco tiempo disponible para realizar el trabajo, se optó por no tomar las posiciones de las células en la molécula como tácticas y sólo contar la cantidad de células por moléculas, mediante el siguiente modelo:

#### Formato final de las Ecuaciones utilizadas
***
<p style="text-align:center;"><img src="https://latex.codecogs.com/png.image?\inline&space;\dpi{110}\bg{white}H=-\frac{1}{2}\sum\limits&space;_{i,j}^{n}w_{i,j}x_i&space;x_j" title="H=-\frac{1}{2}\sum\limits _{i,j}^{n}w_{i,j}x_i x_j" /></p>

<p style="text-align:center;"><img src="https://latex.codecogs.com/png.image?\inline&space;\dpi{110}\bg{white}x_i=c_i" title="x_i=c_i" /></p>

<p style="text-align:center;"><img src="https://latex.codecogs.com/png.image?\inline&space;\dpi{110}\bg{white}w_{i,j}=\sum\limits&space;_{k}^{m}r_{t}x_{s}^{ij}" title="w_{i,j}=\sum\limits _{k}^{m}r_{t}x_{s}^{ij}" /></p>
***


<details>
    <summary> <h3>Reglas básicas Go y sus analogías</h3a></summary>

    Típico tablero de Go de tamaño 9x9, donde con "x" se representan las piezas negras, "o" las blancas y "·" los espacios vacíos.

                              · · o x o x x x o
                              x o o x o · x · o
                              x x . x o o o o o
                              x x x x x x x x x
                              x x o o o o o o o
                              x o · · · · · · ·
                              x o · o · · · o ·
                              x o · · · · · · ·
                              x o · · · · · · ·

    Las libertades de una pieza (stone), son los espacios a izquierda, derecha, arriba y abajo (representado con &). Se considera que las diagonales no cuentan. Una stone que se le ocupan sus 4 libertades, es capturada y es punto para el oponente

                              · · · · · · · · ·
                              · · · · · · & · ·
                              · · · · · & o & ·
                              · · · & · · & · ·
                              · · & x & · · · ·
                              · · · & · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
    
    Las diferentes tácticas que se pueden realizar durante una partida

    1. __*Invasión*__/__*Invasion*__: células anormales aparecen en un tejido y se implantan.

                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · x o · · · ·
                              · · · · x · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·

    2. __*Reducción*__/__*Reduction*__: Células del sistema inmune, quimio- o radio-terapia intentan desactivar o destruir las células cancerosas en las cercanías.

                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · x o · · · ·
                              · · · o · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·     
                              
    3. __*Eye de piezas negras*__/__*Eye from black stones*__: aparecen microtumores en los tejidos.
    Un Eye corresponde a una libertad compartida por 4 stones del mismo color. Está prohibido colocar una stone del color contrario en un eye, ya que sería un suicidio.

                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · x · · · · ·
                              · · x · x · · · ·
                              · · · x · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·                           

    4. __*Eye de piezas blancas*__/__*Eye from white stones*__: barreras supresoras de tumores (equivalente a anticuerpos) aparecen en el tejido.

                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · o · · · · ·
                              · · o · o · · · ·
                              · · · o · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·

    5. __*Escalera de piezas negras*__/__*Ladder from black stones*__: células cancerosas rodean una vecindad de células del sistema inmune. Una escalera, es cuando uno de los colores intenta escapar de la inminente captura y el color contrario comienza una escalera para capturarlo, de esta manera, se continua hasta que el color que queria escapar queda en atari y finalmente es capturado. Este color puede darse cuenta de esto, y cortar la escalera, para evitar perder territorio.

                              · · · · · · · · ·
                              · · · · · · · · ·
                              · o x · · · · · ·
                              x o o x · · · · ·
                              · x o o x · · · ·
                              · · x x · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
    
    6. __*Escalera de piezas blancas*__/__*Ladder from white stones*__: células del sistema inmune rodean un grupo de células cancerosas.


                             · · · · · · · · ·
                             · · · · · · · · ·
                             · x o · · · · · ·
                             o x x o · · · · ·
                             · o x x o · · · ·
                             · · o o · · · · ·
                             · · · · · · · · ·
                             · · · · · · · · ·
                             · · · · · · · · ·

    7. __*Red*__/__*Net*__: una vecindad (blanca o negra) rodeada por células contrarias, en una forma más desordenada. Teniendo la figura, si __blancas__ juega en c o b, __negras__ captura con d o f según el caso.

                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · o x x · · ·
                              · · o x o b f · ·
                              · · x x c x · · ·
                              · · · · d · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·

    8. __*Conección*__/__*Connection*__: entre grupos de células.

                              · · · · · · · · ·
                              · · · · · · · · ·
                              · x o · · · · · ·
                              o x x o · · · · ·
                              · o x x o · · · ·
                              · · o o · · · · ·
                              · · · · · · x x ·
                              · · · · · · · · ·
                              · · · · · · x x ·

    9. __*Atari*__: un grupo de células cancerígenas rodeadas adyacentemente por un grupo de células sanas. Cuando una stone tiene sólo una libertad disponible. Debajo se muestran varios ejemplos donde las piezas blancas tienen sólo una libertad. En el caso que se ve debajo a la izquierda, las negras estan en atari y si blanco toma posición en **, ambas negras son capturadas

                              · · o x · · · x o
                              · · x · · · · · ·
                              · · · · · · · · ·
                              · · · x · · · · ·
                              · · x O X · · · ·
                              · · · · · · · · ·
                              · · · · · · · · ·
                              o o · · · · · · ·
                              x x * · · · · · ·
                    
    10. *Ko*: fuerza equilibrio en una región del tejido. El ko ocurre cuando los colores pueden capturar una pieza enemiga, en un loop infinito. Se pone como regla que si un jugador captura el ko, el oponente no puede capturar el  ko que se generó a menos que coloque una pieza en otro lugar.

                              
                              · · · x o · · · ·   · · · x o · · · ·
                              · · x b x o · · ·   · · x o f o · · ·
                              · · · x o · · · ·   · · · x o · · · ·

</details>

### Simulaciones realizadas

Para comprobar el funcionamiento de la modelización, se realizaron los siguientes casos de estudio:

* Caso A
    * Tablero inicial vacío
    * Fuerza del Cáncer en "Medium"
    * Fuerza del Sistema Inmune "Medium"

* Caso B
    * Tablero inicial vacío
    * Fuerza del Cáncer "Weak"
    * Fuerza del Sistema Inmune "Strong"

* Caso C
    * Tablero inicial vacío
    * Fuerza del Cáncer "Strong"
    * Fuerza del Sistema Inmune "Weak"

* Caso D
    * Tablero inicial con cúmulo de células cancerosas
    * Fuerza del Cáncer "Medium"
    * Fuerza del Sistema Inmune "Medium”

* Caso E
    * Tablero inicial con cúmulo de células Inmunes
    * Fuerza del Cáncer "Medium"
    * Fuerza del Sistema Inmune "Medium"

En el gráfico 1, se puede ver cómo en el caso A, las energías acumuladas para ambos sistemas es equivalente a lo largo de los diferentes turnos, llegando a un valor cercano a 6 de Energía de Ising.
<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/images/Gra1-CasoA.png?raw=true" height="300" width="400" alt="Caso A - Variación de la energía de Sistemas Canceroso e Inmune"/>  
</p>
<p align="center">Gráfico 1. Caso A - Variación de la energía de Sistemas Canceroso e Inmune</p>

Luego, realizando la comparación entre los casos B y C, se puede ver en el gráfico 2 y 3, respectivamente, que las configuraciones que poseen mayor fuerza adquieren al final de la simulación mayor energía. Debe tenerse en cuenta que no poseen igual cantidad de turnos o pasos, debido a las condiciones de corte que posee el programa (Cuando no se coloca una pieza se considera un pase, y si ocurren dos pases seguidos se termina el juego).

<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/images/Gra2-CasoB.png?raw=true" height="300" width="400" alt="Caso B - Variación de la energía de Sistemas Canceroso e Inmune"/>  
</p>
<p align="center">Gráfico 2. Caso B - Variación de la energía de Sistemas Canceroso e Inmune</p>

<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/images/Gra3-CasoC.png?raw=true" height="300" width="400" alt="Caso C - Variación de la energía de Sistemas Canceroso e Inmune"/>  
</p>
<p align="center">Gráfico 3. Caso C - Variación de la energía de Sistemas Canceroso e Inmune</p>


Para los casos D y E, se colocó un cúmulo de células en el mismo lugar para ambos casos y se muestra cómo quedó el tablero antes y después de la corrida de simulación en las figuras 4 y 5, respectivamente. Por otro lado, se observa en los gráficos 4 y 5, que posee mayor energía aquel sistema que inició con un cúmulo de células de su tipo. Además, se debe tener en cuenta que durante el programa, no se tuvo en cuenta la energía inicial, dado que sólo se había considerado tablero inicial vacío, esto generó que al momento de evaluar los casos D y E, falte la energía inicial debida a la existencia inicial del cúmulo.

<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/images/Fig4-TableroCasoD.png?raw=true"  alt="Tablero caso D. Izquierda: Tablero con cúmulo inicial. Derecha: Tablero final luego de la corrida."/>  
</p>
<p align="center">Figura 4. Tablero caso D. Izquierda: Tablero con cúmulo inicial. Derecha: Tablero final luego de la corrida.</p>


<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/images/Fig5-TableroCasoE.png?raw=true"  alt="Figura 5. Tablero caso E. Izquierda: Tablero con cúmulo inicial.Derecha: Tablero final luego de la corrida."/>  
</p>
<p align="center">Figura 5. Tablero caso E. Izquierda: Tablero con cúmulo inicial.Derecha: Tablero final luego de la corrida.</p>


<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/images/Gra4-TablerCasoD.png?raw=true"  alt="Gráfico 4. Caso D - Variación de la energía de Sistemas Canceroso e Inmune"/>  
</p>
<p align="center">Gráfico 4. Caso D - Variación de la energía de Sistemas Canceroso e Inmune</p>


<p align="center">
    <img src="https://github.com/camichaubell/InmuneGo-IsingModel/blob/main/images/Gra5-TableroCasoE.png?raw=true"  alt="Gráfico 5. Caso E - Variación de la energía de Sistemas Canceroso e Inmune"/>  
</p>
<p align="center">Gráfico 5. Caso E - Variación de la energía de Sistemas Canceroso e Inmune</p>


### Conclusiones

Como comentarios se puede decir que se debería aumentar la complejidad del problema añadiendo tácticas, como existen en el Go, considerando sus posiciones además de la cantidad y, por otro lado, situaciones donde se quiten las células del tablero debido a que son capturadas, considerando el cambio de energía que esto genera. Además, debería correrse la simulación cientos de veces más para cada uno de los casos, para observar la tendencia que se tiene y si existe gran cantidad de casos en los que no cumple.

Por otro lado, la mayor dificultad estuvo en la lógica de conocer quiénes eran los vecinos y a qué grupo de moléculas pertenecía cada una de estas piezas. Pero finalmente se obtuvo una solución.

Para concluir, si bien se tomó un modelo muy sencillo para el análisis, se puede ver una correlación entre la interacción y competencia que existe entre el sistema inmune y el cáncer.

### References:
1. Cancer growth and metastasis as a metaphor of Go gaming: An Ising model approach - Didier Barradas-Bautista, Matias Alvarado-Mentado, Mark Agostino, Germinal Cocho (2018)
2. Cancer Metastasis and the Immune System Response: CM-IS Modeling by Ising Model - Matias Alvarado, Renato Arroyo (2020).