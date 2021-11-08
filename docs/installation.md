# Native Installation

!!! note
      If your local machines doesn't meet the requirements for native installation we also offer Docker [Containers as a deployment option](https://xailient-docs.readthedocs.io/en/latest/container.html).

## Device Setup

To meet the minimum requirements, your device must be a x86_64, ARM32 or ARM64 architecture device. We've tested the following operating systems:

* Ubuntu 18.04 LTS
* Ubuntu 19.04
* Raspbian Buster 32-bit
* Raspbian Buster 64-bit

For ARM32, we have tested on the following device:

 * RaspberryPi 3B+
 * RaspberryPi 4B
 * RaspberryPi Zero (this using ARM32v6)

 For ARM64, we have tested:

 * RaspberryPi 4B
 * Jetson Nano

The table below recommends which target to choose for a few of the devices and operating systems:

Device | Operating System | Xailient SDK | Installation Type |
:-------------------------:|:-------------------------: | :-------------------------: | :-------------------------:
| MacBook with Intel Core i5 | Mac BigSur  | X86_64  | Docker only |
| MacBook with Apple M1 Chip | Mac BigSur | ARM64 | Docker only |
| Intel Core i7 | Ubuntu 18.04 | X86_64 | Native and/or Docker |
| Intel Core i7 | Ubuntu 19.04 | X86_64 | Native and/or Docker |
| Raspberry Pi 3B+ | Raspbian Buster OS 32 bit | ARM32 | Native and/or Docker |
| Raspberry Pi 4B | Raspbian Buster OS 32 bit | ARM32 | Native and/or Docker |
| Raspberry Pi 4B | Raspbian Buster OS 64 bit | ARM64 | Native and/or Docker |

!!! note

    To install Xailient SDK inside a docker container, please refer to [Docker Installation section](https://xailient-docs.readthedocs.io/en/latest/container.html)

## SDK Installation

Xailient SDKs are available in Python and C++.

### [Installation of Python SDK](https://xailient-docs.readthedocs.io/en/latest/installation_python.html)

### [Installation of C++ SDK](https://xailient-docs.readthedocs.io/en/latest/installation_c_plus_plus.html)
