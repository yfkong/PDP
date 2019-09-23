A modeling and heuristic algorithm framework for solving political districting problem or similar problems.
------------Sponsored by the National Natural Science Foundation of China (no. 41871307)

For definition and mathematical formulation of political districting problem, see: Yunfeng Kong, Yanfang Zhu & Yujing Wang (2019) A center-based modeling approach to solve the districting problem, International Journal of Geographical Information Science, 33:2, 368-384, DOI: 10.1080/13658816.2018.1474472

Multiple methods are provided to solve the political districting problem:
*center-based modeling
*local-search based heuristic
*genetic algorithm

Computing environment:
*Python 2.7
*CPLEX Python API

How to solve a problem instance:
>>>import pdp    #import the python library.
>>>pdp.readbmfile("gy")  #read data file, using parameters "gy","zy" or "gy2"
>>>pdp.set_districting(4,0.0,1.0)  #set districting parameters: no. of districts, deviation of district population, and the coefficient beta
>>>pdp.set_solver_params("mip",5,50,0,-1)
set solver parameters: solver name, multi_start, loops, is_scp_modeling, and random_seed.
solvers include: ils, mip, vnd, vns, sa, hc ... 
for 'mip' solver, the loops and is_scp_modeling are not used. The solver other than MIP is not provided in this version.
>>>pdp.solve() # solve the problem. 
>>>pdp.print_solution() #output the solution.

or using genetic algorithm:
>>>pdp.set_districting(4,0.0,1.0)
>>>pdp.ga(10,1000, 0, 0.7, 0.03,0,-1)
parameters: population size, generations, crossover method, crossover rate, mutation rate, spp/scp selection and random seed

You may also edit the sample file "sample.py", and run it directly.
____________________________________________________________________________________
import pdp
pdp.readbmfile("gy") 
pdp.set_districting(4,0.0,1.0) 
pdp.set_solver_params("mip",5,50,0,-1)
pdp.ls_operators=[0,1] #local search operators
pdp.solve()
pdp.print_solution() 
_____________________________________________________________________________________

You may prepare new data files for districting.
Use function "pdp.readfile(file1, file2)" to read two files: unit file and connectivity file.
The format of the unit file:
------------------------------------------
Id,POP,POINT_X,POINT_Y
1,136,19670450.702865,3828958.826762
2,103,19687644.561507,3833372.983579
3,277,19670091.388237,3833930.963618
4,85,19687021.107480,3833221.781865
5,255,19673907.891730,3833571.649051
...
------------------------------------------
Each unit has attributes id, population, x and y.

The format of the connectivity file:
------------------------------------------
OID,ID1,ID2
1,1,25
2,1,31
3,1,42
4,1,27
5,1,35
6,2,33
7,2,47
8,2,149
9,2,45
10,2,49
11,2,4
12,2,58
...
------------------------------------------
The two units in each line are adjacent. 

If you have any question, email: yfkong@henu.edu.cn.
Sponsored by the National Natural Science Foundation of China (no. 41871307)
