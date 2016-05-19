.. _todo:

============================================
TODO App
============================================

.. rst-class:: right-menu


The application allows you to add a todo list. 


| *Tested Environments:* Android 4.2.2, iOS 7.1.1

.. raw:: html

  <div class="iframe-samples">
    <iframe src="https://monaca.github.io/project-templates/19-todo-app/www/index.html" style="max-width: 150%;"></iframe>
  </div>

File Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/todo/1.png
    :width: 210px
    :align: center

========================================= =======================================================================================================================
``index.html``                             The startup Page

``js/app.js``                              A JavaScript file used in the application 
========================================= =======================================================================================================================

Required JS/CSS Components 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============================ ============================
``jQuerymobile``
============================ ============================


HTML Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The contents of the HTML body section are shown below. 

.. literalinclude:: download/todo/index.html
   :language: html
   :start-after: <body>
   :end-before: </body>

Since this sample uses jQuery Mobile, the HTML should be written accordingly. Specifically, attributes beginning with *data-*, such as *data-role* and *data-position*, serve special roles in jQuery Mobile. 

In jQuery Mobile, multiple pages can be described in a single HTML file. In this app, for example, both the List Screen and the Add Screen are defined within :file:`index.html`. Specifically, pages are expressed by ``div``  tags in which the ``data-role`` attribute is set to ``page``. The role of the tags is expressed by the ``data-role`` attribute in this manner. For example, ``data-role`` can also specify ``header``, ``content`` , or ``listview``. 

For more information on jQuery Mobile tags and components, please refer to `jQuery Mobile Demo <http://jquerymobile.com/demos/1.2.0/>`_. 

JavaScript Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The JavaScript code is shown below. 

.. literalinclude:: download/todo/index.html
   :language: javascript
   :start-after: <script>
   :end-before: </script>

Here, the two functions, ``addTodoPicture`` and ``addTodo``, are defined. As the names imply, the first function shoots a photo and registers data while the second performs only data registration. 

To shoot a photo, the *addTodoPicture* functions calls *navigator.camera.getPicture*,which is a function provide by PhoneGap. If the call is successful, the function *addTodo* is then executed. if it fails, an error message is generated. Photo shoot options such as fixing the image size and specifying the return type are also set. 

The function ``addTodo`` takes an argument called ``camera_url``. When the function ``navigator.camera.getPicture`` is called and the photo shoot is successful, a reference to the graphic file is stored in this argument. 

DOM operations can easily be performed within these functions through the use of jQuery libraries. For example, in the following snippet, the value of the element with ID ``todo-title`` is acquired and assigned to the variable ``title``. 

.. code-block:: javascript

  var title = $("#todo-title").val();

Accordingly, in lines 14-19, the input values are read and assigned to the appropriate variables ``title``, ``body``, and ``img_tag``. Next, the function *$.mobile.changePage* transitions to the next page and adds a new row to the list. Finally, the list page is redrawn and the program ends. 
