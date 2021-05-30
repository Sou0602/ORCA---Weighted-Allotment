# Weighted Allotment for Velocity Freespace Regions to resolve Deadlocks in Multi-robot Planning

In the code above, we use ORCA constraints for real-time reactive motion planning and compute the controls on a holonomic model. 
We then map the holonomic controls to non-holonomic model using an arc-length parametrization model. On top of the regular model,
we have an allotment criteria based on the environment in the velocity freespace to compute a preferred side of a Collision Cone.

Hence, the entire code is divided into three parts broadly and the files below are classisfied in the similar order for better convenience.

Allotment Based functions:
For generating weights on allotment, we carry out geometrical operations on polyshapes in MATLAB. The functions below involve basic math operations of computing intersections 
between lines and a polyshape(square region), and then constructing polyshapes from intersections etc.

-CC.m  
-CC_plot.m
-constructpoly.m
-dividevshape.m
-getdist_weight.m
-getintersection.m
-allotment_weights.m
