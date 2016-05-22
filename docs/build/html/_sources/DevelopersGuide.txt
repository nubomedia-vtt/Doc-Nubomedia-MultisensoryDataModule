%%%%%%%%%%%%%%%%
Developers Guide
%%%%%%%%%%%%%%%%

This documents provides information how to develope the MultisensoryDataModule (MsData).

Clone repository:

.. code:: bash

    sudo apt-get install git
    git clone https://github.com/nubomedia-vtt/msdata.git

Create a folder to build the MsData

.. code:: bash

    mkdir build
    cd build

Kurento Client Interface
===========================

Now you have an option to generate either Java or JavaScript interface
for the Kurento Client (or naturally both if you need)

Java version

.. code:: bash

    cmake .. -DGENERATE_JAVA_CLIENT_PROJECT=TRUE

JavaScript version

.. code:: bash

    cmake .. -DGENERATE_JS_CLIENT_PROJECT=TRUE

Developing Source Code
===========================

To use the compiled results in Kurento just set into:

.. code:: bash

    /etc/default/kurento-media-server-6.0

for example:

.. code:: bash

    NAME=$(logname)
    export KURENTO_MODULES_PATH=$KURENTO_MODULES_PATH:/home/$NAME/nubomedia/msdata/build
    export GST_PLUGIN_PATH=$GST_PLUGIN_PATH:/home/$NAME/nubomedia/msdata/builds


Data Pad Interface
===========================

MsData utilizes predefined key with key dependent variable arguments this is implemented with gst_structure_new:

.. code:: bash

	  gst_structure_new ()
	  GstStructure *
	  gst_structure_new (const gchar *name,
                   const gchar *firstfield,
	  
This creates a new GstStructure with the given name. Parses the list of variable arguments and sets fields to the values listed. Variable arguments should be passed as field name, field type, and value. Last variable argument should be NULL.

Both MsData and the filter that utilized MsData through data pads must naturally agree on the data that is delivered  but flexible interface between modules is enabled. As a consequence functionality of the MsData can be increased without affecting the MsData interface.


Data Pad Interface Demos
===========================

As an example about utilization of MsData interface
`a heart rate demo <https://github.com/nubomedia-vtt/msdatademopaasheartrate.git>`__ and 
`a graph demo <https://github.com/nubomedia-vtt/msdatademopaasgraph.git>`__
are provided. 

The heart rate demo tells with the 
key 123 that MsData should visualize overlay image with data into window of width and height size so that the window is located into x and y coordinate:

.. code:: bash

	  GstStructure *result = gst_structure_new ("msdata", 
	  "key", G_TYPE_UINT, (guint) (123), 
	  "x", G_TYPE_UINT, (guint) (r->x * resize_factor), 
	  "y", G_TYPE_UINT, (guint) (r->y * resize_factor), 
	  "width", G_TYPE_UINT, (guint) (r->width * resize_factor), 
	  "height", G_TYPE_UINT, (guint) (r->height * resize_factor), 
	  "data", G_TYPE_UINT, (guint) (getMillisecondsTime()), 
	  "overlay", G_TYPE_STRING, overlay.c_str(), NULL);

The graph demo utilizes similar data structure but tells with the key 456 instead that graph should be drawn.


Data Channel Demo
===========================
As an example about utilization of MsData with data channel
`a temperature demo <https://github.com/nubomedia-vtt/msdatademopaastemperature.git>`__ which sends random temperature is provided. 

