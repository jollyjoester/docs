.. _apps_flyer:

=======================================
AppsFlyer
=======================================

`AppsFlyer <https://www.appsflyer.com/overview/>`_ is the market leader in mobile advertising attribution and analytics, helping marketers to pinpoint their targeting, optimize their ad spend and boost their ROI (Return on Investment).

AppsFlyer allows users to monitor and track application installations, downloads, and conversions. The AppsFlyer API allows developers to access and integrate the functionality of AppsFlyer with other applications.


.. note:: The AppsFlyer service integration is available for all Monaca users. However, if you want to use the latest AppsFlyer plugin via `Github <https://github.com/monaca-plugins/com.appsflyer.phonegap.plugins.appsflyer>`_, you can :ref:`import <import_cordova_plugin>` it. In order to import this plugin, you need to subscribe to a valid plan. Please refer to `Pricing <https://monaca.mobi/en/pricing>`_. 


Add AppsFlyer to Monaca
=======================================

1. For Monaca Cloud IDE, go to :menuselection:`Config --> Service Integration` or go to :menuselection:`Build Settings --> Service Integration` for Monaca Localkit.

2. Click :guilabel:`See Details` button of AppsFlyer service.

3. Then, click :guilabel:`Install` button to add it into your project.

  .. figure:: images/apps_flyer/1.png  
      :width: 600px
      :align: left
      
  .. rst-class:: clear

4. You will be asked to confirm the setup. Click :guilabel:`OK` to start the installation.


Configure AppsFlyer in Monaca
========================================

After adding AppsFlyer to your Monaca project, you need to make some configurations before starting to use the plugin. Please follow the configuration below:


1. Add the following xml to your :file:`config.xml` in the root directory of your ``www`` folder:

  .. code-block:: xml

      <!-- for iOS -->
      <feature name="AppsFlyerPlugin">
          <param name="ios-package" value="AppsFlyerPlugin" />
      </feature>


  .. code-block:: xml

      <!-- for Android -->
      <feature name="AppsFlyerPlugin">
          <param name="android-package" value="com.appsflyer.cordova.plugin.AppsFlyerPlugin" />
      </feature>


2. For Android, add the following xml to your :file:`AndroidManifest.xml`:

  .. code-block:: xml

      <uses-permission android:name="android.permission.INTERNET" />
      <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
      <uses-permission android:name="android.permission.READ_PHONE_STATE" />

3. Add new app on AppsFlyer dashboard. Make sure that the value in the manifest and the value entered in the dashboard are identical. If you want to track installations for Android-Out-Of-Store Applications, please take a look `here <https://support.appsflyer.com/hc/en-us/articles/207447023-Tracking-Installs-for-Out-Of-Store-Applications>`_.


4. Add following lines to your code to initialize the tracking with your own AppsFlyer dev key:

  .. code-block:: javascript

      document.addEventListener("deviceready", function(){
          var args = [];
          var devKey = "xxXXXXXxXxXXXXxXXxxxx8";   // your AppsFlyer devKey
          args.push(devKey);
          var userAgent = window.navigator.userAgent.toLowerCase();

          if (/iphone|ipad|ipod/.test( userAgent )) {
              var appId = "123456789";            // your ios app id in app store
              args.push(appId);
          }
          window.plugins.appsFlyer.initSdk(args);
      }, false);

5. Test your app for `Android <https://support.appsflyer.com/hc/en-us/articles/207032136-Testing-AppsFlyer-Android-SDK-Integration-Before-Submitting-to-Google-Play>`_/`iOS <https://support.appsflyer.com/hc/en-us/articles/207032046-Testing-AppsFlyer-iOS-SDK-Integration-Before-Submitting-to-the-App-Store->`_ before submitting to the Google Play/App Store.

.. note:: For more information on how to use AppsFlyer, please refer to `AppsFlyer Documentation <https://support.appsflyer.com/hc/en-us>`_.


Usage
==========================

Once, you have successfully configured AppsFlyer, the plugin is now ready to be used. In this section, we will briefly describe some AppsFly APIs. 


Set Customer User ID (Advanced)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Setting your own custom ID will enable you to cross-reference your own unique ID with AppsFlyer’s user ID and the other devices’ IDs. This ID will be available at AppsFlyer CSV reports along with postbacks APIs for cross-referencing with you internal IDs.

.. code-block:: javascript

    window.plugins.appsFlyer.setAppUserId(userId);


.. note:: The ID must be set during the first launch of the app at the SDK initialization. The best practice is to call to this API during deviceready event if possible.


Set Currency Code (Optional)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

By default, the currency code is set to be ``USD``. You can change it by using the following API:

.. code-block:: javascript

    //For example, you want to change to British Pound
    window.plugins.appsFlyer.setCurrencyCode("GBP");


.. note:: For all acceptable currency codes, please refer to `ISO 4217 Currency Codes <http://www.xe.com/iso4217.php>`_.


In-App Events Tracking API (optional)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In-app events help you track how loyal users discover your app, and attribute them to specific campaigns/media-sources. Please take time to define the event(s) you would like to measure to allow you to track ROI (Return on Investment) and LTV (Lifetime Value).

The ``trackEvent`` method allows you to send in-app events to AppsFlyer analytics. This method allows you to add events dynamically by adding them directly to the application code.

.. code-block:: javascript

    // eventName - any string to define the event name. For example: “registration” or “purchase”
    // eventValue - the sales value. For example: 0.99 or 0.79
    window.plugins.appsFlyer.sendTrackingWithEvent(eventName, eventValue);
    // window.plugins.appsFlyer.sendTrackingWithEvent(eventName, "");


Rich In-App Events Tracking API (optional)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

AppsFlyer’s rich in­-app events provide advertisers with the ability to track any post­-install events and attribute them to a media source and campaign. An in­-app event is comprised of an event name and event parameters.

.. code-block:: javascript

    var eventName = "af_add_to_cart";
    var eventValues = {"af_content_id": "id123", "af_currency":"USD", "af_revenue": "2"};
    window.plugins.appsFlyer.trackEvent(eventName, eventValues);


Get AppsFlyer’s Unique Device UID (Advanced)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This API is used to get AppsFlyer’s proprietary device ID. AppsFlyer device ID is the main ID used by AppsFlyer in the Reports and APIs.

.. code-block:: javascript

    // getUserIdCallbackFn - callback function
    window.plugins.appsFlyer.getAppsFlyerUID(getUserIdCallbackFn);

Here is an example of how to use this API:

.. code-block:: javascript

    var getUserIdCallbackFn = function(id) {
        alert('received id is: ' + id);
    }
    window.plugins.appsFlyer.getAppsFlyerUID(getUserIdCallbackFn);



Accessing AppsFlyer Attribution/Conversion Data from the SDK (Deferred Deep-linking)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

AppsFlyer allows you to access the user attribution data in real time directly at the SDK level. It enables you to customize the landing page a user sees on the very first app open after a fresh app install. This is commonly referred to as “deferred” deeplinking. This is very common on the web, however there is a big challenge doing this in the mobile app ecosystem. Luckily, AppsFlyer provides support for all cases and platforms.

Read more on `Accessing AppsFlyer Attribution or Conversion Data from the SDK for iOS <https://support.appsflyer.com/hc/en-us/articles/207032096-Accessing-AppsFlyer-Attribution-Conversion-Data-from-the-SDK-Deferred-Deeplinking->`_.

.. note:: AppsFlyer plugin will fire ``onInstallConversionDataLoaded`` event with attribution data. You must implement an event listener to receive the data.

.. code-block:: javascript

    document.addEventListener('onInstallConversionDataLoaded', function(e){
        var attributionData = (JSON.stringify(e.detail));
        alert(attributionData);
    }, false);


Remove AppsFlyer from Monaca
=======================================

1. For Monaca Cloud IDE, go to :menuselection:`Config --> Manage Cordova Plugins` or go to :menuselection:`Build Settings --> Cordova Plugins` for Monaca Localkit.

2. Under :guilabel:`Enabled Plugins` section, hover over AppsFlyer plugin and click :guilabel:`Remove` button.

  .. figure:: images/apps_flyer/2.png  
      :width: 600px
      :align: left