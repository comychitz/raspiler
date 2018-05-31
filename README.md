# raspiler
Cross compiler for the Raspberry Pi.

# introduction
I have always found cross compilation to be an interesting topic. The ability to
create programs for a different target than the one your building on was
difficult for me to first grasp, but now understand how it works and have used
it to build programs, I thought I'd give a stab and try to build a cross
compiler targeted for Raspberry Pi development. 

Building a cross compiler involves three systemsr the *build* system, the *host* 
system, and the *target* system. In this example, the build and host system will
be my own development machine (Fedora 28). Our target system is the Raspberry
Pi. The build system will be used to compile the cross compiler by using the
system's native compiler to compile the GCC source code. The host system will
then be used to run the cross compiler we built to compile any program we want
to run on our Raspberry Pi. Sounds simple, right? Well, there are a lot of tiny
details we need to cover, but that is the gist of it. Let's get started.

# building the cross compiler
[TODO]

# resources
I owe tremendous credit to the following resources:
* [Building GCC as a cross compiler for Raspberry Pi](https://solarianprogrammer.com/2018/05/06/building-gcc-cross-compiler-raspberry-pi/)
