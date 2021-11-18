# Python Installation

!!! note      
      If your local machines doesn't meet the requirements for native installation we also offer Docker [Containers as a deployment option](https://xailient-docs.readthedocs.io/en/latest/container.html).

__Minimum software requirements:__

* Glibc 2.27
* Python >=3.6
* Pip
* VirtualEnv
* libcurl4 
* php-curl

If your device does not meet the minimum software required, please follow the instructions below to install them.


### Installing PYTHON SDK

!!! note

    If you are installing C++ SDK, please refer to this [section](https://xailient-docs.readthedocs.io/en/latest/installation_c_plus_plus.html).

__Download the package lists and update information__

```bash
$ sudo apt-get update
```

!!! note
    apt-get update to download the package lists from the repositories and "update" them to get information on the newest versions of packages and their dependencies. It will do this for all repositories and PPAs.

__Install python3__

The Xailient SDK works with python 3.6 or later. Here we install python 3.7 though you could install any version
of python >=3.6.

!!! note

     If you are using Jetson Nano and python3.6 there is an [issue with numpy](https://github.com/numpy/numpy/issues/18131)
     that can be solved using `export OPENBLAS_CORETYPE=ARMV8`

```bash
$ sudo apt-get install python3.7
```

__Install pip for python3__

```bash
$ sudo apt-get install python3-pip
```

__Install other required libraries__

```bash
$ sudo apt-get install libcurl4 php-curl
$ python3 -m pip install scikit-build
```

__Install VirtualEnv__

```bash
$ python3 -m pip install --user virtualenv
```

__Create a Virtual Environment (Recommended)__

Create a new python virtual environment to isolate package installation for the system.

```bash
$ python3 -m venv env
```

Activate the virtual environment.

Before you can start using the virtual environment for package installations, you will need to activate it. Activating a virtual environment will put the virtual environment-specific python and pip executables into your shell's PATH.

```bash
$ source env/bin/activate
```

To deactivate the virtual environment later,

```bash
(env) $ deactivate
```

## Install XailientSDK

__Get SDK Wheel Link__

Go to the Console and navigate to __MANAGE AI MODELS__. For the model you want to deploy, select the SDK you have build for your target platform. 

!!! note
    If you have not build an SDK yet, refer to __Build SDK__ section of the documentation.

Click on the <img src="../latest/img/console/AI Models/Copy.png" height=30 width=30> icon left side of the platform to copy the downlooad link.

<p align="center">
<img src="../latest/img/console/AI Models/PreTrainedModels-SDKBuilt-copy.png">
</p>

Click on the target platform for the model to download.

<p align="center">
<img src="../latest/img/console/AI Models/PreTrainedModels-SDKBuilt-downlaod.png">
</p>


__Install SDK Wheel__

##### Install using downloaded SDK wheel file

```bash
(env) $ python3 -m pip install <download_path/wheel_file_name>
```

##### Install using SDK link

```bash
(env) $ python3 -m pip install "<SDK WHEEL LINKs>"
```

!!! note
    Replace &lt;SDK WHEEL LINK&gt; with the SDK link you copied earlier from the console.

__Start the Xailient Daemon which activates your license__

```bash
(env) $ python3 -m xailient.install
```

That's it! You can now start using the Xailient SDK. If this is your first time using the Xailient
SDK then it may be helpful to read the remainder of this document.

__Info about the installed Xailient SDK__

```bash
(env) $ python3 -m pip show xailient
```

You can get information about the version of xailient sdk installed, support email address, and location of the installation. 

!!! note
    Keep note of the install location "Location" as you will need it in the steps below.

__Go to Xailient Installation Folder__

To go to xailient folder, use the following command. If you do not know the install location, please refer to __"Info about xailient sdk installed"__ section above.

```bash
(env) $ cd <Xailient Install Location>/xailient
```

__Xailient SDK contents__

```bash
(env) $ ls
```

* bin/ -- Executables required for initial registration
* data/ -- Image files you can use with the sample applications
* samples/ -- Sample application demonstrating how the Xailient SDK library can be used
* scripts/ -- License activation scripts
* sharedLib_x86_64/ --Sample models that can be installed or linked with your applications

## Run sample code

In the xailient folder of the install location, go to __samples__ folder. This folder contains a sample python script named "basic_sample.py" that demonstrates how to use the xailient sdk. 

The script reads an image named "beatles.jpg" from __data__ folder, runs the detection sdk on this image and saves output to "beatles_output.jpg" in the current working directory.

Now run the sample script.

```bash
(env) $ python3 -m xailient.samples.basic_sample
```

Input Image | Output Image
:-------------------------:|:-------------------------:
![](../latest/img/x86_64/beatles.jpg)   |  ![](../latest/img/x86_64/beatles_output.jpg)


## Update Xailient SDK Model

```bash
(env) $ python3 -m pip uninstall xailient
(env) $ python3 -m pip install "<new SDK WHEEL URL>"
```

When you install a new SDK with a different model using pip install, you do not need to run the license activation script again.

## Uninstall Xailient

Run the uninstallation script.

```bash
(env) $ python3 -m xailient.uninstall
```

Pip uninstall xailient

```bash
(env) $ python3 -m pip uninstall xailient
```

Note that any changes to the basic_sample.py python script will be overwritten so keep a backup if you intend to keep any changes.