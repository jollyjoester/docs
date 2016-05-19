.. raw:: html

   <!---
       Licensed to the Apache Software Foundation (ASF) under one
       or more contributor license agreements.  See the NOTICE file
       distributed with this work for additional information
       regarding copyright ownership.  The ASF licenses this file
       to you under the Apache License, Version 2.0 (the
       "License"); you may not use this file except in compliance
       with the License.  You may obtain a copy of the License at

         http://www.apache.org/licenses/LICENSE-2.0

       Unless required by applicable law or agreed to in writing,
       software distributed under the License is distributed on an
       "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
       KIND, either express or implied.  See the License for the
       specific language governing permissions and limitations
       under the License.
   -->


=======================
File Plugin
=======================

.. rst-class:: right-menu


.. raw:: html

  <div>
    <div  style="float: left;" align="left"><b>Tested Version: </b><a href="https://github.com/apache/cordova-plugin-file/blob/master/RELEASENOTES.md#300-aug-18-2015">3.0.0</a></div>   
    <div align="right" style="float: right;"><b>Last Edited:</b> November 20th, 015</div>
    <br/>
  </div>

.. note:: 
    
    This document is based on the original Cordova docs available at `Cordova Docs <https://github.com/apache/cordova-plugin-file>`_.

This plugin implements a File API allowing read/write access to files residing on the device.

This plugin is based on several specs, including: The HTML5 File API http://www.w3.org/TR/FileAPI/

The (now-defunct) Directories and System extensions Latest: http://www.w3.org/TR/2012/WD-file-system-api-20120417/ Although most of the plugin code was written when an earlier spec was current: http://www.w3.org/TR/2011/WD-file-system-api-20110419/

It also implements the FileWriter spec: http://dev.w3.org/2009/dap/file-system/file-writer.html

For usage, please refer to HTML5 Rocks' excellent `FileSystem article. <http://www.html5rocks.com/en/tutorials/file/filesystem/>`__

For an overview of other storage options, refer to Cordova's `storage guide <http://cordova.apache.org/docs/en/edge/cordova_storage_storage.md.html>`__.

This plugin defines global ``cordova.file`` object.

Although in the global scope, it is not available until after the ``deviceready`` event.

::

    document.addEventListener("deviceready", onDeviceReady, false);
    function onDeviceReady() {
        console.log(cordova.file);
    }

Plugin ID
=========================================

::
  
  cordova-plugin-file

Adding the Plugin in Monaca
=========================================

In order to use this plugin, please :ref:`enable <add_plugins>` ``File`` plugin in Monaca Cloud IDE.


Supported Platforms
=========================================

-  Amazon Fire OS
-  Android
-  BlackBerry 10
-  Firefox OS
-  iOS
-  OS X
-  Windows Phone 7 and 8\*
-  Windows 8\*
-  Windows\*
-  Browser

\*These platforms do not support ``FileReader.readAsArrayBuffer`` or ``FileWriter.write(blob)``.

API Reference
=========================================


Where to Store Files
--------------------

As of v1.2.0, URLs to important file-system directories are provided. Each URL is in the form *file:///path/to/spot/*, and can be converted to a ``DirectoryEntry`` using ``window.resolveLocalFileSystemURL()``.

-  ``cordova.file.applicationDirectory`` - Read-only directory where the application is installed. (*iOS*, *Android*, *BlackBerry 10*, *OSX*, *windows*)

-  ``cordova.file.applicationStorageDirectory`` - Root directory of the application's sandbox; on iOS & windows this location is read-only (but specific subdirectories [like ``/Documents`` on iOS or ``/localState`` on windows] are read-write). All data contained within is private to the app. (*iOS*, *Android*, *BlackBerry 10*, *OSX*)

-  ``cordova.file.dataDirectory`` - Persistent and private data storage within the application's sandbox using internal memory (on Android, if you need to use external memory, use ``.externalDataDirectory``). On iOS, this directory is not synced with iCloud (use ``.syncedDataDirectory``). (*iOS*, *Android*, *BlackBerry 10*, *windows*)

-  ``cordova.file.cacheDirectory`` - Directory for cached data files or any files that your app can re-create easily. The OS may delete these files when the device runs low on storage, nevertheless, apps should not rely on the OS to delete files in here. (*iOS*, *Android*, *BlackBerry 10*, *OSX*, *windows*)

-  ``cordova.file.externalApplicationStorageDirectory`` - Application space on external storage. (*Android*)

-  ``cordova.file.externalDataDirectory`` - Where to put app-specific data files on external storage. (*Android*)

-  ``cordova.file.externalCacheDirectory`` - Application cache on external storage. (*Android*)

-  ``cordova.file.externalRootDirectory`` - External storage (SD card) root. (*Android*, *BlackBerry 10*)

-  ``cordova.file.tempDirectory`` - Temp directory that the OS can clear at will. Do not rely on the OS to clear this directory; your app should always remove files as applicable. (*iOS*, *OSX*, *windows*)

-  ``cordova.file.syncedDataDirectory`` - Holds app-specific files that should be synced (e.g. to iCloud). (*iOS*, *windows*)

-  ``cordova.file.documentsDirectory`` - Files private to the app, but that are meaningful to other application (e.g. Office files). Note that for *OSX* this is the user's ``~/Documents`` directory. (*iOS*, *OSX*)

-  ``cordova.file.sharedDirectory`` - Files globally available to all applications (*BlackBerry 10*)


Android Quirks
--------------

Android Persistent storage location
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are multiple valid locations to store persistent files on an Android device. See `this page <http://developer.android.com/guide/topics/data/data-storage.html>`__ for an extensive discussion of the various possibilities.

Previous versions of the plugin would choose the location of the temporary and persistent files on startup, based on whether the device claimed that the SD Card (or equivalent storage partition) was mounted. If the SD Card was mounted, or if a large internal storage partition was available (such as on Nexus devices,) then the persistent files would be stored in the root of that space. This meant that all Cordova apps could see all of the files available on the card.

If the SD card was not available, then previous versions would store data under ``/data/data/<packageId>``, which isolates apps from each other, but may still cause data to be shared between users.

It is now possible to choose whether to store files in the internal file storage location, or using the previous logic, with a preference in your application's ``config.xml`` file. To do this, add one of these two lines to ``config.xml``:

::

    <preference name="AndroidPersistentFileLocation" value="Internal" />

    <preference name="AndroidPersistentFileLocation" value="Compatibility" />

Without this line, the File plugin will use ``Internal`` as the default. If a preference tag is present, and is not one of these values, the application will not start.

If your application has previously been shipped to users, using an older (pre- 3.0.0) version of this plugin, and has stored files in the persistent filesystem, then you should set the preference to ``Compatibility`` if your config.xml does not specify a location for the persistent filesystem. Switching the location to "Internal" would mean that existing users who upgrade their application may be unable to access their previously-stored files, depending on their device.

If your application is new, or has never previously stored files in the persistent filesystem, then the ``Internal`` setting is generally recommended.

Slow recursive operations for /android\_asset
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Listing asset directories is really slow on Android. You can speed it up though, by adding ``src/android/build-extras.gradle`` to the root of your android project (also requires cordova-android 4.0.0 or greater).

iOS Quirks
----------

-  ``cordova.file.applicationStorageDirectory`` is read-only; attempting to store files within the root directory will fail. Use one of the other ``cordova.file.*`` properties defined for iOS (only ``applicationDirectory`` and ``applicationStorageDirectory`` are read-only).
-  ``FileReader.readAsText(blob, encoding)``
-  The ``encoding`` parameter is not supported, and UTF-8 encoding is always in effect.

iOS Persistent storage location
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are two valid locations to store persistent files on an iOS device: the Documents directory and the Library directory. Previous versions of the plugin only ever stored persistent files in the Documents directory. This had the side-effect of making all of an application's files visible in iTunes, which was often unintended, especially for applications which handle lots of small files, rather than producing complete documents for export, which is the intended purpose of the directory.

It is now possible to choose whether to store files in the documents or library directory, with a preference in your application's ``config.xml`` file. To do this, add one of these two lines to ``config.xml``:

::

    <preference name="iosPersistentFileLocation" value="Library" />

    <preference name="iosPersistentFileLocation" value="Compatibility" />

Without this line, the File plugin will use ``Compatibility`` as the default. If a preference tag is present, and is not one of these values, the application will not start.

If your application has previously been shipped to users, using an older (pre- 1.0) version of this plugin, and has stored files in the persistent filesystem, then you should set the preference to ``Compatibility``. Switching the location to ``Library`` would mean that existing users who upgrade their application would be unable to access their previously-stored files.

If your application is new, or has never previously stored files in the persistent filesystem, then the ``Library`` setting is generally recommended.

Firefox OS Quirks
-----------------

The File System API is not natively supported by Firefox OS and is implemented as a shim on top of indexedDB.

-  Does not fail when removing non-empty directories
-  Does not support metadata for directories
-  Methods ``copyTo`` and ``moveTo`` do not support directories

The following data paths are supported:

\* ``applicationDirectory`` - Uses ``xhr`` to get local files that are packaged with the app.

\* ``dataDirectory`` - For persistent app-specific data files.

\* ``cacheDirectory`` - Cached files that should survive app restarts (Apps should not rely on the OS to delete files in here).

Browser Quirks
--------------

Common quirks and remarks
~~~~~~~~~~~~~~~~~~~~~~~~~

-  Each browser uses its own sandboxed filesystem. IE and Firefox use IndexedDB as a base. All browsers use forward slash as directory separator in a path.

-  Directory entries have to be created successively. For example, the call ``fs.root.getDirectory('dir1/dir2', {create:true}, successCallback, errorCallback)`` will fail if dir1 did not exist.

-  The plugin requests user permission to use persistent storage at the application first start.

-  Plugin supports ``cdvfile://localhost`` (local resources) only. I.e. external resources are not supported via ``cdvfile``.

-  The plugin does not follow `"File System API 8.3 Naming restrictions" <http://www.w3.org/TR/2011/WD-file-system-api-20110419/#naming-restrictions>`__.

-  Blob and File' ``close`` function is not supported.

-  ``FileSaver`` and ``BlobBuilder`` are not supported by this plugin and don't have stubs.

-  The plugin does not support ``requestAllFileSystems``. This function is also missing in the specifications.

-  Entries in directory will not be removed if you use ``create: true`` flag for existing directory.

-  Files created via constructor are not supported. You should use entry.file method instead.

-  Each browser uses its own form for blob URL references.

-  ``readAsDataURL`` function is supported, but the mediatype in Chrome depends on entry name extension, mediatype in IE is always empty (which is the same as ``text-plain`` according the specification), the mediatype in Firefox is always ``application/octet-stream``. For example, if the content is ``abcdefg`` then Firefox returns ``data:application/octet-stream;base64,YWJjZGVmZw==``, IE returns ``data:;base64,YWJjZGVmZw==``, Chrome returns ``data:<mediatype depending on extension of entry name>;base64,YWJjZGVmZw==``.

-  ``toInternalURL`` returns the path in the form ``file:///persistent/path/to/entry`` (Firefox, IE). Chrome returns the path in the form ``cdvfile://localhost/persistent/file``.

Chrome quirks
~~~~~~~~~~~~~

Chrome filesystem is not immediately ready after device ready event. As a workaround you can subscribe to ``filePluginIsReady`` event.

   Example:

   .. code:: javascript

       window.addEventListener('filePluginIsReady', function(){ console.log('File plugin is ready');}, false);


You can use ``window.isFilePluginReadyRaised`` function to check whether event was already raised.

-  window.requestFileSystem TEMPORARY and PERSISTENT filesystem quotas are not limited in Chrome.

-  To increase persistent storage in Chrome you need to call ``window.initPersistentFileSystem`` method. Persistent storage quota is 5 MB by default.

-  Chrome requires ``--allow-file-access-from-files`` run argument to support API via ``file:///`` protocol.

-  ``File`` object will be not changed if you use flag ``{create:true}`` when getting an existing ``Entry``.

-  events ``cancelable`` property is set to true in Chrome. This is contrary to the `specification <http://dev.w3.org/2009/dap/file-system/file-writer.html>`__.

-  ``toURL`` function in Chrome returns ``filesystem:``-prefixed path depending on application host. For example, ``filesystem:file:///persistent/somefile.txt``, ``filesystem:http://localhost:8080/persistent/somefile.txt``.

-  ``toURL`` function result does not contain trailing slash in case of directory entry. Chrome resolves directories with slash-trailed urls correctly though.

-  ``resolveLocalFileSystemURL`` method requires the inbound ``url`` to have ``filesystem`` prefix. For example, ``url`` parameter for ``resolveLocalFileSystemURL`` should be in the form ``filesystem:file:///persistent/somefile.txt`` as opposed to the form ``file:///persistent/somefile.txt`` in Android.

-  Deprecated ``toNativeURL`` function is not supported and does not have a stub.

-  ``setMetadata`` function is not stated in the specifications and not supported.

-  INVALID\_MODIFICATION\_ERR (code: 9) is thrown instead of SYNTAX\_ERR(code: 8) on requesting of a non-existent filesystem.

-  INVALID\_MODIFICATION\_ERR (code: 9) is thrown instead of PATH\_EXISTS\_ERR(code: 12) on trying to exclusively create a file or directory, which already exists.

-  INVALID\_MODIFICATION\_ERR (code: 9) is thrown instead of NO\_MODIFICATION\_ALLOWED\_ERR(code: 6) on trying to call removeRecursively on the root file system.

-  INVALID\_MODIFICATION\_ERR (code: 9) is thrown instead of NOT\_FOUND\_ERR(code: 1) on trying to moveTo directory that does not exist.

IndexedDB-based impl quirks (Firefox and IE)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  ``.`` and ``..`` are not supported.

-  IE does not support ``file:///``-mode; only hosted mode is supported (http://localhost:xxxx).

-  Firefox filesystem size is not limited but each 50MB extension will request a user permission. IE10 allows up to 10mb of combined AppCache and IndexedDB used in implementation of filesystem without prompting, once you hit that level you will be asked if you want to allow it to be increased up to a max of 250mb per site. So ``size`` parameter for ``requestFileSystem`` function does not affect filesystem in Firefox and IE.

-  ``readAsBinaryString`` function is not stated in the Specs and not supported in IE and does not have a stub.

-  ``file.type`` is always null.

-  You should not create entry using DirectoryEntry instance callback result which was deleted. Otherwise, you will get a 'hanging entry'.

-  Before you can read a file, which was just written you need to get a new instance of this file.

-  ``setMetadata`` function, which is not stated in the Specs supports ``modificationTime`` field change only.

-  ``copyTo`` and ``moveTo`` functions do not support directories. Directories metadata is not supported.

-  Both Entry.remove and directoryEntry.removeRecursively don't fail when removing non-empty directories - directories being removed are cleaned along with contents instead.

-  ``abort`` and ``truncate`` functions are not supported.

-  progress events are not fired. For example, this handler will be not executed:

Example:

   .. code:: javascript

       writer.onprogress = function() { /*commands*/ };


Upgrading Notes
----------------

In v1.0.0 of this plugin, the ``FileEntry`` and ``DirectoryEntry`` structures have changed, to be more in line with the published specification.

Previous (pre-1.0.0) versions of the plugin stored the device-absolute-file-location in the ``fullPath`` property of ``Entry`` objects. These paths would typically look like

::

    /var/mobile/Applications/<application UUID>/Documents/path/to/file  (iOS)
    /storage/emulated/0/path/to/file                                    (Android)

These paths were also returned by the ``toURL()`` method of the ``Entry`` objects.

With v1.0.0, the ``fullPath`` attribute is the path to the file, *relative to the root of the HTML filesystem*. So, the above paths would now both be represented by a ``FileEntry`` object with a ``fullPath`` of

::

    /path/to/file

If your application works with device-absolute-paths, and you previously retrieved those paths through the ``fullPath`` property of ``Entry`` objects, then you should update your code to use ``entry.toURL()`` instead.

For backwards compatibility, the ``resolveLocalFileSystemURL()`` method will accept a device-absolute-path, and will return an ``Entry`` object corresponding to it, as long as that file exists within either the ``TEMPORARY`` or ``PERSISTENT`` filesystems.

This has particularly been an issue with the File-Transfer plugin, which previously used device-absolute-paths (and can still accept them). It has been updated to work correctly with FileSystem URLs, so replacing ``entry.fullPath`` with ``entry.toURL()`` should resolve any issues getting that plugin to work with files on the device.

In v1.1.0 the return value of ``toURL()`` was changed (see `CB-6394 <https://issues.apache.org/jira/browse/CB-6394>`__) to return an absolute 'file://' URL. wherever possible. To ensure a 'cdvfile:'-URL you can use ``toInternalURL()`` now. This method will now return filesystem URLs of the form

::

    cdvfile://localhost/persistent/path/to/file

which can be used to identify the file uniquely.

cdvfile protocol
----------------

**Purpose**

``cdvfile://localhost/persistent|temporary|another-fs-root*/path/to/file`` can be used for platform-independent file paths. cdvfile paths are supported by core plugins - for example you can download an mp3 file to cdvfile-path via ``cordova-plugin-file-transfer`` and play it via ``cordova-plugin-media``.

**Note**: See `Where to Store Files <#where-to-store-files>`__, `File System Layouts <#file-system-layouts>`__ and `Configuring the Plugin <#configuring-the-plugin-optional>`__ for more details about available fs roots.

To use ``cdvfile`` as a tag' ``src`` you can convert it to native path via ``toURL()`` method of the resolved fileEntry, which you can get via ``resolveLocalFileSystemURL`` - see examples below.

You can also use ``cdvfile://`` paths directly in the DOM, for example:

.. code-block:: html

    <img src="cdvfile://localhost/persistent/img/logo.png" />


**Note**: This method requires following Content Security rules updates:

-  Add ``cdvfile:`` scheme to ``Content-Security-Policy`` meta tag of the index page, e.g.:
  
  -  ``<meta http-equiv="Content-Security-Policy" content="default-src 'self' data: gap:``\ **cdvfile:**\ ``https://ssl.gstatic.com 'unsafe-eval'; style-src 'self' 'unsafe-inline'; media-src *">``

-  Add ``<access origin="cdvfile://*" />`` to ``config.xml``.


**Converting cdvfile:// to native path**

.. code:: javascript

    resolveLocalFileSystemURL('cdvfile://localhost/temporary/path/to/file.mp4', function(entry) {
        var nativePath = entry.toURL();
        console.log('Native URI: ' + nativePath);
        document.getElementById('video').src = nativePath;

**Converting native path to cdvfile://**

.. code:: javascript

    resolveLocalFileSystemURL(nativePath, function(entry) {
        console.log('cdvfile URI: ' + entry.toInternalURL());

**Using cdvfile in core plugins**

.. code:: javascript

    fileTransfer.download(uri, 'cdvfile://localhost/temporary/path/to/file.mp3', function (entry) { ...

.. code:: javascript

    var my_media = new Media('cdvfile://localhost/temporary/path/to/file.mp3', ...); my_media.play();

cdvfile quirks
~~~~~~~~~~~~~~~~~~~~~

-  Using ``cdvfile://`` paths in the DOM is not supported on Windows platform (a path can be converted to native instead).

List of Error Codes and Meanings
--------------------------------

When an error is thrown, one of the following codes will be used.

+--------+-----------------------------------+
| Code   | Constant                          |
+========+===================================+
| 1      | ``NOT_FOUND_ERR``                 |
+--------+-----------------------------------+
| 2      | ``SECURITY_ERR``                  |
+--------+-----------------------------------+
| 3      | ``ABORT_ERR``                     |
+--------+-----------------------------------+
| 4      | ``NOT_READABLE_ERR``              |
+--------+-----------------------------------+
| 5      | ``ENCODING_ERR``                  |
+--------+-----------------------------------+
| 6      | ``NO_MODIFICATION_ALLOWED_ERR``   |
+--------+-----------------------------------+
| 7      | ``INVALID_STATE_ERR``             |
+--------+-----------------------------------+
| 8      | ``SYNTAX_ERR``                    |
+--------+-----------------------------------+
| 9      | ``INVALID_MODIFICATION_ERR``      |
+--------+-----------------------------------+
| 10     | ``QUOTA_EXCEEDED_ERR``            |
+--------+-----------------------------------+
| 11     | ``TYPE_MISMATCH_ERR``             |
+--------+-----------------------------------+
| 12     | ``PATH_EXISTS_ERR``               |
+--------+-----------------------------------+

Configuring the Plugin (Optional)
---------------------------------

The set of available filesystems can be configured per-platform. Both iOS and Android recognize a tag in ``config.xml`` which names the filesystems to be installed. By default, all file-system roots are enabled.

::

    <preference name="iosExtraFilesystems" value="library,library-nosync,documents,documents-nosync,cache,bundle,root" />
    <preference name="AndroidExtraFilesystems" value="files,files-external,documents,sdcard,cache,cache-external,root" />

Android
~~~~~~~

-  ``files``: The application's internal file storage directory

-  ``files-external``: The application's external file storage directory

-  ``sdcard``: The global external file storage directory (this is the root of the SD card, if one is installed). You must have the ``android.permission.WRITE_EXTERNAL_STORAGE`` permission to use this.

-  ``cache``: The application's internal cache directory

-  ``cache-external``: The application's external cache directory

-  ``root``: The entire device filesystem

Android also supports a special filesystem named "documents", which represents a "/Documents/" subdirectory within the "files" filesystem.

iOS
~~~

-  ``library``: The application's Library directory

-  ``documents``: The application's Documents directory

-  ``cache``: The application's Cache directory

-  ``bundle``: The application's bundle; the location of the app itself on disk (read-only)

-  ``root``: The entire device filesystem

By default, the library and documents directories can be synced to iCloud. You can also request two additional filesystems, ``library-nosync`` and ``documents-nosync``, which represent a special non-synced directory within the ``/Library`` or ``/Documents`` filesystem.


.. seealso::

  *See Also*

  - :ref:`third_party_cordova_index`
  - :ref:`cordova_core_plugins`
