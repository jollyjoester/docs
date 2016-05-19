.. _building_for_ios:

============================================================================
Building an iOS App
============================================================================

.. rst-class:: right-menu


Prerequisites
============================================================================

Before getting started, you are required to:

- subscribe to `iOS Developer Program <https://developer.apple.com/programs/ios/>`_.
- understand :ref:`types of build <types_of_build_ios>` and their requirements.

.. _types_of_build_ios:

Types of Build
^^^^^^^^^^^^^^^^^^^

In Monaca, iOS app has three types of build: debug version, test version and release version. The differences between these types of build are as follows:

.. rst-class:: wide-table

  +------------------+-----------------------------------+-----------------------------+----------------------------------------------------+
  | Types of Build   | Description                       |Requirement                  | Installation                                       |
  +==================+===================================+=============================+====================================================+
  | *Debug Build*    | Build the app to be installed on  | - Development Certificate   | - iTune                                            |
  |                  | a development device.             | - Development Provisioning  | - :ref:`Network Install <debugger_project_options>`|
  |                  |                                   |   Profile                   |                                                    |
  +------------------+-----------------------------------+-----------------------------+----------------------------------------------------+
  | *Ad Hoc Build*   | Build the app to be installed on  | - Production Certificate    | - QR Code                                          |
  |                  | multiples development devices.    | - Distribution (Ad Hoc)     | - iTune                                            |
  |                  |                                   |   Provisioning Profile      |                                                    |
  +------------------+-----------------------------------+-----------------------------+----------------------------------------------------+
  | *Release Build*  | Build the app to be distributed   | - Production Certificate    | - App Store                                        |
  |                  | in App Store.                     | - Distribution (App Store)  |                                                    |
  |                  |                                   |   Provisioning Profile      |                                                    |
  +------------------+-----------------------------------+-----------------------------+----------------------------------------------------+


.. note:: Ad Hoc distribution is a way to distribute your applications without going through the App Store. Currently, up to *100* applications which are built by using Ad Hoc provisioning profile can be shared with other iOS devices through Ad Hoc distribution. However, the application distribution from the developer organization will be limited to the development stakeholders.


Step 1: Configure iOS App in Monaca
==================================================

.. _config_ios_app_monaca:  

Configure iOS App Settings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From the Monaca Cloud IDE menu, go to :menuselection:`Config --> iOS App Settings`.

2. Fill in the necessary information of your app:

  .. rst-class:: wide-table

    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Application Name        | a name representing your app publicly such as in the Market.                                    |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | App ID                  | a unique ID representing your app. It is recommended to use reverse-domain style (for example,  |
    |                         | mobi.monaca.appname) for App ID. Only alphanumeric characters and periods (at least one period  |
    |                         | must be used) are allowed. Each segment separated by a period should begin with an alphabetic   |
    |                         | character.                                                                                      |
    +-------------------------+-------------------------------------------------------------------------------------------------+
    | Version Number          | a number representing the version of your app which will be required when uploading (publishing |
    |                         | process) your application via iTune Connect later. It needs 3 numbers separated by dots (for    |
    |                         | example, 1.10.2). Each number should be in [0-99].                                              |
    +-------------------------+-------------------------------------------------------------------------------------------------+

  .. figure:: images/build_ios/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear

  .. warning:: The App ID (set in Monaca App Settings) cannot contain asterisk (``*``); otherwise, the build will fail. This App ID must be the same as the explicit App ID you will register (or have registered) in iOS Dev Center. Read more on :ref:`register_appID`. 
  
3. After finishing the configurations, click :guilabel:`Save`.


.. _config_ios_build:  

Configure iOS Build Settings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From the Monaca Cloud IDE menu, go to :menuselection:`Config --> iOS Build Settings`.

  .. figure:: images/build_ios/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

2. You need to create a new private key or import an existing one. To create a new private key, click on :guilabel:`Generate Key and CSR` button and fill in a username (a name representing this new private key) and email address (Apple ID).

  .. figure:: images/build_ios/3.png
    :width: 400px
    :align: left

  .. rst-class:: clear

  .. note:: If you import an existing private key, you will also need to upload the certificate associated with this private key to Monaca. Please refer to :ref:`import_into_monaca`.


3. After creating a new private key, CRS file associated with the private key is also created. Download the CRS file by clicking on :guilabel:`Export` button. It will be used to issue the certificates later in iOS Dev Center.

4. Issue the certificates in iOS Dev Center and download them. Please refer to :ref:`create_cer`.

5. Upload the downloaded certificates to Monaca Cloud.


Step 2: Configure iOS App in iOS Dev Center
==================================================================

1. From `Apple Developer page <https://developer.apple.com/>`_, go to :guilabel:`Member Center`.

2. Sign in using Apple ID and password you used to enroll in the iOS Developer Program. If you haven’t enrolled in this program yet, please subscribe at `here <https://developer.apple.com/programs/ios/>`_.

3. Go to :guilabel:`Certificates, Identifiers & Profiles`. Then, the following page will appear. All actions we need to do (in order to build an iOS app) are inside :guilabel:`iOS` panel.

  .. figure:: images/build_ios/4.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. In this page, we are going to do 3 important things:

  - :ref:`create_cer`
  - :ref:`register_appID`
  - :ref:`register_dev_device`



.. _create_cer:  

Generate Certificates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

There are two types of certificates which can be issued in iOS Dev Center:

- Development certificate: required for Debug build
- Production certificate: required for either Ad Hoc or Release build.


After you have downloaded the CSR (refer to :ref:`config_ios_build`), you are now able to issue and download the certificates in iOS Dev Center. In this example, we will show you how to issue and download a Development certificate. To do this, please follow the instruction below:

1. Under iOS Apps section, go to :menuselection:`Certificates --> Development`.

2. Click the Add button (+) in the upper-right corner.

  .. figure:: images/build_ios/5.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. Choose :guilabel:`iOS App Development` and click :guilabel:`Continue`.

  .. note:: Choose :guilabel:`App Store and Ad Hoc` if you want to issue Production certificate.

4. Click :guilabel:`Continue` again and upload the CSR file that you've downloaded from Monaca Cloud IDE earlier. Then, click :guilabel:`Generate`.

5. By now, your development certificate has been issued. Please download this certificate. You will need to upload it to Monaca Cloud IDE later.
  
.. note:: Follow similar instruction in order to create a Production certificate.


.. _register_appID:  

Register App ID
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

App IDs are primarily used when creating development and distribution provisioning profiles. You can create a wildcard App ID that matches one or more apps or an explicit App ID that exactly matches your bundle ID.

In order to register your App ID, please follow these instructions:

1. Under iOS Apps section, go to :menuselection:`Identifiers --> App IDs`.

2. Click the Add button (+) in the upper-right corner.

3. Fill in the information of your App ID such as:
  
  The App ID string contains two parts (Prefix and Suffix) separated by a period (``.``)
  
  - App ID Description: Description of your App ID. You cannot use special characters such as ``@, &, *, ', "``

  - App ID Prefix: It is defined as your Team ID by default.

  - App ID Suffix: It is defined as a Bundle ID search string. There are two types of App ID Suffixes:

    .. rst-class:: wide-table

      +----------------------+-------------------------------------------------------------------------------------------------------------+
      | Explicit App ID      | Register an explicit App ID if you plan to incorporate app services such as a Game Center, In-App Purchase, |
      |                      | Data Protection, and iCloud, or just want a provisioning profile unique to a single app. Enter a unique     |
      |                      | string in the Bundle ID field of Explicit App ID which should match with the Bundle ID of your app. The App |
      |                      | ID must match the one you set in Monaca Cloud IDE as shown in :ref:`config_ios_app_monaca`.                 |
      +----------------------+-------------------------------------------------------------------------------------------------------------+
      | Wildcard App ID      | Register a wildcard App ID if you want to use a single App ID for building and installing multiple          |
      |                      | applications. Enter an asterisk (``*``) as the last digit in the Bundle ID field of wildcard App ID.        |
      +----------------------+-------------------------------------------------------------------------------------------------------------+

  - App Services: Select the services you want to enable in your app.

4. Then, click :guilabel:`Continue`. After reviewing your App ID’s info, click :guilabel:`Submit`. By now, you have completed your App ID registration into iOS Dev Center.


.. _register_dev_device:  

Register Development Devices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You are required to register your development device(s) before creating development and distribution provisioning profiles.

In order to register a device that you will be using during your app development, please follow these instructions:

1. Under iOS Apps section, go to :guilabel:`Devices`.

2. Click the Add button (+) in the upper-right corner.

3. Fill in the information of your device.

  - Name: a name represent your device (Example: MyiPhone)

  - UDID: a unique device identifier of your device. You can find this identifier by connecting your iOS device to your computer. Then, open iTunes and see the summary of your device. After that, click on the device’s *Serial Number* to reveal the UDID which consists of *40* characters. Right-click on it to copy this UDID. (See below)

    .. figure:: images/build_ios/6.png
        :width: 500px
        :align: left

    .. rst-class:: clear


4. Then, press :guilabel:`Continue`. After reviewing your device’s info, click :guilabel:`Register`. By now, you have completed your device registration into iOS Dev Center.


.. _register_provisioning:  

Create Provisioning Profiles
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

One last step before building your iOS app is creating a provisioning profile. There are two types of provisioning profile:

- Development provisioning profile: used with Development certificate for debug build.
- Distribution provisioning profile: used with Production certificate for ad hoc and release build.

In this example, we will show you how to create a Development provisioning profile. To do this, please follow the instruction below:

1. Under iOS Apps section, go to :menuselection:`Provisioning Profiles --> Development`.

2. Click the Add button (+) in the upper-right corner.

3. Choose :guilabel:`iOS App Development` and click :guilabel:`Continue`.

  .. note:: - Choose :guilabel:`Ad Hoc` if you want to create Distribution provisioning profile for Ad Hoc build.
            - Choose :guilabel:`App Store` if you want to create Distribution provisioning profile for Release build.

4. Select your App ID and click :guilabel:`Continue`.

5. Select the certificate(s) you want to include in this profile and click :guilabel:`Continue`.

6. Select the device you have previously registered for development and click :guilabel:`Continue`.

7. Input a name for the provisioning profile and click :guilabel:`Generate`.

8. Now your Development provisioning profile is ready. Please download it. You will need this file when building your iOS app in Monaca later.

.. note:: Follow similar instruction in order to create a Distribution provisioning profile.


Step 3: Start Building
=================================

1. From the Monaca Cloud IDE menu, go to :menuselection:`Build --> Build App for iOS`.

2. Select appropriate type of build you want and click :guilabel:`Next`.

  .. figure:: images/build_ios/7.png
    :width: 500px
    :align: left

  .. rst-class:: clear

3. Upload the appropriate provisioning profile (refer to :ref:`types_of_build_ios`) and click :guilabel:`Next` button.

4. It may take several minutes for the build to complete. Please wait.


.. seealso::

  *See Also*

  - :ref:`import_export_certificates_and_private_keys`
  - :ref:`app_store_distribution`
  - :ref:`building_for_android`
  - :ref:`building_for_win8`
  - :ref:`build_history`
