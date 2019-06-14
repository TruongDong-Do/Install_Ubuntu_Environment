Install Java JDK 1.8
--------------------

1. cd /data/DATA/dependencies

2. mv jdk1.8.0_162/ /data/developments/

3. sudo update-alternatives --install "/usr/bin/java" "java" "/data/developments/jdk1.8.0_162/bin/java" 1

4. sudo update-alternatives --install "/usr/bin/javac" "javac" "/data/developments/jdk1.8.0_162/bin/javac" 1

5. sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/data/developments/jdk1.8.0_162/bin/javaws" 1

6. sudo update-alternatives --install "/usr/bin/jar" "jar" "/data/developments/jdk1.8.0_162/bin/jar" 1

7. sudo update-alternatives --install "/usr/bin/jps" "jps" "/data/developments/jdk1.8.0_162/bin/jps" 1

8. sudo update-alternatives --config java

9. sudo update-alternatives --config javac

10. sudo update-alternatives --config jar

11. sudo update-alternatives --config jps


PREREQUISITE
------------

1. sudo mkdir -p /data/developments

2. sudo chown tiennguyen:users -R  /data

3. sudo apt-get install build-essential

4. sudo apt-get install libbz2-dev

5. sudo apt-get install libssl-dev

6. sudo apt-get install libreadline-dev

7. sudo apt-get install libsqlite3-dev

8. sudo apt-get install tk-dev

9. sudo apt-get install libpng-dev

10. sudo apt-get install libfreetype6-dev

11. sudo apt-get install gnupg-curl

12. sudo apt-get install curl

13. echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list

14. curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -

15. sudo apt-get update && sudo apt-get install bazel

16. sudo apt-get install librdmacm-dev

17. sudo add-apt-repository ppa:graphics-drivers/ppa

18. sudo apt-get update

19. sudo apt-get install nvidia-387-dev

20. sudo apt-get install libjpeg-dev

Install CUDA 8.0 in Ubuntu 16.04
--------------------------------

1. sudo dpkg -i cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64.deb

2. sudo apt-key add /var/cuda-repo-8-0-local-ga2/7fa2af80.pub

3. sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub

4. sudo apt-get update

5. sudo apt-get install cuda


Install CUDA 9.1 in Ubuntu 16.04
--------------------------------

1. sudo apt-get update

2. sudo apt-get upgrade

3. sudo apt-get install linux-headers-4.10.0-28-generic

4. sudo dpkg -i cuda-repo-ubuntu1604-9-1-local_9.1.85-1_amd64.deb

5. sudo apt-key add /var/cuda-repo-9-1-local/7fa2af80.pub

6. sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub

7. sudo apt-get update

8. sudo apt-get install cuda

CUDA Post-Installation
~~~~~~~~~~~~~~~~~~~~~~

11. sudo /usr/bin/nvidia-persistenced --verbose

12. sudo mkdir /usr/lib/systemd/system

13. Adding the following contents to the file /usr/lib/systemd/system/nvidia-persistenced.service

.. sourcecode:: bash

    [Unit]
    Description=NVIDIA Persistence Daemon
    Wants=syslog.target

    [Service]
    Type=forking
    PIDFile=/var/run/nvidia-persistenced/nvidia-persistenced.pid
    Restart=always
    ExecStart=/usr/bin/nvidia-persistenced --verbose
    ExecStopPost=/bin/rm -rf /var/run/nvidia-persistenced

    [Install]
    WantedBy=multi-user.target

14. sudo systemctl enable nvidia-persistenced

15. In the file  /lib/udev/rules.d/40-vm-hotadd.rules

    Adding # to the line:

.. sourcecode:: bash

    SUBSYSTEM=="memory", ACTION=="add", DEVPATH=="/devices/system/memory/memory[0-9]*", TEST=="state", ATTR{state}="online"

16. sudo /usr/bin/nvidia-persistenced --verbose

17. sudo ln -s /usr/local/cuda/include/crt/math_functions.hpp /usr/local/cuda/include/math_functions.hpp

Install cudnn-8.0-linux-x64-v7.1
--------------------------------

1. tar -xvf cudnn-8.0-linux-x64-v7.1.tgz

2. sudo cp cuda/include/cudnn.h /usr/local/cuda/include

3. sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64

4. sudo chmod a+r /usr/local/cuda/include/cudnn.h

5. sudo chmod a+r /usr/local/cuda/lib64/libcudnn*

6. export LD_LIBRARY_PATH=/usr/local/cuda/lib64

Install cudnn-9.1-linux-x64-v7
------------------------------

1. tar -xvf cudnn-9.1-linux-x64-v7.tgz

2. sudo cp cuda/include/cudnn.h /usr/local/cuda/include

3. sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64

4. sudo chmod a+r /usr/local/cuda/include/cudnn.h

5. sudo chmod a+r /usr/local/cuda/lib64/libcudnn*

6. export LD_LIBRARY_PATH=/usr/local/cuda-9.1/lib64:$LD_LIBRARY_PATH;


Install Python 2.7.13
---------------------

1. tar -xvf Python-2.7.13.tgz

2. cd Python-2.7.13

3. ./configure --prefix=/data/developments/python-2.7.13 --enable-shared --with-system-expat --with-system-ffi --with-ensurepip=yes  --enable-unicode=ucs4

4. make -j4

5. make install

6. export PATH=/data/developments/python-2.7.13/bin:$PATH;

7. pip install wheel

8. pip install numpy

9. pip install scipy

10. pip install matplotlib

11. pip install scikit-learn


Install openmpi-3.0.0
---------------------

1. tar -xvf openmpi-3.0.0.tar.gz

2. cd openmpi-3.0.0

3. ./configure --with-cuda=/usr/local/cuda --prefix=/data/developments/openmpi-3.0.0

4. make -j4

5. make install

6. export LD_LIBRARY_PATH=/data/developments/openmpi-3.0.0/lib:$LD_LIBRARY_PATH


Install tensorflow-r1.5 with GPU and CUDA 9.01
-----------------------------------------------

1. pip install numpy

2. git clone https://github.com/tensorflow/tensorflow.git

3. cd tensorflow

4. git checkout r1.5

5. git submodule update --recursive

5. ./configure

6. Please specify the location of python. [Default is /data/developments/python-2.7.13/bin/python]: Enter

7. Please input the desired Python library path to use.  Default is [/data/developments/python-2.7.13/lib/python2.7/site-packages]: Enter

8. Do you wish to build TensorFlow with jemalloc as malloc support? [Y/n]: Y

9. Do you wish to build TensorFlow with Google Cloud Platform support? [Y/n]: Y

10. Do you wish to build TensorFlow with Hadoop File System support? [Y/n]: Y

11. Do you wish to build TensorFlow with Amazon S3 File System support? [Y/n]: Y

12. Do you wish to build TensorFlow with XLA JIT support? [y/N]: y

13. Do you wish to build TensorFlow with GDR support? [y/N]: y

14. Do you wish to build TensorFlow with VERBS support? [y/N]: y

15. Do you wish to build TensorFlow with OpenCL SYCL support? [y/N]: N

16. Do you wish to build TensorFlow with CUDA support? [y/N]: y

17. Please specify the CUDA SDK version you want to use, e.g. 7.0. [Leave empty to default to CUDA 9.0]: 9.1

18. Please specify the location where CUDA 9.1 toolkit is installed. Refer to README.md for more details. [Default is /usr/local/cuda]: Enter

19. Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 7.0]: 7.0.5

20. Please specify the location where cuDNN 7.0.5 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]: Enter

21. Please note that each additional compute capability significantly increases your build time and binary size. [Default is: 3.5,5.2]: 6.1 for GTX 1060

22. Do you want to use clang as CUDA compiler? [y/N]: N

23. Please specify which gcc should be used by nvcc as the host compiler. [Default is /usr/bin/gcc]: Enter

24. Do you wish to build TensorFlow with MPI support? [y/N]: y

25. Please specify the MPI toolkit folder. [Default is ]: /data/developments/openmpi-3.0.0

26. Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is -march=native]: Enter

27. Would you like to interactively configure ./WORKSPACE for Android builds? [y/N]: N

28. bazel build --config=opt --config=cuda //tensorflow/tools/pip_package:build_pip_package

29. bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg

30. pip install /tmp/tensorflow_pkg/tensorflow-1.5.0rc0-cp27-cp27mu-linux_x86_64.whl

Install APACHE MAVEN
--------------------

1. tar -xvf apache-maven-3.5.2-bin.tar.gz

2. mv apache-maven-3.5.2 /data/developments/

3. export PATH=/data/developments/apache-maven-3.5.2/bin:$PATH;

Configure maven repository directory:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The location of your local repository can be changed in your user configuration. The default value is ${user.home}/.m2/repository/.

4. vi /data/developments/apache-maven-3.5.2/conf/settings.xml

.. sourcecode:: xml

    <localRepository>/data/developments/maven_repo</localRepository>


Environment Source File:
------------------------

.. sourcecode:: bash

    #!/bin/bash

    export PATH=/usr/local/cuda-9.1/bin:$PATH;
    export PATH=/data/developments/python-2.7.13/bin:$PATH;
    export PATH=/data/developments/idea-IC-173.4548.28/bin:$PATH;
    export PATH=/data/developments/apache-maven-3.5.2/bin:$PATH;

    if [ !$LD_LIBRARY_PATH ]
    then
        export LD_LIBRARY_PATH=/usr/local/cuda-9.1/lib64;
    else
        export LD_LIBRARY_PATH=/usr/local/cuda-9.1/lib64:$LD_LIBRARY_PATH;
    fi

    export LD_LIBRARY_PATH=/data/developments/openmpi-3.0.0/lib:$LD_LIBRARY_PATH;

    export ITRC_ROOT=/data/DATA/projects/itrc


Common Errors
-------------

1. dpkg: error processing archive /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb (--unpack)
   
   **Solution**: 
               
.. sourcecode:: bash

    sudo dpkg -i --force-overwrite /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb


INSTALL TORCH 7
---------------

1. git clone https://github.com/torch/distro.git /data/developments/torch --recursive

2. bash install-deps

3. TORCH_NVCC_FLAGS="-D__CUDA_NO_HALF_OPERATORS__" ./install.sh
