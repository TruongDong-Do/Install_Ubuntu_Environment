.. raw:: html
   
    <h1 align="center"> Install Deep Learning Environment on UBUNTU </h1>
    
    <a href='https://install-ubuntu-environment.readthedocs.io/en/latest/?badge=latest'>
    <img src='https://readthedocs.org/projects/install-ubuntu-environment/badge/?version=latest' alt='Documentation Status' />
      </a>
      
    
**Author: Truong Dong Do**

Note:
If you need to install on Windows, refer following links:

- https://blog.quantinsti.com/install-tensorflow-gpu/
- https://towardsdatascience.com/installing-tensorflow-with-cuda-cudnn-and-gpu-support-on-windows-10-60693e46e781

Documentation
-------------
Latest **documentation** is avaliable on `Read the
Docs <https://install-ubuntu-environment.readthedocs.io/en/latest/>`__

0. Create boot USB:
-----------------------
- Download Ubuntu 18.04 LTS
- Use Universal USB Installer to create boot USB (Ubuntu --> Fat32)

1. Boot option:
---------------
- Choose USB boot --> Install Ubuntu

2. DISK:
--------
- Chose something else option when installing.
- swap area: 4 x Ram
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

6. Install Nvidia Driver/ CUDA / CuDNN
------------------------
Follow these instrutions to install tensorflow-gpu:(CUDA 10 + CuDNN 7)
=============================================================
- https://www.tensorflow.org/install/gpu (*official)

- Check NVIDIA Driver:
.. code:: bash

    $ nvidia-smi

Here we have 2 options to work with environments:
------------------------
1/ Install conda: (Recommend)
------------------------
https://docs.anaconda.com/anaconda/install/linux/

- Work with conda (create new conda environment): 
  
  https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/20/conda/\
- Install cudatoolkit by anaconda: 

https://anaconda.org/anaconda/cudatoolkit\ 

(Choose the right version with TF: https://www.tensorflow.org/install/source#linux)

- Install cudnn by anaconda: 

https://anaconda.org/anaconda/cudnn

2/ Virtualenv and virtualenvwrapper: 
------------------------
- Install python: 

https://tecadmin.net/install-python-3-6-ubuntu-linuxmint/

https://docs.python-guide.org/starting/install3/linux/

- Install the virtualenv and virtualenvwrapper:
https://www.pyimagesearch.com/2017/09/27/setting-up-ubuntu-16-04-cuda-gpu-for-deep-learning-with-python/

- Work with virtualenv and virtualenvwrapper: 
  
  https://virtualenvwrapper.readthedocs.io/en/latest/command_ref.html#showvirtualenv

- Make a new virtual environment:

.. code:: bash 

    # In old environment:
    $ pip freeze > requirements.txt #Extract pip requirement file
    
    $ mkvirtualenv env_name -p python3
    # In new environment:
    $ pip install -r requirements.txt
    
- Check CUDA:

.. code:: bash

    $ ncvv --version

- Check Tensorflow 1.x:

.. code:: python

    import tensorflow as tf
    tf.__version__
    hello = tf.constant('Hello, TensorFlow!')
    print(sess.run(hello))
    a = tf.constant(10)
    b = tf.constant(5)
    sess = tf.Session()
    exit()
   
- Check Tensorflow 2.x:

.. code:: python

	import tensorflow as tf
	tf.__version__ # Result should be '2.2.0-rc2'
	tf.config.list_physical_devices('GPU') # should list all available GPUs



7. Install VSCode (Recommend Code Editor)
-----------------
- Download *VSCode.deb*

.. code:: bash 

    $ sudo dpkg -i code_...-.deb

8. Install GitKraken
--------------------

https://support.gitkraken.com/how-to-install/

9. Install Sublime Text 3 (Optional)
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
 `config_SublimeText.json <config_SublimeText.json>`__
	
10. Install PyTorch
-------------------------
- `PyTorch <https://pytorch.org/get-started/locally/>`__
