IDE
================================================================


.. _faq02~001:

What do you need in order to use Monaca?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Internet access is required for your PC and your mobile device. Also, an Internet browser is needed for developing mobile apps using Monaca Cloud IDE. We recommend to use **Safari** and **Google Chrome**. For users of other browsers, please install `Google Chrome <http://google.com/chrome>`_ or `Safari <http://apple.com/safari>`_. 

Monaca users also can develop on their local PC without using Monaca Cloud IDE. This can be done by using :ref:`Monaca Localkit <monaca_localkit_index>`, :ref:`Monaca CLI <monaca_cli_index>` and :ref:`Monaca for Visual Studio <monaca_vs_index>`.

Moreover, it is necessary to register to the `iOS Developer Program <https://developer.apple.com/programs/ios/>`_ to develop iOS applications.

.. _faq02~002:

What kinds of knowledge are required for developing mobile apps using Monaca?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to develop mobile apps using Monaca, it is necessary to have some knowledge of HTML5/CSS3/JavaScript. Monaca does not required you to have knowledge of Java (Android) and Objective-C (iPhone/iPad) which are commonly used for general mobile apps development. 

.. _faq02~003:

Why can I develop smartphone applications with Monaca even without using Java or Objective-C?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  
Monaca utilizes `PhoneGap <http://phonegap.com/>`_ as the library for accessing unique features of mobile devices. Through PhoneGap, your app can access unique features of mobile device using JavaScript, so it is not necessary to use Java (Android) and Objective-C (iPhone/iPad).

.. _faq02~004:

Tell me about the operating systems of devices which are compatible with Monaca. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Monaca is currently supporting the following operating systems:

* Android 4 or higher
* iOS 8 or higher
* Windows 8.1
* Chrome OS
* Kindle Fire OS

.. _faq02~005:

How can I remove a permission to use an unused feature in an Android app?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can control the permissions of any features for an application in the *<uses-permission>* element in an :file:`AndroidManifest.xml` file. For details, please refer to :doc:`../reference/config/android_configuration`. 

.. _faq02~006:

I don't have a Mac, but can I create an iOS application? 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Even if you don't have a Mac, you can still use PC to create iOS apps using Monaca because Monaca can be operated via web browser. However, when building an iOS app and installing it on a device, you must register with `iOS Developer Program <https://developer.apple.com/programs/ios/>`_. Moreover, when you make a release build and submit the app to the App Store, you need an application uploader software provided by Apple which only runs on Mac. In other words, you will need Mac when uploading the app to the App Store. 

.. _faq02~007:

I can't open Monaca Cloud IDE.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As of Sept 2014, Monaca Cloud IDE supports Google Chrome and Safari web browser. It does not support mobile browser. Please make sure using the appropriate browser.

.. _faq02~008:

Can I use my own development environment to develop Monaca apps?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, Monaca comes with :ref:`Monaca Localkit <monaca_localkit_index>` and :ref:`Monaca CLI <monaca_cli_index>` which allow you to do the local development using preferred IDE or code editor. 

.. _faq02~009:

I am a Visual Studio user, can I use Visual Studio to develop Monaca apps?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you are familiar with Visual Studio, Monaca provides an extension :doc:`../../manual/development/monaca_vs/index` to develop Monaca apps. This extension allows to develop as in Monaca Cloud IDE except using the functionalities of Visual Studio.

.. _faq02~010:

Application does not run on preview in the IDE
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cordova APIs and cross-domain ajax requests are not supported in the browser preview.

.. _faq02~011:

Why I can't archive my project?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Project archiving is only available for paid users.


Why Live Preview can't get resource from other domain?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Because of `same origin policy <http://en.wikipedia.org/wiki/Same-origin_policy>`_ which restricts the cross-origin resource sharing. It prevents JavaScript from making requests across domain boundaries, and has spawned various hacks for making cross-domain requests.


How to enable Cross-Origin Resource Sharing (CORS)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to add support to the server, you just need to add the following header into CORS (Cross-Origin Resource Sharing) response:

::

  Access-Control-Allow-Origin: *


In order to permit the url from which app and debugger are able to get resources, you can either config using

- Monaca IDE: :ref:`for iOS<ios_config_ide>` and :ref:`for Android<android_config_ide>`.
- or configuration file: :ref:`for iOS<access_origin>` and :ref:`for Android<access_origin_android>`.


