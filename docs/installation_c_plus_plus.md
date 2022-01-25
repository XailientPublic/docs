# C++ Installation

!!! note      
      If your local machines doesn't meet the requirements for native installation we also offer Docker [Containers as a deployment option](https://xailient-docs.readthedocs.io/en/latest/container.html).

### Installing C++ SDK

!!! note

    If you are installing Python SDK, please refer to this [section](https://xailient-docs.readthedocs.io/en/latest/installation_python.html).


## Install XailientSDK

__Download C++ SDK__

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

__Install C++ SDK__

##### Install using downloaded SDK file

1. Unzip the downloaded SDK.

2. 'cd' into the unzipped SDK folder.

3. Add this line in bashrc to avoid configuring everytime you login using shell.

    ```
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$(pwd)/lib/
    ```

4. Go to script directory 

    ```
    cd scripts
    ```

5. Run xailient-install script

    ```
    ./xailient-install
    ```

6. Go back to root xailient directory 
    
    ```
    cd ..
    ```


__Xailient SDK contents__

```bash
(env) $ ls
```

* bin/ -- Executables required for initial registration
* data/ -- Image files you can use with the sample applications
* samples/ -- Sample application demonstrating how the Xailient SDK library can be used
* scripts/ -- Installation script to install xailient-agent
* example/  -- Sample applications demonstrating how the Xailient Face Detector library can be used
* lib/      -- Xailient detector shared Library 
* include/  -- Header files to include in your application


## Run sample code

Go to __samples__ folder. This folder contains a sample script named "image_ref" that demonstrates how to use the xailient sdk. 

The script reads an image named "beatles.jpg" from __data__ folder, runs the detection sdk on this image and saves output to "output/output.jpg".

Now run the sample script.

```bash
(env) $ cd example
(env) $ mkdir output
(env) $ ./image_ref -f ../data/beatles.jpg
(env) $ file output/output.jpg
```

'output/output.jpg' will contain any predicted bounding boxes drawn. '../data/beatles.jpg' is useful for showing the results of an SDK trained to do face detection. So if you don't see any bounding boxes drawn then try running './image_ref -f <<<path to your image>>>' with an image from your dataset.


Input Image | Output Image
:-------------------------:|:-------------------------:
![](../latest/img/x86_64/beatles.jpg)   |  ![](../latest/img/x86_64/beatles_output.jpg)
