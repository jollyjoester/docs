.. _android_app_push_settings:

================================================
Android App Push Notification Settings
================================================

.. rst-class:: right-menu

Overview 
================================================

Monaca sends push notifications via GCM (Google Cloud Messaging). GCM is a mechanism offered by Google to send push notifications to Android applications. 

In this page, we will show what you need to do in order to enable push notifications service for Android applications with Monaca. 


.. note:: You are required to have a Google account for this configuration. 


Step 1: Enable GCM in the Google API Console
================================================

In this example, we assume that you haven't registered your application to Google Developer Console yet.

1. Go to `Google Developer Console <https://console.developers.google.com/project>`_.

2. Sign in using your Google account. 

3. Click :guilabel:`Create Project`.

4. Input the project's name and click :guilabel:`Create`. After the project is successfully created, the project dashboard page will appear.

  .. figure:: images/gcm/1.png
    :width: 400px
    :align: left

  .. rst-class:: clear

5. From the left menu, go to :menuselection:`API & auth --> APIs --> Cloud Messaging for Android`.

  .. figure:: images/gcm/2.png
    :width: 400px
    :align: left

  .. rst-class:: clear

6. Click :guilabel:`Enable API`.


Step 2: Obtain the Sender ID and Server API Key
=====================================================

Find Sender ID
^^^^^^^^^^^^^^^^^^

Sender ID is the Project Number which can be found in the Project Dashboard page as shown below:

  .. figure:: images/gcm/3.png
    :width: 500px
    :align: left

  .. rst-class:: clear


Find Server API Key
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From the Project Dashboard, go to :menuselection:`APIs & auth --> Credentials`. 

2. Click :guilabel:`add credentials` and choose :guilabel:`API key`.

  .. figure:: images/gcm/4.png
    :width: 500px
    :align: left

  .. rst-class:: clear

3. Select :guilabel:`Server key`. 

4. Name your Server key and click :guilabel:`Create`.

  .. figure:: images/gcm/5.png
    :width: 500px
    :align: left

  .. rst-class:: clear


5. Then, Server API key will be created and displayed as shown below. Copy it. You will need to use this key in Monaca Cloud IDE later. 

  .. figure:: images/gcm/6.png
    :width: 400px
    :align: left

  .. rst-class:: clear

Step 3: Configure GCM Parameters in Monaca
===================================================

1. From the Backend Panel in Monaca Cloud IDE, go to :menuselection:`Push Notification --> Backend Settings --> Push Configuration`.

  .. figure:: images/gcm/7.png
    :width: 600px
    :align: left

  .. rst-class:: clear

2. Under Android section, input the Sender ID and Server API Key and click :guilabel:`Save`. Then, the setup processes for Android app notifications are completed. 

  .. figure:: images/gcm/8.png
    :width: 600px
    :align: left



