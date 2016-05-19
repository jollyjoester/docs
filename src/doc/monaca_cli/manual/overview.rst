.. _cli_overview:

==========================================
Monaca CLI Overview
==========================================

.. rst-class:: right-menu


Introduction
===============================

Monaca CLI provides command line interface for using Monaca Cloud from your local PC. With Monaca CLI, you can:

- create new local projects, import or clone existing projects in Monaca Cloud into your local PC
- debug your app with inspector integration
- remote build your projects without any setups locally. 


Getting Started
=========================

.. _install_monaca_cli:

Step 1: Installation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: You are required to have `Node.js <https://nodejs.org/>`_ installed on your PC in order to use Monaca CLI. After that, you can install Monaca CLI using ``npm`` command.

Use the following command to install Monaca CLI:

  .. code-block:: bash

      $ npm install -g monaca

On some systems you may have to prefix the command with sudo because of permissions:

  .. code-block:: bash

      $ sudo npm install -g monaca
        

.. note:: In order to check the currently installed Monaca CLI's version, use ``monaca`` command. Moreover, if you want to update Monaca CLI, just re-install it using the above command.


Step 2: Creating a New Project and Run on Browser
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: you can also :ref:`import<monaca_import>` or :ref:`clone<monaca_clone>` your existing projects from Monaca Cloud.

1. Create a new project by using the command below:

  .. code-block:: bash

        $ monaca create PROJECT_DIRECTORY

2. Choose a project template. Please see the example below:

  .. code-block:: bash

        $ monaca create PROJECT_DIRECTORY
        Which project template do you use?

        1: Hello World App
        2: Minimum Template
        3: RSS Reader Example
        4: Memo Application

        Type number>     1      

3. Run on the browser.

  .. code-block:: bash

        $ cd PROJECT_DIRECTORY
        $ monaca preview
  
.. _connect_to_debugger:

Step 3: Connecting to Monaca Debugger
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Use :ref:`monaca_debug` command to connect to your Monaca Debugger:

  .. code-block:: bash

        $ monaca debug

2. Then, a popup message, prompting you to pair the Debugger with the local PC, will appear in the Monaca Debugger. This message will only be displayed if it's the first time you are connecting to the device. After this, your application should be running on your Monaca Debugger.

.. note:: Before connecting Monaca Debugger to the local PC, please pay attention to the following points:

        1. Monaca Debugger and the local PC have to connect to the same WiFi network.
        2. Use the same Monaca account for either Monaca Debugger and the local PC.
        3. Disable the local PC's firewall.


.. seealso::

  *See Also*

  - :doc:`../../../quick_start/cli/index`
  - :doc:`cli_commands`
  - :doc:`pairing_debugging`
  - :doc:`build_publish`