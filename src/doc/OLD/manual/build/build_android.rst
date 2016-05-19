.. _building_for_android:

============================================================================
Building for Android
============================================================================

.. rst-class:: right-menu

.. _types_of_build_android:

Types of Build
=============================

In Monaca, Android app has two types of build: debug version and release version. The differences between these types of build are as follows:


+------------------+----------------------------------------+----------------------------------------------------+
| Types of Build   | Description                            |  Installation                                      |
+==================+========================================+====================================================+
| *Debug Build*    | An unsigned package which cannot       | - QR Code                                          |
|                  | be distributed in the market.          | - :ref:`Network Install <debugger_project_options>`|
|                  |                                        | - Sideloading                                      |
+------------------+----------------------------------------+----------------------------------------------------+
| *Release Build*  | a signed package with the developer's  | - Sideloading                                      |
|                  | code sign which can be distributed in  | - Google Play Store and other eligible markets     |
|                  | the market.                            |                                                    |
+------------------+----------------------------------------+----------------------------------------------------+


.. note:: Sideloading means installing an application package in APK format onto an Android device. After building your app, you can download the APK file and install it.

.. _config_android_app:  

Step 1: Configure Android App
=================================

1. From the Monaca Cloud IDE menu, go to :menuselection:`Config --> Android App Settings`.

2. Fill in the necessary information of your app:

  - General settings:

      .. rst-class:: wide-table

        +-------------------------+-------------------------------------------------------------------------------------------------+
        | Application Name        | a name representing your app publicly such as in the Market.                                    |
        +-------------------------+-------------------------------------------------------------------------------------------------+
        | Package Name            | a unique name which will be used when uploading to the Android Market. It is recommended to use |
        |                         | reverse-domain style (for example, mobi.monaca.appname) for App ID. Only alphanumeric characters|
        |                         | and periods (at least one period must be used) are allowed. Each segment separated by a period  |
        |                         | should begin with an alphabetic character.                                                      |
        +-------------------------+-------------------------------------------------------------------------------------------------+
        | Use Different Package   | if enable, the package name of the release-built and debug-built apps are different. In other   |
        | Name for Debug Build    | words, the package name of debug-built app will have ``.debug`` extension, and the one for      |
        |                         | project debugger will have ``.debugger`` extension. However, this option is disable by default  |
        |                         | because it made some plugins impossible to be debugged due to the fact that they are tied to    |
        |                         | exact package names (eg. in-app purchase).                                                      |
        +-------------------------+-------------------------------------------------------------------------------------------------+
        | Version                 | the version number of your app. A version number consist of only number seperated by dots       |
        |                         | (for example, 1.0.0).                                                                           |
        +-------------------------+-------------------------------------------------------------------------------------------------+
        | Version Code            | an internal version number of your app, relative to other versions. The value must be integer,  |
        |                         | so that the applications can programmatically evaluate it for an upgrade.                       |
        +-------------------------+-------------------------------------------------------------------------------------------------+
        | Fullscreen              | this option is only available with the PhoneGap 3.5 and later. If enable, your app will be run  |
        |                         | in a fullscreen mode which hide the status bar.                                                 |
        +-------------------------+-------------------------------------------------------------------------------------------------+

    .. figure:: images/android/1.png
      :width: 600px
      :align: left

    .. rst-class:: clear

  - Misc: various settings regarding your Android app such as:

      .. rst-class:: wide-table

        +---------------------+----------------+-----------------------------------------------------------------------+
        | Settings            | Default Value  |    Description                                                        |
        +=====================+================+=======================================================================+
        | Allowed URL         | ``*``          | Specify URL(s) which can be accessed from your app. If set to ``*``,  |
        |                     |                | you can access all domains from your app.                             |
        +---------------------+----------------+-----------------------------------------------------------------------+
        | Keep Running        | Enable         | Enable this if you want Cordova to keep running in the background.    |
        +---------------------+----------------+-----------------------------------------------------------------------+
        | Disallow Overscroll | Enable         | Enable this if you want to disable the glow when a user scrolls       |
        |                     |                | beyond the edge of the webview.                                       |
        +---------------------+----------------+-----------------------------------------------------------------------+
        | WebView Engine      | Stock WebView  | Set to High Performance (Crosswalk) for a more powerful and larger    |
        |                     |                | app size. It's required Android 4.0 and up. For phonegap 5.2 and      |
        |                     |                | and higher, Stock WebView will be applied as default.                 |
        +---------------------+----------------+-----------------------------------------------------------------------+
        | Screen Orientation  | Default        | You can also set the device's screen orientation when running your    |
        |                     |                | app as Landscape or Portrait.                                         |
        +---------------------+----------------+-----------------------------------------------------------------------+

3. After finishing the configurations, click :guilabel:`Save`.


.. _config_android_keystore:  

Step 2: Configure Android Keystore
======================================

A keystore is a binary file that contains a set of private keys. A private key represents the entity to be identified with the app, such as a person or a company. A keystore is encrypted with a password and it cannot be restored if the password is lost. When a keystore is lost or it overwrites another keystore, it is impossible to use the same key to re-sign the signed package.

A keystore is required for the building of a release version for your Android app. In Monaca, you can either create a new keystore or import an existing one. In order to create a new keystore, please do as follows:

1. From the Monaca Cloud IDE menu, go to :menuselection:`Config --> Android KeyStore Settings`.

2. Then, Manage KeyStore and Alias page will appear.

  .. figure:: images/android/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. Click on :guilabel:`Clear and Generate New...` button. Then, the following screen will appear:

  .. figure:: images/android/3.png
    :width: 400px
    :align: left

  .. rst-class:: clear

4. Fill in the necessary information as shown in the above screen such as 
    
  - Alias: a name representing a private key that you will use later when signing your app. Multiple aliases can be stored within one keystore.
  - Password: a password for the private key (alias).
  - Password of the keystore: a password for the keystore. You will need this password when importing this keystore. 

5. Then, click :guilabel:`Generate Keystore and Alias` button to Generate the keystore.

.. note:: When a keystore is lost, it is impossible to use the same key to re-sign the signed package. Therefore, always back up and keep the keystore which is used to sign application(s). Use the :guilabel:`Export` button to download your keystore.


.. _start_build_android:  

Step 3: Start Building
====================================

1. From the Monaca Cloud IDE menu, go to :menuselection:`Build --> Build App for Android`.

2. Select appropriate type of build you want and click :guilabel:`Next`.

  .. figure:: images/android/4.png
    :width: 500px
    :align: left

  .. rst-class:: clear

3. Select the CPU architecture. ARM option is recommended since it has higher compatibility. For more information regarding the CPU architecture and its differences, please refer to `CPUs and Architectures <http://developer.android.com/ndk/guides/arch.html>`_. If you choose Release Build option in Step 2, you may also need to select an alias to sign your package.

  .. figure:: images/android/5.png
    :width: 500px
    :align: left

    Debug Build

  .. figure:: images/android/6.png
    :width: 500px
    :align: left

    Release Build

  .. rst-class:: clear

4. Click :guilabel:`Next`.

5. It may take several minutes for the build to complete. Please wait.




.. seealso::

  *See Also*

  - :ref:`building_for_ios`
  - :ref:`building_for_win8`
  - :ref:`google_play_distribution`
  - :ref:`building_for_chrome_app`
  - :ref:`build_history`
