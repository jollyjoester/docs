=========================================
Using Camera and Photo Album
=========================================

.. rst-class:: right-menu


*  This sample code is confirmed to work with Android 2.3.6, Android 3.2, Android 4.0.3 and iOS 7.0.4.

You will need to use PhoneGap Camera API to access the camera of a device. In order to use PhoneGap API, you need to load :file:`components/loader.js` file. Please be sure to add the following lines in the HTML files. 

::

   ...

   <head>
   <script type="text/javascript" charset="utf-8" src="components/loader.js"></script>
   </head>

   ...


PhoneGap has two JavaScript "Camera" object APIs. 

+----------------+------------------------------------------------------------------------------+
|Function        |Description                                                                   |
|                |                                                                              |
+================+==============================================================================+
|getPicture      |Captures an image with the Camera or displays images from the internal album. |
+----------------+------------------------------------------------------------------------------+
|cleanUp         |Cleans up temporary directory used by the Camera API.                         |
+----------------+------------------------------------------------------------------------------+


Take a Picture (Base64 Format)
=========================================

.. literalinclude:: download/camera/en/index.html
   :language: html




``navigator.camera.getPicture()`` function is used to deal with Camera API. ``getPicture()`` function has 2 callback functions: ``onSuccess`` and ``onFail``. Also, it can be used to pass an option object to specify picture quality and return type.


.. code-block:: xml

	navigator.camera.getPicture(onSuccess, onFail, { quality: 50, destinationType: Camera.DestinationType.DATA_URL});
	



After capturing and saving a picture with the Camera, ``onSuccess`` callback (1st argument) will be called. Then, the callback function will receive the reference to the picture. In case of having error while using the Camera, ``onFail`` callback (2nd argument) will be called. ``option`` object will return *jpeg/png* encoded string by default. The example above returns a picture with ``quality`` as ``"50"``, ``destinationType`` as ``"Camera.DestinationType.DATA_URL"`` in a *Base64* format.


Take a Picture (FILE_URI Format)
=========================================

This is a sample to display a taken picture using an image tag. 



.. literalinclude:: download/camera/en/index1.html
   :language: html




Obtain Pictures from a Device's Album
=========================================



.. literalinclude:: download/camera/en/index2.html
   :language: html

  

The 3rd argument of ``getPicture()`` function has ``"sourceType: navigator.camera.PictureSourceType.SAVEDPHOTOALBUM"`` which defines the picture source obtained from the device's album. This way, you can access the device's album.



Camera API Options
========================================

``getPicture()`` function has the following options. You can adjust Camera API behavior by overriding the default values listed here. Please note that this is not fully documented. Please check `Camera <http://docs.monaca.mobi/reference/phonegap_34/en/camera/camera/>`_ for more details. 

.. rst-class:: wide-table

   ===================== ================================================ ========================================================
    Option                Value                                            Description                                           
   ===================== ================================================ ========================================================
    quality               ``0`` to ``100``                                 Specify picture quality.                              
   
    destinationType       ``Camera.DestinationType.DATA_URL``              Obtain a picture in BASE64 format.                    
   
    destinationType       ``Camera.DestinationType.FILE_URI``              Obtain a picture in File URI format.                  
   
    sourceType            Can be one of the following values:              Corresponding description of each value:              

                          - ``Camera.PictureSourceType.PHOTOLIBRARY``      - Select pictures from the photo library.             
                          - ``Camera.PictureSourceType.CAMERA``            - Take a picture from the device's camera.            
                          - ``Camera.PictureSourceType.SAVEDPHOTOALBUM``   - Select pictures from the album.                     
   
   
    allowEdit             true or false                                    Allow simple editing before returning the picture.    
   
    encodingType          JPEG or PNG                                      Specify encoding format of the picture.               
   
    targetWidth           Number                                           Scale the picture with a specific width (in pixels).  
   
    targetHeight          Number                                           Scale the picture with a specific height (in pixels). 
   
    correctOrientation    true or false                                    Rotate the picture as taken.                          
   
    saveToPhotoAlbum      true or false                                    Save the picture to the album after capturing.        
   ===================== ================================================ ========================================================
