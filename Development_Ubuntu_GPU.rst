INSTALL UBUNTU 16.04
~~~~~~~~~~~~~~~~~~~~
**Author: Truong Dong Do**

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
