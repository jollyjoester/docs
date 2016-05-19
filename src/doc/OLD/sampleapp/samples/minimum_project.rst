.. _minimum_project:

============================================
Minimum Template
============================================

.. rst-class:: right-menu


This is an empty template of a Monaca project. 


| *Tested Environments:* Android 4.2.2, iOS 7.1.1


.. raw:: html

  <div class="iframe-samples">
    <iframe src="https://monaca.github.io/project-templates/1-minimum/www/index.html" style="max-width: 150%;"></iframe>
  </div>


File Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When using the *Minimum Template*, the following files will be automatically created:

.. image:: images/minimum_project/minimum_1.png
    :width: 200px


================================== ===========================================================================================================================
``index.html``                       The Startup page   
``css/style.css``                    The style sheet file for the project. 
================================== ===========================================================================================================================


HTML Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: html

    <meta name="viewport" content="width=device-width, user-scalable=no">

The above ``<meta>`` tag sets the display width to the actual width of the device screen. Some devices may display slight screen differences.

.. code-block:: html

    <script src="components/loader.js"></script>
    <link rel="stylesheet" href="components/loader.css">

The above ``loader.js`` and ``loader.css`` files are used to load the necessary files and style sheets for the components included in the project.


The :file:`index.html` is the Startup page. Here is the screenshot of the Startup page:

.. figure:: images/minimum_project/minimum_2.png
    :width: 250px
    :align: center
