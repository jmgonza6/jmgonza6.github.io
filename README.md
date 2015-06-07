# MSL-Suite V 0.1 06.06.2015

This is a library which contains several routines focused on preparing,
conducting, and analyzing atomistic simulations.  The entire suite is written 
in C99 and C++99 making using of standard libraries and some STL for the C++ codes.


##Contents:

* `lib/`   Source for shared libraries, libDMol libLAMMPS libMSL, libVASP

* `include/`  Headers containing definitions of libraries

* `examples/`  Directory containing several codes demonstrating the various library methods and there usage


##Dependencies:

The custom math namespace can be built with or without a BLAS installation.  If 
you wish to build with BLAS, define the path in BLAS along with the flag -DBLAS.

	
##Building the libraries

These libraries can be built as either shared objects (*.so) or as an archive (*.a).  
Simply execute the following accordingly:
```
$ cd lib
$ make shared
$ make shared-install
$ cd ../
```
```
$ cd lib
$ make archive
$ make archive-install
$ cd ../
```

To change the default install directory, /usr/local/lib and /usr/local/include, run as,
```
$ make shared-install LIB_DIR=/lib/path/you/want/instead INC_DIR=/include/path/you/want/instead 
```

This will build all the libraries individually with their .a/.so files contained in their main directory
as well as being installed in the proper directory.

If you need just a single library, run the following to see how to make that target,
```
$ make help
```

Note: By default, in the serial codes, it is assumed that you are using icc/icpc/ifort 
(Intel compilers) in your environment.  If you are using some other compiler, execute 
the following instead of basic (c)make, for example:
```
$ make CC=gcc
```

##Usage:

See the directory `examples/libxxx` for some examples of calls to the various library subroutines.

If you changed your install location, dont forget to export your new LD_LIBRARY_PATH environment 
variable when compiling and executing your programs.

Build your programs wit the libraries as follows,
```
icpc -L$(LIB_DIR)/libs -llammps -lmathns ... -I$(INC_DIR)/include code.cpp -o out.x 
```

