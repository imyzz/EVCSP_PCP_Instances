# EVCSP_RA_instances
This repository contains the instances used for electric vehicle charging scheduling problem presented at paper "Minimizing grid capacity in preemptive electric vehicle charging orchestration: complexity, exact and heuristic approaches".

This research was done at the [laboratoire lorrain de recherche en informatique et ses applications (LORIA)](https://www.loria.fr/en/) laboratory of the [Université de Lorraine](https://www.univ-lorraine.fr/), [OPTIMIST](https://optimist.loria.fr/) Team. and the [Institut de Recherche en Informatique, Mathématiques, Automatique et Signal (IRIMAS)](https://www.irimas.uha.fr/) laboratory of the [Université de Haute-Alsace (UHA)](https://www.uha.fr/) by:

| Name                | Email                      | Institute |
|:--------------------|:---------------------------|:---------:|
| Imene Zaidi         | imene.zaidi@loria.fr       |    1,2    |
| Ammar Oulamara      | ammar.oulamara@loria.fr    |    1      |
| Lhassane Idoumghar  | lhassane.idoumghar@uha.fr  |    2      |
| Michel Basset       | michel.basset@uha.fr       |    2      |

| Ref. | Institute                                                            |
|:----:|:---------------------------------------------------------------------|
|  1   |  LORIA Laboratory UMR7503, Université de Lorraine Nancy, France      |
|  2   |  IRIMAS UR 7499, F-68100, Université de Haute-Alsace Mulhouse, France |


## Instances Description
An instance represents charging demands and it was generated as described [below](#instances-generation). All instances files are `.csv` files. Each row represents an electric vehicle. For each vehicle we have:
- Column `arrival_time` indicates the desired arrival time to the charging station in hours.
-  Column `departure_time` gives the departure time in hours.
-  Column `required_energy` displays the requested energy in kWh.


## Instances generation
We consider two types of instances: `small instances` and `hard instances`. The first type of instances represent typical scenarios, whereas the second types of instances represent more extreme situations.

### Small instances
We consider five groups of instances, where the number of charging demands $n$ in groups 1, 2, 3, 4, and 5 is equal to 10, 20, 40, 50, and 100, respectively, and for each group, we generate ten different random instances as follows.
- The arrival times of vehicles are generated from the uniform distribution in the interval  $[0, 0.2 n]$ (in hours). This means that the time horizon length depends on the number of vehicles $n$.  
 - The required energy are generated from the uniform distribution $[5.5, 66]$ (in kWh).
- To generate the departure times of vehicles, we  calculate, for each vehicle $j, j \in \mathcal{J}$, the charging times $p_{1j}$,  assuming that it can be charged with type 1 chargers as $p_{1j} = \frac{e_j}{11}$. Then, the departure time of each vehicle $j$ is calculated as $d_j = r_j  + (1+ \alpha) p_{1j}$ where $\alpha$ is randomly chosen according to the value $p_{1j}$ as:

|$p_{1j}$ (hours) |  $\alpha$ |
|:----:|:-----------------------|
| $[0.5, 1)$ | $[0.1, 1]$ |
|$[1, 2)$ | $[0.1, 0.9]$ |
| $[2,3)$ | $[0.1, 0.8]$ |
| $[3,4)$ | $[0.1, 0.7]$ |
| $[4,5)$ |  $[0.1, 0.6]$ |
| $[5,6)$ | $[0.1, 0.5]$|

 

## Hard instances
`hard_instances` folder contains 60 instances grouped into 6 groups. The number of charging demands $n$ in groups 1 and 4 is equal to 100, it is equal to 200 for groups 2 and 5, and it is equal to 200 for groups 3 and 6. For each group, we generate 10 different random instances as in type 1 instances, except for $\alpha$ values. For groups 1, 2, and 3 for half of the vehicles, $\alpha$ is fixed to $0.1$, and for the other half, it is fixed to $0.2$. For groups 4, 5, and 6 for $75$\% of vehicles, $\alpha$ is fixed to $0.1$, and for the other half, it is fixed to $0.2$. A summary of those values are shown below:

|instances group | instances number | $n$ | $\alpha =0.1 p_{1j}$  | $\alpha =0.2 p_{1j}$ |
|:--------------:|:----------------:|:---:|:---------------------:|:---------------------|
|1 | 1 to 10 | 100 | 50% | 50% |
|2 | 11 to 20 | 200 | 50% | 50% |
|3 | 21 to 30 | 400 | 50% | 50% |
|4 | 31 to 40 | 100 | 75% | 25% |
|5 | 41 to 50 | 200 | 75% | 25% |
|6 | 51 to 60 | 400 | 75% | 25% |


## License

<img align="right" src="http://opensource.org/trademarks/opensource/OSI-Approved-License-100x137.png">

USCP is licensed under the [MIT License](http://opensource.org/licenses/MIT):

Copyright &copy; 2022 [Imene ZAIDI](https://github.com/imyzz)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
