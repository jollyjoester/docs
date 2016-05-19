.. _debugger_on_emulator:

======================================================================
Monaca Debugger for Android Emulator
======================================================================

.. rst-class:: right-menu


In this page, we will describe how Monaca Debugger works on AVD (Android Virtual Device) called Android Emulator. With this, you can simulate Android apps on a PC. Moreover, it is useful when you want to test your apps on more than one Android device. 

.. note:: In this page, the instruction is made on a Mac OS X. Internet is needed in order to run Monaca Debugger on emulator.

Step 1: Setting up an Android Virtual Device
================================================

1. Download and install `Android Studio <http://developer.android.com/sdk/index.html>`_.

2. Run Android Studio.

3. Create a new project or open an existing one.

4. Click on :guilabel:`AVD Manager`. Then, Android Virtual Device Manager dialog will appear.

  .. figure:: images/debugger_emulator/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear

5. Click :guilabel:`+ Create Virtual Device`.

6. Select an Android device and click :guilabel:`Next`.

  .. figure:: images/debugger_emulator/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

7. Select a system image (you may need to download it first) and click :guilabel:`Next`.
  
  .. figure:: images/debugger_emulator/3.png
    :width: 600px
    :align: left

  .. rst-class:: clear

8. Make the virtual device's configurations. Go to :guilabel:`Show Advanced Settings` for other settings such as Memory and Storage, Device Frame and Keyboard.
  
  .. figure:: images/debugger_emulator/4.png
    :width: 600px
    :align: left

  .. figure:: images/debugger_emulator/4_1.png
    :width: 600px
    :align: left

  .. rst-class:: clear


9. After completing the configurations, click :guilabel:`Finish`.


Step 2: Installing Monaca Debugger
==========================================

1. Go to :guilabel:`AVD Manager` and launch the virtual device.

  .. figure:: images/debugger_emulator/5.png
    :width: 600px
    :align: left

  .. rst-class:: clear

2. From your virtual device, open a browser and go to ``http://monaca.mobi/bin/MonacaDebugger.apk`` to download Monaca Debugger for emulator.

  .. figure:: images/debugger_emulator/6.png
    :width: 350px
    :align: left

  .. rst-class:: clear

3. After the download is completed, click on the downloaded file to start installing the debugger.

  .. figure:: images/debugger_emulator/7.png
    :width: 350px
    :align: left

  .. rst-class:: clear

4. Follow the installation wizard.

  .. figure:: images/debugger_emulator/8.png
    :width: 350px
    :align: left

  .. rst-class:: clear

5. Once the installation is completed, you can find Monaca Debugger in your apps page.

  .. figure:: images/debugger_emulator/9.png
    :width: 350px
    :align: left

  .. rst-class:: clear


Step 3: Running a Project on Monaca Debugger
===================================================

1. Open Monaca Debugger and sign in with your Monaca account.

  .. figure:: images/debugger_emulator/10.png
    :width: 350px
    :align: left

  .. rst-class:: clear

2. Click on a project you want to run in Monaca Debugger.

  .. figure:: images/debugger_emulator/11.png
    :width: 350px
    :align: left

  .. rst-class:: clear

3. Now, your project is running. You can start testing your project. Please refer to :ref:`monaca_debugger_features` and :ref:`debugging_monaca_app` on what you can do with Monaca Debugger in order to help enhancing your app development processes.

  .. figure:: images/debugger_emulator/12.png
    :width: 350px
    :align: left

  .. rst-class:: clear


.. seealso::

  *See Also*

  - :ref:`Debugger's Functionalities <monaca_debugger_features>`
  - :ref:`Debugger's Usage <debugging_monaca_app>`


