# libz80
libz80 library - EmulatorKit / RC2040 compatible version
========================================================

Version 3.0.3, Tim Holyoake, March 2024.

This library takes the [EmulatorKit](https://github.com/EtchedPixels/EmulatorKit/) / [RC2040](https://github.com/ExtremeElectronics/RC2040/) fork of the libz80 library as of February 2024 and fixes a number of issues. I've created it as there are 
breaking fixes in both the EmulatorKit / RC2040 version of the library (see the Z80 context structure for example) and the current 
[Gabriel Gambetta](https://github.com/ggambetta/libz80/) 
version (see the size_t pointer issue) which mean that merging the two versions together is beyond my current scope of wanting to ensure the RC2040 
emulator software is as close as possible in the operation of the Z80 cpu to real RC2014 hardware.

The library now passes all except one of the zexdoc test suite and all bar two of the zexall test suite (as found in yaze-ag 2.51.3).

Unsurprisingly, both these test suites pass in their entirety when run on actual RC2014 hardware. 

For all practical purposes the failing tests are unlikely to impact anything running on an RC2040 under CP/M 2.2 - unless you know differently!

The rc2040tests directory contains a couple of programs that now produce correct results. They require the Digital Research CBASIC 2.0 (or 2.07) compiler
and linker - see instructions in the comments of primes80.bas.

libz80 - Z80 emulation library
===============================

*© Gabriel Gambetta (gabriel.gambetta@gmail.com) 2000 - 2014*

*Version 2.1.1*

Building and Installing
-----------------------

The Makefile creates `libz80.so`, which together with `z80.h` make up the binary
package. `make install` installs these files in `/usr/lib` and `/usr/include`
respectively.

Emulation code itself is generated by the `codegen` directory. `mktables.spec`
includes a specification of the opcodes, using regular expressions to express
similar opcodes in a compact way. Binary representation of the opcodes is listed
in `opcodes.lst`. This makes tweaking the 'processor' relatively easy, as it
isn't done manually.

Pre-generated files are included - these are `opcodes_decl.h`, `opcodes_table.h`
and `opcodes_impl.c` in the `codegen` directory.

Authors
-------

Gabriel Gambetta (gabriel.gambetta@gmail.com)

Wayne Conrad (wconrad@yagni.com) - MAJOR fixes and emulation improvements.
