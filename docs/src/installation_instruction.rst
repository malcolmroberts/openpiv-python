.. _installation_instruction:

========================
Installation instruction
========================

.. _dependencies:

Dependencies
============

OpenPIV would not have been possible if other great open source projects did not
exist. We make extensive use of code and tools that other people have created, so 
you should install them before you can use OpenPIV.

The dependencies are:

* `Python 2.7 <http://python.org/>`_
* `Scipy <http://numpy.scipy.org/>`_
* `Numpy <http://www.scipy.org/>`_
* `Cython <http://cython.org/>`_

On all platforms, the following Python distributions arerecommended:

* Anaconda <https://store.continuum.io/cshop/anaconda/>  

Missing package ``progressbar``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ 

Some distributions lack `progressbar` package. Install it separately using `pip`

    pip install progressbar


Get OpenPIV source code!
========================

The easiest way to get the latest released beta version is using PyPI server:

    pip install openpiv
    
or if you have an older version, then use

    pip install openpiv --upgrade
    

Bleeding edge development version
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you are interested in the source code you are welcome to browse out git repository
stored at https://github.com/alexlib/openpiv-python. If you want to download the source code
on your machine, for testing, you need to set up git on your computer. Please look at 
http://help.github.com/ which provide extensive help for how to set up git.

To follow the development of OpenPIV, clone our repository with the command::

    git clone http://github.com/alexlib/openpiv-python.git

and update from time to  time. You can also download a tarball containing everything.

Then add the path where the OpenPIV source are to the PYTHONPATH environment variable, so 
that OpenPIV module can be imported and used in your programs. Remeber to build the extension
with :: 

    python setup.py build_ext --inplace 
    

Module import on Windows 7 64-bit
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If you are working on a Windows 7 64-bit computer, you may face several problems while trying
to import the OpenPIV modules. The following instructions provide a workaround and a short list
of issues encountered while trying other alternatives than the one here presented.

Install Enthought Canopy 32-bit no matter if the OS is 64-bit.

Install Visual Studio 8 Express (32 bit) from 
    
    http://download.microsoft.com/download/A/5/4/A54BADB6-9C3F-478D-8657-93B3FC9FE62D/vcsetup.exe

Install the full version of Windows SDK for Windows 7 and .NET Framework 3.5 SP1 from
    
    http://www.microsoft.com/en-us/download/details.aspx?id=3138

Remove in /openpiv/src/ the two .c files: lib.c and process.c - so they'll be regenerated by 
Cython from the .pyx files

In Command Prompt Interface, while executing Python, go to the directory containing OpenPIV and 
import the OpenPIV modules with:
    
    python setup.py build_ext --inplace


PS. I have had a similar experience while working with a GIS system on a Windows 64-bit machine and 
trying to get Python modules to work. I started with a Python 64-bit MSI Installer and was not able 
to find the modules from the GIS system. I ended up installing the Python 32-bit version which worked. 
My uneducated (perhaps obvious) guess is that the problem lies on the flavour. Maybe a header line 
stating this (if proved) would be good. 


Issues that led to this Workaround: 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When using the visual Studio Redistributable Setup x64 the vcvarsall.bat file may not be 
available, which is needed to activate the C+ compiler. 

When installing just the C+ compiler tools from SDK the fike basetsd.h may not be 
available or simply not found, causing cl.exe to not be properly executed, with following 
error message:
    "Fatal error C1083: Cannot open include file: 'basetsd.h': No such file or directory
    error: command '"C:\Program Files (x86)\Microsoft Visual Studio 9.0\VC\BIN\cl.exe"

If the command line python setup.py build is used, the following error may appear: 
    "ImportError: No module named lib"

The use of MinGW instead of Visual Studio for the C compiler has been tried and produces 
the same error as above:
    "ImportError: No module named lib"


.. Stable source distribution
.. ^^^^^^^^^^^^^^^^^^^^^^^^^^
.. If you do not want to follow the development of OpenPIV and you prefer a more stable
.. version, download the source distributions available at http://www.openpiv.sourceforge.net,
.. in the downloads page. Then unpack it and execute the following command::

..    python setupy.py install --prefix=$DIR
    
.. where ``$DIR`` is the folder you want ot install OpenPIV in. If you want to install it system
.. wide omit the ``--prefix`` option, but you should have root priviles to do so. Remember to 
.. update the PYTHONPATH environment variable if you used a custom installation directory.


.. Download pre-built binary distributions
.. =======================================

.. For Windows we provide pre-built distributions which can be used without the hassles
.. of compilation and other boring things you may not want to dig into. This is currently  .. a work
.. in progress. Check back soon!





Having problems?
================
If you encountered some issues, found difficult to install OpenPIV following these instructions
please drop us an email to openpiv-users@googlegroups.com , so that we can help you and 
improve this page!




