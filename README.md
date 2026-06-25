# Shallow Water Equations on a Yin–Yang Grid: Strategy 2

This repository contains the implementation of Strategy 2 for the numerical solution of the shallow water equations (SWEs) on a Yin–Yang overset grid.

The solver combines a fourth-order compact MacCormack scheme for spatial discretization with the classical fourth-order Runge–Kutta (RK4) method for time integration. Strategy II represents an enhanced grid-coupling approach designed to improve stability and consistency across Yin–Yang interfaces.

---

## Overview

The Yin–Yang grid provides an efficient overset-grid framework for spherical computations while avoiding coordinate singularities associated with conventional latitude–longitude grids. However, high-order numerical methods on overlapping grids may experience stability issues near interpolation interfaces.

Strategy II addresses these challenges through enhanced overlap regions and additional information transfer between the Yin and Yang subgrids during each time-integration stage.

---

## Numerical Method

* Governing equations: Shallow Water Equations (SWEs)
* Grid topology: Yin–Yang overset grid
* Spatial discretization: Fourth-order compact MacCormack scheme
* Time integration: Fourth-order Runge–Kutta (RK4)
* Inter-grid communication through high-order interpolation

---

## Strategy II

Strategy II introduces two stabilization mechanisms within the standard Yin–Yang solution framework.

### Enhanced Overlap Region

The overlap between the Yin and Yang component grids is enlarged in order to improve information exchange and reduce numerical inconsistencies near grid interfaces.

### Prognostic Variable and Derivative Transfer

At every Runge–Kutta stage:

1. Prognostic variables are exchanged between the Yin and Yang grids within the overlap region.
2. Updated values from the Yin grid are transferred to the overlapping region of the Yang grid.
3. Spatial derivatives are computed on both component grids using their local solution fields.
4. For Yang-grid boundary points located near the overset interface, derivative information is obtained from the Yin grid through interpolation.

This procedure improves consistency between the two subgrids while maintaining derivative evaluations on both Yin and Yang component grids.

---

## Validation

The implementation is validated using two classical benchmark test cases for the shallow water equations on the sphere.

These benchmark problems are used to assess:

* Numerical accuracy
* Stability characteristics
* Conservation properties
* Effectiveness of the Strategy II stabilization procedure

---

## Relation to Other Strategies

This repository contains only the implementation of Strategy 2.

Implementations of Strategy 1 and Strategy 3 are provided in separate repositories. A detailed comparison of the three strategies, including their advantages and limitations, is presented in the associated publication.

---

## Repository Structure

```text
.
├── src/          # Source code
├── grid/         # Yin–Yang grid and interpolation routines
├── tests/        # Benchmark test cases
├── results/      # Numerical results and visualizations
└── README.md
```

---

## Citation

If you use this code in your research, please cite the associated publication describing the proposed stabilization strategies and their comparative evaluation.

---

## License

See the LICENSE file for licensing information.
