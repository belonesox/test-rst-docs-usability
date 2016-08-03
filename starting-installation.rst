Starting Installation
---------------------

Virtuozzo can be installed from

-  DVD discs

-  USB drives (see :ref:`Preparing for Installation from USB Storage Drives`)

-  PXE servers (see the *Installation via PXE Server* guide for information on installing Virtuozzo over the network)

    .. note:: Time synchronization via NTP is enabled by default.

To start the installation, do the following:

1. Configure the server to boot from a DVD or USB drive.

2. Boot the server from the chosen media and wait for the welcome screen:

Choosing Installation Type
~~~~~~~~~~~~~~~~~~~~~~~~~~

You can install Virtuozzo 7 in one of the following modes:

-  graphics (default, recommended), see :ref:`Installing Virtuozzo in Graphics Mode`,

-  basic graphics (in case of issues with video card drivers), see :ref:`Installing Virtuozzo in Basic Graphics Mode`,

-  graphics via VNC, see :ref:`Installing Virtuozzo via VNC`,

-  text (Virtuozzo Storage cannot be installed in this mode), see :ref:`Installing Virtuozzo in Text Mode`.

Your further installation steps will differ depending on the chosen mode.

.. _Enabling Forced Detection of SSDs:

Enabling Forced Detection of SSDs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Certain solid-state drives (SSDs) may not be autodetectable by the installer. This may result in issues when you create or join Virtuozzo Storage clusters. To avoid this problem, you can force the installer to identify the required drives as SSDs by doing the following:

1. Select the required installation option (e.g., **Install Virtuozzo 7**) and press **E** to start editing it.

2. Add ``ssd_hack=sd<N>[,...]`` at the end of the line starting with ``linux /images/pxeboot/vmlinuz``. For example:

   ::

       linux /images/pxeboot/vmlinuz inst.stage2=hd:LABEL=vz-iso-7.0.0-3589.iso quiet ip=dhcp \
       ssd_hack=sdb,sdc

3. Press **Ctrl-X** to start booting the chosen installation option.

The installer should identify the specified drives as SSDs.

