# Fresnel example notebooks

These [jupyter](https://jupyter.org/) notebooks provide a tutorial for the
[fresnel](https://github.com/glotzerlab/fresnel) visualization software. Static versions are included in
[fresnel's documentation](http://fresnel.readthedocs.io/).

## Index

### Basic tutorials

Basic tutorials introduce the user to the essential elements **fresnel** via short examples with extended descriptions. Later example scripts assume that the user is familiar with these concepts and do not to re-introduce them.

* [Introduction](00-Basic-tutorials/00-Introduction.ipynb)
* [Primitive properties](00-Basic-tutorials/01-Primitive-properties.ipynb)
* [Material properties](00-Basic-tutorials/02-Material-properties.ipynb)
* [Outline materials](00-Basic-tutorials/03-Outline-materials.ipynb)
* [Scene properties](00-Basic-tutorials/04-Scene-properties.ipynb)
* [Lighting setups](00-Basic-tutorials/05-Lighting-setups.ipynb)

### Primitives

Demonstrate each of the geometry primitives that you can use to build a **fresnel** `Scene`.

* [Sphere](01-Primitives/00-Sphere-geometry.ipynb)
* [Cylinder](01-Primitives/01-Cylinder-geometry.ipynb)
* [Convex polyhedron](01-Primitives/02-Convex-polyhedron-geometry.ipynb)
* [Mesh](01-Primitives/03-Mesh-geometry.ipynb)
* [Polygon](01-Primitives/04-Polygon-geometry.ipynb)
* [Box](01-Primitives/05-Box-geometry.ipynb)

### Advanced topics

* [Multiple geometries](02-Advanced-topics/00-Multiple-geometries.ipynb)
* [Devices](02-Advanced-topics/01-Devices.ipynb)
* [Tracer methods](02-Advanced-topics/02-Tracer-methods.ipynb)
* [Interactive scene view](02-Advanced-topics/03-Interactive-scene-view.ipynb)
* [Rendering images in matplotlib](02-Advanced-topics/04-Rendering-images-in-matplotlib.ipynb)
* [GSD visualization](02-Advanced-topics/05-GSD-visualization.ipynb)

## Prerequisites

These examples use the following python packages:

* [fresnel](https://github.com/glotzerlab/fresnel)
* [GSD](https://github.com/glotzerlab/gsd)
* [jupyter](http://jupyter.org/)
* [matplotlib](http://matplotlib.org/)
* [pillow](https://python-pillow.org/)

Anaconda users can install these from [conda-forge](https://conda-forge.org/):

```bash
conda install -c conda-forge fresnel gsd jupyter matplotlib pillow
```
