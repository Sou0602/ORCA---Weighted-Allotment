# Weighted Allotment for Velocity Freespace Regions to resolve Deadlocks in Multi-robot Planning

In the code above, we use ORCA constraints for real-time reactive motion planning and compute the controls on a holonomic model. 
We then map the holonomic controls to non-holonomic model using an arc-length parametrization model. On top of the regular model,
we have an allotment criteria based on the environment in the velocity freespace to compute a preferred side of a Collision Cone.

Hence, the entire code is divided into three parts broadly and the files below are classisfied in the similar order for better convenience.

Allotment Based functions:

For generating weights on allotment, we carry out geometrical operations on polyshapes in MATLAB. The functions below involve basic math operations of computing intersections 
between lines and a polyshape(square region), and then constructing polyshapes from intersections etc.

- CC.m , tangent.m

- CC_plot.m

- constructpoly.m

- dividevshape.m

- getdist_weight.m

- getintersection.m

- allotment_weights.m

Non - Holonomic Mapping functions: 

To compute the non-holonomic controls given an acceptable holonomic velocity.

- a1.m , a2.m , a3.m , a4.m

- theta.m , theta_in.m , x_fren.m , y_fren.m

- vel-prof.m

- curve_generate.m

- optimize_spiral.m

Remaining functions: 

All the remaining functions are to define the parameters, plot the simulations and the optimization framework is included in getControls.m

_________________________________________________________________________________________________________________________________________________________________

To run the simulation , go to run.m. At the top of the document, there are sample confirations where an agents start, goal , and desired velocity max are specified for 
each agent in the configuration. 

As a default case, the first configuration is uncommented. To run other configurations, make sure to comment the previous block and uncomment the block of configuration that you are trying to run. 

In cases where, you are using a pre-saved configuration and not starting from the start,name the configrations are "agents1", instead of the default setting "agents" and then uncomment the block shown below(at the end of all the configurations):

    %{ 
    for i = 1:length(agents)
    agents1(i).position = agents(i).position;
    agents1(i).velocity = agents(i).velocity;
    end
 
    clear agents;
    agents = agents1;
    clear agents1;
    %}
 
In the getControls.m function, we have a desired-velocity cost and a smoothness cost. We also have a repulsion cost and a goal-reaching cost but are not used regularly or tuned. Appropriate weights can be given to them to tune the performance of the configurations.

Among other tunable parameters:
- In the getconstraints_orca_r.m and getconstraints_orca_l.m - the parameter r can be tuned with weights ranging from 3.2 to 4.8. We lower values suggest, close proximity collision avoidance. 3.2 is the minimum value since we have the parameter tau fixed to 1.6.
- All the corresponding weights can be adjusted in the getControl.m and optimize_spiral.m optimization functions for a different performance. 
- The weights in getdist_weight.m can be changed for a different non-linear weighting strategy.

_____________________________________________________________________________________________________________________________________________________________________________

The code can be run in situations where we have different levels of overlap between the ORCA strategy and the Allotment based strategy. Often, configurations based only on ORCA resort to deadlock like scenarios, whereas only Allotment may resolve the deadlock but take a longer path to converge to the goal. Hence, an optimial overlap is preferred. By changing the orca_t parameter in getControls.m , you can adjust the iterations for the ORCA strategy to overlap the allotment strategy.

_______________________________________________________________________________________________________________________________________________________________________________

For more details regarding the method , go through the presentation in the link:

https://docs.google.com/presentation/d/1TuZpSDHAAKmwWytC9QK7Br_yVPMgy5JQuyWmhDZe1gA/edit?usp=sharing
    
