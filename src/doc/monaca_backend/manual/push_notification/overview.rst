.. _push_notification_manual:

================================================
Introduction to Push Notification
================================================

.. rst-class:: right-menu


What is Push Notification?
================================================

Push notification is a type of notification sent from a server to an application. The push notification function can send the following kinds of information to applications:

1. *Text*: It's simply a pure text sent to an application
2. *Badge*: It's a round, red, numerical icon that appears on the top right corner of an application icon.
3. *Sound*: It's played to alert the user of a new notification.
4. *JSON Data*: It's data in JSON format used by applications. 

.. note:: The types of push notifications you can use with Monaca are text and badges. it is not possible to send sound notifications with Monaca. 

The behavior of an application upon receiving a push notification differs depending on the operating system and whether the application is opened or closed. On Android devices, a text message is displayed in the upper portion of the screen in a notification bar. On iOS devices, the push notification is displayed in a pop-up dialogue box. 

How to Send Push Notification Using Monaca
================================================


In order to send push notifications from Monaca Cloud IDE, you need to have Monaca Backend first. If you don't have one yet, please refer to :ref:`Monaca Backend Tutorial <cloud_ide_adding_backend>` or :ref:`backend_control_panel_getting_started` on how to create a Monaca Backend.

In order to send push notifications from Monaca Cloud IDE, please do as follows:

1. From Monaca Cloud IDE, click on :guilabel:`Cloud` icon and select :guilabel:`Push Notification`.

2. The Push Status & History tab will appear as shown below:

  .. figure:: images/overview/1.png
      :width: 600px
      :align: left

  .. rst-class:: clear


3. From the Push Status & History tab, click :guilabel:`Push to App`. Then the following screen will appear:

  .. figure:: images/overview/2.png
      :width: 400px
      :align: left

  .. rst-class:: clear


4. Choose the intended OS. When sending a push notification to an application, it is necessary to change the settings depending on whether the application is on an Android or iOS device. For information, please refer to :ref:`android_app_push_settings` and :ref:`ios_app_push_settings`.

5. Fill in necessary information regarding the push notification as shown below:

  ================= =======================================================================================================================================
  Field              Description
  ================= =======================================================================================================================================
  Title              Only required on Android. It will be displayed in the title of the notification area. 

  Message            Required on both platforms. It will be displayed as the main content of the notification. 

  Badge              Only available on iOS. If you enable this function and set the field to an Integer of 1 or greater, it will be displayed in the top 
                     right corner of the app icon. 

  JSON Data          Optional. It defines the data sent to the application once the user opens the notification. 
  ================= =======================================================================================================================================

6. Click :guilabel:`Add` button to send the push notification. The notification will be queued and then sent immediately.



Confirmation of Push Notification Delivery
================================================

You can monitor your push notification activities in the Push Status & History page. In this page, you can see various information related to each push notification such as:

- Platform: The platform of the recipient.
- Status: Status of the push notification which can be Queued or Finished.
- Date: The date and time when sending the push notification.
- Devices: It displays ``Successful Distribution Number/Total Number of Distribution`` in which Successful Distribution represents the number of successfully sent notification while the Total Number of Distribution is the total number of sent notifications. (See the example in the screenshot below.)
- Message: The content of the notification.

  .. figure:: images/overview/3.png
      :width: 600px
      :align: left

  .. rst-class:: clear


How to Receive JSON Data
================================================

When sending a push notification, data can be sent from the application and received by a JavaScript program. You can receive JSON data by using ``monaca.cloud.Push.setHandler`` function. Please specify callback at the first parameter of the function, and the JSON data will be passed to the callback.

.. note:: The callback function will be called after the page is loaded; However, there may be some time lag. Therefore, please be cautious about this.

An example of the data sent from an application after receiving a push notification is shown below.

.. code-block:: javascript

    monaca.cloud.Push.setHandler(function(data) {
      // data variable contains information sent from push notification
      console.log(data);
      console.log(data.item)
    });



.. seealso::

  *See Also*

  - :ref:`Monaca Backend APIs for Push Notifications <push_notification_api>`
  - :ref:`Monaca Backend Management APIs for Push Notifications <push_notification_for_backend_management_api>`
