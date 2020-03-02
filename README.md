# Learn OpenCL

OpenCL stands for Open Compute Language. OpenCL is a C/C++ library for general-purpose heterogenous (CPU, GPU, FGPA, etc.) computing. Use it to do cross-vendor GPGPU programming.

## Learning Resources

You can learn the details of OpenCL in this [website](https://handsonopencl.github.io/). It contains a PowerPoint slides that contains the actual learning material that you can find in this [link](https://github.com/HandsOnOpenCL/Lecture-Slides/releases).

## Concepts

1. Host
    
    The main machine where the program is executed. It is in the CPU.

1. OpenCL Platform

    In my Asus 1225B notebook laptop with AMD APU C-60, one platform contains 1 CPU and 1 GPU.

1. OpenCL Device

    The CPU, GPU, etc.

1. Compute Unit

    One CU (Compute Unit) per CPU core.

1. Processing Element

    One PE (Processing Element) per CU or n-PE where _n_ matches SIMD width.

1. Work Group

    Contains many Work Item. It is like a fraction/slice of a 2D image. All work items can be synchronized. Work groups cannot be synchronized. This is like a single GPU core that processes a slice of a 2D image; a single GPU core can process all the pixels in a slice of a 2D image in a sequential fashion like a CPU. Whereas many GPU cores runs in parallel; like processing many slices of a 2D image.

1. Work Item

    This is like computing a single pixel in a 2D image.

1. Kernel

    The program that is run on the device. It is a single function that takes arguments and do a simple vector operation, like `A = B + C` where `A, B, C` are vectors.

1. Context

    Contains one or more devices, device memory, and one or more command queues.

1. Command Queue

    Contains all commands for a device like kernel execution, synchronization, and memory transfer operations. A command queue can be configured in two ways: _In-order_ or _Out-of-order_ execution. There is one command queue for each device.

1. NDRange (N-Dimensional Range)
    
    This is a command that is sent to the command queue. It executes the kernel to N-dimensions (up to 3 dimensions) input data. There is a _global_ and _local_ size. The _global_ size is the max length of the vector. The _local_ size is the size of a Work Group.

## OpenCL Programming Flow

1. Define host memory objects.
1. Create context. Define the platform.
1. Create command queues in the context. One command queue for each device.
1. Define device memory objects. This copies the host memory objects to the device memory objects.
1. Create OpenCL program (either from `*.cl` file or a string literal).
1. Build the OpenCL program. This creates an IR (Intermediate Representation).
1. Create the kernel from the OpenCl program. This extracts a single function in the OpenCL program.
1. Add kernel arguments.
1. Execute the kernel.
1. Transfer results from device to host by pushing a read command to the command queue.

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
