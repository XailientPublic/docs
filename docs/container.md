<p align="center">
  <img src="../latest/img/container/docker_xailient.png">
</p>
<br>

While the Xailient SDK is designed to provide state of the art machine vision performance efficient enough to run on
low power IoT devices using technology inspired by human biology, we also offer a Docker container as an option to
deploy your trained models from your desktop.
This option is a great way to see the Xailient SDK in action using a desktop OS like Mac or Windows.

We recommend this option for users who don't have access to an IoT device or Linux VM, or that simply want to be able to use a Xailient SDK from their Mac or Windows computers.

## Build a customized Docker container

First, download and install Docker Desktop.

Next, you must ensure you have a trained model to use. You can either:

Use a pretrained model available in the Xailient console, OR
Train a custom model. To achieve this follow the steps at Training a model.

Next you will need to Build a Xailient SDK for your target device.

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

    To install Xailient SDK natively, please refer to [Native Installation section](https://xailient-docs.readthedocs.io/en/latest/installation.html)

The remaing of this document will take you through the process step by step.

### Download and Install Docker
1. Download Docker Desktop using this [link](https://www.docker.com/products/docker-desktop).
2. [Install Docker Desktop](https://docs.docker.com/get-docker/).

### Start docker
Ensure that the Docker Desktop app is running.

### Prepare the SDK

1. Make sure the SDK from the Xailient console is downloaded

2. Create any folder in the local machine (e.g Documents/Input), and put the downloaded SDK is this folder 

### Run the docker container
1. Open the Terminal, and go to the folder that have the sdk file (e.g cd Documents/Input)
2. Enter the command ls (To see the list of files in the folder).
3. Enter the following command (ensure the docker is opened):

```bash
docker run --rm -it -v $(pwd):/input python:3.7 bash
```

Ensure the next line should show the "root@&lt;numbers&gt;" this means that you are already in the container.
  
!!! note

    Note that the command above also will create the same folder "input" inside the container and also get the sdk file the same as the local machine. (Basically it's copying from the local machine to the container)

Then enter the command ls, to make sure the sdk file is in the input folder.

### Install XailientSDK

Once in the container, you can install the Xailient SDK and run it inside the container.

1. Run the following command to install the SDK 

```bash
python3.7 -m pip install <SDK file name>.whl 
#(e.g python3.7 -m pip install xailient-2.1.1-py3-none-linux_aarch64.whl )
```

!!! note

    Replace the SDK file name with your file name, or use * if you would like to run all files in the folder.

__Start the Xailient Daemon which activates your license__

```bash
python3 -m xailient.install
```

Once the installation is success, then run this command python3.7 -m xailient.install, and the following message will be displayed:

```bash
Registering device!  Thank you for being our customer...
```

That's it! You can now start using the Xailient SDK. If this is your first time using the Xailient
SDK then it may be helpful to read the remainder of this document.

__Info about the installed Xailient SDK__

Run the following command to show the Installed Xailient SDK information:

```bash
python3 -m pip show xailient
```

### Run sample code

Use the following command to run the sample script that comes along with Xailient SDK.

```bash
python3 -m xailient.samples.basic_sample
```

Input Image | Output Image
:-------------------------:|:-------------------------:
![](../latest/img/x86_64/beatles.jpg)   |  ![](../latest/img/x86_64/beatles_output.jpg)

Now on your working directory, you should see the beatles_output.jpg image file.

### Update Xailient SDK Model

```bash
python3 -m pip uninstall xailient
python3 -m pip install "<new SDK WHEEL URL>"
```

When you install a new SDK with a different model using pip install, you do not need to run the license activation script again.

### Uninstall Xailient

Run the uninstallation script.

```bash
python3 -m xailient.uninstall
```

Pip uninstall xailient

```bash
python3 -m pip uninstall xailient
```

Note that any changes to the basic_sample.py python script will be overwritten so keep a backup if you intend to keep any changes.