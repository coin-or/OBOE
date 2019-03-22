# Oracle Based Optimization Engine (OBOE)

## Introduction

OBOE (Oracle Based Optimization Engine) is an open source software for general convex optimization.
It assumes that a user-made code, thereafter named oracle, is capable of delivering first order information on the key elements of the problem (support the feasible set, support to the objective function).
The engine exploits this information to construct the so-called localization set which is a polyhedral approximation of the set of optimal solutions.

To implement OBOE on a typical problem of convex optimization such as "min {f(x) | x in X}" the user must implement an oracle with the following specification:

 * Input to the Oracle: a query point x provided by OBOE.
 * Output from the Oracle:
   * If x is feasible, the oracle returns the value f(x) and an element of the subgradient of f at x.
   * If x is infeasible, the oracle returns a  hyperplane separating x and the feasible set X.

An optimization session alternates computations by the oracle and by OBOE until the relative optimality gap at the current iterate meets the target value assigned by the user.
The user can alternatively set his own stopping rule.

The query points that OBOE selects are approximate minimizers of a logarithmic barrier function on the polyhedral set plus a proximal term.
OBOE is an implementation of ACCPM, the Analytic Center Cutting Plane Method. 

<!--A complement to this introduction can be found in [ScopeOboe the scope of OBOE].-->


## Download and Installation

OBOE is an open source software written in C++.
It is released under the [Common Public License (CPL)](https://opensource.org/licenses/cpl1.0.php).
It is made available by the [COIN-OR initiative](http://www.coin-or.org/).  

You can get the source code directly from the oboe GitHub repository with the command:

```
git clone https://github.com/coin-or/OBOE.git
```

Old released source packages can be found [here](https://github.com/coin-or/OBOE/releases).

OBOE has been mainly developed for a Linux based environment but does have Windows support via Mingw or MSVisualStudio project files.
A complete step-by-step procedure to install OBOE is available for:
 * [Ubuntu](https://github.com/coin-or/OBOE/wiki/UbuntuOboe) (a good start point for any other Linux distribution)
 * [Mac OS X with fink](https://github.com/coin-or/OBOE/wiki/MacosxOboe)


## Recently added features

OBOE can handle twice differentiable functional components in an optimization problem via the logarithmic barrier function.
The present implementation does this for two special cases
 * Components of the objective function with a diagonal Hessian.
 * Euclidean ball constraints. 
Extension to functionals with non-diagonal Hessian will necessitate additional work on the linear algebra involved in the computation of the analytic center.

## Documentation

 * [Latest user-guide](doc/userguide/OBOE-UserGuide.pdf).
 * [Proximal-ACCPM: a versatile oracle based optimization method](http://www.ordecsys.com/uploads/docs/OBOE_23_06_05.pdf).


## A few references

### Theoretical papers

 * Goffin, J., Haurie, A., and Vial, J.-P. [Decomposition and nondifferentiable optimization with the projective algorithm](http://www.jstor.org/view/00251909/di012921/01p0222b/0). _Management Science_ 37 (1992), 284-302.
 * Nesterov, Y., and Vial, J.-P. [Homogeneous analytic center cutting plane methods for convex problems and variational inequalities](http://scitation.aip.org/getabs/servlet/GetabsServlet?prog=normal&id=SJOPE8000009000003000707000001). _SIAM Journal on Optimization_ 9 (1999), 707-728.

### Application papers

 * **Column generation** and/or **Lagrangian relaxation** for the p-median and the uncapacitated location problems.
   * Beltran, C., Tadonki, C., and Vial, J.-P. [Solving the p-median problem with a semi-Lagrangian relaxation](http://www.springerlink.com/content/4786567415172326). _Computational Optimization and Applications_, 35 (2006).
   * Beltran, C., Vial, J.-P., and Alonso-Ayuso, A. [Solving the uncapacitated facility location problem with semi-Lagrangian relaxation](http://www.optimization-online.org/DB_HTML/2007/02/1597.html). Working paper, Statistics and Operations Research, Rey Juan Carlos University, Madrid, Spain, 2007.
 * **Multicommodity Flows Problems**
   * Babonneau, F., du Merle, O., and Vial, J.-P. [Solving large scale linear multicommodity flow problems with an active set strategy and Proximal-ACCPM](http://www.optimization-online.org/DB_HTML/2004/08/922.html). _Operations Research_ 54, 1 (2006), 184-197.
   * Babonneau, F., and Vial, J.-P. [ACCPM with a nonlinear constraint and an active set strategy to solve nonlinear multicommodity flow problems](http://www.optimization-online.org/DB_HTML/2005/06/1148.html). Tech. rep., HEC/Logilab, University of Geneva, 40 Bd du Pont d'Arve, CH-1211, 2005. To appear in _Mathematical Programming_.
 * **Traffic Assignment with Elastic Demand**
   * Babonneau, F., and Vial, J.-P. [An efficient method to compute traffic assignment problems with elastic demands](http://www.optimization-online.org/DB_HTML/2006/07/1432.html). Technical Report (to appear in _Transportation Research_),  2006, revised march 2007.
 * **Climate Models Calibration**
   * Beltran, C., Edwards, N., Haurie, A., Vial, J.-P., and Zachary, D. [Oracle-based optimization applied to climate model calibration](http://www.springerlink.com/content/3q70671666058227). _Environmental Modeling and Assessment_ 11, 1 (2006), 31-43.
 * **Models Integration**
   * Drouet, L., Edwards, N. R. and Haurie, A. [Coupling climate and economic models in a cost-benefit framework: A convex optimisation approach](http://dx.doi.org/10.1007/s10666-006-9047-5). _Environmental Modeling and Assessment_, 11, 2 (2006).
 * **Benders decomposition** for Stochastic Programming.
   * Bahn, O., du Merle, O., Goffin, J.-L., and Vial, J.-P. [A cutting plane method from analytic centers for stochastic programming](http://www.springerlink.com/content/q3435k468p8523j2/). _Mathematical Programming_ 69 (1995), 45-73.

## Project Links

 * [ORDECSYS](http://www.ordecsys.com/)
 * [OBOE mailing list](http://list.coin-or.org/mailman/listinfo/oboe)
