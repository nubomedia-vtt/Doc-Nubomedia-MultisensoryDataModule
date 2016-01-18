%%%%%%%%%%%%%%%%
Developers Guide
%%%%%%%%%%%%%%%%

This documents provides information how to develope the MultisensoryDataModule (MsData).

Clone repository:

.. code:: bash

    sudo apt-get install git
    git clone https://github.com/nubomedia-vtt/msdata.git

Setup the developing environment

.. code:: bash

    cd msdata/misc
    chmod u+x setup.sh
    ./setup.sh
    cd ..

Create a folder to build the MsData

.. code:: bash

    mkdir build
    cd build

Now you have an option to generate either Java or JavaScript interface
for the Kurento Client (or naturally both if you need)

Java version

.. code:: bash

    cmake .. -DGENERATE_JAVA_CLIENT_PROJECT=TRUE

JavaScript version

.. code:: bash

    cmake .. -DGENERATE_JS_CLIENT_PROJECT=TRUE

To use the compiled results in Kurento just set into:

.. code:: bash

    /etc/default/kurento-media-server-6.0

for example:

.. code:: bash

    NAME=$(logname)
    export KURENTO_MODULES_PATH=$KURENTO_MODULES_PATH:/home/$NAME/nubomedia/msdata/build
    export GST_PLUGIN_PATH=$GST_PLUGIN_PATH:/home/$NAME/nubomedia/msdata/build

