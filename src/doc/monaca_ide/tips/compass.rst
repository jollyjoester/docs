Using Compass
=====================================

.. rst-class:: right-menu


.. literalinclude:: download/compass/en/index.html
   :language: html



Use the following API to retrieve device orientation:

``navigator.compasss.watchHeading()``

This method has three arguments: onSuccess callback, onError callback and option object.

When the compass retrieval is successful, onSuccess callback function will be called. The passed parameter will contain numeric value from 0 to 359 indicating device heading. Above example displays heading directly to the page by using innerHTML.

The used variables and parameter names of *onSuccess*, *onError*, option, heading, etc can be chosen freely.
