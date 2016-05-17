.. _backend_control_panel:

==========================================================
Backend Control Panel
==========================================================

.. rst-class:: right-menu

There is a growing need for mobile apps to have user management functions which allow users to register and keep their data in a database. Monaca Backend provides these functionalities in advance as a cloud-based service that can manage users without a need for server-side development on the client's part.

Specifically, the following functions can be implemented with Monaca Backend:

- management of end user data on a server.
- end user registration and authentication. 

This manual will show user management from the Monaca Cloud IDE.

.. _backend_control_panel_getting_started:

Getting Started with Monaca Backend
==========================================================

1. From Monaca Cloud IDE, click on :guilabel:`Cloud` icon above the file tree menu to go to the Backend Control Panel. Then, click :guilabel:`Start Using Backend` button.

  .. figure:: images/control_panel/1.png
      :width: 250px
      :align: left

  .. rst-class:: clear

2. The following dialog will appear. You can create a new Backend, or select an existing one which is used in a different project. Then, click :guilabel:`Apply` to attach the Backend to your project.

  .. figure:: images/control_panel/2.png
      :width: 400px
      :align: left

  .. rst-class:: clear

3. After attaching the Backend, your Backend Control Panel will look similar to this:

  .. figure:: images/control_panel/3.png
      :width: 250px
      :align: left

  .. rst-class:: clear


Backend Configuration
==========================================================

Switching the Backend
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From Backend Control Panel, click on the gear icon and choose :guilabel:`Select a Backend`.

  .. figure:: images/control_panel/25.png
      :width: 250px
      :align: left

  .. rst-class:: clear

2. Backend dialog will appear. You can switch to another existing backend or a new one. Then, click :guilabel:`Apply`.

  .. figure:: images/control_panel/26.png
      :width: 400px
      :align: left

  .. rst-class:: clear


Security Settings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From Backend Control Panel, click on the gear icon and choose :guilabel:`Backend Settings`.

  .. figure:: images/control_panel/27.png
      :width: 250px
      :align: left

  .. rst-class:: clear

2. Backend Settings dialog will appear. In this page, you can:

  - enable or disable automatic login, and change the expiration period.
  - change the minimum character length required for password and username.
  - and set password reset token expiration period.

  .. figure:: images/control_panel/28.png
      :width: 600px
      :align: left

  .. rst-class:: clear

3. Then, click :guilabel:`Apply`.


.. _backend_management_api_key:

Backend Management API Key
==========================================================


Backend Management API key is needed when you want to use Monaca Backend Management API. This API allows you to manage your Monaca Backend from your server rather than from Monaca Cloud IDE. For more information about this, please refer to :ref:`backend_management_api_index`.


In order to get Backend Management API key, please follow the instruction below:

1. From Backend Control Panel, click on the gear icon and choose :guilabel:`Backend Settings`.

  .. figure:: images/control_panel/29.png
      :width: 250px
      :align: left

  .. rst-class:: clear

2. Backend Settings dialog will appear. In this page, go to :guilabel:`Management API` and click :guilabel:`Enable`.

  .. figure:: images/control_panel/30.png
      :width: 600px
      :align: left

  .. rst-class:: clear

3. In this page, there are two important information such as:

  - Management API Endpoint URL: This URL looks like this ``"https://cloud.monaca.mobi/manage/json-rpc/CLOUD_PROJECT_ID"`` in which ``CLOUD_PROJECT_ID`` is your Monaca Backend ID. This URL will be used as *JSON-RPC Request URL* (See :ref:`backend_management_api_index`). 
  - IP Address Range: You can specify one API key for a particular range of IP addresses. Leaving it blank is not recommended. 

  .. figure:: images/control_panel/31.png
      :width: 600px
      :align: left

  .. rst-class:: clear


4. Click :guilabel:`Create` button to generate the API key.


.. seealso::

  *See Also*

  - :ref:`backend_api_index`
  - :ref:`backend_database_memo`

