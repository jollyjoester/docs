======================================================
Using Database
======================================================

.. rst-class:: right-menu


HTML5 Web SQL Database connects to the device database. This section describes Web SQL Database usage. 

Web SQL Database
==========================

You need to create a new Database object before accessing to it. *window.openDatabase* function creates a new SQLite database. 

.. code-block:: javascript

    var db = window.openDatabase(database_name, database_version, database_displayname, database_size);


------------------------------------------------------
Creating a Database (SQLite)
------------------------------------------------------

::

  <!DOCTYPE html>
  <html>
    <head>

      <meta name="viewport" content="width=device-width, user-scalable=no">
      <script type="text/javascript" charset="utf-8" src="components/loader.js"></script>
      <script type="text/javascript" charset="utf-8">
    
      document.addEventListener("deviceready", onDeviceReady, false);


    
      function onDeviceReady() {
          var db = window.openDatabase("database", "1.0", "testdatabase", 1000000);
      }

      </script>
    </head>
    <body>
    <pre>Web SQL Database</pre>
    </body>
  </html>


openDatabase Arguments
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

=============================== ========================= ======================
Arguments                       Description               Value
=============================== ========================= ======================
database_name                   Database name             String
database_version                Database version          String  
database_displayname            Database display name     String
database_size                   Database size (in bytes)  Integer number
=============================== ========================= ======================


Database Object Methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

=============================== ==============================================================================
Function                        Description                                      　 
=============================== ==============================================================================
transaction                     Starts transaction. 
changeVersion                   Checks version and updates schema if necessary. 
=============================== ==============================================================================


*executesql* function in SQLTransaction object is an actual method to execute SQL. You need to execute transaction function in Database object to get SQLTransaction object. When executing *executeSql* function in SQLTransaction object, the callback function is executed and *SQLResultSet* object is passed to it. 

SQLResultSet Object Properties
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

=============================== ==================================================================================
Function                        Description                                      　 
=============================== ==================================================================================
insertId                        Returns row number when INSERT statement is successful. 
rowsAffected                    Returns affected rows after sql execution. 
rows                            Returns *ResultSetRowList* object. It represents the results of the sql execution. 
=============================== ==================================================================================



---------------------------------------------------------------------------
Executing SQL (SQLite)
---------------------------------------------------------------------------

.. literalinclude:: download/storage/en/index.html
   :language: html

  








