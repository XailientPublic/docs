# FAQs

### 1. I'm getting _"Connection Failed"_ error when running the SDK. How do I resolve this?

Network manager might have restarted, causing Xailient daemon to terminate. 

__Solution:__ Ensure that you are connected to the internet. Manually start the Xailient daemon using the following command:

```bash
$ sudo systemctl start xailient
```

### 2. I'm getting _"undefined symbol: __atomic_fetch_add_8"_ error when running the SDK. What should I do?

__Solution:__ Install the correct version of OpenCV contrib.

```bash
$ python3.7 -m pip install opencv-contrib-python==4.1.0.25
```

If you still face this issue, add __LD_PRELOAD=/usr/lib/arm-linux-gnueabihf/libatomic.so.1__ to bash.rc file in the Pi.

```bash
$ export LD_PRELOAD=/usr/lib/arm-linux-gnueabihf/libatomic.so.1

```

### 3. I'm getting "ImportError: libcblas.so.3: cannot open shared object file: No such file or directory"

Some of the required libraries maybe missing on your device. 

__Solution:__ Install the following dependencies:

* libjasper-dev 
* libqtgui4 
* libqt4-test 
* libatlas-base-dev

Use the following command:

```bash
$ sudo apt-get install libjasper-dev libqtgui4 libqt4-test libatlas-base-dev
```

### 4. I'm getting _"Dnn.detector not found (AttributeError: module 'dnn' has no attribute 'Detector')"_ error when running hte SDK. What do I do?

You will get this error if you had previously installed the Xailient Face SDK on this device and even when you installed the latest version of the SDK using pip install, the code is still refering back to the older version.

__Solution:__ Remove dnn.so and xailient.so from previous installation and then install new version of the SDK again.

To list all "xailient.so" files, use the following command:

```bash
$ sudo find / -type f -name "xailient.so"
```

To remove the file, use the following command:

```bash
$ sudo rm "[file_path]/xailient.so"
```

Similarly, to list all "dnn.so" files, use the following command:
```bash
$ sudo find / -type f -name "dnn.so"
```

To remove the file, use the following command:

```bash
$ sudo rm "[file_path]/dnn.so"
```

### 5. I'm facing issues installing OpenCV on Raspberry Pi 3B+.

__Solution__: Raspberry Pi 3 needs some dependencies if it has a fresh raspbian OS for opencv-python to work. Install the following dependencies:

* libjasper-dev 
* libqtgui4 
* libqt4-test 
* libatlas-base-dev

Use the following command:

```bash
$ sudo apt-get install libjasper-dev libqtgui4 libqt4-test libatlas-base-dev
```

### 6. My model training failed.

If you’re model fails training, first thing you want to check the format of the labels file. Sometimes although the labels file passed the the Xailient Console sainity check, it might contain bad invalid data. 

For example, if your xmin column had "???" value in one of the columns, it might pass the sanity check, but the model training will fail.

### 7. I'm getting "ImportError: libboost_python-py37.so.1.62.0: cannot open shared object file: No such file or directory"

When activating the xailient license using command sudo ./xailient-install, you should have received a confirmation message asking where xailient-agent can copy the compiled Boost library files for you. If you typed in "yes" then there is no need to do it manually. 
If not, then you will have to setup it up manually.

__Solution__: To copy the Boost library files and update ldconfig, go to xailient installation folder and use the following command:

``` bash
sudo cp -r sharedLib /usr/lib/xailient
sudo sh -c "echo '/usr/lib/xailient' > /etc/ld.so.conf.d/xailient.conf"
sudo chmod +x /usr/lib/xailient/*
sudo ldconfig
```

### 8. I'm getting "error while loading shared libraries: libcurl.so.4: cannot open shared object file: No such file or directory"

Some of the required libraries maybe missing on your device. 

__Solution:__ Install the following dependencies:

``` bash
sudo apt-get install libcurl4 php-curl
```

### 9. I'm getting the error "Illegal instruction (core dumped)" when using python3.6 on Jetson Nano

There is a known [issue with numpy](https://github.com/numpy/numpy/issues/18131).

__Solution:__ Export the OPENBLAS_CORETYPE=ARMV8 env variable before running any python code

``` bash
export OPENBLAS_CORETYPE=ARMV8
```


