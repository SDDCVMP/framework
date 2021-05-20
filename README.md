# [DEPRECATED] Dynamic Virtual Machine Placement Framework

This project contains the source code and results of the following research:

#### *"Towards Elastic Virtual Machine Placement in Overbooked OpenStack Clouds under Uncertainty"*

*Jornadas de Cloud Computing & Big Data, 2018* \
 **Authors**: F. López-Pires and B. Barán and C. Pereira and M. Velázquez and O. González \
 **Ref.:** [JCC&BD-2018](https://github.com/marcev93/DynamicVMPFramework)

###### Abstract 

Cloud computing datacenters currently provide millions of virtual machines in highly dynamic Infrastructure as a Service (IaaS) markets. As a first step on implementing algorithms previously proposed by the authors for the Virtual Machine Placement (VMP) in a real-world IaaS middleware, this work presents an experimental comparison of these algorithms against current algorithms considered for solving VMP problems in OpenStack. Several experiments considering scenario-based simulations for uncertainty modelling demonstrate that the proposed algorithms present promising results for its implementation towards real-world operations. Next steps are also summarized. 


##  


#### *"Machine Learning Opportunities in Cloud Computing Datacenter Management for 5G Services"*


*ITU Kaleidoscope, 2018* \
 **Authors**: F. López-Pires and B. Barán \
 **Ref.:** [ITU-2018](https://github.com/DynamicVMP/dynamic-vmp-framework)

###### Abstract 

Emerging paradigms associated to Cloud Computing operations are considered to serve as a basis to integrate 5G components and protocols. In the context of resource management for Cloud Computing Datacenters, several research challenges could addressed considering state-of-the-art machine learning techniques. This paper presents identified opportunities on improving critical resource management decisions, analyzing the potential on applying machine learning to solve these relevant problems, mainly in two-phase optimization schemes for Virtual Machine Placement (VMP). Future research directions are also presented.

##



To develop and execute the following items are required:

### To develop:

1. Maven 3 or greater
2. Java 8 (JDK 1.8)
3. Java IDE (i.e. eclipse, intellij, ...)

### To run:
The framework could be compile with maven.

1. Go to the project root and execute:
``` bash
$ mvn clean package
```

2. In the target directory is the compiled framework, to execute use the following command:
``` bash
$ java -jar target/DynamicVMPFramework.jar inputs/ivmp.conf inputs/vmpr.conf inputs/scenarios.con
f outputs/
```

##
#### Input File
- *parameter:* Configuration file and scenarios

##### Parameter File Structure

ivmp.conf:
1. APPROACH = Algorithm approach
 * CENTRALIZED
 * DISTRIBUTED -> This approach will automatically launch the distributed approach and you don't need to specify the following inputs: VMPr, VMPr_TRIGGERING, VMPr_RECOVERING.
 
2. iVMP = Algorithm for the incremental phase (iVMP).
 * FF -> First Fit
 * BF -> Best Fit
 * WF -> Worst Fit
 * FFD -> First Fit Decreasing
 * BFD -> Best Fit Decreasing

vmpr.conf:
3. VMPr = Algorithm for the reconfiguration phase (VMPr).
 * MEMETIC -> Memetic Algorithm
 * ACO -> Ant Colony Optimization
4. VMPr_TRIGGERING = VMPr triggering strategy
 * PERIODICALLY
 * PREDICTION-BASED
5. VMPr_RECOVERING = VMPr recovering strategy
 * CANCELLATION
 * UPDATE-BASED
6. PM_CONFIG = Load CPU Configuration
 * LOW -> (<10%)
 * MED  -> (<30%)
 * HIGH  -> (<80%)
 * FULL  -> (<95%)
 * SATURATED  -> (<120%)
7. DERIVE_COST = Cost per each derived VM
8. PROTECTION_FACTOR_01 = Resource1 protection factor [0;1]
9. PROTECTION_FACTOR_02 = Resource2 protection factor [0;1]
10. PROTECTION_FACTOR_03 = Resource3 protection factor [0;1]
11. PENALTY_FACTOR_01 = Resource1 penalty factor (greater than 1)
12. PENALTY_FACTOR_02 = Resource1 penalty factor (greater than 1)
13. PENALTY_FACTOR_03 = Resource1 penalty factor (greater than 1)
14. INTERVAL_EXECUTION_MEMETIC = Periodic Time of MA Execution
15. POPULATION_SIZE = Population size for MA
16. NUMBER_GENERATIONS = Generations size for MA
17. EXECUTION_DURATION = Time of Duration
18. LINK_CAPACITY = Link Capacity for Migration
19. MIGRATION_FACTOR_LOAD = Factor Load per Migration
20. HISTORICAL_DATA_SIZE = Historical Data Sieze
21. FORECAST_SIZE = Forecast Size
22. SCALARIZATION_METHOD = Scalarization Method
 * ED -> Euclidean Distance
 * MD -> Manhattan Distance
 * CD -> Chevyshev Distance
 * WS -> Weighted Sum
23. MAX_PHEROMONE = Max pheromone allowed in ACO
24. PHEROMONE_CONSTANT = Pheromone constant for ACO, range [0,1],
determines how fast pheromone evaporates. Pheromones evaporates
quicker as pheromone constant grows
25. N_ANTS = Number of ants used for ACO
26. ACO_ITERATIONS = Number of iterations to be performed in ACO
to return a solution

scenarios.conf:
27. SCENARIOS = List of Request

#### Output Files
The framework generates the following file:
- *resutls: contains F1, F2, F3 values
