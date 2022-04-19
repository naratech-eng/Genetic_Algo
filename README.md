* Student Details: 

Name: Sanjeewa Narayana
Student ID: 1075602
Course: CIS4780. 

## install Box2D

* Task 1-3:

The tasks 1-3 were implemented and used to generate the data for task 4,
which are shown in detail in the following.

For testing purposes, the program was modified slightly. First, a
constant seed value was ensured to have identical landscapes and
starting values for the cars. Second, when switching over to the next
generation, the distance of the elite cars from the previous generation
is saved to a file 'stats.dat'. In all cases, the game was allowed to
evolve for 10 generations.

To allow a comparison of the different scenarios, the maximum travelled
distance of the 'winning' car was chosen as a figure of merit.

* Task 4a: Comparison of different cross-over strategies, no mutations

Related game runs:

+---------------------+--------+-------+------------+--------+
|                     | mut. % | elite | max. dist. | gen. # |
+---------------------+--------+-------+------------+--------+
| 2pt cross-over      |      0 |     3 |        155 |      9 |
| 1pt cross-over      |      0 |     3 |        153 |      8 |
| uniform cross-over  |      0 |     3 |        154 |   8-10 |
+---------------------------------------------------+--------+

Without mutations, the best performance is reached for uniform
cross-over. The maximum distance (~ 153) is reached already within the
second generation. The next best seems to be 2-point cross-over, where
the same final distance of is reached after 8 generations. In contrast
to the uniform cross-over, here the best three cars reach this distance.
For comparison, the 1-point cross-over reaches a similar distance with
one car, after 5 generations, although this does decay again after 7
generations for unknown reasons.

* Task 4b: Evaluating the effect of mutations

Related game runs:

+---------------------+--------+-------+------------+--------+
|                     | mut. % | elite | max. dist. | gen. # |
+---------------------+--------+-------+------------+--------+
| 1pt cross-over      |      0 |     3 |        153 |      8 |
| 1pt cross-over      |     10 |     3 |        163 |      4 |
| 1pt cross-over      |     25 |     3 |        155 |      4 |
| 1pt cross-over      |     40 |     3 |        163 |      5 |
+---------------------+--------+-------+------------+--------+
| uniform cross-over  |      0 |     3 |        154 |   8-10 |
| uniform cross-over  |     10 |     3 |        153 |    4-5 |
| uniform cross-over  |     25 |     3 |        153 |    2-8 |
| uniform cross-over  |     40 |     3 |        182 |      6 |
+---------------------------------------------------+--------+

Each property of the non-elite cars gets a 10%, 25% or 40%  chance for a
mutation. Mutations only affect the wheel radius, density and chassis
density. The position and number of wheels is kept constant.

The comparison is done for the worst (1-point cross-over) and best
(uniform cross-over) cases of the previous study. The situation for
1-point cross-over is dramatically improved, distances of up to 163 are
reached in the 4th generation, although the typical maximum lies around
153. The situation for uniform cross-over gets slightly worse. The
maximum distance around 153 is still reached, but typically with less
cars than in the case of no mutations. Higher mutation rates of 25% and
40% do not significantly change the statistics. The typical maximum for
a game run remains around 153, with exceptions up to 182 for a single
car in a single generation.

For both cases, the maximum values seem to be reached after fewer
generations, thus underlining that mutations speed up the development
(for better or for worse).

* Task 4c: Influence of elite survival

Related game runs:

+---------------------+--------+-------+------------+--------+
|                     | mut. % | elite | max. dist. | gen. # |
+---------------------+--------+-------+------------+--------+
| uniform cross-over  |      0 |     1 |        154 |    2-3 |
| uniform cross-over  |      0 |     3 |        154 |   8-10 |
| uniform cross-over  |      0 |     5 |        154 |      3 |
+---------------------------------------------------+--------+

There seems to be no large statistical influence of the elite survival
parameter. This was studied for 1, 3 and 5 surviving cars. Mutations are
turned off in this case, as the surviving cars do not undergo mutations,
therefore, there should be no direct influence.

* Summary

The fact that the uniform cross-over strategy appears to be the most
successful points towards an equal distribution of the relevant
features. This means that there is not one distinct feature like the
wheel size or the chassis density that is dominant, but rather a more
complex combination of these factors.

It should be noted that all of these statistics were done using the same
random seed. This provides the advantage that they are comparable, but
it bears the risk that one of the methods enters a particularly
favourable or unfavourable path.
