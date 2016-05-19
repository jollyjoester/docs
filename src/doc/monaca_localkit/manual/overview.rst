.. _localkit_overview:

================================================
Monaca Localkit Overview
================================================


Introduction
===============================

Monaca Localkit is a tool to support local development environment for Monaca apps. You can use it with various development tools including editors, source code management system, task runner and so on. Monaca Localkit allows you to develop offline with a faster synchronization with Monaca debugger. 

Monaca Localkit can accelerate your app development process because it provides the following functions:

- create and import Cordova project: You can create a new project based on templates provided by Monaca. Moreover, you can import either Monaca project from Monaca Cloud IDE or existing Cordova project.

- live reload of project: By pairing with Monaca Debugger, you can run your project instantly on your device. All changes made to the source code of the project will be updated immediately after those changes are saved.

- integrate with Chrome DevTools: By connecting your device (running Monaca Debugger) to the host PC (running Monaca Localkit) via USB cable, you can debug your app using Chrome DevTools. With the DevTools, you can set breakpoint and perform JavaScript debugging and app inspection.

- remote build: Monaca Localkit allows you to build your app for various platforms with the support from Monaca server.


.. note:: Please remember that the projects you have in :ref:`Monaca Cloud IDE<monaca_ide_index>` and Monaca Localkit are not synchronized. They are completely seperated. However, you can :ref:`import projects from Monaca Cloud IDE to Monaca Localkit<localkit_import>`.


.. note:: You are required to have a valid plan in order to use Monaca Localkit. Otherwise, Monaca Localkit will run in an evaluation mode for 30 days after the first login. Please refer to `Pricing <https://monaca.mobi/en/pricing?type=2>`_ for more details of each Monaca plan.

.. warning:: Please note that :ref:`Backend <monaca_backend_index>` as well as :ref:`push_notification_index` are currently not available in Monaca Localkit yet.

Installation and Setup
===============================

Before getting started, you need to install Monaca Localkit on the computer and :ref:`monaca_debugger_index` on the device(s).

.. ifconfig:: language == 'ja'

  1. Monaca Localkit の `最新版はこちら <https://ja.monaca.io/localkit.html>`_ から、ダウンロードできます。変更履歴に関しては、 `GitHub の release ページ <https://github.com/monaca/Localkit/releases>`_ をご確認ください。

  2. :ref:`こちら<debugger_installation_index>` の記載内容に従い、Monaca デバッガーをインストールします。

.. ifconfig:: language == 'en'

  1. Download the latest version of Monaca Localkit `here <https://monaca.io/localkit.html>`_. Please refer to `GitHub release page <https://github.com/monaca/Localkit/releases>`_ for change logs.
  2. Install Monaca Debugger as described in :ref:`Debugger Installation<debugger_installation_index>`.


Usage
===================

Starting Monaca Localkit
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Open Monaca Localkit and then sign in using Monaca account.

  .. figure:: images/overview/1.png
    :width: 400px
    :align: left

  .. rst-class:: clear

2. After a successful login, Monaca Localkit dashboard will appear.

  .. figure:: images/overview/2.png
    :width: 600px
    :align: left

  .. rst-class:: clear


.. _create_project_localkit:

Creating a New Project
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can create a new project based on templates provided by Monaca.

1. From Monaca Localkit dashboard, click on :guilabel:`+` button. Then, click :guilabel:`Create` button.

  .. figure:: images/overview/3.png
    :width: 600px
    :align: left

  .. rst-class:: clear

2. Fill in the necessary information such as:

  - Project Name: create a name to represent your new project which will be shown in the project list.
  - Working Directory: specify a directory where you want to keep your project files.
  - Select Template: choose a template for your new project. Please use :guilabel:`Preview` button to see how each template looks like.

  .. figure:: images/overview/4.png
    :width: 500px
    :align: left

  .. rst-class:: clear

3. If the project is created successfully, the new project will be shown in the project list.


.. _localkit_import:

Importing a Project
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

There are two types of projects you can import into Monaca Localkit:

1. From Cloud IDE: projects you have in your Monaca Cloud IDE.

2. From Local Cordova Project: Cordova projects you have on your PC. There some limitations while importing Cordova projects such as:

  - App icons and splash images may not be imported. They can be configured on Build Config screen.
  - The scripts in hooks directory are ignored.
  - Platform specific codes including Cordova are not imported. Monaca will use its own Cordova and surrounded libraries.


In order to import a project into Monaca Localkit, please do as follows:

1. From Monaca Localkit dashboard, click on :guilabel:`+` button on the top right corner of the left panel. Then, click :guilabel:`Import` button. Then, choose which option you want to import Monaca project.

  .. figure:: images/overview/5.png
    :width: 600px
    :align: left

  .. rst-class:: clear

2. If you choose :guilabel:`From Cloud IDE` option, fill in the necessary information such as:

  - Select Project: select a project from a list of all projects you have in Monaca Cloud IDE.
  - Working Directory: specify a directory where you want to keep your project files.

  .. figure:: images/overview/6.png
    :width: 500px
    :align: left

  .. rst-class:: clear

3. On the other hand, if you choose :guilabel:`From Local Cordova Project` option, fill in the necessary information such as:

  - Working Directory: specify a directory where you want to keep your project files.
  - Project Name: create a name to represent your new project which will be shown in the project list.

  .. figure:: images/overview/7.png
    :width: 500px
    :align: left

  .. rst-class:: clear

4. After that, the new project will be shown in the project list.

.. _localkit_open_in:

Adding Editor Program for Local Projects
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monaca Localkit provides an "Open in" feature which is used to open your local project files in different ways such as:

- Finder/File Explorer: This will reveal the selected project's folder in Finder (for Mac) or File Explorer (for Windows).
- Terminal/Command Prompt: This will open the selected project's folder in Terminal (for Mac) or Command Prompt for (Windows). 
- Other editor programs: You can also add any preferred editors to open your local project files from Monaca Localkit. 

In order to add an editor program to Monaca Localkit, please do as follows:

1. In Monaca Localkit, select a project.

2. Click :guilabel:`Open in...` button and select :guilabel:`Add More Program...`.

  .. figure:: images/overview/8.png
    :width: 300px
    :align: left

  .. rst-class:: clear

3. Then, Add Editor Application dialog will appear. Fill in the necessary information related to the editor program such as:
  
  - Application Path: browse the editor execution file (``.app`` file for Mac or ``.exe`` file for Windows).
  - Application Name: name the selected editor program. It will be shown in the list of programs when you click :guilabel:`Open in...`.
  - Command-line Arguments: [optional] applicable arguments for the selected editor program.

    .. figure:: images/overview/9.png
      :width: 400px
      :align: left

    .. rst-class:: clear

4. Click :guilabel:`OK`. Now, the new editor program should appear in the "Open in" list as shown below:

  .. figure:: images/overview/10.png
    :width: 250px
    :align: left

  .. rst-class:: clear

.. _localkit_preference:

Preference Dialog
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From Monaca Localkit menu, go to :guilabel:`Preferences` (for Mac) or go to :menuselection:`File --> Preferences` (for Windows).
  
  .. figure:: images/overview/11.png
    :width: 250px
    :align: left

  .. rst-class:: clear

2. In this Preferences dialog, you can do the following settings:

  - Working Directory: specify a default location to store your local projects.
  - Listening Port: specify a port number to be used when pairing Monaca Localkit with Monaca Debugger. 
  - Proxy Server: specify a proxy server.
  - Log Output: specify where you want to store a log file.

  .. figure:: images/overview/12.png
    :width: 500px
    :align: left

  .. rst-class:: clear

3. Save the settings.


.. seealso::

  *See Also*

  - :doc:`../../../quick_start/localkit/index`
  - :doc:`pairing_debugging`
  - :doc:`build_publish`
  - :doc:`troubleshooting`

