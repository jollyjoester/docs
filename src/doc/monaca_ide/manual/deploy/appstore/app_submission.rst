.. _upload_via_ide:

================================================
Monaca Upload Feature
================================================

.. note:: In order to use this upload feature, you are required to subscribe to a valid plan. Please refer to `Pricing <https://monaca.mobi/en/pricing>`_.

.. warning:: If you use activation code to upgrade your account, you can use Monaca upload feature in case your plan supports this feature. Please `contact us <https://monaca.mobi/en/support/inquiry>`_ for more details.

Monaca allows you to upload your app to iTunes Connect right from Monaca IDE. In order to do this, please do as follows:


1. Create a release build version of your app through Monaca. Please refer to :ref:`building_for_ios`.

2. When you successfully build a release version of your app, the following screen will appear. Click on the Upload button as shown in the screen below.

  .. figure:: images/app_submission/1.png
    :width: 400px
    :align: left

  .. rst-class:: clear

3. Then, the App Upload window will appear. Click :guilabel:`Next`.

  .. figure:: images/app_submission/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

4. Fill in a valid Apple account information. Click :guilabel:`Next`.

  .. figure:: images/app_submission/3.png
    :width: 600px
    :align: left

  .. rst-class:: clear

5. Make sure you've :ref:`registered this app with iTunes Connect <apply_itune_connect>` before uploading your app. Then, tick :guilabel:`We've registered the application with iTunes Connect.`. Click :guilabel:`Upload`.

  .. figure:: images/app_submission/4.png
    :width: 600px
    :align: left

  .. rst-class:: clear

6. The uploading will start. Please wait.

  .. note:: If you upload multiple versions of the app, please make sure that each app file has different version number. Otherwise, the upload will fail.

  .. figure:: images/app_submission/5.png
    :width: 600px
    :align: left

  .. rst-class:: clear

7. If your upload is successful, the following screen will appear. It may take sometimes until the app shows up in the iTunes Connect.

  .. figure:: images/app_submission/6.png
    :width: 600px
    :align: left

  .. rst-class:: clear

  .. note:: Sometimes Monaca is successfully uploaded your app to iTunes Connect but Apple may find error(s) on their end and report to you via email. If this happens, please see the report and fix the error(s) appropriately. Then, re-upload your app.


8. Now that you successfully uploaded your app, you can start selecting it in iTunes Connect. Please refer to :ref:`Selecting the Uploaded App<select_uploaded_app>`.


.. seealso::

  *See Also*

  - :ref:`app_store_distribution`
  - :ref:`itunes_connect`