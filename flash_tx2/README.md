# Flashing TX2
* Steps of Flashing
* Test installation

## Steps of Flashing TX2
1. Prepare a PC as host machine with Ubuntu 18.04 installed (>16.04 is recommended)
    * WARNING: VM might cause failures!
2. Download Jetpack 4.2 from [the website](https://developer.nvidia.com/embedded/jetpack-archive)
3. Install Sdkmanager
    * `sudo apt install ./sdkmanager_0.9.11-3405_amd64.deb`
    * or `sudo dkpg -i ./sdkmanager_0.9.11-3405_amd64.deb`
4. Open a terminal and type `sdkmanager` to start
    * login</br>
    <img src="img/login.jgp" width="300" height="200" />
    * Step1: choose target device to NVIDIA TX2</br>
    <img src="img/stap1.jgp" width="300" height="200" />
    * Step2: accept the terms and continue</br>
    <img src="img/stap2.jgp" width="300" height="200" />
    * Step3: downloading and manual setup TX2</br>
    <img src="img/stap3.jgp" width="300" height="200" /></br>
        1. Power-Off TX2 and reconnect the power adapter
        2. Press the POWER button
        3. Hold down the RECOVERY FORCE button
        4. Press and release the RESET button (while keep pressing the RECOVERY FORCE button)
        5. Wait 2 secs and release the RECOVERY FORCE button</br>
    * Step4: Flash to continue
5. Go to TX2 and set up the ubuntu
6. Back to sdkmanager and type your username and password you just setup on TX2</br>
    <img src="img/stap4.jgp" width="300" height="200" />
7. If there aren't error message, you are done!

## Test CUDA and cuDNN installation on TX2

* CUDA10.0

1. `cd /usr/local/cuda/bin`
2. `./cuda-install-smaples-10.0.sh ~`
3. `cd ~/NVIDIA_CUDA-10.0_Samples/`
4. `make -j4`
5. `cd bin/aarch64/linux/release`
6. `./oceanFFT`
There are many examples you can try.

* cuDNN
1. `cp -r /usr/src/cudnn_samples_v7/ ~`
2. `cd ~/cudnn_samples_v7/mnistCUDNN`
3. `make -j4`
4. `./mnistCUDNN`