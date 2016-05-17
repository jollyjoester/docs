Using Location (GPS)
=====================================

.. rst-class:: right-menu


.. literalinclude:: download/gps/en/index.html
   :language: html


Using Location (GPS)

``navigator.geolocation.getCurrentPosition()``

This method has three arguments: *onSuccess*, *onError*, and option object. When the call is successful, *onSuccess* callback (1st argument) will be called. An object containing various location sensor information (position object in this case) will be returned.

This example will simply output position.coords.longitude and position.coords.latitude. The used variables and parameter names of *onSuccess*, *onError*, option, position, etc can be chosen freely.
