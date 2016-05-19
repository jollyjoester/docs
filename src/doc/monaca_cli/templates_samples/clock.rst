.. _the_clock_app:

============================================
Clock App
============================================

.. rst-class:: right-menu


.. note:: This sample application is reprinting of `Think IT article <http://thinkit.co.jp/story/2013/03/11/3987>`_ relaesed on 3/11/2013.

This sample app is a clock app displaying current Date and time.

| *Tested Environments:* Android 4.2.2, iOS 7.1.1


.. raw:: html

  <div class="iframe-samples">
    <iframe src="https://monaca.github.io/project-templates/21-clock-app/www/index.html" style="max-width: 150%;"></iframe>
  </div>


File Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/clock/1.png
    :width: 200px


========================== ================================================================================================================================
``index.html``              The Startup page

``js/app.js``               The JavaScript file handling implementation in the project

``css/style.css``           The style Sheet for the project

``images/*.png``            All image files needed to use this template
========================== ================================================================================================================================


HTML Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

index.html
=========================

The following HTML body of :file:`index.html` file is for displaying the current Date and time (see screenshot below): 

.. code-block:: html

    <div id="wrapper">
        <div id="container">
            <img src="images/figure-0.png" class="figure" /> 
            <img src="images/figure-0.png" class="figure" />
            <img src="images/figure-colon.png" />
            <img src="images/figure-0.png" class="figure" />
            <img src="images/figure-0.png" class="figure" />
            <img src="images/figure-colon.png" />
            <img src="images/figure-0.png" class="figure" />
            <img src="images/figure-0.png" class="figure" />
            <div id="date"></div>
        </div>
        <img src="images/logo-monaca.png" style="position: absolute; left: 40px; top: 40px;" />
    </div>


.. figure:: images/clock/3.png
    :width: 500px
    :align: center


JavaScript Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

js/app.js
======================

When the application is loaded, the ``clock()`` function is called every 1 seconds (1000 ms) by this statement:

.. code-block:: javascript

    setInterval(clock, 1000);



The ``clock()`` function is used to display the current date and time. First, it gets the current time (hour, minute and second) and then display the images (digit image) according to the time. Next, it gets the current date (day, month and year) and then display it in the format as defined in ``renderDay()`` and ``renderMonth()`` functions (see below screenshot). Here is content of the ``clock()`` function:

.. code-block:: javascript

    function clock() {
        // (3) Obtain "figure" class(image of the number)
        var figures = document.getElementsByClassName('figure');
        // (4) Obtain the "date" ID (Date display area)
        var date = document.getElementById('date');

        // (5) Obtain the current time
        var now = new Date();

        // (6) Set the digits for the hours
        figures[0].src = 'images/figure-' + tendigit(now.getHours()) + '.png';
        figures[1].src = 'images/figure-' + onedigit(now.getHours()) + '.png';

        // (7) Set the digits for the minutes
        figures[2].src = 'images/figure-' + tendigit(now.getMinutes()) + '.png';
        figures[3].src = 'images/figure-' + onedigit(now.getMinutes()) + '.png';

        // (7) Set the digits for the seconds
        figures[4].src = 'images/figure-' + tendigit(now.getSeconds()) + '.png';
        figures[5].src = 'images/figure-' + onedigit(now.getSeconds()) + '.png';

        // (8) Display the date
        date.textContent = renderDay(now.getDay()) + ", " + renderMonth(now.getMonth()) + " " + now.getDate() + ", " + now.getFullYear();
    }




.. figure:: images/clock/4.png
    :width: 500px
    :align: center