.. _import_export_certificates_and_private_keys:

================================================================================
Build Settings between Monaca and Xcode
================================================================================

.. rst-class:: right-menu


If you want to develop your Monaca app in both Monaca Cloud IDE and Xcode on your Mac OS X, you will need to synchronize the build settings (private keys and certificates) of the app you use in these two environments.


In this page, we will show you how to: 

- :ref:`from_mac_to_monaca`
- :ref:`from_monaca_to_mac`


.. _from_mac_to_monaca:

Export the Build Settings from Xcode to Monaca Cloud IDE
================================================================================

In case you've already had your build settings (private keys and certificates) in your Mac OS X (Xcode) and you want to export them to Monaca Cloud IDE, please do as follows:

.. _export_with_keychain: 

Step 1: Export Private Key and Certificate in Keychain Access
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In order to export the private key in Keychain Access, please follow the instruction below:

1. In your Mac OS X, go to :menuselection:`Applications --> Utilities --> Keychain Access`.

2. Select :guilabel:`Certificates` on the left panel of the Keychain Access window.

  .. figure:: images/import_export/1.png
    :width: 600px
    :align: left

  .. rst-class:: clear

3. Right-click on the certificate you want to export and select :guilabel:`Export “CERTIFICATE NAME”`. Please make sure to choose the certificate that has a private key. Only the certificate which has a private key can be imported into Monaca. 

  .. figure:: images/import_export/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear

4. Then, the export screen will be displayed. Let's save it as a private key by selecting the file format as ``Personal Information Exchange (.p12)``, and then click :guilabel:`Save`.

  .. figure:: images/import_export/3.png
    :width: 500px
    :align: left

  .. rst-class:: clear

5. Enter a password for this private key, and then click :guilabel:`OK`. By doing so, a private key file with extension of ``.p12`` will be created. Please take note of this password since you will need it when importing this file into Monaca Cloud IDE later.

  .. figure:: images/import_export/4.png
    :width: 300px
    :align: left

  .. rst-class:: clear

6. Now, right-click on the certificate you want to export again and select :guilabel:`Export “CERTIFICATE NAME”`. This time, we are going to save it as a certificate by selecting the file format as ``Certificate (.cer)``, and then click :guilabel:`Save`.

  .. figure:: images/import_export/5.png
    :width: 500px
    :align: left

  .. rst-class:: clear


.. _import_into_monaca: 

Step 2 :Import Private Key and Certificate into Monaca
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: In Monaca, you can register only one private key. If you are using different private keys for the developer and the distribution certificates, you will need to re-import the private key which is related with the certificate you are going to use.

In order to import the private key and certificate in Monaca Cloud IDE, please follow the instruction below:

1. From the Monaca Cloud IDE menu, go to :menuselection:`Config --> iOS Build Settings`.

  .. figure:: images/import_export/6.png
    :width: 600px
    :align: left

  .. rst-class:: clear


2. Click on :guilabel:`Import`. Browse the private key file (``.p12`` file) and enter the password for that key. Then click :guilabel:`Import`.

  .. figure:: images/import_export/7.png
    :width: 300px
    :align: left

  .. rst-class:: clear


3. In the *Upload Certificate* section, click on :guilabel:`Upload` button for the Developer or Distribution certificate. 

  .. figure:: images/import_export/8.png
    :width: 500px
    :align: left

  .. rst-class:: clear

4. Select the certificate file (``.cer`` file) and then upload it.


.. _from_monaca_to_mac: 

Export the Build Settings from Monaca Cloud IDE to Xcode
======================================================================

.. note:: From Monaca Cloud IDE, the private key and certificate are exported as one file.

In order to export the private key and certificate from Monaca Cloud IDE, please follow the instruction below:

1. From the Monaca Cloud IDE menu, select :menuselection:`Config --> iOS Build Settings`.

2. In the *Upload Certificate* section, click on :guilabel:`Export` button of the type of certificate you want to export.

  .. figure:: images/import_export/9.png
    :width: 500px
    :align: left

  .. rst-class:: clear

3. Then, you will be ask to input a password before exporting. Please remember this password because you will need it when importing this certificate later.

  .. figure:: images/import_export/10.png
    :width: 400px
    :align: left

  .. rst-class:: clear

4. After clicking :guilabel:`Export` button, you will then be able to download a file with ``.p12`` extension (Ex: ``dev_certification_ios.p12``). This file consists of a private key and a certificate.

5. Double-click on the downloaded file. Then, you will be asked to input the password for the file and click :guilabel:`OK`. After that you can use the private key and certificate in Xcode.

  .. figure:: images/import_export/11.png
    :width: 300px
    :align: left

  .. rst-class:: clear


.. seealso::

  *See Also*

  - :ref:`building_for_ios`
