
Fresnel example notebooks
=========================

These `jupyter <https://jupyter.org/>`_ notebooks provide a tutorial for the
`fresnel <https://bitbucket.org/glotzer/fresnel/>`_ visualization software. Static versions are included in
`fresnel's documentation <http://fresnel.readthedocs.io/>`_. You can download these notebooks from the
`fresnel-examples <https://bitbucket.org/glotzer/fresnel-examples>`_ repository and run them interactively.

Launch with anaconda
--------------------

Download and install `miniconda <http://conda.pydata.org/miniconda.html>`_.
Then add the ``conda-forge`` channel and install **fresnel**\ , **jupyter** and several other python packages:

.. code-block:: bash

   ▶ conda config --add channels conda-forge
   ▶ conda install fresnel jupyter pillow matplotlib

Clone the **fresnel-examples** repository and start **jupyter notebook**

.. code-block:: bash

   ▶ git clone https://bitbucket.org/glotzer/fresnel-examples.git
   ▶ cd fresnel-examples
   ▶ jupyter notebook

Launch with singularity
-----------------------

Clone the **fresnel-examples** repository.

.. code-block:: bash

   ▶ git clone https://bitbucket.org/glotzer/fresnel-examples.git
   ▶ cd fresnel-examples

If you control your Linux system, install `Singularity <http://singularity.lbl.gov/>`_ (if you haven't already).
Many compute clusters already have Singularity installed. Then pull the
`glotzerlab/software <https://hub.docker.com/r/glotzerlab/software/>`_ docker image:

.. code-block:: bash

   ▶ umask 002
   ▶ singularity pull docker://glotzerlab/software

The image contains all software needed to execute these notebooks. Use singularity to launch the container:

.. code-block:: bash

   ▶ singularity exec -B $XDG_RUNTIME_DIR software.simg jupyter notebook

Add ``--nv`` after exec to utilize GPUs.

Explanation:


* ``singularity exec`` - Ask singularity to execute a command in a container.
* ``-B $XDG_RUNTIME_DIR`` - Bind mount your user specific temporary director. Jupyter uses this directory and singularity does not mount it by default.
* ``software.simg`` - The image to launch.
* ``jupyter notebook`` Execute ``jupyter notebook`` inside the image

Once **jupyter** starts, point your browser to the URL **jupyter** prints on the terminal. **jupyter** inside the container accesses the configuration in your home directory on the host system. If you have a password configured for **jupyter** on your host system, use that to login. Otherwise, the URL should include a token that will log you in.

Launch with Docker
------------------

Install `Docker <https://www.docker.com/>`_ on your system if you haven't already. Then pull the
`glotzerlab/software <https://hub.docker.com/r/glotzerlab/software/>`_ image:

.. code-block:: bash

   ▶ docker pull glotzerlab/software

The ``glotzerlab/software`` image contains all software needed to execute these notebooks and a copy of the notebooks themselves in ``/fresnel-examples``. Run this command to start **jupyter**\ :

.. code-block:: bash

   ▶ docker run --rm -p 127.0.0.1:9999:9999 glotzerlab/software jupyter notebook --port 9999 --ip 0.0.0.0 --no-browser /fresnel-examples

If you have installed the docker NVIDIA runtime, add ``--runtime=nvidia`` after ``run`` to utilize your GPUs.

Explanation:


* ``docker run`` - Ask docker to run a command in a container.
* ``--rm`` - Delete the container when finished.
* ``-p 127.0.0.1:9999:9999`` - Make port 9999 in the container available at localhost:9999. Don't leave off the ``127.0.0.1`` prefix - *doing so will expose port 9999 to the world!*.
* ``glotzerlab/software`` - name of the image to execute.
* ``jupyter notebook`` - execute the **jupyter** notebook.
* ``--port 9999 --ip 0.0.0.0`` - Jupyter should listen on port 9999 for connections from outside the container.
* ``--no-browser`` - Tell Jupyter not to attempt to launch a browser.
* ``/fresnel-examples`` - Location of the example notebooks in the image.

Once Jupyter starts, point your browser to ``localhost:9999``. Copy the token from the **jupyter** terminal output and past it into the password box to access the notebook.
