.. _localkit_pairing_debugging:

===============================
Pairing and Debugging
===============================

.. rst-class:: right-menu



In order to debug Monaca app with Monaca Localkit, you need to pair your host PC (running Monaca Localkit) with your device (running Monaca Debugger) first.

.. note:: Make sure your host PC and your mobile device are in the same network connection (LAN or Wi-Fi). Some public networks do not allow connections between clients; therefore, pairing cannot be done in this case.

Start Pairing
===============================

1. Log in to Monaca Localkit on your host PC.

2. Use the same account to log in to Monaca Debugger on your mobile device.

3. Once logged in, Monaca Debugger should be able to detect the host PC as shown below. Then, click :guilabel:`Pair` button to start the pairing. However, if Monaca Debugger is unable to detect the host PC automatically, please refer to :ref:`Troubleshoot the Pairing<troubleshoot_pair>`.

  .. figure:: images/pairing_debugging/1.png
    :width: 250px
    :align: left

  .. rst-class:: clear

4. If the pairing is successful, the debugger will be shown under "Debuggers" tab in Monaca Localkit.

  .. figure:: images/pairing_debugging/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

5. Moreover, when the debugger is successfully connected to Monaca Localkit, a local projects list will be shown in Monaca Debugger as shown below:

  .. figure:: images/pairing_debugging/3.png
    :width: 250px
    :align: left

  .. rst-class:: clear


Stop Pairing
===============================

1. From Monaca Debugger, click on the toggle menu on the top-left corner and go to :guilabel:`Local Computers` button.

2. Then, the connected PC will be shown. Click on the "Information" icon of the connected PC (see the screenshot below).

  .. figure:: images/pairing_debugging/4.png
    :width: 250px
    :align: left

  .. rst-class:: clear

3. The information of the connected PC will be shown here. Click :guilabel:`Unpair this computer` button to disconnect from the selected PC. Once you unpair, you can't debug your local Monaca projects with this debugger anymore unless you pair it again.


.. _localkit_debug_app:

Debugging Monaca Apps with Monaca Localkit
=======================================================

Please refer to :ref:`debugger_with_local_tools`. 


.. seealso::

  *See Also*

  - :doc:`../../../quick_start/localkit/index`
  - :doc:`overview`
  - :doc:`build_publish`
  - :doc:`troubleshooting`