.. _memo_application:

============================================
Memo Application
============================================

.. rst-class:: right-menu


This sample app allows user to create a memo application using local storage.


| *Tested Environments:* Android 4.2.2, iOS 7.1.1


.. raw:: html

  <div class="iframe-samples">
    <iframe src="https://monaca.github.io/project-templates/4-jqm-memo/www/index.html"></iframe>
  </div>


File Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/memo_application/memo_0.png
    :width: 200px


================================== ===========================================================================================================================
``index.html``                       The Home screen

``js/memo.js``                       A JavaScript file handling data manipulation in local storage

``js/app.js``                        A JavaScript file handling various implementation in the application
================================== ===========================================================================================================================

Required JS/CSS Components 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============================ ============================
``jQuery``
``jQuery Mobile``
============================ ============================


HTML Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This sample app's user interface is based on jQuery Mobile. In jQuery Mobile, multiple pages can be integrated to a single HTML file. In this app, for example, all pages (Top page, Add Memo page and Detail page) are defined within :file:`index.html`. Specifically, pages are expressed by ``div`` tags in which the ``data-role`` attribute is set to ``page``. The role of the tags is expressed by the ``data-role`` attribute in this manner. For example, ``data-role`` can also specify as ``header``, ``content`` , or ``listview``. For more information on jQuery Mobile tags and components, please refer to `jQuery Mobile Demo <http://demos.jquerymobile.com/>`_.


The following content of the HTML body tag of ``index.html`` file: 

::

  <body>
    <!-- TOP Page -->
    <div data-role="page" id="TopPage"> 
      <header data-role="header" data-position="fixed">
        <h1>Monaca Memo</h1>
        <a href="#AddPage" data-icon="plus" class="ui-btn-right">Add</a>
      </header>
      <section data-role="content">
        <ul id="TopListView" data-role="listview"
          data-collapsed-icon="arrow-r" data-expanded-icon="arrow-d" data-split-icon="delete">
        </ul>
      </section> 
    </div> 
    ...
  </body>

corresponds to this screenshot of the Top page (Home screen) which allows a user to add, view or delete memos:

.. figure:: images/memo_application/memo_3.png
   :width: 250px
   :align: center

The following content of the HTML body tag of ``index.html`` file:

::

  <body>
    ...
    <!-- Add Memo Page -->
    <div data-role="page" id="AddPage">
      <header data-role="header" data-position="fixed">
        <a data-role="button" data-rel="back" data-icon="back">Back</a>
        <h1>Add Memo</h1>
      </header> 
      <section data-role="content">
        <label for="Memo">Memo:</label>
        <textarea id="Memo"></textarea>
        <a data-role="button" data-icon="check" id="SaveBtn">Save</a>
      </section>
    </div> 
    ...
  </body>

corresponds to this screenshot of the Add Memo page which allows a user to add/save a memo:

.. figure:: images/memo_application/memo_2.png
   :width: 250px
   :align: center

The following content of the HTML body tag of :file:`index.html` file:

::

  <body>
    ...
    <!-- Detail Page -->
    <div data-role="page" id="ShowPage">
      <header data-role="header" data-position="fixed">
        <a data-role="button" data-rel="back" data-icon="back">Back</a>
        <h1></h1>
      </header> 
      <section data-role="content">
        <p></p>
      </section>
    </div>
  </body>

corresponds to this screenshot of the Detail page which allows a user to see the full content of each memo:

.. figure:: images/memo_application/memo_5.png
   :width: 250px
   :align: center


JavaScript Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

app.js
========================

:file:`app.js` is a JavaScript file handling various implementation of the application. 

As soon as the application starts, the ``initTopPage()`` function is called. This function is used to initialize the Top page (Home screen). The initialization process is to get all the previously stored memo(s) (using the ``getMemoList()`` function which is defined in the :file:`memo.js` file) and put them into a list view. If there is no previously created memo (when using the application for the first time), ``"No memo found"`` will be displayed (see below screenshot). 

.. figure:: images/memo_application/memo_1.png
   :width: 250px
   :align: center

Below is the source code of this function:

.. code-block:: javascript

    ...
    ///// Initialize top page
    function initTopPage() {
        $("#TopListView").empty();
        
        var list = getMemoList();
        for (var i in list) {
            var memo = list[i];
            var d = new Date(memo.time);
            var date = d.getFullYear() + "/" + (d.getMonth() + 1) + "/" + d.getDate();
            
            $li = $("<li><a href='#' class='show'><h3></h3><p></p></a><a href='#' class='delete'>Delete</a></li>");
            $li.data("id", memo.id);
            $li.find("h3").text(date);
            $li.find("p").text(memo.text);
            $("#TopListView").prepend($li);
        }
        if (list.length == 0) {
            $li = $("<li>No memo found</li>");
            $("#TopListView").prepend($li);
        }
        $("#TopListView").listview("refresh");  // Call refresh after manipulating list
    }
    ...

On the Top page, when a user clicks on the :guilabel:`+Add` button, the Add Memo page will be shown. After filling in the Memo text box, the ``onSaveBtn()`` function is called when the :guilabel:`Save` button is clicked. In this function, the input text will be saved to local storage via the ``addMemo()`` function (defined in the :file:`memo.js` file) and then it goes back to the Top page with an updated list. Below is the source code of this function:

.. code-block:: javascript

    ///// Save memo and return to top page
    function onSaveBtn() {
        var text = $("#Memo").val();
        if (text != '') {
            // Save to local storage
            addMemo(text);
            // Clear form
            $("#Memo").val("");
            // Initialize top page
            initTopPage();
        }
        $.mobile.changePage("#TopPage", { reverse: true });
    }

On the Top page, when a user clicks on an item in the list, the ``onShowLink()`` function (defined in the :file:`memo.js` file) is called. In this function, the Detail page will be shown and either the title or the full content of the selected item will be displayed as shown below:

.. figure:: images/memo_application/memo_5.png
   :width: 250px
   :align: center

Below is the source code of this function:

.. code-block:: javascript

    ///// Move to detail page
    function onShowLink() {
        var $li = $(this).parent();
        var memoTitle = $li.find("h3").text();
        var memoHtml = $li.find("p").html().replace(/\n/g, "<br>");
        
        $("#ShowPage h1").text(memoTitle);
        $("#ShowPage p").html(memoHtml);
        $.mobile.changePage("#ShowPage");
    }

On the Top page, a user can delete any item in the list by clicking on the :guilabel:`delete` icon at the end of each item. When the :guilabel:`delete` icon is clicked, the ``onDeleteLink()`` function is called. In this function, a message confirming the deleting action is shown (see below screenshot). If the :guilabel:`OK` button is clicked, the selected item will be deleted from the local storage via the ``deleteMemo()`` function (defined in the :file:`memo.js` file). Then, it will go back the Top page with an updated list.

.. figure:: images/memo_application/memo_4.png
   :width: 250px
   :align: center

Below is the source code of this function:

.. code-block:: javascript

    ///// Delete memo
    function onDeleteLink() {
        if (!confirm("Are you sure to delete this memo?")) {
          return;
        }
        var $li = $(this).parent();
        var id = $li.data("id");
        deleteMemo(id);
        
        initTopPage();
        
        // Return to top
        $.mobile.changePage("#TopPage", { reverse: true });
    }


memo.js
========================

:file:`memo.js` file is a JavaScript file handling data manipulation in local storage. Inside this file, there are 4 functions such as:

1. ``getMemoList()``: get the list of all memo stored in the local storage.
2. ``saveMemoList()``: save the list of all memo into the local storage.
3. ``AddMemo()``: add a new memo into the memo list and then save the new list into the local storage using ``saveMemoList()`` function.
4. ``deleteMemo()``: delete a specific memo from the memo list and then save the new list into the local storage using ``saveMemoList()`` function.


