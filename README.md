# checkpoint_intro

2. Estimación del nivel socioeconómico de un radio censal
La siguiente metodología permite obtener una estimación del nivel socioeconómico de un radio censal de la Ciudad Autónoma de Buenos Aires. Esta metodología es una adaptación con modificaciones de la utilizada por el ITDP de México (Instituto de Políticas para el Transporte y el Desarrollo) para la estimación del nivel socioeconómico de un área geoestadística básica (AGEB) de la Zona Metropolitana del Valle de México (ZMVM).

En líneas generales, consiste en realizar un análisis de componentes principales a partir de tres índices que reflejan diferentes aspectos del nivel socioeconómico de un radio censal de la Ciudad.

Esta técnica busca encontrar las causas de la variabilidad de un conjunto de datos y ordernarlas por importancia. De esta manera, se construye una lista de componentes principales (que son combinaciones lineales de los índices utilizados) ordenadas por el grado de poder explicativo que tienen sobre la variabilidad de los tres índices.

El primer componente principal construido a partir de estos tres índices es utilizado después para ordenar los radios censales por nivel socioeconómico.

Todos los datos utilizados para calcular los índices que componen el nivel socioeconómico provienen de la base de datos REDATAM del Censo Nacional 2010.

$IndiceComputadora = \frac{NúmeroDeHogaresConComputadora}{ConComputadora \cup ConHeladera \cup ConCelular \cup ConTeléfono}$

Calcula el porcentaje de hogares que tienen computadora, dentro de aquellos que tienen al menos una computadora, heladera, celular o teléfono de línea.

$IndiceEscolaridad = \frac{MenoresDe18Asisten}{MenoresDe18}$

Calcula el porcentaje de habitantes menores a 18 años que concurre a algún establecimiento educativo.

$IndiceEducSuperior = \frac{MayoresDe25Universitarios}{MayoresDe25}$

Calcula el porcentaje de habitantes mayores a 25 años que tiene nivel universitario completo.

Cuadro 1: Matriz de correlaciones

*	educ_sup	escolaridad	compu
educ_sup	1	0.496032	0.792191
escolaridad	0.496032	1	0.64806
compu	0.792191	0.64806	1
El análisis de los tres primeros componentes principales arrojó los siguientes porcentajes de varianza explicada:

88.32%
10.11%
1.57%
Utilizando este método, se reduce la dimensionalidad de la información que aporta cada uno de los índices aprovechando las variaciones conjuntas entre ellos. El primer componente principal es una combinación lineal de los tres índices según la siguiente ecuación:

PC1=0.76120783∗IndiceEducSup+0.10759338∗IndiceEscolaridad+0.63952037∗IndiceCompu
Utilizaremos a este primer componente principal como una estimación del nivel socioeconómico de los radios censales. Pero siendo que el PC1 arroja un rango de valores entre 0 y 1.32 (aproximadamente) se procede a una normalización para facilitar la lectura de los valores.

$NSE = \frac{PC1}{PC1Max} * 10$

De esta manera todos los valores del índice de NSE de radios censales se expresan en una escala del 0 al 10, donde 10 es el máximo valor de NSE alcanzado por el primer radio censal del ranking y 0 es el mínimo.
