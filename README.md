# Learn OpenCL

OpenCL is a C/C++ library for general-purpose heterogenous (CPU, GPU, FGPA, etc.) computing. Use it to do cross-vendor GPGPU programming.

## Learning Resources

You can learn the details of OpenCL in this [website](https://handsonopencl.github.io/). It contains a PowerPoint slides that contains the actual learning material that you can find in this [link](https://github.com/HandsOnOpenCL/Lecture-Slides/releases).

## Asus 1225B with AMD APU C-60 (Radeon 6290)

1. Download drivers from [amd.com/drivers](http://amd.com/drivers).
1. Select Processor with Graphics.
1. Then select C-series.
1. Then select C-60.
1. Then select Radeon 6290.
1. Download the first two for Ubuntu 14.04 (`fglrx`, `fglrx-core`).
1. Install first the `fxlrx-core` then the `fglrx`.
1. Reboot.
1. In terminal, type `clinfo` for the list of supported platforms (See the result from my machine in the `clinfo` file in this repository).

## Example

This repository contains an example from this [website](https://subscription.packtpub.com/book/application_development/9781849692342/1/ch01lvl1sec12/an-example-of-opencl-program). Run the following:

```sh
make
./saxpy
```
