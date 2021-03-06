.. image:: /Current_Release_Notes/amdblack.jpg


====================================
AMD ROCm™ Patch Release Notes v3.9.1
====================================

Users of RPM-based operating systems (RHEL, CentOS, and others) are recommended to use the ROCm v3.9.1 patch release due to a potential compatibility issue with certain drivers.

================================
AMD ROCm™ Release Notes v3.9.0
================================
October, 2020

This page describes the features, fixed issues, and information about downloading and installing the ROCm software. It also covers known issues in the ROCm v3.9.0 release.

`Download AMD ROCm Release Notes PDF <https://github.com/RadeonOpenCompute/ROCm>`__


Support for Ubuntu 20.04.1
--------------------------

In this release, AMD ROCm extends support to Ubuntu 20.04.1, including
v5.4 and v5.6-oem.

Support for SLES 15 SP2
-----------------------

This release extends support to SLES 15 SP2.


List of Supported Operating Systems
-----------------------------------

The AMD ROCm platform is designed to support the following operating
systems:

The AMD ROCm platform is designed to support the following operating
systems:

-  Ubuntu 20.04.1 (5.4 and 5.6-oem) and 18.04.5 (Kernel 5.4)

**Note**: AMD ROCm only supports Long Term Support (LTS) versions of Ubuntu. Versions other than LTS may work with ROCm, however, they are not officially supported. 

-  CentOS 7.8 & RHEL 7.8 (Kernel 3.10.0-1127) (Using devtoolset-7
   runtime support)

-  CentOS 8.2 & RHEL 8.2 (Kernel 4.18.0 ) (devtoolset is not required)

-  SLES 15 SP2


Fresh Installation of AMD ROCm v3.9 Recommended
-----------------------------------------------

A fresh and clean installation of AMD ROCm v3.9 is recommended. An upgrade from previous releases to AMD ROCm v3.9 is not supported.

For more information, refer to the AMD ROCm Installation Guide at:

https://rocmdocs.amd.com/en/latest/Installation_Guide/Installation-Guide.html

**Note**: AMD ROCm release v3.3 or prior releases are not fully compatible with AMD ROCm v3.5 and higher versions. You must perform a fresh ROCm installation if you want to upgrade from AMD ROCm v3.3 or older to 3.5 or higher versions and vice-versa.

**Note**: *render group* is required only for Ubuntu v20.04. For all other ROCm supported operating systems, continue to use *video group*.

-  For ROCm v3.5 and releases thereafter,the *clinfo* path is changed to
   - */opt/rocm/opencl/bin/clinfo*.

-  For ROCm v3.3 and older releases, the *clinfo* path remains unchanged
   - */opt/rocm/opencl/bin/x86_64/clinfo*.
   
ROCm MultiVersion Installation Update
---------------------------------------

With the AMD ROCm v3.9 release, the following ROCm multi-version installation changes apply:

The meta packages rocm-dkms are now deprecated for multi-version ROCm installs. For example, rocm-dkms3.7.0, rocm-dkms3.8.0.

-   Multi-version installation of ROCm should be performed by installing rocm-dev using each of the desired ROCm versions. For example, rocm-dev3.7.0, rocm-dev3.8.0, rocm-dev3.9.0.

-  Version files must be created for each multi-version rocm <= 3.9.0

   -  command: echo \| sudo tee /opt/rocm-/.info/version

   -  example: echo 3.9.0 \| sudo tee /opt/rocm-3.9.0/.info/version

-  The rock-dkms loadable kernel modules should be installed using a single rock-dkms package.

- ROCm v3.9 and above will not set any *ldconfig* entries for ROCm libraries for multi-version installation.  Users must set *LD_LIBRARY_PATH* to load the ROCm library version of choice.

**NOTE**: The single version installation of the ROCm stack remains the same. The rocm-dkms package can be used for single version installs and is not deprecated at this time.



AMD ROCm Documentation Updates
-----------------------------------

AMD ROCm Installation Guide
================================

The AMD ROCm Installation Guide in this release includes:

-  Updated Supported Environments
-  Multi-version Installation Instructions

https://rocmdocs.amd.com/en/latest/Installation_Guide/Installation-Guide.html

ROCm Compiler Documentation Updates
=======================================

The ROCm Compiler documentation updates include,

-  OpenMP Extras v12.9-0
-  OpenMP-Extras Installation
-  OpenMP-Extras Source Build
-  AOMP-v11.9-0
-  AOMP Source Build

For more information, see

https://rocmdocs.amd.com/en/latest/Programming_Guides/openmp_support.html



ROCm System Management Information
====================================

ROCM-SMI version: 1.4.1 \| Kernel version: 5.6.20

-  ROCm SMI and Command Line Interface
-  ROCm SMI APIs for Compute Unit Occupancy

   -  Usage
   -  Optional Arguments
   -  Display Options
   -  Topology
   -  Pages Information
   -  Hardware-related Information
   -  Software-related/controlled information
   -  Set Options
   -  Reset Options
   -  Auto-response Options
   -  Output Options

For more information, refer to

https://rocmdocs.amd.com/en/latest/ROCm_System_Managment/ROCm-System-Managment.html#rocm-command-line-interface

For ROCm SMI API Guide, see

https://github.com/RadeonOpenCompute/ROCm/blob/master/ROCm_SMI_Manual_v3.9.pdf


AMD ROCm - HIP Documentation Updates
=======================================

-  HIP Porting Guide - CU_Pointer_Attribute_Memory_Type

For more information, refer to

https://rocmdocs.amd.com/en/latest/Programming_Guides/HIP-porting-guide.html#hip-porting-guide



General AMD ROCm Documentation Links
------------------------------------

Access the following links for more information:

-  For AMD ROCm documentation, see

   https://rocmdocs.amd.com/en/latest/

-  For installation instructions on supped platforms, see

   https://rocmdocs.amd.com/en/latest/Installation_Guide/Installation-Guide.html

-  For AMD ROCm binary structure, see

   https://rocmdocs.amd.com/en/latest/Installation_Guide/Installation-Guide.html#build-amd-rocm

-  For AMD ROCm Release History, see

   https://rocmdocs.amd.com/en/latest/Installation_Guide/Installation-Guide.html#amd-rocm-version-history
   

What's New in This Release
-----------------------------

ROCm Compiler Enhancements
=============================

The ROCm compiler support in the llvm-amdgpu-12.0.dev-amd64.deb package is enhanced to include support for OpenMP. To utilize this support, the additional package openmp-extras_12.9-0_amd64.deb is required.

Note, by default, both packages are installed during the ROCm v3.9 installation. For information about ROCm installation, refer to the ROCm Installation Guide.

AMD ROCm supports the following compilers:

-  C++ compiler - Clang++
-  C compiler - Clang
-  Flang - FORTRAN compiler (FORTRAN 2003 standard)

**NOTE** : All of the above-mentioned compilers support:

-  OpenMP standard 4.5 and an evolving subset of the OpenMP 5.0 standard
-  OpenMP computational offloading to the AMD GPUs

For more information about AMD ROCm compilers, see the Compiler Documentation section at,

https://rocmdocs.amd.com/en/latest/index.html

Auxiliary Package Supporting OpenMP
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The openmp-extras_12.9-0_amd64.deb auxiliary package supports OpenMP within the ROCm compiler. It contains OpenMP specific header files,
which are installed in /opt/rocm/llvm/include as well as runtime libraries, fortran runtime libraries, and device bitcode files in
/opt/rocm/llvm/lib. The auxiliary package also consists of examples in the /opt/rocm/llvm/examples folder.

**NOTE**: The optional AOMP package resides in /opt/rocm//aomp/bin/clang and the ROCm compiler, which supports OpenMP for AMDGPU, is located in
/opt/rocm/llvm/bin/clang.

AOMP Optional Package Deprecation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Before the AMD ROCm v3.9 release, the optional AOMP package provided support for OpenMP. While AOMP is available in this release, the optional package may be deprecated from ROCm in the future. It is recommended you transition to the ROCm compiler or AOMP standalone releases for OpenMP support.

Understanding ROCm Compiler OpenMP Support and AOMP OpenMP Support
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The AOMP OpenMP support in ROCm v3.9 is based on the standalone AOMP v11.9-0, with LLVM v11 as the underlying system. However, the ROCm compiler's OpenMP support is based on LLVM v12 (upstream).

**NOTE**: Do not combine the object files from the two LLVM implementations. You must rebuild the application in its entirety using either the AOMP OpenMP or the ROCm OpenMP implementation.


Example - OpenMP Using the ROCm Compiler
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

   $ cat helloworld.c
   #include <stdio.h>
   #include <omp.h>
    int main(void) {
     int isHost = 1; 
   #pragma omp target map(tofrom: isHost)
     {
       isHost = omp_is_initial_device();
       printf("Hello world. %d\n", 100);
       for (int i =0; i<5; i++) {
         printf("Hello world. iteration %d\n", i);
       }
     }
      printf("Target region executed on the %s\n", isHost ? "host" : "device");
     return isHost;
   }
   $ /opt/rocm/llvm/bin/clang  -O3 -target x86_64-pc-linux-gnu -fopenmp -fopenmp-targets=amdgcn-amd-amdhsa -Xopenmp-target=amdgcn-amd-amdhsa -march=gfx900 helloworld.c -o helloworld
   $ export LIBOMPTARGET_KERNEL_TRACE=1
   $ ./helloworld
   DEVID: 0 SGN:1 ConstWGSize:256  args: 1 teamsXthrds:(   1X 256) reqd:(   1X   0) n:__omp_offloading_34_af0aaa_main_l7
   Hello world. 100
   Hello world. iteration 0
   Hello world. iteration 1
   Hello world. iteration 2
   Hello world. iteration 3
   Hello world. iteration 4
   Target region executed on the device

For more examples, see */opt/rocm/llvm/examples*.

.. _rocm-system-management-information-1:



ROCm System Management Information
==================================

The AMD ROCm v3.9 release consists of the following ROCm System Management Information (SMI) enhancements:

-  Shows the hardware topology

-  The ROCm-SMI showpids option shows per-process Compute Unit (CU) Occupancy, VRAM usage, and SDMA usage

-  Support for GPU Reset Event and Thermal Throttling Event in ROCm-SMI Library

ROCm-SMI Hardware Topology
~~~~~~~~~~~~~~~~~~~~~~~~~~

The ROCm-SMI Command Line Interface (CLI) is enhanced to include new options to denote GPU inter-connect topology in the system along with
the relative distance between each other and the closest NUMA (CPU) node for each GPU.

.. image:: /Current_Release_Notes/images/ROCMCLI1.PNG 
    :align: center

  

Compute Unit Occupancy
~~~~~~~~~~~~~~~~~~~~~~

The AMD ROCm stack now supports a user process in querying Compute Unit (CU) occupancy at a particular moment. This service can be accessed to
determine if a process P is using sufficient compute units.

A periodic collection is used to build the profile of a compute unit occupancy for a workload.

.. image:: /Current_Release_Notes/images/ROCMCLI2.PNG 
   :align: center

ROCm supports this capability only on GFX9 devices. Users can access the functionality in two ways:

-  indirectly from the SMI library

-  directly via Sysfs

**NOTE**: On systems that have both GFX9 and non-GFX9 devices, users should interpret the compute unit (CU) occupancy value carefully as the
service does not support non-GFX9 devices.

Accessing Compute Unit Occupancy Indirectly
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The ROCm System Management Interface (SMI) library provides a convenient interface to determine the CU occupancy for a process. To get the CU
occupancy of a process reported in percentage terms, invoke the SMI interface using rsmi_compute_process_info_by_pid_get(). The value is
reported through the member field cu_occupancy of struct rsmi_process_info_t.

::

   /**
      * @brief Encodes information about a process
      * @cu_occupancy Compute Unit usage in percent
      */
     typedef struct {
         - - -,
         uint32_t cu_occupancy;
     } rsmi_process_info_t;

     /**
      * API to get information about a process
     rsmi_status_t
         rsmi_compute_process_info_by_pid_get(uint32_t pid,
             rsmi_process_info_t *proc);

Accessing Compute Unit Occupancy Directly Using SYSFS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Information provided by SMI library is built from sysfs. For every valid device, ROCm stack surfaces a file by the name cu_occupancy in Sysfs.
Users can read this file to determine how that device is being used by a particular workload. The general structure of the file path is
/proc//stats\_/cu_occupancy

::

   /**
      * CU occupancy files for processes P1 and P2 on two devices with 
      * ids: 1008 and 112326
      */
     /sys/devices/virtual/kfd/kfd/proc/<Pid_1>/stats_1008/cu_occupancy
     /sys/devices/virtual/kfd/kfd/proc/<Pid_1>/stats_2326/cu_occupancy
     /sys/devices/virtual/kfd/kfd/proc/<Pid_2>/stats_1008/cu_occupancy
     /sys/devices/virtual/kfd/kfd/proc/<Pid_2>/stats_2326/cu_occupancy
     
   // To get CU occupancy for a process P<i>
     for each valid-device from device-list {
       path-1 = Build path for cu_occupancy file;
       path-2 = Build path for file Gpu-Properties;
       cu_in_use += Open and Read the file path-1;
       cu_total_cnt += Open and Read the file path-2;
     }
     cu_percent = ((cu_in_use * 100) / cu_total_cnt);
     

GPU Reset Event and Thermal Throttling Event
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The ROCm-SMI library clients can now register for the following events:

.. image:: /Current_Release_Notes/images/ROCMCLI3.PNG 
   :align: center




ROCm Math and Communication Libraries
======================================

"rocfft_execution_info_set_stream" API
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rocFFT is a software library for computing Fast Fourier Transforms (FFT). It is part of AMDâ€™s software ecosystem based on ROCm. In addition
to AMD GPU devices, the library can be compiled with the CUDA compiler using HIP tools for running on Nvidia GPU devices.

The ˜rocfft_execution_info_set_stream" API is a function to specify optional and additional information to control execution. This API
specifies the compute stream, which must be invoked before the call to rocfft_execute. Compute stream is the underlying device queue/stream
where the library computations are inserted.

PREREQUISITES
^^^^^^^^^^^^^

Using the compute stream API makes the following assumptions:

-  This stream already exists in the program and assigns work to the stream

-  The stream must be of type hipStream_t. Note, it is an error to pass the address of a hipStream_t object

PARAMETERS
^^^^^^^^^^

Input

-  info execution info handle
-  stream underlying compute stream

Improved GEMM Performance
~~~~~~~~~~~~~~~~~~~~~~~~~

Currently, rocblas_gemm_ext2() supports matrix multiplication D <= alpha \* A \* B + beta \* C, where the A, B, C, and D matrices are
single-precision float, column-major, and non-transposed, except that the row stride of C may equal 0. This means the first row of C is
broadcast M times in C:

.. image:: /Current_Release_Notes/images/GEMM2.PNG
   :align: center

If an optimized kernel solution for a particular problem is not available, a slow fallback algorithm is used, and the first time a
fallback algorithm is used, the following message is printed to standard error:

*Warning: Using slow on-host algorithm, because it is not implemented in Tensile yet.*

**NOTE**: ROCBLAS_LAYER controls the logging of the calls. It is recommended to use logging with the rocblas_gemm_ext2() feature, to
identify the precise parameters which are passed to it.

-  Setting the ROCBLAS_LAYER environment variable to 2 will print the problem parameters as they are being executed.

-  Setting the ROCBLAS_LAYER environment variable to 4 will collect all of the sizes, and print them out at the end of program execution.

For more logging information, refer to

https://rocblas.readthedocs.io/en/latest/logging.html.

New Matrix Pruning Functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this release, the following new Matrix Pruning functions are introduced.

.. image:: /Current_Release_Notes/images/matrix.png 
   :align: center

   
rocSOLVER General Matrix Singular Value Decomposition API
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The rocSOLVER General Matrix Singular Value Decomposition (GESVD) API is now available in the AMD ROCm v3.9 release.

GESVD computes the Singular Values and, optionally, the Singular Vectors of a general m-by-n matrix A (Singular Value Decomposition).

The SVD of matrix A is given by:

::

   A = U * S * V'

For more information, refer to

https://rocsolver.readthedocs.io/en/latest/userguide_api.html


ROCm AOMP Enhancements
========================

AOMP v11.9-0
~~~~~~~~~~~~~

The source code base for this release is the upstream LLVM 11 monorepo release/11.x sources as of August 18, 2020, with the hash value 

1e6907f09030b636054b1c7b01de36f281a61fa2

The llvm-project branch used to build this release is aomp11. In addition to completing the source tarball, the artifacts of this release include the file llvm-project.patch. This file shows the delta from the llvm-project upstream release/11.x. The size of this patch XXXX lines in XXX files. These changes include support for flang driver, OMPD support, and the hsa libomptarget plugin. The goal is to reduce this with continued upstreaming activity.

The changes for this release of AOMP are:

- Fix compiler warnings for build_project.sh and build_openmp.sh.

- Fix: [flang] The AOMP 11.7-1 Fortran compiler claims to support the -isystem flag, but ignores it.

- Fix: [flang] producing internal compiler error when a character is used with KIND.

- Fix: [flang] openmp map clause on complex allocatable expressions !$omp target data map( chunk%tiles(1)%field%density0).

- DeviceRTL memory footprint has been reduced from ~2.3GB to ~770MB for AMDGCN target.

- Workaround for red_bug_51 failing on gfx908.

- Switch to python3 for ompd and rocgdb.

- Now require cmake 3.13.4 to compile from source.

- Fix aompcc to accept file type cxx.


AOMP v11.08-0
~~~~~~~~~~~~~

The source code base for this release is the upstream LLVM 11 monorepo release/11.x sources as of August 18, 2020 with the hash value

*aabff0f7d564b22600b33731e0d78d2e70d060b4*

The amd-llvm-project branch used to build this release is amd-stg-openmp. In addition to complete source tarball, the artifacts of this release includes the file llvm-project.patch. This file shows the delta from the llvm-project upstream release/11.x which is currently at 32715 lines in 240 files. These changes include support for flang driver, OMPD support and the hsa libomptarget plugin. Our goal is to reduce this with continued upstreaming activity.

These are the major changes for this release of AOMP:

-  Switch to the LLVM 11.x stable code base.

-  OMPD updates for flang.

-  To support debugging OpenMP, selected OpenMP runtime sources are included in lib-debug/src/openmp. The ROCgdb debugger will find these
   automatically.

-  Threadsafe hsa plugin for libomptarget.

-  Updates to support device libraries.

-  Openmpi configure issue with real16 resolved.

-  DeviceRTL memory use is now independent of number of openmp binaries.

-  Startup latency on first kernel launch reduced by order of magnitude.


AOMP v11.07-1
~~~~~~~~~~~~~

The source code base for this release is the upstream LLVM 11 monorepo development sources as July 10, 2020 with hash valued 979c5023d3f0656cf51bd645936f52acd62b0333 The amd-llvm-project branch used to build this release is amd-stg-openmp. In addition to complete source tarball, the artifacts of this release includes the file
llvm-project.patch. This file shows the delta from the llvm-project upstream trunk which is currently at 34121 lines in 277 files. Our goal is to reduce this with continued upstreaming activity.

-  Inclusion of OMPD support which is not yet upstream

-  Build of ROCgdb

-  Host runtime optimisation. GPU image information is now mostly read on the host instead of from the GPU.

-  Fixed the source build scripts so that building from the source tarball does not fail because of missing test directories. This fixes issue #116.



Fixed Defects
-------------------

The following defects are fixed in this release:

-  Random Soft Hang Observed When Running ResNet-Based Models

-  (AOMP) "Undefined Hidden Symbol" Linker Error Causes Compilation Failure in HIP

-  MIGraphx -> test_gpu_ops_test FAILED

-  Unable to install RDC on CentOS/RHEL 7.8/8.2 & SLES


Known Issues
-------------------

The following are the known issues in this release.

(AOMP) HIP Example device_lib Fails to Compile
===================================================

The HIP example device_lib fails to compile and displays the following error:

*lld: error: undefined hidden symbol: inc_arrayval*

The recommended workaround is to use */opt/rocm/hip/bin/hipcc to compile HIP applications*.


Hipfort Installation Failure
===============================

Hipfort fails to install during the ROCm installation.

As a workaround, you may force install hipfort using the following instructions:

Ubuntu
~~~~~~

::

   sudo apt-get -o Dpkg::Options::="--force-overwrite" install hipfort

SLES
~~~~

Zypper gives you an option to continue with the overwrite during the installation.

CentOS
~~~~~~

Download hipfort to a temporary location and force install with rpm:

::

   yum install --downloadonly --downloaddir=/tmp/hipfort hipfort
   rpm -i --replacefiles hipfort<package-version>


Memory Fault Access Error During Memory Test of ROCm Validation Suite 
========================================================================

When the ROCm Validation Suite (RVS) is installed using the prebuilt Debian/rpm package and run for the first time, the memory module displays the following error message, 

*“Memory access fault by GPU node-<x> (Agent handle: 0xa55170) on address 0x7fc268c00000. Reason: Page not present or supervisor privilege.
Aborted (core dumped).”*

As a workaround, run the test again. Subsequent runs appear to fix the error.

**NOTE**: The error may appear after a system reboot. Run the test again to fix the issue.  

Note, reinstallation of ROCm Validation Suite is not required. 



Deprecations
-------------------

This section describes deprecations and removals in AMD ROCm.

**WARNING: COMPILER-GENERATED CODE OBJECT VERSION 2 DEPRECATION**

Compiler-generated code object version 2 is no longer supported and will be removed shortly. AMD ROCm users must plan for the code object version 2 deprecation immediately. 

Support for loading code object version 2 is also being deprecated with no announced removal release.


Deploying ROCm
-------------------

AMD hosts both Debian and RPM repositories for the ROCm v3.9.x packages.

For more information on ROCM installation on all platforms, see

https://rocmdocs.amd.com/en/latest/Installation_Guide/Installation-Guide.html



DISCLAIMER 
----------------
The information contained herein is for informational purposes only, and is subject to change without notice. In addition, any stated support is planned and is also subject to change. While every precaution has been taken in the preparation of this document, it may contain technical inaccuracies, omissions and typographical errors, and AMD is under no obligation to update or otherwise correct this information. Advanced Micro Devices, Inc. makes no representations or warranties with respect to the accuracy or completeness of the contents of this document, and assumes no liability of any kind, including the implied warranties of noninfringement, merchantability or fitness for particular purposes, with respect to the operation or use of AMD hardware, software or other products described herein. No license, including implied or arising by estoppel, to any intellectual property rights is granted by this document. Terms and limitations applicable to the purchase or use of AMD’s products are as set forth in a signed agreement between the parties or in AMD's Standard Terms and Conditions of Sale.
AMD, the AMD Arrow logo, Radeon, Ryzen, Epyc, and combinations thereof are trademarks of Advanced Micro Devices, Inc.  
Google®  is a registered trademark of Google LLC.
PCIe® is a registered trademark of PCI-SIG Corporation.
Linux is the registered trademark of Linus Torvalds in the U.S. and other countries.
Ubuntu and the Ubuntu logo are registered trademarks of Canonical Ltd.
Other product names used in this publication are for identification purposes only and may be trademarks of their respective companies.






AMD ROCm Version History
-----------------------------

This file contains archived version history information for the ROCm project.

New features and enhancements in ROCm v3.8
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Release Notes: https://github.com/RadeonOpenCompute/ROCm/tree/roc-3.8.x

- Hipfort-Interface for GPU Kernel Libraries

- ROCm Data Center Tool

- Error-Correcting Code Fields in ROCm Data Center Tool

- Static Linking Libraries

New features and enhancements in ROCm v3.7
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Release Notes: https://github.com/RadeonOpenCompute/ROCm/tree/roc-3.7.x

- AOMP Enhancements

- Compatibility with NVIDIA Communications Collective Library v2.7 API

- Singular Value Decomposition of Bi-diagonal Matrices

- rocSPARSE_gemmi() Operations for Sparse Matrices



Patch Release -  ROCm v3.5.1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

AMD ROCm released a maintenance patch release v3.5.1. For more information about the release see,

Release Notes: https://github.com/RadeonOpenCompute/ROCm/tree/roc-3.5.1


New features and enhancements in ROCm v3.5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Release Notes: https://github.com/RadeonOpenCompute/ROCm/tree/roc-3.5.0

**rocProf Command Line Tool Python Requirement**
SQLite3 is a required Python module for the rocprof command-line tool. You can install the SQLite3 Python module using the pip utility and set env var ROCP_PYTHON_VERSION to the Python version, which includes the SQLite3 module.

**Heterogeneous-Compute Interface for Portability**
In this release, the Heterogeneous Compute Compiler (HCC) compiler is deprecated and the HIP-Clang compiler is introduced for compiling Heterogeneous-Compute Interface for Portability (HIP) programs.

**Radeon Open Compute Common Language Runtime**
In this release, the HIP runtime API is implemented on top of Radeon Open Compute Common Language Runtime (ROCclr). ROCclr is an abstraction layer that provides the ability to interact with different runtime backends such as ROCr.

**OpenCL Runtime**
The following OpenCL runtime changes are made in this release:

-AMD ROCm OpenCL Runtime extends support to OpenCL2.2
-The developer branch is changed from master to master-next

**AMD ROCm GNU Debugger (ROCgdb)**
The AMD ROCm Debugger (ROCgdb) is the AMD ROCm source-level debugger for Linux based on the GNU Debugger (GDB). It enables heterogeneous debugging on the AMD ROCm platform of an x86-based host architecture along with AMD GPU architectures and supported by the AMD Debugger API Library (ROCdbgapi).

**AMD ROCm Debugger API Library**
The AMD ROCm Debugger API Library (ROCdbgapi) implements an AMD GPU debugger application programming interface (API) that provides the support necessary for a client of the library to control the execution and inspect the state of AMD GPU devices.

**rocProfiler Dispatch Callbacks Start Stop API**
In this release, a new rocprofiler start/stop API is added to enable/disable GPU kernel HSA dispatch callbacks. The callback can be registered with the 'rocprofiler_set_hsa_callbacks' API. The API helps you eliminate some profiling performance impact by invoking the profiler only for kernel dispatches of interest. This optimization will result in significant performance gains.

**ROCm Communications Collective Library**
The ROCm Communications Collective Library (RCCL) consists of the following enhancements:

-Re-enable target 0x803
-Build time improvements for the HIP-Clang compiler

**NVIDIA Communications Collective Library Version Compatibility**
AMD RCCL is now compatible with NVIDIA Communications Collective Library (NCCL) v2.6.4 and provides the following features:

Network interface improvements with API v3
Network topology detection
Improved CPU type detection
Infiniband adaptive routing support

**MIOpen Optional Kernel Package Installation**
MIOpen provides an optional pre-compiled kernel package to reduce startup latency.

**New SMI Event Interface and Library**
An SMI event interface is added to the kernel and ROCm SMI lib for system administrators to get notified when specific events occur. On the kernel side, AMDKFD_IOC_SMI_EVENTS input/output control is enhanced to allow notifications propagation to user mode through the event channel.

**API for CPU Affinity**
A new API is introduced for aiding applications to select the appropriate memory node for a given accelerator(GPU).

**Radeon Performance Primitives Library**
The new Radeon Performance Primitives (RPP) library is a comprehensive high-performance computer vision library for AMD (CPU and GPU) with the HIP and OpenCL backend. The target operating system is Linux.


New features and enhancements in ROCm v3.3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Release Notes: https://github.com/RadeonOpenCompute/ROCm/tree/roc-3.3.0

**Multi-Version Installation**
Users can install and access multiple versions of the ROCm toolkit simultaneously. Previously, users could install only a single version of the ROCm toolkit.

**GPU Process Information**
A new functionality to display process information for GPUs is available in this release. For example, you can view the process details to determine if the GPU(s) must be reset.

**Support for 3D Pooling Layers**
AMD ROCm is enhanced to include support for 3D pooling layers. The implementation of 3D pooling layers now allows users to run 3D convolutional networks, such as ResNext3D, on AMD Radeon Instinct GPUs.

**ONNX Enhancements**
Open Neural Network eXchange (ONNX) is a widely-used neural net exchange format. The AMD model compiler & optimizer support the pre-trained models in ONNX, NNEF, & Caffe formats. Currently, ONNX versions 1.3 and below are supported.


New features and enhancements in ROCm v3.2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This release was not productized.


New features and enhancements in ROCm v3.1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

'Release Notes: https://github.com/RadeonOpenCompute/ROCm/tree/roc-3.1.0

**Change in ROCm Installation Directory Structure**

A fresh installation of the ROCm toolkit installs the packages in the /opt/rocm-<version> folder. 
Previously, ROCm toolkit packages were installed in the /opt/rocm folder.

**Reliability, Accessibility, and Serviceability Support for Vega 7nm**

The Reliability, Accessibility, and Serviceability (RAS) support for Vega7nm is now available. 

**SLURM Support for AMD GPU**

SLURM (Simple Linux Utility for Resource Management) is an open source, fault-tolerant, and highly scalable cluster management and job scheduling system for large and small Linux clusters. 


New features and enhancements in ROCm v3.0
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Release Notes: https://github.com/RadeonOpenCompute/ROCm/tree/roc-3.0.0

* Support for CentOS RHEL v7.7
* Support is extended for CentOS/RHEL v7.7 in the ROCm v3.0 release. For more information about the CentOS/RHEL v7.7 release, see:

* CentOS/RHEL

* Initial distribution of AOMP 0.7-5 in ROCm v3.0
The code base for this release of AOMP is the Clang/LLVM 9.0 sources as of October 8th, 2019. The LLVM-project branch used to build this release is AOMP-191008. It is now locked. With this release, an artifact tarball of the entire source tree is created. This tree includes a Makefile in the root directory used to build AOMP from the release tarball. You can use Spack to build AOMP from this source tarball or build manually without Spack.

* Fast Fourier Transform Updates
The Fast Fourier Transform (FFT) is an efficient algorithm for computing the Discrete Fourier Transform. Fast Fourier transforms are used in signal processing, image processing, and many other areas. The following real FFT performance change is made in the ROCm v3.0 release:

* Implement efficient real/complex 2D transforms for even lengths.

Other improvements:

• More 2D test coverage sizes.

• Fix buffer allocation error for large 1D transforms.

• C++ compatibility improvements.

MemCopy Enhancement for rocProf
In the v3.0 release, the rocProf tool is enhanced with an additional capability to dump asynchronous GPU memcopy information into a .csv file. You can use the '-hsa-trace' option to create the results_mcopy.csv file. Future enhancements will include column labels.

New features and enhancements in ROCm v2.10
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rocBLAS Support for Complex GEMM

The rocBLAS library is a gpu-accelerated implementation of the standard Basic Linear Algebra Subroutines (BLAS). rocBLAS is designed to enable you to develop algorithms, including high performance computing, image analysis, and machine learning.

In the AMD ROCm release v2.10, support is extended to the General Matrix Multiply (GEMM) routine for multiple small matrices processed simultaneously for rocBLAS in AMD Radeon Instinct MI50. Both single and double precision, CGEMM and ZGEMM, are now supported in rocBLAS.

Support for SLES 15 SP1

In the AMD ROCm v2.10 release, support is added for SUSE Linux® Enterprise Server (SLES) 15 SP1. SLES is a modular operating system for both multimodal and traditional IT.

Code Marker Support for rocProfiler and rocTracer Libraries

Code markers provide the external correlation ID for the calling thread. This function indicates that the calling thread is entering and leaving an external API region.

New features and enhancements in ROCm 2.9
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Initial release for Radeon Augmentation Library(RALI)

The AMD Radeon Augmentation Library (RALI) is designed to efficiently decode and process images from a variety of storage formats and modify them through a processing graph programmable by the user. RALI currently provides C API.

Quantization in MIGraphX v0.4

MIGraphX 0.4 introduces support for fp16 and int8 quantization. For additional details, as well as other new MIGraphX features, see MIGraphX documentation.

rocSparse csrgemm

csrgemm enables the user to perform matrix-matrix multiplication with two sparse matrices in CSR format.

Singularity Support

ROCm 2.9 adds support for Singularity container version 2.5.2.

Initial release of rocTX

ROCm 2.9 introduces rocTX, which provides a C API for code markup for performance profiling. This initial release of rocTX supports annotation of code ranges and ASCII markers. 

* Added support for Ubuntu 18.04.3
* Ubuntu 18.04.3 is now supported in ROCm 2.9.

New features and enhancements in ROCm 2.8
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Support for NCCL2.4.8 API

Implements ncclCommAbort() and ncclCommGetAsyncError() to match the NCCL 2.4.x API

New features and enhancements in ROCm 2.7.2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This release is a hotfix for ROCm release 2.7.

Issues fixed in ROCm 2.7.2
~~~~~~~~~~~~~~~~~~~~~~~~~~~

* A defect in upgrades from older ROCm releases has been fixed.
* rocprofiler --hiptrace and --hsatrace fails to load roctracer library
* In ROCm 2.7.2, rocprofiler --hiptrace and --hsatrace fails to load roctracer library defect has been fixed.
* To generate traces, please provide directory path also using the parameter: -d <$directoryPath> for example:

/opt/rocm/bin/rocprof  --hsa-trace -d $PWD/traces /opt/rocm/hip/samples/0_Intro/bit_extract/bit_extract
All traces and results will be saved under $PWD/traces path

Upgrading from ROCm 2.7 to 2.7.2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To upgrade, please remove 2.7 completely as specified for ubuntu or for centos/rhel, and install 2.7.2 as per instructions install instructions

Other notes
To use rocprofiler features, the following steps need to be completed before using rocprofiler:

Step-1: Install roctracer
Ubuntu 16.04 or Ubuntu 18.04:
sudo apt install roctracer-dev
CentOS/RHEL 7.6:
sudo yum install roctracer-dev

Step-2: Add /opt/rocm/roctracer/lib to LD_LIBRARY_PATH
New features and enhancements in ROCm 2.7
[rocFFT] Real FFT Functional
Improved real/complex 1D even-length transforms of unit stride. Performance improvements of up to 4.5x are observed. Large problem sizes should see approximately 2x.

rocRand Enhancements and Optimizations

Added support for new datatypes: uchar, ushort, half.

Improved performance on "Vega 7nm" chips, such as on the Radeon Instinct MI50

mtgp32 uniform double performance changes due generation algorithm standardization. Better quality random numbers now generated with 30% decrease in performance

Up to 5% performance improvements for other algorithms

RAS

Added support for RAS on Radeon Instinct MI50, including:

* Memory error detection
* Memory error detection counter
* ROCm-SMI enhancements
* Added ROCm-SMI CLI and LIB support for FW version, compute running processes, utilization rates, utilization counter, link error counter, and unique ID.

New features and enhancements in ROCm 2.6
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ROCmInfo enhancements

ROCmInfo was extended to do the following: For ROCr API call errors including initialization determine if the error could be explained by:

ROCk (driver) is not loaded / available
User does not have membership in appropriate group - "video"
If not above print the error string that is mapped to the returned error code
If no error string is available, print the error code in hex
Thrust - Functional Support on Vega20

ROCm2.6 contains the first official release of rocThrust and hipCUB. rocThrust is a port of thrust, a parallel algorithm library. hipCUB is a port of CUB, a reusable software component library. Thrust/CUB has been ported to the HIP/ROCm platform to use the rocPRIM library. The HIP ported library works on HIP/ROCm platforms.

Note: rocThrust and hipCUB library replaces https://github.com/ROCmSoftwarePlatform/thrust (hip-thrust), i.e. hip-thrust has been separated into two libraries, rocThrust and hipCUB. Existing hip-thrust users are encouraged to port their code to rocThrust and/or hipCUB. Hip-thrust will be removed from official distribution later this year.

MIGraphX v0.3

MIGraphX optimizer adds support to read models frozen from Tensorflow framework. Further details and an example usage at https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/wiki/Getting-started:-using-the-new-features-of-MIGraphX-0.3

MIOpen 2.0

This release contains several new features including an immediate mode for selecting convolutions, bfloat16 support, new layers, modes, and algorithms.

MIOpenDriver, a tool for benchmarking and developing kernels is now shipped with MIOpen. BFloat16 now supported in HIP requires an updated rocBLAS as a GEMM backend.

Immediate mode API now provides the ability to quickly obtain a convolution kernel.

MIOpen now contains HIP source kernels and implements the ImplicitGEMM kernels. This is a new feature and is currently disabled by default. Use the environmental variable "MIOPEN_DEBUG_CONV_IMPLICIT_GEMM=1" to activation this feature. ImplicitGEMM requires an up to date HIP version of at least 1.5.9211.

A new "loss" catagory of layers has been added, of which, CTC loss is the first. See the API reference for more details. 2.0 is the last release of active support for gfx803 architectures. In future releases, MIOpen will not actively debug and develop new features specifically for gfx803.

System Find-Db in memory cache is disabled by default. Please see build instructions to enable this feature. Additional documentation can be found here: https://rocmsoftwareplatform.github.io/MIOpen/doc/html/

Bloat16 software support in rocBLAS/Tensile

Added mixed precision bfloat16/IEEE f32 to gemm_ex. The input and output matrices are bfloat16. All arithmetic is in IEEE f32.

AMD Infinity Fabric™ Link enablement

The ability to connect four Radeon Instinct MI60 or Radeon Instinct MI50 boards in two hives or two Radeon Instinct MI60 or Radeon Instinct MI50 boards in four hives via AMD Infinity Fabric™ Link GPU interconnect technology has been added.

ROCm-smi features and bug fixes

mGPU & Vendor check

Fix clock printout if DPM is disabled

Fix finding marketing info on CentOS

Clarify some error messages

ROCm-smi-lib enhancements

Documentation updates

Improvements to *name_get functions

RCCL2 Enablement

RCCL2 supports collectives intranode communication using PCIe, Infinity Fabric™, and pinned host memory, as well as internode communication using Ethernet (TCP/IP sockets) and Infiniband/RoCE (Infiniband Verbs). Note: For Infiniband/RoCE, RDMA is not currently supported.

rocFFT enhancements

Added: Debian package with FFT test, benchmark, and sample programs
Improved: hipFFT interfaces
Improved: rocFFT CPU reference code, plan generation code and logging code

New features and enhancements in ROCm 2.5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

UCX 1.6 support

Support for UCX version 1.6 has been added.

BFloat16 GEMM in rocBLAS/Tensile

Software support for BFloat16 on Radeon Instinct MI50, MI60 has been added. This includes:

Mixed precision GEMM with BFloat16 input and output matrices, and all arithmetic in IEEE32 bit

Input matrix values are converted from BFloat16 to IEEE32 bit, all arithmetic and accumulation is IEEE32 bit. Output values are rounded from IEEE32 bit to BFloat16

Accuracy should be correct to 0.5 ULP

ROCm-SMI enhancements

CLI support for querying the memory size, driver version, and firmware version has been added to ROCm-smi.

[PyTorch] multi-GPU functional support (CPU aggregation/Data Parallel)

Multi-GPU support is enabled in PyTorch using Dataparallel path for versions of PyTorch built using the 06c8aa7a3bbd91cda2fd6255ec82aad21fa1c0d5 commit or later.

rocSparse optimization on Radeon Instinct MI50 and MI60

This release includes performance optimizations for csrsv routines in the rocSparse library.

[Thrust] Preview

Preview release for early adopters. rocThrust is a port of thrust, a parallel algorithm library. Thrust has been ported to the HIP/ROCm platform to use the rocPRIM library. The HIP ported library works on HIP/ROCm platforms.

Note: This library will replace https://github.com/ROCmSoftwarePlatform/thrust in a future release. The package for rocThrust (this library) currently conflicts with version 2.5 package of thrust. They should not be installed together.

Support overlapping kernel execution in same HIP stream

HIP API has been enhanced to allow independent kernels to run in parallel on the same stream.

AMD Infinity Fabric™ Link enablement

The ability to connect four Radeon Instinct MI60 or Radeon Instinct MI50 boards in one hive via AMD Infinity Fabric™ Link GPU interconnect technology has been added.

New features and enhancements in ROCm 2.4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

TensorFlow 2.0 support

ROCm 2.4 includes the enhanced compilation toolchain and a set of bug fixes to support TensorFlow 2.0 features natively

AMD Infinity Fabric™ Link enablement

ROCm 2.4 adds support to connect two Radeon Instinct MI60 or Radeon Instinct MI50 boards via AMD Infinity Fabric™ Link GPU interconnect technology.

New features and enhancements in ROCm 2.3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Mem usage per GPU

Per GPU memory usage is added to rocm-smi. Display information regarding used/total bytes for VRAM, visible VRAM and GTT, via the --showmeminfo flag

MIVisionX, v1.1 - ONNX

ONNX parser changes to adjust to new file formats

MIGraphX, v0.2

MIGraphX 0.2 supports the following new features:

New Python API

* Support for additional ONNX operators and fixes that now enable a large set of Imagenet models
* Support for RNN Operators
* Support for multi-stream Execution
* [Experimental] Support for Tensorflow frozen protobuf files

See: Getting-started:-using-the-new-features-of-MIGraphX-0.2 for more details

MIOpen, v1.8 - 3d convolutions and int8

This release contains full 3-D convolution support and int8 support for inference.
Additionally, there are major updates in the performance database for major models including those found in Torchvision.
See: MIOpen releases

Caffe2 - mGPU support

Multi-gpu support is enabled for Caffe2.

rocTracer library, ROCm tracing API for collecting runtimes API and asynchronous GPU activity traces
HIP/HCC domains support is introduced in rocTracer library.

BLAS - Int8 GEMM performance, Int8 functional and performance
Introduces support and performance optimizations for Int8 GEMM, implements TRSV support, and includes improvements and optimizations with Tensile.

Prioritized L1/L2/L3 BLAS (functional)
Functional implementation of BLAS L1/L2/L3 functions

BLAS - tensile optimization
Improvements and optimizations with tensile

MIOpen Int8 support
Support for int8

New features and enhancements in ROCm 2.2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rocSparse Optimization on Vega20
Cache usage optimizations for csrsv (sparse triangular solve), coomv (SpMV in COO format) and ellmv (SpMV in ELL format) are available.

DGEMM and DTRSM Optimization
Improved DGEMM performance for reduced matrix sizes (k=384, k=256)

Caffe2
Added support for multi-GPU training

New features and enhancements in ROCm 2.1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

RocTracer v1.0 preview release – 'rocprof' HSA runtime tracing and statistics support -
Supports HSA API tracing and HSA asynchronous GPU activity including kernels execution and memory copy

Improvements to ROCM-SMI tool -
Added support to show real-time PCIe bandwidth usage via the -b/--showbw flag

DGEMM Optimizations -
Improved DGEMM performance for large square and reduced matrix sizes (k=384, k=256)

New features and enhancements in ROCm 2.0
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Adds support for RHEL 7.6 / CentOS 7.6 and Ubuntu 18.04.1

Adds support for Vega 7nm, Polaris 12 GPUs

Introduces MIVisionX
A comprehensive computer vision and machine intelligence libraries, utilities and applications bundled into a single toolkit.
Improvements to ROCm Libraries
rocSPARSE & hipSPARSE
rocBLAS with improved DGEMM efficiency on Vega 7nm

MIOpen
This release contains general bug fixes and an updated performance database
Group convolutions backwards weights performance has been improved

RNNs now support fp16
Tensorflow multi-gpu and Tensorflow FP16 support for Vega 7nm
TensorFlow v1.12 is enabled with fp16 support
PyTorch/Caffe2 with Vega 7nm Support

fp16 support is enabled

Several bug fixes and performance enhancements

Known Issue: breaking changes are introduced in ROCm 2.0 which are not addressed upstream yet. Meanwhile, please continue to use ROCm fork at https://github.com/ROCmSoftwarePlatform/pytorch

Improvements to ROCProfiler tool

Support for Vega 7nm

Support for hipStreamCreateWithPriority

Creates a stream with the specified priority. It creates a stream on which enqueued kernels have a different priority for execution compared to kernels enqueued on normal priority streams. The priority could be higher or lower than normal priority streams.

OpenCL 2.0 support

ROCm 2.0 introduces full support for kernels written in the OpenCL 2.0 C language on certain devices and systems.  Applications can detect this support by calling the “clGetDeviceInfo” query function with “parame_name” argument set to “CL_DEVICE_OPENCL_C_VERSION”.  

In order to make use of OpenCL 2.0 C language features, the application must include the option “-cl-std=CL2.0” in options passed to the runtime API calls responsible for compiling or building device programs.  The complete specification for the OpenCL 2.0 C language can be obtained using the following link: https://www.khronos.org/registry/OpenCL/specs/opencl-2.0-openclc.pdf

Improved Virtual Addressing (48 bit VA) management for Vega 10 and later GPUs

Fixes Clang AddressSanitizer and potentially other 3rd-party memory debugging tools with ROCm

Small performance improvement on workloads that do a lot of memory management

Removes virtual address space limitations on systems with more VRAM than system memory
Kubernetes support

New features and enhancements in ROCm 1.9.2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

RDMA(MPI) support on Vega 7nm

Support ROCnRDMA based on Mellanox InfiniBand

Improvements to HCC

Improved link time optimization

Improvements to ROCProfiler tool

General bug fixes and implemented versioning APIs

New features and enhancements in ROCm 1.9.2

RDMA(MPI) support on Vega 7nm

Support ROCnRDMA based on Mellanox InfiniBand

Improvements to HCC

Improved link time optimization

Improvements to ROCProfiler tool

General bug fixes and implemented versioning APIs

Critical bug fixes

New features and enhancements in ROCm 1.9.1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Added DPM support to Vega 7nm

Dynamic Power Management feature is enabled on Vega 7nm.

Fix for 'ROCm profiling' that used to fail with a “Version mismatch between HSA runtime and libhsa-runtime-tools64.so.1” error

New features and enhancements in ROCm 1.9.0
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Preview for Vega 7nm
Enables developer preview support for Vega 7nm

System Management Interface
Adds support for the ROCm SMI (System Management Interface) library, which provides monitoring and management capabilities for AMD GPUs.

Improvements to HIP/HCC
Support for gfx906

Added deprecation warning for C++AMP. This will be the last version of HCC supporting C++AMP.

Improved optimization for global address space pointers passing into a GPU kernel

Fixed several race conditions in the HCC runtime

Performance tuning to the unpinned copy engine

Several codegen enhancement fixes in the compiler backend

Preview for rocprof Profiling Tool

Developer preview (alpha) of profiling tool rocProfiler. It includes a command-line front-end, rpl_run.sh, which enables:

Cmd-line tool for dumping public per kernel perf-counters/metrics and kernel timestamps

Input file with counters list and kernels selecting parameters

Multiple counters groups and app runs supported

Output results in CSV format

The tool can be installed from the rocprofiler-dev package. It will be installed into: /opt/rocm/bin/rpl_run.sh

Preview for rocr Debug Agent rocr_debug_agent

The ROCr Debug Agent is a library that can be loaded by ROCm Platform Runtime to provide the following functionality:

Print the state for wavefronts that report memory violation or upon executing a "s_trap 2" instruction.
Allows SIGINT (ctrl c) or SIGTERM (kill -15) to print wavefront state of aborted GPU dispatches.
It is enabled on Vega10 GPUs on ROCm1.9.
The ROCm1.9 release will install the ROCr Debug Agent library at /opt/rocm/lib/librocr_debug_agent64.so

New distribution support
Binary package support for Ubuntu 18.04
ROCm 1.9 is ABI compatible with KFD in upstream Linux kernels.
Upstream Linux kernels support the following GPUs in these releases: 4.17: Fiji, Polaris 10, Polaris 11 4.18: Fiji, Polaris 10, Polaris 11, Vega10

Some ROCm features are not available in the upstream KFD:

More system memory available to ROCm applications
Interoperability between graphics and compute
RDMA
IPC
To try ROCm with an upstream kernel, install ROCm as normal, but do not install the rock-dkms package. Also add a udev rule to control /dev/kfd permissions:

    echo 'SUBSYSTEM=="kfd", KERNEL=="kfd", TAG+="uaccess", GROUP="video"' | sudo tee /etc/udev/rules.d/70-kfd.rules
    
New features as of ROCm 1.8.3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ROCm 1.8.3 is a minor update meant to fix compatibility issues on Ubuntu releases running kernel 4.15.0-33

New features as of ROCm 1.8
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

DKMS driver installation

Debian packages are provided for DKMS on Ubuntu

RPM packages are provided for CentOS/RHEL 7.4 and 7.5

See the ROCT-Thunk-Interface and ROCK-Kernel-Driver for additional documentation on driver setup

New distribution support

Binary package support for Ubuntu 16.04 and 18.04

Binary package support for CentOS 7.4 and 7.5

Binary package support for RHEL 7.4 and 7.5

Improved OpenMPI via UCX support

UCX support for OpenMPI

ROCm RDMA

New Features as of ROCm 1.7
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

DKMS driver installation

New driver installation uses Dynamic Kernel Module Support (DKMS)

Only amdkfd and amdgpu kernel modules are installed to support AMD hardware

Currently only Debian packages are provided for DKMS (no Fedora suport available)

See the ROCT-Thunk-Interface and ROCK-Kernel-Driver for additional documentation on driver setup

New Features as of ROCm 1.5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Developer preview of the new OpenCL 1.2 compatible language runtime and compiler

OpenCL 2.0 compatible kernel language support with OpenCL 1.2 compatible runtime

Supports offline ahead of time compilation today; during the Beta phase we will add in-process/in-memory compilation.

Binary Package support for Ubuntu 16.04

Binary Package support for Fedora 24 is not currently available

Dropping binary package support for Ubuntu 14.04, Fedora 23

IPC support
                 



DISCLAIMER 
===========
The information contained herein is for informational purposes only and is subject to change without notice. While every precaution has been taken in the preparation of this document, it may contain technical inaccuracies, omissions and typographical errors, and AMD is under no obligation to update or otherwise correct this information.  Advanced Micro Devices, Inc. makes no representations or warranties with respect to the accuracy or completeness of the contents of this document, and assumes no liability of any kind, including the implied warranties of noninfringement, merchantability or fitness for particular purposes, with respect to the operation or use of AMD hardware, software or other products described herein.  No license, including implied or arising by estoppel, to any intellectual property rights is granted by this document.  Terms and limitations applicable to the purchase or use of AMD’s products are as set forth in a signed agreement between the parties or in AMD’s Standard Terms and Conditions of Sale. S
AMD, the AMD Arrow logo, Radeon, Ryzen, Epyc, and combinations thereof are trademarks of Advanced Micro Devices, Inc.  
Google®  is a registered trademark of Google LLC.
PCIe® is a registered trademark of PCI-SIG Corporation.
Linux is the registered trademark of Linus Torvalds in the U.S. and other countries.
Ubuntu and the Ubuntu logo are registered trademarks of Canonical Ltd.
Other product names used in this publication are for identification purposes only and may be trademarks of their respective companies.

