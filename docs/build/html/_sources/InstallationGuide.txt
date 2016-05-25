*****
Installation Guide
*****

MultisensoryDataModule 
=================================

Installation instructions
-------------------------


Recommend easy installation
===========================

These are the instructions to utilize the multisensorydata filter.

If you wish to have the most convenient installation, you should install
the following in this order:

KMS (this refers to the latest KMS version eg KMS6)

Option apt-get

Note that for each of these, installation instructions are given below.

Installing KMS
==============

For installing Kurento Media Server (KMS),

please refer to

.. code:: bash

    www.kurento.org/


Installing with Option apt-get
==============================

Choose this if you wish to install with apt-get the latest release
version (not necessarily contains the latest features).

Execute:

.. code:: bash

    echo "deb [arch=amd64] http://ssi.vtt.fi/ubuntu trusty main" | sudo tee -a /etc/apt/sources.list
    sudo apt-get update
    sudo apt-get install msdata
    sudo ldconfig
    sudo /etc/init.d/kurento-media-server-6.0 restart

Installing with Option dpkg
===========================

Note that this is alternative to the Option apt-get.

Choose this if you wish to install with dpkg the latest release version
(not necessarily contains the latest features).

Fetch and install the latest debian package (eg at the moment 6.4.0 or newer):
`msdata_6.4.0_amd64.deb <http://ssi.vtt.fi/ubuntu/dists/trusty/main/binary-amd64/amd64/msdata_6.4.0_amd64.deb>`__

.. code:: bash

    sudo dpkg -i msdata_6.4.0_amd64.deb
    sudo apt-get -f install
    sudo ldconfig
    sudo /etc/init.d/kurento-media-server-6.0 restart

