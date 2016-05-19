.. _amazon_store_distribution_en:

================================================================
Amazon Appstore Distribution
================================================================

.. rst-class:: right-menu



Prerequisite
=============================

In order to publish Android apps at Amazon Appstore, you will need to create a developer account at `Amazon Apps Developer Portal <https://developer.amazon.com/appsandservices>`_. The registration is free.

Create a Release Build of the App
==========================================

Using Monaca Cloud IDE build feature, you can build a release version of your app and upload it to Amazon Appstore. Follow the steps in :ref:`building_for_android` to build the app with “Release Build”. Then, download the built app (APK file).

.. _register_app_in_amazon:

Register the Apps in Amazon AppStore
===============================================

1. Go to `Amazon Apps Developer Portal <https://developer.amazon.com/appsandservices>`_ and login with a valid Amazon developer account. 

2. Under :guilabel:`DASHBOARD` tab, click :guilabel:`Add a New App`.

  .. figure:: images/amazon_store/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. Select :guilabel:`Android` and click :guilabel:`Next`.

4. The New App Submission page will appear. In this page, you will need to fill in the necessary information such as:

  .. rst-class:: wide-table

    +-------------------------+--------------------------------------------------------------------------------------------------+
    | App title               | Name of your app                                                                                 |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Category                | Select a category for your app.                                                                  |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Customer support contact| You can either use your default support information or input new information about email address,|
    |                         | phone number and website.                                                                        |
    +-------------------------+--------------------------------------------------------------------------------------------------+

5. Click :guilabel:`Save`. Then, the following page will appear:

  .. figure:: images/amazon_store/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

6. Go to :guilabel:`Availability & Pricing` tab, select appropriate type of your app and answer listed questions. Then, click :guilabel:`Save`.

  .. figure:: images/amazon_store/3.png
    :width: 600px
    :align: left

  .. rst-class:: clear

  .. note:: Amazon covers over 200 countries. Your app can only be released after it has been approved.

7. Go to :guilabel:`Description` tab. In this page, you will need to fill in the following necessary information and click :guilabel:`Save`.

  .. rst-class:: wide-table

    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Display Title           | Name of your app                                                                                 |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Short description       | Description of your app shown in the store.                                                      |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | long description        | Description of your app shown in the store.                                                      |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Product feature bullets | Input a list of your app's features. They will be displayed in Amazon.com website.               |
    +-------------------------+--------------------------------------------------------------------------------------------------+

8. Go to :guilabel:`Images & Multimedia` tab. In this page, you will need to upload at least 3 screenshots, a small icon (114x114 PNG file) and a large icon (512x512 PNG file) of your app and click :guilabel:`Save`.

9. Go to :guilabel:`Content Rating` tab. In this page, you will be asked to complete a questionnaire regarding content rating for your app. Complete the questionaire and click :guilabel:`Save`.

10. Go to :guilabel:`Binary File(s)` tab. In this page, you will need to fill in the following necessary information and click :guilabel:`Save`.

  .. rst-class:: wide-table

    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Apply Amazon DRM?       | Select Yes if you want to protect your application from unauthorized.                            |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Binary file             | Upload your APK file. There is no size restriction for an APK file. However, files larger than   |
    |                         | 150 MB will need to be uploaded via                                                              |
    |                         | `SFTP <https://developer.amazon.com/ftp/account.html?appId=MPU22LL128ECT>`_.                     |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Device Support          | Select only the devices you intend to target with this binary file.                              |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Language Support        | Select available language support for your app.                                                  |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Export Compliance       | Check this if your app may be imported to and exported from the United States and all other      |
    |                         | countries.                                                                                       |
    +-------------------------+--------------------------------------------------------------------------------------------------+
    | Use Amazon Maps         | Amazon devices do not support the Google Maps API. However, the Amazon Maps API                  |
    | Redirection             | provides interface parity with the Google Maps v1 API.                                           |
    +-------------------------+--------------------------------------------------------------------------------------------------+

11. After completing the configuration, click :guilabel:`Save draft`. At this point, your app should be ready to be published.

Release the App
========================

You can't publish your app unless you properly fill in necessary information related to your app. Once, you successfully complete the required information, click on :guilabel:`Submit App` to release your app. This button is disable if the required information is not completed properly.

After submission is complete, Amazon will review your app. The security of the app will be the primary concern. Review typically takes 1-2 days to complete.

After approved by Amazon, your app will be published on the Amazon Appstore for Android. The release date will be the specified date and time you have set in Step 6 in :ref:`register_app_in_amazon`, or as soon as it’s approved if you haven’t set any date or time yet.

  .. figure:: images/amazon_store/4.png
    :width: 600px
    :align: left

  .. rst-class:: clear

Inquiry
========================

You can contact `Amazon customer support <https://developer.amazon.com/public/support/contact/contact-us>`_ at the Amazon Appstore for Android with any inquiries. They can assist you with various issues including how to submit your app or use the API.


Amazon Badges for Amazon Appstore for Android
========================================================================

You can use Amazon badges to promote the availability of your app on the Amazon store. Badges are available from `Amazon Badges <https://developer.amazon.com/public/support/legal/tuabg>`_.


.. seealso::

  *See Also*

  - :ref:`building_for_android`
  - :ref:`google_play_distribution`
  - :ref:`app_store_distribution`
  - :ref:`non_market_app_distribution`

