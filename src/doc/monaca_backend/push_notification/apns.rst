.. _ios_app_push_settings:

================================================
iOS App Push Notification Settings
================================================

.. rst-class:: right-menu


Overview
================================================

APNs (Apple Push Notification Service) is a push notification mechanism created by Apple to use with iOS apps. 

In this page, we will show what you need to do in order to enable push notifications service for iOS applications with Monaca. 

There are two types of Push certificates:

- Development Push Certificate: required for Debug build.
- Production Push Certificate: required for either Ad Hoc or Release build.

Please refer to :ref:`types_of_build_ios`.

.. note:: In order to build iOS applications and send push notifications to them, it is necessary to join the `iOS Developer Program <https://developer.apple.com/programs/ios/>`_. 


Step 1: Create a Request File in Monaca Cloud IDE
===========================================================

1. From the Backend Panel in Monaca Cloud IDE, go to :menuselection:`Push Notification --> Backend Settings --> Push Configuration`.

  .. figure:: images/apns/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear

2. Under iOS section, select :guilabel:`Generate Key and Make CSR` of Development or Production Push Certificate as you prefer.

  .. figure:: images/apns/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. Enter a name (for the key) and email address (the Apple ID you have registered with the iOS Dev Center) and click :guilabel:`Generate`. 

  .. figure:: images/apns/3.png
    :width: 300px
    :align: left

  .. rst-class:: clear

4. After the CSR has been created, download it.


Step 2: Create Push Certificates in iOS Dev Center
=========================================================

There are two types of Push certificates which can be issued in iOS Dev Center:

- Development SSL Certificate: required for Debug build
- Production SSL Certificate: required for either Ad Hoc or Release build.

1. From `Apple Developer page <https://developer.apple.com/>`_, go to :guilabel:`Member Center`.

2. Sign in using Apple ID and password you used to enroll in the iOS Developer Program. If you haven’t enrolled in this program yet, please subscribe at `here <https://developer.apple.com/programs/ios/>`_.

3. Go to :guilabel:`Certificates, Identifiers & Profiles`. Then, the following page will appear.

  .. figure:: images/apns/4.png
    :width: 600px
    :align: left

  .. rst-class:: clear

4. Register your App ID as an Explicit App ID and enable Push Notifications service in iOS Dev Center. Please refer to :ref:`register_appID`.

  .. warning:: Push notification can't be used if your App ID is registered as Wildcard and Push Notifications service is not enable.

5. From the list of App IDs, Select on your explicit App ID and click :guilabel:`Edit`.

  .. figure:: images/apns/5.png
    :width: 600px
    :align: left

  .. rst-class:: clear

6. Click :guilabel:`Create Certificate` button of the type of certificate you want to create. And click :guilabel:`Continue`.

  .. figure:: images/apns/6.png
    :width: 600px
    :align: left

  .. rst-class:: clear

7. Browse the CSR file you downloaded from Monaca Cloud IDE earlier and click :guilabel:`Generate`.

8. Once, your certificate is generated, please download it. You will need to upload this file to Monaca Cloud IDE later.


Step 3: Upload Push Certificates to Monaca Cloud IDE
=========================================================

1. From the Backend Panel in Monaca Cloud IDE, go to :menuselection:`Push Notification --> Backend Settings --> Push Configuration`.

  .. figure:: images/apns/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear

2. Under iOS section, select :guilabel:`Upload Certificate` of Development or Production Push Certificate appropriately. After that, the push notificaton configuration for iOS app is now completed. 

  .. figure:: images/apns/7.png
    :width: 600px
    :align: left


