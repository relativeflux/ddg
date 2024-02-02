# DDG

## Discrete Differential Geometry

This repository extracts the main [Discrete Differential Geometry](https://www.ams.org/publications/journals/notices/201710/rnoti-p1153.pdf) code from [geometry-processing-js](https://github.com/Martin-Eriksson/geometry-processing-js):

- [core](https://github.com/relativeflux/ddg/tree/master/core) - A flexible halfedge mesh data structure.
- [linear-algebra](https://github.com/relativeflux/ddg/tree/master/linear-algebra) - An optimized linear algebra package (based on [Eigen](https://eigen.tuxfamily.org)),

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

