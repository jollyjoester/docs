.. _debugger_troubleshooting_guide:

================================================
Debugger Troubleshooting Guide
================================================

.. rst-class:: right-menu



.. _troubleshoot_pair:

Fail to Pair Monaca Debugger
================================================

Several reasons can be considered when Monaca Debugger fails to pair with Monaca Localkit.

1. Monaca Debugger can see Monaca Localkit but fail to pair: this is most likely a firewall problem in the host PC. Localkit needs to accept TCP connection from the debugger. Port `8001` will be used, and you can change the server port in :ref:`Preferences dialog<localkit_preference>`. Please change the port or configure your firewall settings to try agian.

2. Monaca Debugger does not detect Monaca Localkit: please check and see if your device and the host PC are connected to the same network. If they are connected to the same network but Monaca Debugger still can't detect the host PC, please do a manual pairing.

You can manually pair Monaca Debugger with Monaca Localkit as follows:

1. From Monaca Debugger, click on the toggle menu on the top-left corner and select :guilabel:`Local Computers` button.

  .. figure:: images/troubleshooting/1.png
    :width: 250px
    :align: left

  .. rst-class:: clear

2. Click :guilabel:`Pair the New Computer` button.

3. Input :ref:`the IP address of the host PC and port number<ip_port>`. Then, click :guilabel:`Pair` button.

  .. figure:: images/troubleshooting/2.png
    :width: 250px
    :align: left

  .. rst-class:: clear

4. Once the pairing is successfully completed, the host PC should appear under "Paired computers" as shown below:

  .. figure:: images/troubleshooting/3.png
    :width: 250px
    :align: left

  .. rst-class:: clear

.. note:: Some Wi-Fi access points (usually that is available for public access) don't allow the connected clients to communicate each other. In this case, please try pairing on another local network.

.. _ip_port:

*IP Address and Port Number*

IP address and port number are needed to establish the communication path between Monaca Debugger and Monaca Localkit. IP address represents the host PC and port number (set to 8001 by default) represents Monaca Localkit. Please note that the communication can't be established if the port number you use is not opened or is already used.

+------------------+------------------------------------------------------------------+------------------------------------------------+
|*OS*              | Mac                                                              | Windows                                        |
+------------------+------------------------------------------------------------------+------------------------------------------------+
|*IP Address*      | Find IP address:                                                 | Find IP address:                               |
|                  |                                                                  |                                                |
|                  | 1. Open "Terminal" window.                                       | 1. Open "Command Prompt" window.               |
|                  | 2. Type ``ifconfig``.                                            | 2. Type ``ipconfig``.                          |
+------------------+------------------------------------------------------------------+------------------------------------------------+
| *Port Number*    | Check if a port number is available:                             | Check if a port number is available:           |
|                  |                                                                  |                                                |
|                  | 1. Open "Terminal" window.                                       | 1. Open "Command Prompt" window.               |
|                  | 2. Type ``lsof -i :PORT_NUMBER``.                                | 2. type ``netstat``.                           |
+------------------+------------------------------------------------------------------+------------------------------------------------+

.. _troubleshoot_inspector:

Inspector Isn't Loaded
================================================

If the inspector does not open, please try the following actions:
  
- verify if you have done all necessary setups described :ref:`here<localkit_debug_app>`.
- verify that you are running the application on the debugger.
- try plug off & in to see if the computer can find the device.
- check if the device and the host PC are connected via USB cable.
- check if you use the right Monaca Debugger. :ref:`Read more<localkit_debug_app>`.
- kill all ``adb`` processes if multiple of them are running.
- kill all ``iosWebKitDebugProxy`` processes if multiple of them are running.
- restart the host PC.


