## saturn-loader

Flashing utility for Numato Lab Saturn FPGA boards.

## FAQ

### What is saturn-loader?

saturn-loader is a flashing utility for Numato Lab's Saturn FPGA board. This was
initially written because I was not able to find a suitable Linux friendly
flashing utility for this development board.

### What license is saturn-loader release under?

saturn-loader is released under the MIT/X Consortium License, see LICENSE file
for details.

Currently, the library dependencies are:

libftdi (LGPLv2.1, dynamically linked)
libmpsse (modified BSD license, statically linked)

### What architectures does saturn-loader support?

Currently saturn-loader has been successfully built and tested on x86_64, i686,
and armv7l (Raspberry Pi 2).

### How do you use saturn-loader?

First you need to build the project, install libftdi before proceeding:

	$ git clone https://github.com/amilkovich/saturn-loader.git
	$ cd saturn-loader
	$ make
	$ ./saturn-loader -l

Some common examples of running saturn-loader would be as follows:

	$ ./saturn-loader design.bin # flash design.bin to saturn
	$ ./saturn-loader -e # erase the flash (bulk erase)

### Help! I get flash id mismatch every time I try to flash/erase!

If something weird happened, like the saturn-loader process was killed in the
middle of a write, then the Xilinx Spartan's PROGRAM_B pin may be left asserted
(active low) and the Saturn may be in an undesirable state. In this case, you'll
need to manually tie the PROGRAM_B pin to GROUND. When that is wired up, flash
or erase as before. Once finished, disconnect the wire. See the Numato Lab
Saturn user guide for more details on the locations of PROGRAM_B (aka PROGB) and
available GROUND pins.
