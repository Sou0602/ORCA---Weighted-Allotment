# Weighted Allotment for Velocity Freespace Regions to resolve Deadlocks in Multi-robot Planning

In the code above, we use ORCA constraints for real-time reactive motion planning and compute the controls on a holonomic model. 
We then map the holonomic controls to non-holonomic model using an arc-length parametrization model. On top of the regular model,
we have an allotment criteria based on the environment in the velocity freespace to compute a preferred side of a Collision Cone.

Hence, the entire code is divided into three parts broadly and the files below are classisfied in the similar order for better convenience.

Allotment Based functions:

For generating weights on allotment, we carry out geometrical operations on polyshapes in MATLAB. The functions below involve basic math operations of computing intersections 
between lines and a polyshape(square region), and then constructing polyshapes from intersections etc.

-CC.m , tangent.m

-CC_plot.m

-constructpoly.m

-dividevshape.m

-getdist_weight.m

-getintersection.m

-allotment_weights.m

Non - Holonomic Mapping functions: 

To compute the non-holonomic controls given an acceptable holonomic velocity.

- a1.m , a2.m , a3.m , a4.m

- theta.m , theta_in.m , x_fren.m , y_fren.m

-vel-prof.m

-curve_generate.m

-optimize_spiral.m

Remaining functions: 

All the remaining functions are to define the parameters, plot the simulations and the optimization framework is included in getControls.m
