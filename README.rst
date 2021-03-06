Dockerfiles (and `images`__)
============================

__ https://hub.docker.com/r/mcranmer/dockers/tags/

This is assortment of dockerfiles, images, scripts, and other things
that I find useful.

Example
-------

Converting latex to rich text format:

.. code::
    
    ./docker_cmd.sh latex2rtf latex2rtf myfile.tex

This command pulls from `mcranmer/dockers:latex2rtf`, runs it,
then executes the `latex2rtf` command inside the container
on the linked file `myfile.tex`, which creates an rtf file.

I'm also
keeping some dockerfiles for notoriously
difficult to built astronomy software packages. All of these
things are listed below.

Other scripts
-------------

I have two incuded shell scripts (Linux and OS X) which
automatically set up a X11 for some container, so you can launch a GUI
from inside it and interact. You probably need to fiddle with 
the environment of the container (e.g., `ENV DISPLAY :0`) to
get it to work.

List of Dockerfiles (all built on `Docker Hub`__):
==================================================

__ https://hub.docker.com/r/mcranmer/dockers/tags/


Quick commands
--------------

-  latex2rtf: https://sourceforge.net/projects/latex2rtf/
-  pandoc: http://pandoc.org/

Other libraries
---------------

-  spinmob: https://github.com/Spinmob/spinmob
-  ciao: http://cxc.harvard.edu/ciao/
-  ds9: http://ds9.si.edu/
-  cfitsio: https://heasarc.gsfc.nasa.gov/fitsio/fitsio.html
-  healpix: http://healpix.jpl.nasa.gov/
-  wcslib: http://www.atnf.csiro.au/people/mcalabre/WCS/


Manual building
===============

To build any, run:

.. code::

    $ docker build -t <image name> -f <filename> .

So, for healpix, this would be:

.. code::

    $ docker build -t healpix -f healpix .

GUI usage:
==========

Linux:

.. code::

    $ ./launch_gui_linux_docker.sh <image> <directory to link> 

Mac (a bit more developed):

.. code::

    $ ./launch_gui_mac_docker.sh <image> <directory to link> <starting command> <container name>

Note that the Mac version requires Xquartz and socat installed.

The default port for both is 8888.


More examples
=============

Use my dev environment to edit a file:

.. code::

    $ ./docker_command_tty.sh dev vim myfile.txt

Look at an astronomical image on Mac OS:

.. code::

    $ ./launch_gui_mac_docker.sh mcranmer/dockers:ds9 $(pwd) "ds9 /workspace/myfile.fits" my_container
