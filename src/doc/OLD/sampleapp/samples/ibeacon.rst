.. _monaca_with_ibeacon:

============================================
iBeacon
============================================

.. rst-class:: right-menu


(Last Updated: 2014/02/05)

This sample app uses iBeacon service to detect its proximity to iBeacon device. This Monaca app has `Onsen UI <http://docs.monaca.mobi/onsen/index.html>`_ as its UI. When the mobile (running this app) gets close enough to a predefined iBeacon device, a new page showing its UUID will be displayed.


| *Tested Environments:* Android 4.4, iOS 8.0.2

.. raw:: html

  <div class="iframe-samples">
    <iframe src="https://monaca.github.io/project-templates/24-ibeacon/www/index.html"></iframe>
  </div>


.. note:: In order to test this application, you can either build the application or use the custom built Monaca Debugger.


Prerequisite
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Download the iBeacon plugin from `here <https://github.com/petermetz/cordova-plugin-ibeacon.git>`_ and import it into Monaca Cloud IDE. See :ref:`import_cordova_plugin`.

2. Find at least one iBeacon device.

3. Get information of each iBeacon device by using its conresponded utility software. In our case, we use `My Beacon Tool <https://itunes.apple.com/jp/app/mybeacon-tool/id848908053?mt=8>`_.

4. Take note of the UUID of each iBeacon device.


File Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/ibeacon/3.png
    :width: 200px
    :align: center

======================== ===================================================================================================================================== 
``index.html``             Startup Page (Consists of Connect Screen)

``top_page.html``          Top page of the application

``info_page.html``         The page showing information of each iBeacon

``js/app.js``              JavaScript file handling app interactions.

``css/style.css``          Stylesheet file for the application
======================== =====================================================================================================================================

Required JS/CSS Components 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============================ ============================
``Onsen UI``
============================ ============================

Required Cordova Plugins
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

================================================================================================= ============================
`Proximity Beacon Plugin <https://github.com/petermetz/cordova-plugin-ibeacon.git>`_
``Bluetooth``
================================================================================================= ============================


HTML Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The User Interface of this sample app is based on *Onsen UI*. For more information on *Onsen UI* tags and components, please refer to `Onsen UI Documentation <http://docs.monaca.mobi/onsen/index.html>`_.

The following contents of the HTML body of :file:`index.html` file loads the :file:`top-page.html` file at startup: 

.. code-block:: xml

  ...
    <ons-navigator var="myNavigator" page="top-page.html"></ons-navigator> 
  ...


The following contents of the HTML body of :file:`top-page.html` file:

.. code-block:: xml

  <ons-page ng-controller="TopPageCtrl">
    <ons-toolbar>
        <div class="center">iBeacon Testing</div>
    </ons-toolbar>

    <ons-list modifier="inset" style="margin: 10px">
        <ons-list-item class="list-item-container" ng-repeat="(uuid, beacon) in beacons">
            <ons-row>
                <ons-col width="70px">
                    <img ng-src="{{beacon.icon}}" class="top-page-icon">
                </ons-col>
                <ons-col>
                    <div class="top-page-name">{{beacon.name}}</div>
                    <div class="top-page-proximity">{{beacon.proximity}}</div>
                    <div class="top-page-proximity">{{beacon.rssi}} dBm</div>
                </ons-col>
            </ons-row>
        </ons-list-item>
    </ons-list>
  </ons-page>

corresponds to the screenshot below which allows a user to see a list of predefined iBeacon devices with its proximity:

.. figure:: images/ibeacon/1.png
   :width: 300px
   :align: center


The following contents of the HTML body of :file:`info-page.html` file: 

.. code-block:: xml

  <ons-page ng-controller="InfoPageCtrl">
    <ons-toolbar>
        <div class="left"><ons-back-button>Back</ons-back-button></div>
        <div class="center">{{beacon.name}}</div>
    </ons-toolbar>
    
    <ons-list>
        <ons-list-item class="list-item-container">
            <ons-row>
                <ons-col width="110px">
                    <img src="{{beacon.icon}}" class="info-page-img">
                </ons-col>
                <ons-col>
                    <div class="info-page-description">
                        <p style="text-decoration: underline;">UUID</p>
                      {{beaconUuid}}   
                  </div>  
                  
                </ons-col>
            </ons-row>
        </ons-list-item>
    </ons-list>
  </ons-page>

corresponds to the screenshot below which shows the information (UUID) of the closest iBeacon device to the mobile.

.. figure:: images/ibeacon/2.png
   :width: 270px
   :align: center


JavaScript Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The JavaScript codes of this sample app is based on AngularJS. In AngularJS, each page, which requires interactions, contains its own controller function. In this sample, we have 2 controller functions: :envvar:`TopPageCtrl` and :envvar:`InfoPageCtrl` corresponded to :file:`top-page.html` page and :file:`info-page.html` page, respectively. In order to create global vairables used between these controller functions, we create a service function to store those global variables as follows:

.. code-block:: javascript

  ...
    app.service('iBeaconService', function() {
      this.currentBeaconUuid = null;
      this.onDetectCallback = function(){};
      
      var beacons = {
          "00000000-EA98-1001-B000-001C4D9C64FA": {icon: 'img/1.jpg', rssi: -63, proximity: PROX_UNKNOWN, name: 'JIBBER', number: '1', id: '000265C9', major: 1, minor: 1},
          "F5A10AF9-A670-4F54-B491-8607393F0DDC": {icon: 'img/2.jpg', rssi: -63, proximity: PROX_UNKNOWN, name: 'BUONO', number: '2', id: '0002D08D', major: 1, minor: 1},
          "ABE425B2-0000-4409-8035-1668AFC7FCFE": {icon: 'img/3.jpg', rssi: -63, proximity: PROX_UNKNOWN, name: 'LION', number: '3', id: '00029BAA', major: 1, minor: 1},
          "BC564E82-0000-43A3-94E7-1D54EC02622D": {icon: 'img/4.jpg', rssi: -63, proximity: PROX_UNKNOWN, name: 'COMA', number: '4', id: '0003F321', major: 1, minor: 1},
          "6F29CF85-0000-414A-A7A6-6206A2DA9773": {icon: 'img/5.jpg', rssi: -63, proximity: PROX_UNKNOWN, name: 'GNAR', number: '5', id: '00027EA8', major: 1, minor: 1},
          "EEB52632-0000-47E2-8C15-897494E12015": {icon: 'img/6.jpg', rssi: -63, proximity: PROX_UNKNOWN, name: 'TEEMO', number: '6', id: '00032449', major: 1, minor: 1}
      };
      this.beacons = beacons;
      
      createBeacons = function() {
          var result = [];
          try {
              angular.forEach(beacons, function(value, key) {
                  result.push(new cordova.plugins.locationManager.BeaconRegion(value.id, key, value.major, value.minor));
              });
          } catch (e) {
              console.log('createBeacon err: ' + e);
          }
          return result;
      };
      
      this.watchBeacons = function(callback){
          document.addEventListener("deviceready", function(){
              var deviceVersion = window.device ? device.version : ''; 

              var beacons = createBeacons();
              
              try {    
                  var delegate = new cordova.plugins.locationManager.Delegate();

                  delegate.didDetermineStateForRegion = function (pluginResult) {
                  
                      console.log('[DOM] didDetermineStateForRegion: ' + JSON.stringify(pluginResult));
                  
                      cordova.plugins.locationManager.appendToDeviceLog('[DOM] didDetermineStateForRegion: '
                          + JSON.stringify(pluginResult));
                  };
                  
                  delegate.didStartMonitoringForRegion = function (pluginResult) {
                      console.log('didStartMonitoringForRegion:', pluginResult);
                  
                      console.log('didStartMonitoringForRegion:' + JSON.stringify(pluginResult));
                  };
                  
                  delegate.didRangeBeaconsInRegion = function (pluginResult) {
                      var beaconData = pluginResult.beacons[0];
                      var uuid = pluginResult.region.uuid.toUpperCase();
                      if (!beaconData || !uuid) {
                          return;
                      }
                      
                      callback(beaconData, uuid);
                      console.log('[DOM] didRangeBeaconsInRegion: ' + JSON.stringify(pluginResult));
                  };
                  
                  cordova.plugins.locationManager.setDelegate(delegate);
                  
                  // required in iOS 8+
                  cordova.plugins.locationManager.requestWhenInUseAuthorization(); 
                  // or cordova.plugins.locationManager.requestAlwaysAuthorization()
                  
                  beacons.forEach(function(beacon) {
                      cordova.plugins.locationManager.startRangingBeaconsInRegion(beacon);
                  });
                  
              } catch (e) {
                  console.log('Delegate err: ' + e);   
              }
          }, false);
      };
    });
  ...

Inside this service function, we are able to:
  
  - create an array of all predefined iBeacon devices' information (UUID, proximity, name, icon file and so on).
  - create a function to search for iBeacon devices nearby and retrieve the UUID of the closest iBeacon devices.


Next, we will explain each controller function:

TopPageCtrl
====================

:envvar:`TopPageCtrl` controls the interactions and processes in :file:`top-page.html` file. In other words, it searching for nearby iBeacon devices. If the predefined iBeacon devices are in range, their proximity and rssi (received signal strength indicator) information will be updated. Otherwise, their proximity value will appear as ``ProximityUnknown`` and their rssi value will appear as ``-63 dBm`` (see below screenshot).

.. figure:: images/ibeacon/4.png
   :width: 270px
   :align: center


Below is the JavaScript code of this function:

.. code-block:: javascript

  ...
  app.controller('TopPageCtrl', ['$scope', 'iBeaconService', function($scope, iBeaconService) {        
    
    $scope.beacons = iBeaconService.beacons;
    
    var callback = function(deviceData, uuid)
    {
        var beacon = $scope.beacons[uuid];
        $scope.$apply(function()
        {
            beacon.rssi = deviceData.rssi;
            switch (deviceData.proximity)
            {
                case PROX_IMMEDIATE:
                    beacon.proximity = 'Immediate';
                    break;
                case PROX_NEAR:
                    beacon.proximity = 'Near';
                    break;
                case PROX_FAR:
                    beacon.proximity = 'Far';
                    break;
                case PROX_UNKNOWN:
                default:
                    break;
            }

            if (iBeaconService.currentBeaconUuid === null && beacon.rssi > -45) {
                $scope.enterInfoPage(uuid);
            }
        });
    };
    iBeaconService.watchBeacons(callback);

    
    $scope.enterInfoPage = function(currentUuid) {
        iBeaconService.currentBeaconUuid = currentUuid;
        $scope.ons.navigator.pushPage('info-page.html');
        $scope.ons.navigator.on("prepop", function() {
          iBeaconService.currentBeaconUuid = null;
        });
    };
    
  }]);
  ...


InfoPageCtrl
=================

:envvar:`InfoPageCtrl` controls the interactions and processes in :file:`info-page.html` file. This controller simply displays the UUID of the closest iBeacon device by using the UUID value passing by the ``iBeaconService``. By "closest", we mean that the proximity of the iBeacon device is "Immediate". Otherwise, the :file:`info-page.html` will not displayed.


Below is the JavaScript code of this function:

.. code-block:: javascript

  ...
    app.controller('InfoPageCtrl', ['$scope', 'iBeaconService', function($scope, iBeaconService) {
        $scope.beacon = iBeaconService.beacons[iBeaconService.currentBeaconUuid];
        $scope.beaconUuid = iBeaconService.currentBeaconUuid;
    }]);
  ...

