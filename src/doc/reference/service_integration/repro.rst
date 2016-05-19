.. _repro:

-----------------------------
Repro (iOS only)
-----------------------------

.. rst-class:: right-menu



`Repro <https://repro.io/>`__ is a service which provides the confirmation of how a user handles an application by recording the user's actions. Currently, it supports iOS only.

.. note:: This Repro service integration is available for all Monaca users. However, if you want to use the latest Repro plugin via `Github <https://github.com/reproio/repro-ios-sdk>`_, you can :ref:`import <import_cordova_plugin>` it. In order to import this plugin, you need to subscribe to a valid plan. Please refer to `Pricing <https://monaca.mobi/en/pricing>`_. 

Add Repro Service to Monaca
=======================================

1. For Monaca Cloud IDE, go to :menuselection:`Config --> Service Integration` or go to :menuselection:`Build Settings --> Service Integration` for Monaca Localkit.

2. Click :guilabel:`See Details` button of Repro service.

3. Then, click :guilabel:`Install` button to add it into your project.

  .. figure:: images/repro/2.png  
      :width: 600px
      :align: left
      
  .. rst-class:: clear

4. You will be asked to confirm the setup. Click :guilabel:`OK` to start the installation.


Remove Repro Service from Monaca
=======================================

1. For Monaca Cloud IDE, go to :menuselection:`Config --> Manage Cordova Plugins` or go to :menuselection:`Build Settings --> Cordova Plugins` for Monaca Localkit.

2. Look for Repro plugin and click :guilabel:`Disable` button.

  .. figure:: images/repro/3.png  
      :width: 600px
      :align: left

  .. rst-class:: clear

Configure Repro Service in Monaca
========================================

You are required to have the app's token in order to use Repro. In order to get the token, please do as follows:

1. Register your app with Repro.

2. Find the app's token by going to :menuselection:`Settings --> Setup SDK`.

  .. figure:: images/repro/4.png  
      :width: 700px
      :align: left

  .. rst-class:: clear

3. After you get the app's token, replace it in the following snippet of ``onDeviceReady`` function. Then, add this snippet to your project. 


.. code-block:: javascript

    document.addEventListener("deviceready",onDeviceReady,false);     
    function onDeviceReady() {
        Repro.setup("YOUR_APP_TOKEN");
        Repro.startRecording();
    }

.. note:: For more information on how to use Repro, please refer to `Repro Documentation <http://doc.repro.io/>`__.


Usage
==========================

.. note:: You need to run your application on a real device for Repro to record your action. 

1. Build your Monaca app. Please refer to :ref:`building_monaca_for_ios`.

2. Install the built app on a real device.

3. Start using your app for a few seconds, then press :guilabel:`Home` button. Then, the recorded video will be uploaded to Repro server after your app go to the background.

  .. figure:: images/repro/5.png  
      :width: 250px
      :align: left

  .. rst-class:: clear

4. Repro will send you an email with a link to the recorded video.