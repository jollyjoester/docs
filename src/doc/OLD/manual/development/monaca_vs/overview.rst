====================================================
Monaca for Visual Studio Overview
====================================================

.. rst-class:: right-menu



Monaca for Visual Studio is an extension which allows you to develop Monaca applications using Microsoft Visual Studio IDE. Several features found in Monaca Cloud IDE are included in this extension. Therefore, app development with Monaca for Visual Studio is very similar to the app development on Monaca Cloud IDE.

  .. figure:: images/introduction/1.png
    :alt: Monaca for Visual Studio
    :width: 700px   
    :align: left

  .. rst-class:: clear


Prerequisites
====================================================

In order to use Monaca for Visual Studio, you need:

- Microsoft Visual Studio 2015 Community Edition, Professional Edition or higher editions.
- a valid plan subscription. Please refer to `Pricing <https://monaca.mobi/en/pricing>`_.
  
.. _monaca_vs_installation:

Installing Monaca for Visual Studio
====================================================

.. note:: It is necessary to install :ref:`tools for Apache Corodva <install_tools_for_apache_cordova>` in Visual Studio in order to run Monaca for Visual Studio properly. 

There are two ways to install Monaca for Visual Studio such as:

1. :ref:`install_from_vs`
2. :ref:`install_from_web`

.. _install_from_vs:

Installing from Visual Studio
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From Visual Studio menu, go to :menuselection:`Tools --> Extensions and Updates`.

2. Then, go to :menuselection:`Online --> Visual Studio Gallery`. Next, input ``monaca`` in a search box on the top-right corner. 

3. Select ``Monaca for Visual Studio 2015`` and click :guilabel:`Download`. Wait until the download is finished, then install it. 

  .. figure:: images/introduction/2.png
    :width: 700px   
    :align: left

  .. rst-class:: clear

  .. note:: If you want to have Onsen UI templates within Visual Studio, please download and install ``Onsen UI Templates for Visual Studio 2015``.

4. When the installation is completed, restart Visual Studio. Then, :guilabel:`MONACA` menu can be found in the Visual Studio menu.

  .. figure:: images/introduction/3.png
  	:width: 321px   
  	:align: left

  .. rst-class:: clear



.. _install_from_web:

Installing from Web
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Download Monaca for Visual Studion extension `here <https://visualstudiogallery.msdn.microsoft.com/21a7a495-5a24-4eab-a519-2f6e6d176049>`_.

2. Open the downloaded file and follow the installation instruction.

3. Restart Visual Studio if it is opened during installation. Then, :guilabel:`MONACA` menu can be found in Visual Studio menu. 


.. _install_tools_for_apache_cordova:

Installing Tools for Apache Cordova 
====================================================

1. From Visual Studio menu, go to :menuselection:`File --> New --> Project`.

2. Then, go to :menuselection:`Installed --> Templates --> JavaScript --> Apache Cordova Apps`.

3. Select ``Install Tools for Apache Cordova Update 7`` and click :guilabel:`OK`.

  .. figure:: images/introduction/11.png
    :width: 700px   
    :align: left

  .. rst-class:: clear

4. Click :guilabel:`Install`.

  .. figure:: images/introduction/12.png
    :width: 400px   
    :align: left

  .. rst-class:: clear

5. Please close Visual Studio before the update begins. Otherwise, the following dialog asking you to close the Visual Studio will appear.

  .. figure:: images/introduction/13.png
    :width: 400px   
    :align: left

  .. rst-class:: clear

6. Click :guilabel:`Next`.

  .. figure:: images/introduction/14.png
    :width: 400px   
    :align: left

  .. rst-class:: clear


7. Click :guilabel:`Update`. It will take sometimes until the installation completes. Please wait.

  .. figure:: images/introduction/15.png
    :width: 400px   
    :align: left

  .. rst-class:: clear


.. _monaca_vs_uninstall:

Uninstalling Monaca for Visual Studio
====================================================

To completely uninstall Monaca for Visual Studio, you need to perform the following steps:

1. :ref:`uninstall_from_vs`
2. :ref:`uninstall_from_pc`

.. _uninstall_from_vs:

Uninstalling from Visual Studio
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From Visual Studio menu, go to :menuselection:`Tools --> Extensions and Updates`.

2. Then, go to :menuselection:`Installed --> Tools`.

3. Select ``Monaca`` and click :guilabel:`Uninstall`.

  .. figure:: images/introduction/10.png
    :width: 700px   
    :align: left

  .. rst-class:: clear


.. _uninstall_from_pc:

Uninstalling from Windows PC
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Go to :menuselection:`Control Panel --> Programs --> Uninstall a program`.

2. Select ``Monaca for Visual Studio`` and click :guilabel:`Uninstall`.



Monaca Panel Features
====================================================

Once Monaca is successfully installed and added into Visual Studio IDE, please log in with a valid Monaca account.

.. figure:: images/introduction/9.png
    :width: 327px
    :align: center

.. rst-class:: clear


Run in Device
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This function is available when at least one :ref:`monaca_debugger_index` is connected to the host PC (running Visual Studio). It will run the current project in Monaca Debugger. Please refer to :ref:`How to Connect Monaca Debugger with Monaca for Visual Studio<monaca_vs_testing_debugging>`.

  .. figure:: images/introduction/4.png
      :width: 300px 
      :align: left

      Monaca Debugger is not Connected

  .. figure:: images/introduction/5.png
      :width: 346px
      :align: left

      Monaca Debugger is Connected

  .. rst-class:: clear


Build Settings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Just like in Monaca Cloud IDE, this function will open a Build Settings window which allows you to configure project settings as well as build settings such as: 

- :ref:`Cordova Plugins<cordova_plugins_setting>`
- :ref:`js_css`
- :ref:`service_integration_index`
- :ref:`Android App and Build Settings<building_for_android>`
- :ref:`iOS App and Build Settings<building_for_ios>`
- :ref:`Windows App Settings<building_for_win8>`
- :ref:`Chrome Apps Settings<building_for_chrome_app>`
  

  
.. figure:: images/introduction/6.png
    :width: 700px
    :align: center

.. rst-class:: clear

Build
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This function will open a Build window which allows you to build your project for 4 different platforms as shown in the screenshot below:

.. figure:: images/introduction/7.png
    :width: 700px
    :align: center

.. rst-class:: clear

Preferences
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

While trying to pair/connect Monaca Debugger with the PC hosting Monaca within Visual Studio, you might need to configure HTTP Server Port and Proxy Server. Please refer to :ref:`troubleshooting the Pairing<troubleshoot_pair>` on when this function is needed.

You can find this function by going to :menuselection:`MONACA --> Preferences`.

.. figure:: images/introduction/8.png
    :width: 429px
    :align: center

.. rst-class:: clear

There are two ways to define the proxy server address as follows:

1. Proxy Server with basic authentication

 .. code-block:: html

     http://user:pass@server-host:port

2. Proxy Server without basic authentication

 .. code-block:: html

     http://server-host:port


.. seealso::

  *See Also*

  - :doc:`../../../quick_start/monaca_vs/index`
  - :doc:`build_publish`
  - :doc:`pairing_debugging`

