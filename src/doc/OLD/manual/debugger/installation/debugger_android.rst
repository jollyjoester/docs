.. _debugger_on_android:

================================================
Monaca Debugger for Android
================================================

.. rst-class:: right-menu



.. figure:: images/debugger_android/3.png
  :height: 250px
  :align: center

  Monaca Debugger for Android

.. rst-class:: clear


.. note:: If the Cordova version of your project is lower than 5.2, it might not work properly with Monaca Debugger 5.X.X. There are two ways to fix this issue:
      
  1. :ref:`upgrade Cordova version <changing_cordova_version>` of your project.
  2. use :ref:`custom built Monaca Debugger <custom_debugger_and>`.

.. rst-class:: wide-table

  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | Debugger Type         |    Monaca Debugger (Store Version)        | Custom Built Monaca Debugger                                          |
  +=======================+===========================================+=======================================================================+
  | Description           | Monaca Debugger available at the store.   | Monaca Debugger built from Monaca Cloud IDE.                          |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | Installation          | - `Play Store`__                          | Refer to :ref:`custom_debugger_and`                                   |
  |                       | - `Amazon App Store`__                    |                                                                       |  
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | :ref:`cordova_and`    | Core and some third-party Cordova plugins | In addition to core and third-party Cordova plugins, user submitted   |
  |                       | are automatically included.               | plugins (of the current project) are included.                        |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | App ID                | ``mobi.monaca.debugger``                  | App ID set by user                                                    |
  | (Android:PackageName) |                                           |                                                                       |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | Version Name          | Fixed (currently 5.0.0)                   | Display version name set by user                                      |
  | (Android:versionName) |                                           |                                                                       |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | App Version           | Fixed (currently 50000)                   | Version set by user                                                   |
  | (Android:versionCode) |                                           |                                                                       |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | :ref:`usb_and`        | Available (Chrome Dev Tools)              | Available (Chrome Dev Tools)                                          |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | :ref:`localkit_and`   | Available                                 | Available                                                             |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | :ref:`webview_and`    | Stock and Crosswalk                       | Stock and Crosswalk                                                   |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+
  | :ref:`network_and`    | Available                                 | Available                                                             |
  +-----------------------+-------------------------------------------+-----------------------------------------------------------------------+


.. _PlayStoreNormal: https://play.google.com/store/apps/details?id=mobi.monaca.debugger&hl=en
__ PlayStoreNormal_

.. _AmazonAppStore: http://www.amazon.com/Asial-Corporation-Monaca-Debugger/dp/B00H1M1518
__ AmazonAppStore_


.. _cordova_and:

Cordova Plugins
==============================

In Monaca Debugger, core and third-party Cordova plugins are automatically included. 

Monaca includes Core cordova plugins which are a minimal set of APIs such as Battery Status, Camera, Contacts, Device and so on. For a complete list of core Cordova plugins, please refer to :ref:`cordova_core_plugins`.

Monaca also includes some third-party Cordova plugins such as Statusbar, DatePicker, BarcodeScanner and so on. For a complete list of currently included third-party Cordova plugins, please refer to :ref:`third_party_cordova_index`.

While developing your project, you may need to add other third-party or :ref:`custom <custom_cordova_plugin>` Cordova plugins to your project. The standard Monaca Debugger (Store Version) doesn't have these newly added plugins. For this reason, your project might not run properly in the debugger. Therefore, you need to use Custom Built Monaca Debugger. Custom Built Monaca Debugger is a debugger which is built from a Monaca Project within Monaca Cloud IDE. Please refer to :ref:`custom_debugger_and`.


.. _usb_and:

USB Debugging
==============================

Monaca Debugger for Android supports USB debugging functions with Google Chrome browser such as:

- console debugging: using console to diplay message.
- DOM inspection: viewing and modifying DOM structure with live updates.
- JavaScript debugging: profiling JavaScript performance, setting breakpoint and execution control.

For more information, please refer to :ref:`USB Debugging with Monaca Debugger for Android Apps<usb_debugging_android>`.

.. _localkit_and:

Localkit Inspector Function
==============================

Inspector can be used when developing either on Windows or Mac OS.

.. _webview_and:

WebView
==============================

Monaca Debugger for Android contains both stock and Crosswalk WebView engines. The WebView is switched automatically depending on the type of WebView is used in each application.

.. _network_and:

Network Install
==============================

Network Install is a feature provided by Monaca Debugger for Android allowing you to install the built app (debug build only) using the debugger. For more information, please refer to :ref:`how to use Network Install feature<debugger_project_options>`.


.. _custom_debugger_and:

Build and Install Custom Built Monaca Debugger
==================================================

1. From Monaca Cloud IDE menu, go to :menuselection:`Debug --> Setup Monaca Debugger`.

2. Select :menuselection:`Debugger for Android --> Build and Install`.

  .. figure:: images/debugger_android/1.png   
    :width: 400px
    :align: left

  .. rst-class:: clear

3. This may take sometimes until your building is completed. The following screen will appear after the build is successfully completed. Then, you can use the QR code to install the debugger on your device or download the built file to your PC.

  .. figure:: images/debugger_android/4.png   
    :width: 400px
    :align: left

  .. rst-class:: clear

4. After installing the debugger on your device, sign in with your Monaca account. Then, tick :guilabel:`I've installed Monaca Debugger and logged in` and click :guilabel:`Next`.

5. Monaca Cloud IDE will then try looking for the debugger. Once it's found and connected, click :guilabel:`Run on Device` to start running the current app in your debugger right away.

  .. figure:: images/debugger_android/5.png   
    :width: 400px
    :align: left

  .. rst-class:: clear

6. By now your app should be running in your debugger. Try testing your app in the debugger and making some changes in the IDE. You will be able to see the changes reflected in the debugger once you save the changes. 

  .. figure:: images/debugger_android/6.png   
    :width: 400px
    :align: left

  .. rst-class:: clear

.. seealso::

  *See Also*

  - :ref:`Debugger Installation on Emulator<debugger_on_emulator>`
  - :ref:`Debugger Installation on iOS<debugger_on_ios>`
  - :ref:`monaca_debugger_features`
  - :ref:`debugging_monaca_app`
