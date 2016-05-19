.. _building_for_win8:

============================================================================
Building for Windows
============================================================================

.. rst-class:: right-menu

Windows Store Apps
============================================================================

Windows Store apps are created by using HTML5 and JavaScript , and they run natively on the WinRT architecture. Therefore, applications created by using Monaca are equipped with the same functionalities as created by development tools such as Visual Studio, and can use all native features including WinJS. 

Windows Store apps run on PCs and tablets installed with Windows and Windows RT. However, if you want to publish the app to the Windows Store, you will need to rebuild it separately by using Visual Studio or other development tools since the release build from Monaca are not supported yet. 

On the other hand, Windows Store apps have various constraints that are not found on Android or iOS such as:

* There are some methods or features that are not supported since HTML5 or JavaScript runs in Trident/Chakra application mode. For more details, please refer to HTML, CSS, and JavaScript Features and Difference on `<http://msdn.microsoft.com/en-us/library/windows/apps/hh465380.aspx>`_. 
 
Prerequisite
=================================

You are required to have a valid Microsoft Developer License in order to build Windows apps. It's free but you need to have a Microsoft account. If you don't have the license, please register `here <https://dev.windows.com/en-us/programs/join>`_.

.. _app_settings_win8:

Step 1: Configure Windows App Settings
============================================================================

1. From the Monaca Cloud IDE menu, go to :menuselection:`Config --> Windows App Settings`.

2. Fill in the necessary information of your app:

  .. rst-class:: wide-table

    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Package Certificate Key | This certificate is used when Monaca compiles to Windows app. It will also be used when doing   |
    |                         | side-loading or submitting to Windows Store. It will be generated automatically in the first    |
    |                         | Windows build if it does not exist. If you want to upload existing certificate file, it should  |
    |                         | be a PKCS#7 format without password.                                                            |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | App Display Name        | Enter the application name. It will appear on the Start screen.                                 |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Package Display Name    | Enter the package name.                                                                         |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Short Name              | Enter a name to be displayed on the taskbar.                                                    |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Show Name               | Define default setting of logo displayed in start menu of windows 8 or higher.                  |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Version                 | Enter the version number of your app. A version number consist of only number seperated by dots |
    |                         | (for example, 0.0.1.0).                                                                         |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | App Description         | A short summary about your app.                                                                 |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Package Publisher Name  | It could be your name, group name, company name, etc.                                           |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Architecture            | Select a CPU Architecture. Available options are AnyCPU, x86, x64 and Arm.                      |
    +-------------------------+-------------------------------------------------------------------------------------------------+
  
  .. figure:: images/winrt/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear
    
3. After finishing the configurations, click :guilabel:`Save`.


.. _build_win8:

Step 2: Start Building
==================================

1. From the Monaca Cloud IDE menu, go to :menuselection:`Build --> Build App for Windows`.

2. Click :guilabel:`Next`.

  .. figure:: images/winrt/2.png
    :width: 400px
    :align: left

  .. rst-class:: clear

3. After the build is successfully completed, download the zip file of the built app.

  .. figure:: images/winrt/3.png
    :width: 500px
    :align: left

  .. rst-class:: clear

Step 3: Install the App
==========================================

1. Extract the downloaded zip file.

2. In the extracted folder, Right-click on the :file:`Add-AppDevPackage.ps1` file and select :guilabel:`Run with PowerShell`. Then, the installation will begin. 

  .. figure:: images/winrt/4.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. Then, you might be asked to confirm the opening of the selected file. Click :guilabel:`Open`. 

  .. figure:: images/winrt/5.png
    :width: 400px
    :align: left

  .. rst-class:: clear

4. Press Enter to continue. 

  .. figure:: images/winrt/6.png
    :width: 600px
    :align: left

  .. rst-class:: clear

5. Then, the UAC (User Account Control) prompt will appear asking you to grant the Administrative privilege. Click :guilabel:`Yes`.

6. Confirm the running of the app by typing ``R`` in the PowerShell windows.

  .. figure:: images/winrt/7.png
    :width: 600px
    :align: left

  .. rst-class:: clear

7. Then, press ``Y``.

  .. figure:: images/winrt/8.png
    :width: 600px
    :align: left

  .. rst-class:: clear

8. Once, the installation is completed, press Enter.

  .. figure:: images/winrt/9.png
    :width: 600px
    :align: left

  .. rst-class:: clear

9. Now, your app should be successfully installed. Find your app in the App windows.

  .. figure:: images/winrt/10.png
    :width: 600px
    :align: left

  .. rst-class:: clear

10. Click on it to launch the app. Then, your app should be running.

  .. figure:: images/winrt/11.png
    :width: 600px
    :align: left




.. seealso::

  *See Also*

  - :ref:`building_for_ios`
  - :ref:`building_for_android`
  - :ref:`google_play_distribution`
  - :ref:`building_for_chrome_app`
  - :ref:`build_history`
