# Linux kernel for Raspberry Pi 4

There are several guides for kernel developers and users. These guides can
be rendered in a number of formats, like HTML and PDF. Please read
Documentation/admin-guide/README.rst first.

In order to build the documentation, use ``make htmldocs`` or
``make pdfdocs``.  The formatted documentation can also be read online at:

    https://www.kernel.org/doc/html/latest/

There are various text files in the Documentation/ subdirectory,
several of them using the Restructured Text markup notation.

## Setup development workspace

Clone the repository and install the following packages(ubuntu):

```
gcc-aarch64-linux-gnu
gcc-arm-linux-gnueabihf (optional for 32bit)
build-essential
git
flex
bison
bc
```

And setup the environment variables:

```bash
export ARCH=arm64 #for 32bit, set instead ARCH=arm
export CROSS_COMPILE=aarch64-linux-gnu- #for 32bit, set instread CROSS_COMPILE=arm-linux-gnueabihf-
export DTS_SUBDIR=broadcom
export IMAGE=Image.gz
```

To build the kernel, just run:

```bash
make bcm2711_defconfig
# Replace $JOB_COUNT for the number of jobs to build the kernel
make -j $JOB_COUNT
```