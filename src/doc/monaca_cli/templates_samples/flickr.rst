.. _flickr_sample:

============================================
Flickr Sample
============================================

.. rst-class:: right-menu


This sample app shows how to retrieve pictures from Flickr and displays them as a slide show.

| *Tested Environments:* Android 4.1.1, iOS 7.1.1

.. raw:: html

  <div class="iframe-samples">
    <iframe src="https://monaca.github.io/project-templates/18-flickr-sample/www/index.html" style="max-width: 150%;"></iframe>
  </div>

File Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/flickr/1.png
    :width: 210px
    :align: center

========================== ==================================================================================================================================
``index.html``               The startup page
``css/style.css``            A stylesheet for the project
``js/main.js``               A JavaScript file for this project
``js/jquery.bxslider.js``    A Javascript file for photo sliding animation
``images/*.png``             Image files used in the project
========================== ==================================================================================================================================


Required JS/CSS Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

=========================== ==========================================
``jQuery``
=========================== ==========================================

HTML Explanation
^^^^^^^^^^^^^^^^^^^^^^

The following HTML body of :file:`index.html` file is for the title bar, spinner and container for displaying the images (see screenshot below):

.. code-block:: html

    <div id="title-bar">
        <h2>Monaca Photo Viewer</h2>
    </div>
    <div id="loadSpinner"></div>
    <div id="container"></div>
    <div id="bottom"><img src="images/logo-monaca.png" width="160"></div>


.. figure:: images/flickr/3.png
   :width: 250px
   :align: center

JavaScript Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

There are 2 main functions in this sample app which will be explained as follows: 

jsonFlickrFeed()
====================

``jsonFlickrFeed()`` is fired when the Flickr API is loaded. The Flickr API is called when the :file:`index.html` file is loaded. Inside the header of :file:`index.html` file, there is a line: ``<script src="http://api.flickr.com/services/feeds/photos_public.gne?format=json" defer></script>``. This is where the Flickr API is called. In this function, the retrieved photos are then pushed into a local variable ``images`` and the photos are display as a slide show by calling ``displayPicture()`` function every *1 second*. Below is the JavaScript code of this function:

.. code-block:: javascript

    var images = [];
 
    // This function is fired when the Flickr API is loaded.
    function jsonFlickrFeed(result) {
      for (var j in result.items) {
        var img = result.items[j].media.m;
        images.push(img);
      }
      
      // display next photo every 1 second
      setTimeout(displayPicture, 1000);
    }




displayPicture()
====================

:envvar:`displayPicture()` displays the photos stored inside ``images`` variable (photos retrieved from Flickr) in a container created by HTML code in :file:`index.html` file. Below is the JavaScript code of this function:

.. code-block:: javascript

    //Display the retrieved photos from Flickr as a slide show
    function displayPicture() { 
      $("#container").css("visibility", "hidden");
      var $ul = $("<ul>");

      for(var j in images) {
        var srcUrl = images[j];
        li = '<li><img src="' + srcUrl + '" id ="list" width="60%"  /></li>';
        $ul.append($(li));
      }
      
      $("#container").append($ul);
      //Setting for photo sliding animation
      $ul.bxSlider({
        auto: true,
        pager: false,
        speed: 500,
        pause: 1800,
        controls: false,
      });

      $("#loadSpinner").remove();
      $("#container img").addClass("shadow");
      
      setTimeout(function() {
        $("#container").css("visibility", "visible");
      }, 1000);
    }

