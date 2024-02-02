# DDG

## Discrete Differential Geometry

This repository extracts the core Discrete Differential Geometry code from [geometry-processing-js](https://github.com/Martin-Eriksson/geometry-processing-js).

At a high level, the framework is divided into three parts - a flexible a halfedge mesh data structure, an optimized linear algebra package (based on [Eigen](https://eigen.tuxfamily.org)), and code for various geometry processing algorithms. Each algorithm comes with its own viewer for rendering.

### Code Snippet

Since geometry-processing-js already implements many of the fundamental operations needed for geometry processing, it's easy to get up and running very quickly. Here's a short snippet showing how to solve a Poisson equation on a mesh loaded by the GUI, which uses built-in routines for constructing the Laplace and mass matrices:

```
// assign an index to each vertex of the mesh
let vertexIndex = indexElements(geometry.mesh.vertices);

// build cotan-Laplace and mass matrices
let A = geometry.laplaceMatrix(vertexIndex);
let M = geometry.massMatrix(vertexIndex);
let rhs = M.timesDense(rho);

// solve Poisson equation with a given right-hand side rhs
let llt = A.chol();
let phi = llt.solvePositiveDefinite(rhs);
```

