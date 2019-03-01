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

### Advanced topics

* [Multiple geometries](02-Advanced-topics/00-Multiple-geometries.ipynb)
* [Devices](02-Advanced-topics/01-Devices.ipynb)
* [Tracer methods](02-Advanced-topics/02-Tracer-methods.ipynb)
* [Interactive scene view](02-Advanced-topics/03-Interactive-scene-view.ipynb)

## Executing the examples

You can [install fresnel](https://fresnel.readthedocs.io/en/stable/installation.html) and run these examples
interactively. Different installation methods require different steps to launch.

### Host installation (from source or anaconda package)

Clone the **fresnel-examples** repository and start **jupyter notebook**

```bash
▶ git clone https://github.com/glotzerlab/fresnel-examples
▶ cd fresnel-examples
▶ jupyter notebook
```

### Singularity container

Clone the **fresnel-examples** repository.

```bash
▶ git clone https://github.com/glotzerlab/fresnel-examples
▶ cd fresnel-examples
```

The image contains all software needed to execute these notebooks. Use singularity to launch the container:

```bash
▶ singularity exec -B $XDG_RUNTIME_DIR software.simg jupyter notebook
```

Add ``--nv`` after exec to utilize GPUs.

Explanation:

* ``singularity exec`` - Ask singularity to execute a command in a container.
* ``-B $XDG_RUNTIME_DIR`` - Bind mount your user specific temporary director. Jupyter uses this directory and
  singularity does not mount it by default.
* ``software.simg`` - The image to launch.
* ``jupyter notebook`` Execute ``jupyter notebook`` inside the image

Once **jupyter** starts, point your browser to the URL **jupyter** prints on the terminal. **jupyter** inside the
container accesses the configuration in your home directory on the host system. If you have a password configured for
**jupyter** on your host system, use that to login. Otherwise, the URL should include a token that will log you in.

### Docker container

The **glotzerlab/software** image contains all software needed to execute these notebooks and a copy of the notebooks
themselves in ``/fresnel-examples``. Run this command to start **jupyter**:

```bash
▶ docker run --rm -p 127.0.0.1:9999:9999 glotzerlab/software jupyter notebook --port 9999 --ip 0.0.0.0 --no-browser /fresnel-examples
```

If you have installed the docker NVIDIA runtime, add ``--runtime=nvidia`` after ``run`` to utilize your GPUs.

Explanation:

* ``docker run`` - Ask docker to run a command in a container.
* ``--runtime=nvidia`` - (if applicable) use the NVIDIA runtime to make host GPUS accessible in the container.
* ``--rm`` - Delete the container after exiting.
* ``-p 127.0.0.1:9999:9999`` - Make port 9999 in the container available at ``localhost:9999``.
* ``glotzerlab/software`` - name of the image to execute.
* ``jupyter notebook`` - execute the **jupyter** notebook.
* ``--port 9999 --ip 0.0.0.0`` - **jupyter** should listen on port 9999 for connections from outside the container.
* ``--no-browser`` - Tell Jupyter not to attempt to launch a browser.
* ``/fresnel-examples`` - Location of the example notebooks in the image.

Once **jupyter** starts, point your browser to ``localhost:9999``. Copy the token from the **jupyter** terminal output
and paste it into the password box to access the notebook.
