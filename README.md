# MiniFEM-2D: Python Finite Element Solver

**A Python-based 2D Finite Element Solver for Linear Elasticity**

MiniFEM-2D is an educational finite element solver developed using Python, NumPy, and SciPy. It implements the fundamental computational procedures of the finite element method (FEM), including triangular element formulation, global stiffness matrix assembly, boundary condition enforcement, displacement calculation, stress recovery, and numerical verification.

The project demonstrates the implementation of core numerical algorithms commonly used in Computer-Aided Engineering (CAE) software.

## Key Features

- **Mesh Generation:** Structured two-dimensional triangular meshes
- **Finite Element Formulation:** Three-node Constant Strain Triangle (CST) elements
- **Material Model:** Isotropic linear elasticity under plane stress
- **Matrix Assembly:** Sparse global stiffness matrix construction
- **Linear Solver:** Sparse direct solution using SciPy
- **Boundary Conditions:** Fixed displacement constraints and external loads
- **Post-processing:** Displacement visualization and Von Mises stress contours
- **Numerical Verification:** Force equilibrium, residual checks, and mesh convergence analysis

## Mathematical Formulation

The governing equation for static equilibrium is:

\[
\nabla \cdot \boldsymbol{\sigma}+\mathbf{f}=0
\]

The finite element system is expressed as:

\[
\mathbf{K}\mathbf{u}=\mathbf{F}
\]

The element stiffness matrix is computed using:

\[
\mathbf{K}_e=tA\mathbf{B}^T\mathbf{D}\mathbf{B}
\]

where \(t\) is the thickness, \(A\) is the element area, \(\mathbf{B}\) is the strain-displacement matrix, and \(\mathbf{D}\) is the constitutive matrix.

## Numerical Example: Cantilever Beam

A two-dimensional cantilever beam is modeled with the following parameters:

| Parameter | Value |
|---|---|
| Length | 1.0 m |
| Height | 0.2 m |
| Thickness | 0.01 m |
| Young's modulus | 210 GPa |
| Poisson's ratio | 0.30 |
| Applied vertical load | 1000 N |
| Element type | CST triangular element |

### Point-Load Example

For the initial mesh with 288 triangular elements and a concentrated nodal load:

- Tip vertical displacement: **−0.219477 mm**
- Maximum element Von Mises stress: **13.31 MPa**
- Vertical support reaction: **1000 N**
- Relative linear system residual: **1.521 × 10⁻¹²**

These results demonstrate equilibrium satisfaction and successful solution of the discretized linear system.

### Mesh Convergence Study

A separate load case applies an equivalent total downward force of 1000 N, uniformly distributed along the right boundary.

| Triangular Elements | Vertical Displacement (mm) |
|---:|---:|
| 128 | 0.194643 |
| 288 | 0.219226 |
| 1,152 | 0.237519 |
| 4,608 | 0.242693 |
| 10,368 | 0.243699 |

The displacement approaches a stable value as the mesh is refined.

The finest-mesh result differs from the Timoshenko beam approximation (0.245524 mm) by approximately 0.74%. This comparison is informative but is not an exact error estimate for the two-dimensional elasticity problem.

## Technologies

- Python
- NumPy
- SciPy
- Matplotlib
- Google Colab / Jupyter Notebook

## How to Run

1. Download `MiniFEM_2D_Elasticity.ipynb` from this repository.
2. Open the notebook in Google Colab or Jupyter.
3. Run the cells sequentially from top to bottom.
4. Inspect the mesh, displacement results, stress contours, and convergence study.

The implementation uses NumPy and SciPy for numerical operations but constructs finite element stiffness matrices and assembles the global system explicitly.

## Current Limitations

MiniFEM-2D is an educational prototype, not a production-grade CAE solver.

The current implementation supports small-deformation, isotropic linear elasticity in plane stress. Material nonlinearity, geometric nonlinearity, contact mechanics, and advanced element formulations have not yet been implemented.

Further verification against analytical benchmarks and established FE software would strengthen its reliability.

## Future Development

Potential improvements include elastoplastic material models, Newton–Raphson nonlinear solution algorithms, additional element formulations, and performance benchmarking.

## Project File

[View the MiniFEM Jupyter Notebook](MiniFEM_2D_Elasticity.ipynb)
