.. _Chap:InputsLoadBalancing:

Gridding and Load Balancing
===========================

The following inputs must be preceded by "amr" and determine how we create the grids and how often we regrid.

+----------------------+-----------------------------------------------------------------------+-------------+-----------+
|                      | Description                                                           |   Type      | Default   |
+======================+=======================================================================+=============+===========+
| regrid_int           | How often to regrid (in number of steps at level 0)                   |   Int       |    -1     |
|                      |  if regrid_int = -1 then no regridding will occur                     |             |           |
+----------------------+-----------------------------------------------------------------------+-------------+-----------+
| max_grid_size_x      | Maximum number of cells at level 0 in each grid in x-direction        |    Int      | 32        |
+----------------------+-----------------------------------------------------------------------+-------------+-----------+
| max_grid_size_y      | Maximum number of cells at level 0 in each grid in y-direction        |    Int      | 32        |
+----------------------+-----------------------------------------------------------------------+-------------+-----------+
| max_grid_size_z      | Maximum number of cells at level 0 in each grid in z-direction        |    Int      | 32        |
+----------------------+-----------------------------------------------------------------------+-------------+-----------+
| blocking_factor_x    | Each grid must be divisible by blocking_factor_x in x-direction       |    Int      |  8        |
+----------------------+-----------------------------------------------------------------------+-------------+-----------+
| blocking_factor_y    | Each grid must be divisible by blocking_factor_y in y-direction       |    Int      |  8        |
+----------------------+-----------------------------------------------------------------------+-------------+-----------+
| blocking_factor_z    | Each grid must be divisible by blocking_factor_z in z-direction       |    Int      |  8        |
+----------------------+-----------------------------------------------------------------------+-------------+-----------+

The following inputs must be preceded by "particles"

+-------------------+-----------------------------------------------------------------------+-------------+-----------+
|                   | Description                                                           |   Type      | Default   |
+===================+=======================================================================+=============+===========+
| max_grid_size_x   | Maximum number of cells at level 0 in each grid in x-direction        |    Int      | 32        |
|                   | for grids in the ParticleBoxArray if dual_grid is true                |             |           |
+-------------------+-----------------------------------------------------------------------+-------------+-----------+
| max_grid_size_y   | Maximum number of cells at level 0 in each grid in y-direction        |    Int      | 32        |
|                   | for grids in the ParticleBoxArray if dual_grid is true                |             |           |
+-------------------+-----------------------------------------------------------------------+-------------+-----------+
| max_grid_size_z   | Maximum number of cells at level 0 in each grid in z-direction        |    Int      | 32        |
|                   | for grids in the ParticleBoxArray if dual_grid is true.               |             |           |
+-------------------+-----------------------------------------------------------------------+-------------+-----------+

The following inputs must be preceded by "mfix" and determine how we load balance:

+----------------------+-----------------------------------------------------------------------+-------------+--------------+
|                      | Description                                                           |   Type      | Default      |
+======================+=======================================================================+=============+==============+
| dual_grid            | If true then use the "dual_grid" approach for load balancing          |  Bool       | False        |
+----------------------+-----------------------------------------------------------------------+-------------+--------------+
| load_balance_fluid   | Only relevant if (dual_grid); if so do we also regrid mesh data       |  Int        | 1            |
+----------------------+-----------------------------------------------------------------------+-------------+--------------+
| load_balance_type    | What strategy to use for load balancing                               |  String     | FixedSize    |
|                      | Options are "FixedSize", "KDTree" or "Knapsack"                       |             |              |
+----------------------+-----------------------------------------------------------------------+-------------+--------------+
| knapsack_weight_type | What weighting function to use if using Knapsack load balancing       |  String     | RunTimeCosts |
|                      | Options are "RunTimeCosts" or "NumParticles""                         |             |              |
+----------------------+-----------------------------------------------------------------------+-------------+--------------+
| knapsack_nmax        | Maximum number of grids per MPI process if using knapsack algorithm   |  Int        | 128          | 
+----------------------+-----------------------------------------------------------------------+-------------+--------------+

