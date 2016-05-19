.. _building_for_chrome_app:

============================================================================
Building for Chrome Apps
============================================================================

.. rst-class:: right-menu

.. _chrome_apps_settings:

Step 1: Configure Chrome Apps
==========================================

1. From the Monaca Cloud IDE menu, go to :menuselection:`Config --> Chrome Apps Settings`.

2. Fill in the necessary information of your app:

  .. rst-class:: wide-table

    +-------------------------+-------------------------------------------------------------------------------------------------+
    | App Name                | Enter the application name. It is displayed in the following locations: install dialog,         |
    |                         | management UI, and Chrome Web Store.                                                            |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Short Name              | Enter a short name to be displayed in case that there is not enough space displaying the full   |
    |                         | App Name such as App launcher or Chrome tab bar.                                                |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Description             | Enter the description of the application. It is a plain text string no more than 132 characters.|
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Version                 | Enter the version of the application.                                                           |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | This app works offline  | Check if your app works offline.                                                                |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Allowed Hosts           | Specify the host permission. It is required if extensions or apps need to interact with code    |
    |                         | running on page such as cross-origin XMLHttpRequests, content injection script, and the         |
    |                         | extension's cookies API that requires host permission.                                          |
    +-------------------------+-------------------------------------------------------------------------------------------------+

  .. figure:: images/chrome/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear
    
3. After finishing the configurations, click :guilabel:`Save`.


.. _build_chrome_app:

Step 2: Start Building
==========================================

1. From the Monaca Cloud IDE menu, go to :menuselection:`Build --> Build for Chrome Apps`.

2. Click :guilabel:`Next`.

  .. figure:: images/chrome/2.png
    :width: 500px
    :align: left

  .. rst-class:: clear

3. After the build is successfully completed, download the zip file of the built app.

  .. figure:: images/chrome/3.png
    :width: 500px
    :align: left

  .. rst-class:: clear

Step 3: Install the App
==========================================

1. Open Chrome browser and type :guilabel:`chrome://extensions`. 

2. Extract the downloaded zip file.

3. Drag and drop the extracted folder into Chrome Extenstions page. This will install the app as Chrome extension.

  .. figure:: images/chrome/4.png
    :width: 600px
    :align: left

  .. rst-class:: clear

4. Now your app is installed and ready to launch. It’s also automatically added to Chrome App Launcher. To run the app, click :guilabel:`Launch` (as shown in the screenshot above) or click on it from Chrome App Launcher (as shown in the screenshot below).

  .. figure:: images/chrome/5.png
    :width: 600px
    :align: left

  .. rst-class:: clear


.. seealso::

  *See Also*

  - :ref:`building_for_android`
  - :ref:`building_for_ios`
  - :ref:`building_for_win8`
  - :ref:`google_play_distribution`
  - :ref:`build_history`
