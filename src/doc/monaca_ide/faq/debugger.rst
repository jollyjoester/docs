Debug
===================================================================================================


.. _faq06~001:

What is the Monaca Debugger?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Monaca Debugger is an application for debugging that can check the functionality of the app on an actual device without building. 
When using Monaca Debugger, any changes made to the code immediately reflect to the actual running device. No build and run process are required.
This would help to speed up the development and testing process. For more details, please refer to  :doc:`../manual/debugger/index`. 


.. _faq06~002:

Are the operations of an app on the Monaca Debugger the same as when the app is installed on an actual device?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The app operations on Monaca Debugger may differ from the ones on the actual device. 
After building and installing the app, it is necessary to check its icon, installation and operations without Monaca Debugger. 
Moreover, the app works more slowly on Monaca Debugger than the built apps because of the connection to the Monaca Cloud IDE. 


.. _faq06~003:

The application using Monaca Debugger doesn't seem to be running properly. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Please try the following instructions:

* Make sure that you are having the latest version of Monaca Debugger.
* Reset the cache: in Monaca debugger menu select "Delete the sync data" and restart the app. 

If the issue still persists, please contact us via `Monaca Support <https://monaca.mobi/en/support/index>`_.

.. _faq06~004:

Before building, can I check application operations during development?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Monaca provides utiliy to check the display and operations of application which is :ref:`Live Preview<preview_tab>` feature on the Monaca Cloud IDE. In addition, you can check application operations on the device prior to building by using Monaca Debugger. Both are very useful tools for improving development efficiency, so please make the most use of them. 


.. _faq06~005:

The debug log is not displayed. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For some devices, such as devices from HTC, there are confirmed cases of which the debug log cannot be displayed. If possible, please inform us of any information about devices that have such problem via `Monaca Support <https://monaca.mobi/en/support/index>`_,  we will look into it and provide the solution as soon as possible. 

.. _faq06~006:

Why are there two types (App Store version and Build version) of iOS version for Monaca Debugger?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Due to the reviewing process of Apple App Store, the availability of the latest version of Monaca Debugger in App Store may take sometimes. Therefore, to provide the lastes version of iOS-based Monaca Debugger as soon as possible to our customers, we have prepared other option which is the build version of Monaca debugger.


.. _faq06~007:

When I started the app on Android, the app crashed. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There may have problems of configuration in :file:`AndroidManifest.xml` file. If you use PhoneGap, please make sure to have this setting: *<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"></uses-permission>*. For details, please refer to :doc:`../reference/config/android_configuration`. 


.. _faq06~009:

Monaca Debugger is not working. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Please try to reinstall Monaca Debugger. If it is still not working, please `contact us <https://monaca.mobi/en/support/inquiry>`_ . 

.. _faq06~010:

I cannot use CSS and JavaScript files in Live Preview. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

While reading external JavaScript or CSS codes, there is a possibility that they are not readable for some reasons such as requirement for an authentication. 


.. _faq06~011:

Cannot Login to Monaca Debugger. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following issues are the common issues and solutions when logging in Monaca Debugger:

* If your password consists of non-alphanumeric character(s). Please change your password to alphanumeric character only.
* Please check your Internet connection.
* The email address was auto-completed. Please manually input the email address and password. 


.. _faq06~012:

JavaScript error when loading Angular.js or other external library.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In some cases, Monaca Debugger may assume the exceptions occurs internally by the external JavaScript library as errors. As long as the errors do not stop the functionality of your app, it should be fine to ignore them. Please note that in the built version, these errors should not be occurred when running on actual device.

.. _faq06~013:

What is the difference between Monaca Debugger and its custom build version?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here are some important differences:

1. Where you download the debugger: Monaca Debugger can be downloaded from application markets. Custom build debugger can be installed from Monaca IDE.

2. Plugins included in the debugger: Monaca Debugger contains all core Cordova plugins. Custom build debugger will contain the plugins user submitted from Cordova Plugins configuration page.

3. USB debugging support (iOS Only): For iOS devices, USB debugging can be only enabled when the app is debug built. Therefore, you cannot do USB debugging on Monaca Debugger downloaded from App Store. For more details, please see :doc:`../manual/debugger/installation/debugger_ios`.

.. _faq06~014:

How can I debug my application?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We are providing 3 different ways to debug your application.

1. Debug using preview panel
2. Debug using Monaca Debugger with Monaca IDE (Weinre)
3. Debug using Monaca Debugger with USB debugging

For more details, please refer to :doc:`../manual/debugger/debug`.

.. _faq06~15:

What is a network install?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Network installation is a way to install your debug or ad-hoc built app to your devices from Monaca Debugger. For more details, please refer to :ref:`Network Install for Android <network_and>` or :ref:`Network Install for iOS <network_ios>`.
