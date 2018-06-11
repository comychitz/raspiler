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
The build & host machine I'll be using is Fedora 28 which is running in a
VirtualBox image on my Macbook Pro Retina Late 2012 (Macbook Pro 10,1)

To perform building the cross compiler I followed the following guide, modifying
commands as needded (the guide was using Ubuntu as the build machine).

I owe tremendous credit to the following resource:
* [Building GCC as a cross compiler for Raspberry Pi](https://solarianprogrammer.com/2018/05/06/building-gcc-cross-compiler-raspberry-pi/)

When building the first portion of gcc, had to modify some things before running
`make install-gcc`
* while in the build-gcc dir, ran: `cp -r
    ./build-x86_64-pc-linux-gnu/fixincludes ./`
* also, modified ./fixincludes/Makefile line 37 to remove one level of `../` 
    * and line 52 to set gcc_version to `6.3.0`
* before running `make install-gcc` i had to singlely compile libiberty myself:
    `cd libiberty && make`

[STOPPING POINT] - need to continue by building (partially) glibc, then
completing gcc, then completing glibc, then we should be ready!
