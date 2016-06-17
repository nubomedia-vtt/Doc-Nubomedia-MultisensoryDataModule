.. _README:

*****
Readme
*****
This project is part of NUBOMEDIA
`www.nubomedia.eu <http://www.nubomedia.eu>`__


**MultisensoryDataFilter (MsData)**

The repository contains documentation for installing and utilising the MsData. The repository contains description of the architecture of the MsData and also the source code of the MsData implementation.

MsData implements multi-domain AR filter providing 2D graphics visualisation service to other modules through data pads. Data channels are utilized thus MsData Interface enables sending of different kinds of content based on the identification and variable arguments thus the format of the data is quite flexible. Developers can create new visualisations not yet known thus extending MsData. Example for drawing a graph is available. Because the filter needs to support data-pads, the filter is based on Kurento GStreamer module. Refer the 
`Kurento documentation <http://www.kurento.org/>`__ 
for a more complete view of the Kurento architecture.

The following image show the current visualisations provided ie heart rate, temperature and graph. In addition, speed meter visualisation is considered.

.. image:: sleeps.jpg

.. image:: temperature.jpg

.. image:: graph.jpg

