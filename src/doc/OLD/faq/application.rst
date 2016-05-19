Application
===================================================================================================

.. _faq04~001:

Can I use an external ad network?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


For Monaca, there is no particular restriction on installing an ad network in an application. Technically, ads can be posted on WebView, so please use them according to the agreements of each ad network company. 

 
If they are InMobi, mediba (Japanese) or nend (Japanese), you can display the ads in apps created by Monaca. In regard to nend, please refer to :doc:`../sampleapp/tips/external_services/nend_ad`. Please refer to :ref:`inmobi_sample` regarding the sample app using InMobi.


Moreover, please note that in case of Android apps, the network ads will not be displayed if the permission *<uses-permission android:name="android.permission.INTERNET"></uses-permission>* in :file:`AndroidManifest.xml` was not allowed. For more information, please refer to :doc:`../reference/config/android_configuration`. 


.. _faq04~002:

Can I use external backend service?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can use external backend services with Monaca. We also provide some external services (including backend) you can integrate into your project right from Monaca Cloud IDE.

From Monaca Cloud IDE, go to :menuselection:`Config --> Service Integration --> Backend` to see exisiting external backend services. If you cannot find the backend service you want there, you can import its SDK into Monaca by going to :menuselection:`Config --> Manage Cordova Plugins --> Import Cordova Plugin`.


.. _faq04~003:

What kind of features can be used in applications developed using Monaca?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
   
With Monaca you can develop applications that are able to use all types of unique features on smartphones.(Camera, GPS, etc.)
Please refer to the document below.

* `PhoneGap API English <http://docs.monaca.mobi/3.5/en/reference/phonegap_34/en/>`_ 
* `PhoneGap API Japanese <http://docs.monaca.mobi/3.5/ja/reference/phonegap_34/ja/>`_ 
* :doc:`../sampleapp/index`

Windows Store apps are not compatible with PhoneGap API, but compatible with developments that used WinJS. 


.. _faq04~004:

Is there any way to implement Push Notification features such as membership management?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. ifconfig:: language == 'ja'

  `NIFTY cloud mobile backend <http://mb.cloud.nifty.com/>`_ をはじめとする各種バックエンドサービスを使用すれば、会員管理にも役立つ、プッシュ通知機能をプロジェクトに 組み込むことができます。特に、NIFTY cloud mobile backend では、簡単に実装できる API も提供しているので、プッシュ通知機能を手軽にご利用いただけます。

.. ifconfig:: language == 'en'

  You can implement Push Notification features such as membership management by using backend services such as `Kii Platform <http://en.kii.com/>`_ since it can be easily implemented using the provided APIs.

.. _faq04~005:

Can I develop applications that run in the background?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


One of the common issues in mobile apps development is unstable functionality due to memory issue. As a result, currently Monaca does not support the development of apps running in the background.


.. _faq04~006:

In applications that are developed using Monaca, can I embed codes written in Java? (For Android)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Monaca currently does not support the embedding of Java native codes. 

.. _faq04~007:

Can I use UIKit in applications developed using Monaca? (For iOS)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Monaca currently does not support the uses of UIKit. 

.. _faq04~008:

Can I develop applications with many different screen sizes?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to develop application with many deferent screen sizes, you can include the following mata tag in your code.

::
  
    <meta name="viewport" content="width=device-width, height=device-height, initial-scale=1, maximum-scale=1, user-scalable=no">

.. _faq04~009:

Can I use Cordova plugins?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    
For Basic and Personal plans, you can use the built-in Cordova plugins such as ChildBrowser, DatePicker, Bluetooth and so on. Please refer to :ref:`third_party_cordova_index` for all the built-in Cordova plugins provided by Monaca. However, In order to add Custom Cordova plugin, you will need to have a Gold or Platinum plan. To add a custom Cordova plugin, please refer to :ref:`custom_cordova_plugin`.

.. _faq04~010:

Tell me about restrictions for developing Windows Store apps. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
For Windows Store app development, native JavaScript and HTML5 features are used. Therefore, features such as those in PhoneGap cannot be used. For this reason, in order to develop an app runs on both Windows (Windows store app) and other platforms, you can't use features such as those in PhoneGap. Also, for Windows Store app, there are some features and properties in the standard JavaScript and HTML5 that can't be used. For more details, please refer to `HTML, CSS, and JavaScript features and difference <http://msdn.microsoft.com/en-us/library/windows/apps/hh465380.aspx>`_. 


.. _faq04~011:

Can I develop a full-screen app?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
   
You can develop a full-screen app by using predefined configuration in *AndroidManifest* or :file:`MonacaSkeleton-Info.plist` file. For more details, please refer to `here <http://docs.monaca.mobi/reference/config/ios_configuration/>`_ . 

.. _faq04~012:


Can I always use the latest version of Cordova?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Monaca supports specific Cordova versions. However, we regularly update and provide the latest Cordova version support as soon as possible.

.. _faq04~013:

How can I make font size bigger for input and textarea controls?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can fix this problem by applying following styles.

.. code-block:: css

  form input, form textarea {
    font-size: 100%;
  }

.. _faq04~015:

Cordova API and Monaca JavaScript API do not work.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Please check your code if :file:`components/loader.js` file is loaded. You can't use Cordova API and other JavaScript APIs provided by Monaca if the file was not loaded.

.. _faq04~016:

How to change the app start page from index.html to another?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Go to ``config.xml`` file under ``www`` folder.

2. Under ``<widget>`` element, input the location of the file you want for the starting page in the ``<content>`` tag. The default value is ``index.html``. See the example below:

  .. code-block:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <widget xmlns="http://www.w3.org/ns/widgets" id="com.example.helloworld" version="1.0.0">
      ...
      <content src="https://monaca.io/" /> 
    </widget>


.. warning:: This method won't work in Android Debugger downloaded from Google Play. Creating a custom Android debugger will solve this issue. Please refer to :ref:`custom_debugger_and`.



.. _faq04~017:

Limitation of version number and version code for Monaca apps
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Based on Cordova, the maximum value of version number is 99.99.99 and the corresponding maximum value of version code
is 999999 for Monaca apps.

If you want to use a larger version code value, you need to modify ``config.xml`` file directly. See below example:

.. code-block:: xml

    <widget xmlns="http://www.w3.org/ns/widgets" id="your packagename" version="xx.yy.zz">
    <!--Substitute xx.yy.zz to 100.1.3, the version code becomes 1000103.-->


.. note:: Starting from 2014/04/02, ``config.xml`` file is located under ``www`` folder. If your project is created before that, ``config.xml`` file is located as ``android/config.xml`` and  ``ios/config.xml`` for Android and iOS respectively. 

.. _faq04~018:

Cordova APIs (such as camera, compass, and so on) are not working
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When using Cordova APIs (such as camera, compass, and so on), you need to make sure that those APIs are called after they have loaded and are ready to access. 

The ``deviceready`` event fires once the Cordova has fully loaded. You can safely use Cordova APIs when this event is fired. For more information, please refer to `deviceready event <http://docs.phonegap.com/en/4.0.0/cordova_events_events.md.html#deviceready>`_.

.. note:: For Onsen UI, ``ons.ready()`` function is called when both ``deviceready`` and ``DOMContentLoaded`` events are fired. Therefore, you can deal with both events by using ``ons.ready()`` function.



.. _faq04~019:


The built app does not work, or works differently than what it runs on the debugger.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It is likely that the built app does not contain the necessary Cordova plugin.
Although Monaca Debugger contains all core plugins by default, you need to manually specify which plugin to install when you build the app. You can manage the plugins to include in the app by enabling in Manage Cordova Plugins configuration.
