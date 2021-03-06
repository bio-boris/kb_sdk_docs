Manually build the SDK
======================

.. warning::

    The recommended installation option is to run the `SDK as a
    Docker container. </tutorial/install.html>`_

2. Install and Build SDK
~~~~~~~~~~~~~~~~~~~~~~~~

Java JDK 7+
'''''''''''

http://www.oracle.com/technetwork/java/javase/downloads/index.html

After downloading and installing the JDK, set your ``JAVA_HOME``
environment variable to point to your JDK installation. If you're not
sure where that is, on a Mac the command ``/usr/libexec/java_home``
should tell you and on Linux ``readlink -f $(which javac)`` will provide
the installed location of the javac, which you can use to find the base
directory of the installation. On a Mac you can set the variable like
so:

::

    # for bash
    export JAVA_HOME=`/usr/libexec/java_home`
    # for tcsh/csh
    setenv JAVA_HOME `/usr/libexec/java_home`  

You should probably add this command to the end of your
``~/.bash_profile`` or ``~/.bashrc`` file so it is always set when you start
a terminal.

Apache Ant
''''''''''

http://ant.apache.org

http://ant.apache.org/manual/install.html

The easist way to install Ant on a Mac is probably to use a package
manager like `HomeBrew <http://brew.sh/>`__, which allows you to install
simply by ``brew install ant``. Make sure the Ant install location is
added to your PATH environment variable, which is generally handled for
you if you use a package manager like HomeBrew.

Fetch the code from GitHub:
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create a directory in which you want to work. All your work should go
here. All commands that follow are assuming you are using a UNIX shell.

::

    cd <working_dir>
    git clone https://github.com/kbase/kb_sdk
    git clone https://github.com/kbase/jars
    cd kb_sdk
    make bin  # or "make" to compile from scratch

You should now have the kb-sdk program built in kb\_sdk/bin. It will be
helpful to add this to your execution path. From within the kb\_sdk
directory, you can run in Bash:

::

    export PATH=$(pwd)/bin:$PATH

Optionally, you can also install command completion with:

::

    source src/sh/sdk-completion.sh

Like ``JAVA_HOME``, you should consider adding these last two commands
to your ``~/.bash_profile`` or ``~/.bashrc`` file so the SDK is always
available in the terminal with command completion.

Test installation
^^^^^^^^^^^^^^^^^

To make sure you installed the SDK successfully, type kb-sdk help

Download the KBase SDK base Docker image
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

KBase modules run in Docker containers. Docker containers are built on
top of existing base images. KBase has a public base image that includes
a number of installed runtimes, some basic bioinformatics tools, and
other KBase specific tools. To run this locally, you will need to
download and build the KBase SDK base image. There is a Makefile target
that does most of the work for you:

::

    make sdkbase

You will get a failure if the Docker daemon is not running when you
invoke the above command. See `Install SDK Dependencies -
Docker </tutorial/dependencies.html>`_ for guidance.

The image is fairly large, so it will take some time to run and build
the image.
