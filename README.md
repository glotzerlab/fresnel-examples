
# Fresnel example notebooks

These [jupyter](https://jupyter.org/) notebooks provide a tutorial for the
[fresnel](https://bitbucket.org/glotzer/fresnel/`) visualization software. Static versions are included in
[fresnel's documentation](http://fresnel.readthedocs.io/`).

You can [install fresnel](https://fresnel.readthedocs.io/en/stable/installation.html) and run these examples
interactively. Different installation methods require different steps to launch.

## Host installation (from source or anaconda package)

Clone the **fresnel-examples** repository and start **jupyter notebook**

```bash
▶ git clone https://bitbucket.org/glotzer/fresnel-examples.git
▶ cd fresnel-examples
▶ jupyter notebook
```

## Singularity container

Clone the **fresnel-examples** repository.

```bash
▶ git clone https://bitbucket.org/glotzer/fresnel-examples.git
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

## Docker container

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
