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


MsData utilizes predefined key with key dependent variable arguments this is implemented with gst_structure_new:

.. code:: bash
	  gst_structure_new ()
	  GstStructure *
	  gst_structure_new (const gchar *name,
                   const gchar *firstfield,
                   ...);
	  
		   Creates a new GstStructure with the given name. Parses the list of variable arguments and sets fields to the values listed. Variable arguments should be passed as field name, field type, and value. Last variable argument should be NULL.

Both MsData and the filter that utilized MsData through data pads must naturally agree on the data that is delivered  but flexible interface between modules is enabled. As a consequence functionality of the MsData can be increased without affecting the MsData interface.


As an example, here the utilizer of the MsData tells with the key 123 
that MsData should be able to retrieve data about rectangle, image and value.
As a result the utilizer should also known what kind of visualization is done with this. 
.. code:: bash
	  GstStructure *result = gst_structure_new ("msdata", "key", G_TYPE_UINT, (guint) (123), "x", G_TYPE_UINT, (guint) (r->x * resize_factor),
        "y", G_TYPE_UINT, (guint) (r->y * resize_factor),
        "width", G_TYPE_UINT,
        (guint) (r->width * resize_factor), "height",
        G_TYPE_UINT, (guint) (r->height * resize_factor),
        "b", G_TYPE_UINT, (guint) (255),
        "g", G_TYPE_UINT, (guint) (0),
        "r", G_TYPE_UINT, (guint) (255),
        "d", G_TYPE_UINT, (guint) (getMillisecondsTime()),
      "overlay", G_TYPE_STRING, overlay.c_str(), NULL);
