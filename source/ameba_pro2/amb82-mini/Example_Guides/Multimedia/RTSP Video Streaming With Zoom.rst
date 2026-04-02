RTSP Video Streaming With Zoom
================================

Materials
---------

- `AMB82-mini <https://www.amebaiot.com/en/where-to-buy-link/#buy_amb82_mini>`__ x 1

Example
-------

In this example, we will use the Ameba Pro2 board to stream video data from the on-board camera sensor while demonstrating a dynamic zoom function, to a computer via RTSP (Real Time Streaming Protocol).


Open the example in :guilabel:`File -> Examples -> AmebaMultimedia -> StreamRTSP -> VideoOnlyWithZoom`

|image01|

The dynamic zoom behavior can be configured by modifying the following macro:

Users can update DYN_ZOOM_MODE to select between two zoom modes:

SCALE_UP_MODE (default): Creating a zoom-in effect.

SCALE_DOWN_MODE: Creating a zoom-out effect.

|image02|

In the highlighted code snippet, fill in the "ssid" with your WiFi network SSID and "pass" with the network password.

|image03|

Compile the code and upload it to Ameba. After pressing the Reset button, wait for the Ameba Pro 2 board to connect to the WiFi network. The board's IP address and network port number for RTSP will be shown in the Serial Monitor.

You may download VLC media player from the link (`here <https://www.videolan.org/vlc/>`__).

Upon the completion of the software installation, open VLC media player, and go to :guilabel:`Media -> Open Network Stream`

|image04|

Make sure your PC is connected to the same network as the Ameba Pro2 board for streaming. Since RTSP is used as the streaming protocol, key in ``rtsp://{IPaddress}:{port}`` as the Network URL in VLC media player, replacing {IPaddress} with the IP address of your Ameba Pro2 board, and {port} with the RTSP port shown in Serial Monitor ``e.g., rtsp://192.168.1.154:554``. The default RTSP port number is 554. In the case of two simultaneous RTSP streams, the second port number defaults to 555.

|image05|

You may choose to change the caching time in "Show more options". A lower cache time will result in reduced video latency but may introduce playback stuttering in the case of poor network conditions.

|image06|

Next, click "Play" to start RTSP streaming. The video stream from the camera will be shown in VLC media player. Meanwhile, in your Serial Monitor, the message "rtp started (UDP)" will appear.

|image07|

OSD text is drawn on the video to display the current zoom mode and ROI resolution.

|image08|

|image09|

Code Reference
--------------
The camera can produce 3 simultaneous video stream channels, with the default configuration for each channel as shown. You may choose to edit the code to use a different video stream.

| Channel 0: 1920 x 1080, 30FPS, H264 format
| Channel 1: 1280 x 720, 30FPS, H264 format
| Channel 2: 1280 x 720, 30FPS, MJPEG format

|image10|

You may adjust the video bitrate based on your WiFi network quality, by uncommenting the highlighted code below.

|image11|

.. |image01| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image01.png
   :width:  973 px
   :height:  1031 px

.. |image02| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image02.png
   :width:  672 px
   :height:  489 px

.. |image03| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image03.png
   :width:  706 px
   :height:  559 px

.. |image04| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image04.png
   :width:  432 px
   :height:  482 px

.. |image05| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image05.png
   :width:  562 px
   :height:  357 px

.. |image06| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image06.png
   :width:  383 px
   :height:  471 px

.. |image07| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image07.png
   :width:  529 px
   :height:  343 px

.. |image08| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image08.png
   :width:  1942 px
   :height:  1030 px
   :scale:  60%

.. |image09| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image09.png
   :width:  481 px
   :height:  504 px

.. |image10| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image10.png
   :width:  482 px
   :height:  427 px

.. |image11| image:: ../../../../_static/amebapro2/Example_Guides/Multimedia/RTSP_Streaming_With_Zoom/image11.png
   :width:  665 px
   :height:  754 px