aiortc
======

Installing
----------
Linux
.....

On Debian/Ubuntu run:

.. code:: bash

    apt install libavdevice-dev libavfilter-dev libopus-dev libvpx-dev pkg-config

`pylibsrtp` comes with binary wheels for most platforms, but if it needs to be
built from you will also need to run:

.. code:: bash

    apt install libsrtp2-dev

Install python==3.9.7

Install aiortc in developer mode
.. code:: bash
    pip install -e .

Running experiments
----------

Run cli.py from examples/videostream-cli
On sender side run:
.. code:: bash
    python cli.py --offer --play-from test.mp4

This will generate a message, which should be copied to the receiver side.

On receiver side run:
.. code:: bash
    python cli.py --answer
or
.. code:: bash
    python cli.py answer --record-to video.mp4
to save the received video.

Copy the message from sender side. The receiver will also generate a message, which should be copied to the sender side.
After the answer message is entered on the sender side, the video will start sending.
Currently it is quite tedious to repeat this process everytime we run the code, but in the future, we can use automate this.

Rate Measurement
----------

The data rate measurement is made on the receiver side, everytime a packet is received.
See rtcrtpreceiver.py : _handle_rtp_packet()
See rate_mod.py : class RemoteBitrateEstimator_mod



