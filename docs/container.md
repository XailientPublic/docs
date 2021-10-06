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
Next you will need to Build a Xailient SDK and choose the x86-64 option.


The remaing of this document will take you through the process step by step.

### Download and Install Docker
1. Download Docker Desktop using this [link](https://www.docker.com/products/docker-desktop).
2. [Install Docker Desktop](https://docs.docker.com/get-docker/).

### Create docker files

You will need 2 files.
1. Dockerfile
2. docker-compose.yml

Let's create them.

1. Create a new folder and name it __XailientDocker__. This will be your working directory.

2. Create a file and name it __Dockerfile__. Add the following content to it and save it to your working directory.

filename: Dockerfile
```
FROM python:3.7

# This builds a docker container that can be used to run the integration tests for an SDK

RUN apt-get update && \
    apt-get install -y ffmpeg && \
    apt-get clean

RUN python3.7 -m pip install opencv-python

# set the working directory
WORKDIR "/app"
```

3. Create a file and name it __docker-compose.yml__. Add the following content to it and save it to your working directory.


filename: docker-compose.yml
```
version: '3'
services:
  app:
    build: .
    volumes:
      - .:/app

volumes:
  .:
```

### Start docker
Ensure that the Docker Desktop app is running.

### Run the docker container
To run the docker container, open terminal, go to your working directory and run enter the following command:

```bash
cd XailientDocker
docker-compose run --rm app bash
```

### Install XailientSDK

Once in the container, you can install the Xailient SDK and run it inside the container.

__Get SDK Wheel Link__

1. Go to the Console and navigate to __MANAGE AI MODELS__. For the model you want to deploy, select the SDK you have build for your target platform. 

    !!! note

        If you have not build an SDK yet, refer to __Build SDK__ section of the documentation. You need to select x86_64 as the target platform.

2. Click on the "COPY URL" icon left side of __X86_64 (Python)__ to copy the downlooad link.

<p align="center">
<img src="../latest/img/console/AI Models/PreTrainedModels-SDKBuilt-x86_64.png">

__Install SDK Wheel using SDK link__ 

```bash
python3 -m pip install "<SDK WHEEL LINKs>"
```

!!! note
    Replace &lt;SDK WHEEL LINK&gt; with the SDK link you copied earlier from the console.

__Start the Xailient Daemon which activates your license__

```bash
python3 -m xailient.install
```

That's it! You can now start using the Xailient SDK. If this is your first time using the Xailient
SDK then it may be helpful to read the remainder of this document.

__Info about the installed Xailient SDK__

```bash
python3 -m pip show xailient
```

### Run sample code

In the xailient folder of the install location, go to __samples__ folder. This folder contains a sample python script named "basic_sample.py" that demonstrates how to use the xailient sdk. 

The script reads an image named "beatles.jpg" from __data__ folder, runs the detection sdk on this image and saves output to "beatles_output.jpg" in the current working directory.

Now run the sample script.

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