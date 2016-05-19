.. _itunes_connect:

================================================
iTunes Connect Guide
================================================

.. rst-class:: right-menu



.. raw:: html

  <div>
    <div  style="float: left;" align="left"><b>Last Updated: </b> January 28th, 2016</div>
    <br/>
  </div>


This document describes how to use iTunes Connect to submit an app for distribution through the App Store.

Prerequisite
=============================

You are required to have a `Team Agent account <https://developer.apple.com/support/roles/>`_ under `iOS Developer Program <https://developer.apple.com/>`_.


.. _apply_itune_connect:

Registering the App
===================================================

In order to register your app in iTunes Connect, please do as follows:

1. Login to `iTunes Connect <https://itunesconnect.apple.com/>`_ with your Team Agent account.

2. Go to :guilabel:`My Apps`.

3. Select :menuselection:`+ --> New App`.

  .. figure:: images/itunes_connect/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear

4. Enter the information about the app on the form that appears as seen below:

  .. rst-class:: wide-table

    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Platforms               | Choose a platform for your app.                                                                  |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Name                    | Enter your app's name as it will appear on the App Store. It can't be longer than 255 characters.|
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Primary Language        | Choose a default language for your app.                                                          |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Bundle ID               | Select a Bundle ID which can be an explicit App ID or a wildcard App ID. If it’s a wildcard App  |
    |                         | ID, you also need to specify a bundle ID suffix. If it's an explicit App ID, it must exactly     |
    |                         | match the bundle identifier in your app.                                                         |          
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Bundle ID Suffix        | Once you select a Bundle ID, the input field for Bundle ID Suffix will be displayed. It's a      |
    |                         | string that is appended to the bundle ID property if the bundle ID is a wildcard App ID. The     |
    |                         | bundle ID and bundle ID suffix must form a bundle identifier that exactly matches the bundle     |
    |                         | identifier in your app.                                                                          |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | SKU                     | Enter the code to identify the app. Although the code is up to your decision, it is necessary to |
    |                         | create an ID that will identify the app in a unique way.                                         |
    +-------------------------+--------------------------------------------------------------------------------------------------+

  .. figure:: images/itunes_connect/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

5. Click :guilabel:`Create`. Then, you will be redirected to the App Information page.

6. In the App Information page, choose a category for your app and click :guilabel:`Save`.

  .. figure:: images/itunes_connect/3.png
    :width: 600px
    :align: left

  .. rst-class:: clear

7. Go to :guilabel:`Pricing and Availability`. In this page, you will need to configure 3 main points such as price schedule, available areas for your app and volume purchase program. Then, click :guilabel:`Save`.

  .. figure:: images/itunes_connect/4.png
    :width: 600px
    :align: left

  .. rst-class:: clear

8. Go to :guilabel:`Prepare for Submission`. In this page, you will need to configure:

  - App video preview and screenshots: at least one screenshot is required.
  - Description
  - Keywords
  - Support URL
  - App icon
  - Copyright
  - Contact information.

  .. figure:: images/itunes_connect/9.png
    :width: 600px
    :align: left

  .. rst-class:: clear

9. After the configuration, click :guilabel:`Save`.



.. _upload_the_app:

Uploading the App
===================================================

In the past, it was not necessary to have a Mac environment for submission. However, since August 2012, a Mac environment has become necessary as the Application Loader is needed to upload the apps to iTunes Connect and it is only compatible with Mac. 

Fortunately, Monaca allows you to upload your app to iTunes Connect right from Monaca IDE. In other words, you don't need a Mac to upload your apps anymore. 

.. note:: For more information on how to use this upload feature, please refer to :ref:`upload_via_ide`.

Alternatively, you can use the Application Loader as described below:

1. Create and download a release build version of your app through Monaca. Please refer to :ref:`building_for_ios`.

2. From iTunes Connect, download and install Application Uploader.

  .. figure:: images/itunes_connect/10.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. Open Application Uploader and login with your Apple account.

4. Select :guilabel:`Deliver Your App` and click :guilabel:`Choose`.

  .. figure:: images/itunes_connect/5.png
    :width: 500px
    :align: left

  .. rst-class:: clear

5. Browse the release build file of your app. Then, the following screen will apear. Click :guilabel:`Next` to start uploading your app.

  .. figure:: images/itunes_connect/6.png
    :width: 500px
    :align: left

  .. rst-class:: clear

6. Once, the uploading is completed, click :guilabel:`Next` and :guilabel:`Done`. It may take sometimes until the app shows up in the iTunes Connect.

  .. note:: If you upload multiple versions of the app, please make sure that each app file has different version number. Otherwise, the upload will fail.

.. _select_uploaded_app:

Selecting the Uploaded App
===================================================

Once you successfully uploaded your app to iTunes Connect, it can be selected to submit to the App Store. Please do as follows:

1. From iTunes Connect, go to :guilabel:`Prepare for Submission`. Under Build section, click :guilabel:`+`.

  .. figure:: images/itunes_connect/7.png
    :width: 600px
    :align: left

  .. rst-class:: clear

2. Select your build and click :guilabel:`Done`. 

  .. figure:: images/itunes_connect/8.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. Click :guilabel:`Save`.


Submitting the App
===================================================

Now that you have completed the necessary configurations, your app is ready to be submitted. 

1. From iTune Connect, go to :guilabel:`Prepare for Submission`.

2. Click :guilabel:`Submit for Review`.


After you've successfully submitted the app, you will need to wait for the review from Apple. Apple will review your app and see if it is eligible or qualified to be in App Store. Usually, it takes two weeks for the review. Therefore, please wait patiently for it.


.. _app_release:

Publishing the App
===================================================

When your app is accepted by Apple, it will be up in the App Store.

.. note:: The large app icon, which was not necessary before, is now required for the submission. In fact, the required environment and information have changed in the submission procedure for the registration. If a registration/submission is not successful, please make sure you complete necessary configurations properly.



.. seealso::

  *See Also*

  - :ref:`upload_via_ide`
  - :ref:`building_for_ios`
  - :ref:`google_play_distribution`
  - :ref:`non_market_app_distribution`
  - :ref:`amazon_store_distribution_en`
