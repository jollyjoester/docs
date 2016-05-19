.. _onsen_ui_sliding_menu:

============================================
Onsen UI Sliding Menu
============================================

.. rst-class:: right-menu

This is a template using `Onsen UI sliding menu <http://onsenui.io/guide/overview.html#UsingSlidingMenu>`_.


| *Tested Environments:* Android 4.2.2, iOS 7.1.1


.. raw:: html

  <div class="iframe-samples">
    <iframe src="https://monaca.github.io/project-templates/8-ons-sliding-menu-nav/www/index.html" style="max-width: 150%;"></iframe>
  </div>


File Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/onsen_ui_sliding_menu/sliding_1.png
    :width: 200px


================================== ===========================================================================================================================
``index.html``                       Startup page   
``menu.html``                        Menu Page
``page1.html``                       Page 1
``page2.html``                       Page 2
``styles/app.css``                   Style sheet file of this project
``images/ico_swipe_right_s.png``     Image file used in this project
================================== ===========================================================================================================================

Required JS/CSS Components 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============================ ============================
``Onsen UI``
============================ ============================

HTML Explanation
^^^^^^^^^^^^^^^^^^^^^^^

index.html
======================

:file:`index.html` is the Startup page. It is the starting point of the app and contains the sliding menu component (``<ons-sliding-menu>`` tag). The ``ons-sliding-menu`` component has main page :file:`page1.html` and menu page :file:`menu.html`. When the :file:`index.html` is loaded at the start of the app, the :file:`page1.html` and :file:`menu.html` are loaded as the main page and menu page, respectively.

menu.html
=================

:file:`menu.html` is shown when the :guilabel:`Toggle Menu` button is clicked or when the user swipe the page right. This page contains a list of 2 items: Page 1 (``page1.html``) and Page 2 (``page2.html``). (See the screenshot below)

.. figure:: images/onsen_ui_sliding_menu/sliding_3.png
    :width: 250px


While the behind-page (:file:`menu.html`) of the sliding menu element is always the same, its above-page is changed to :file:`navigator1.html` or :file:`navigator2.html` when the :guilabel:`Page 1` or :guilabel:`Page 2` is selected, respectively.


page1.html
===============================

:file:`page1.html` has several lines of text, a :guilabel:`Toggle Menu` button and an image file. (See the screenshot below)

.. figure:: images/onsen_ui_sliding_menu/sliding_2.png
    :width: 250px


page2.html
===============================

:file:`page2.html` has only a line of text (``Page 2``) and a :guilabel:`Toggle Menu` button. (See the screenshot below)

.. figure:: images/onsen_ui_sliding_menu/sliding_4.png
    :width: 250px

