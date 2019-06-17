.. raw:: html
   
    <h1 align="center"> Install Deep Learning Environment on UBUNTU </h1>
    
    <a href='https://install-ubuntu-environment.readthedocs.io/en/latest/?badge=latest'>
    <img src='https://readthedocs.org/projects/install-ubuntu-environment/badge/?version=latest' alt='Documentation Status' />
      </a>
**Author: Truong Dong Do**

Documentation
-------------
Latest **documentation** is avaliable on `Read the
Docs <https://install-ubuntu-environment.readthedocs.io/en/latest/>`__

0. Create boot USB:
-----------------------
- Download Ubuntu 16.04 LTS
- Use Universal USB Installer to create boot USB (Ubuntu --> Fat32)

1. Boot option:
---------------
- Choose USB boot --> Install Ubuntu

2. DISK:
--------
- Chose something else option when installing.
- swap area: Ram
- ext4: /

3. Install Google Chrome:
---------------------------
- Download *Google Chrome.deb*

.. code:: bash

    $ sudo dpkg -i google-chrome-stable_current_amd64.deb
    $ sudo apt-get install -f

4. Install Teamviewer.
------------------------
- Download *Teamviewer.deb*

.. code:: bash

    $ sudo dpkg -i teamviewer_14.1.18533_amd64.deb
    $ sudo apt-get install -f
    
5. Install iBus-Unikey.
-----------------------
.. code:: bash

    $ sudo apt-get install ibus-unikey
    $ ibus restart

--> Text Entry --> Vietnamese(ibus)

.. code:: bash

    $ sudo reboot

6. Install Nvidia Driver
------------------------

- Setting --> Software & Updates --> Additional Drivers --> Nvidia -- Apply changes.
- Test NVIDIA Driver:

.. code:: bash

    $ nvidia-smi


Lam theo huong dan de cai tensorflow-gpu:(CUDA 10 + CuDNN 7)
------------------------------------------------------------

- https://www.tensorflow.org/install/gpu
- https://www.pyimagesearch.com/2017/09/27/setting-up-ubuntu-16-04-cuda-gpu-for-deep-learning-with-python/

Check CUDA:

.. code:: bash

    $ ncvv --version

Check Tensorflow:

.. code:: python

    import tensorflow as tf
    tf.__version__
    hello = tf.constant('Hello, TensorFlow!')
    print(sess.run(hello))
    a = tf.constant(10)
    b = tf.constant(5)
    sess = tf.Session()
    exit()


7. Install VSCode
-----------------
- Download *VSCode.deb*

.. code:: bash 

    $ sudo dpkg -i code_...-.deb

8. Install GitKraken
--------------------

9. Install Sublime Text 3
-------------------------

.. code:: bash

    $ wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
    $ sudo apt-get install apt-transport-https
    $ echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
    $ sudo apt-get update
    $ sudo apt-get install sublime-text
    $ sudo apt-get autoremove

--> Install: Package Control
============================
- Ctrl + Shift + P
- Install --> Package Control --> Install Materialize, Materialize Theme
- Github Link:
    - https://github.com/CoreyMSchafer/dotfiles/tree/master/settings

- Go to Preferences --> Setings --> User:

- Preferences.sublime-settings:
 `config_SublimeText.json </config_SublimeText.json>`__
	
10. Install PyTorch
-------------------------
- `PyTorch <https://pytorch.org/get-started/locally/>`__

.. code:: bash

	$ pip3 install https://download.pytorch.org/whl/cu100/torch-1.1.0-cp35-cp35m-linux_x86_64.whl
   	$ pip3 install https://download.pytorch.org/whl/cu100/torchvision-0.3.0-cp35-cp35m-linux_x86_64.whl
	
.. image:: /images/torch_install.jpg
    :width: 200px
    :align: center
    :height: 100px
    :alt: alternate text
