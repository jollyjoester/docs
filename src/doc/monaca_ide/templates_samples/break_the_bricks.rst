.. _break_the_bricks:

============================================
Break the Bricks
============================================

.. rst-class:: right-menu


This is a sample game based on :file:`pixi.js` which is a super fast HTML5 2D rendering engine that uses webGL with canvas fallback. For more information about Pixi, please refer to `here <https://github.com/GoodBoyDigital/pixi.js>`_. In the game, player controlls a paddle to prevent a ball from falling while trying to clear the bricks. The objective of the game is to clear all the bricks.


| *Tested Environments:* Android 4.4, iOS 8.1.1


.. raw:: html

  <div class="iframe-samples">
    <iframe src="https://monaca.github.io/project-templates/5-monacanoid/www/index.html" style="max-width: 150%;"></iframe>
  </div>

File Components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: images/break_the_bricks/break_1.png
    :width: 200px


================================== ===========================================================================================================================
``index.html``                       The Startup page (Home page)

``js/main.js``                       A JavaScript file handling various implementation in the application
 
``css/style.css``                    Style Sheet for the whole application 

``img/*.png``                        All image files needed to use this template

``res/VT323-Regular.ttf``            A true type font
================================== ===========================================================================================================================

Required JS/CSS Components 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

============================ ============================
``Pixi``
============================ ============================


Source Code Explanation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

js/main.js
=======================

:file:`main.js` is a JavaScript file handling various functionalities of the application. 

Below is the code of ``BB`` object which is the main object of this application. Its properties are screensize, paddle, balls, blocks, score and so on. Its methods are creating block map (``setMap()``), creating a ball (``addBall()``), creating a paddle (``addPaddle()``), resetting the game after it ended (``reset()``), calculating the score (``addScore()``), ending the game (``endGame()``) and so on.


.. code-block:: javascript

    ...
    var BB = {
        stage: new PIXI.Stage(0x000000),
        renderer: null,
        screenSize: null,
        paddle: null,
        balls: [],
        blocks: [],
        score: 0,
        scoreLabel: null,
        accelLabel: null,
        isMouseDown: false,
        
        // Create blocks map
        setMap: function() {
            var blockMap = [
                [null,      null,       null,       null,       null,       'blue',     null,       null,       null,       null],
                [null,      null,       null,       null,       'red',      'red',      'blue',     null,       null,       null],
                [null,      null,       null,       'red',      'red',      null,       null,       'blue',     null,       null],
                [null,      null,       'red',      'red',      null,       null,       null,       null,       'blue',     null],    
                [null,      'red',      'red',      null,       null,       'gold',     null,       null,       'silver',   'silver'],    
                [null,      null,       'red',      'red',       null,       null,       null,       'silver',   'silver',   null],    
                [null,      null,       null,       'red',      'red',       null,       'silver',   'silver',   null,       null],    
                [null,      null,       null,       null,       'silver',   'silver',   'silver',   null,       null,       null],
                [null,      null,       null,       null,       null,       'silver',   null,       null,       null,       null]
            ];
            
            for(j = 0; j < blockMap.length; j++) {
                for(i = 0; i < blockMap[j].length; i++) {
                    if(blockMap[j][i] !== null) {
                        var block = BB.addBlock(10 + (30 * i), 80 + (12 * j), blockMap[j][i]);
                    }
                }
            }
        },
        
        /**
         * @param {int} x
         * @param {int} y
         * @param {String} color red,blue,silver,gold
         * @return {Object} block
         **/
        addBlock: function(x, y, color) {
            switch (color) {
                case "red":
                case "blue":
                    var point = SETTINGS_POINT;
                    break;
                case "silver":
                    var point = SETTINGS_POINT_SILVER;
                    break;
                case "gold":
                    var point = SETTINGS_POINT_GOLD;
                    break;    
                default:
                    var point = SETTINGS_POINT;
                    color = "red";
                    break;
            }
            
            var texture = PIXI.Texture.fromImage(imgPath["block_" + color], false);
            var block = new PIXI.Sprite(texture);
         
            block.anchor.x = 0.5;
            block.anchor.y = 0.5;
         
            block.position.x = x;
            block.position.y = y;
            
            block.width = 30;
            block.height = 12;
            
            block.point = point;
         
            BB.stage.addChild(block);
            BB.blocks.push(block);
            
            return block;
        },
        
        // Create a ball and add it to PIXI.Stage
        addBall: function() {
            var texture = PIXI.Texture.fromImage(imgPath["ball"], false);
            var ball = new PIXI.Sprite(texture);
         
            ball.anchor.x = 0.5;
            ball.anchor.y = 0.5;
         
            ball.position.x = parseInt(BB.renderer.width * 0.5);
            ball.position.y = 200;
            
            ball.width = 10;
            ball.height = 10;
            
            ball.delta = {
                'x' : Math.random() - 0.5,
                'y' : -0.4 
            };
         
            BB.stage.addChild(ball);
            BB.balls.push(ball);
        },
        
        // Create a paddle and add it to PIXI.Stage
        addPaddle: function() {
            var texture = PIXI.Texture.fromImage(imgPath["paddle"], false);
            BB.paddle = new PIXI.Sprite(texture);
         
            BB.paddle.anchor.x = 0.5;
            BB.paddle.anchor.y = 0.5;
         
            BB.paddle.position.x = parseInt(BB.renderer.width * 0.5);
            BB.paddle.position.y = BB.renderer.height - 60;
            
            BB.paddle.width = 60;
            BB.paddle.height = 10;
            
            BB.paddle.accel = 0;
            BB.paddle.delta = {
                'x' : Math.random() - 0.5,
                'y' : -3.8 
            };
         
            BB.stage.addChild(BB.paddle);
        },
        
        /**
         * Add points to current score
         * @param {int} val points to add
         */
        addScore: function(val) {
            BB.score += parseInt(val);
            BB.scoreLabel.setText(BB.score);        
        },
        
        /**
         * Set score
         * @param {int} val new score
         */
        setScore: function(val) {
            BB.score = val;
            BB.scoreLabel.setText(BB.score);
        },
        
        /**
         * callback for PhoneGap Acceleration Watch
         * @param {Object} a a.x, a.y, a.z
         */
        updateAcceleration: function(a) {
            var accelText = "", ac = a.x.toFixed(2);
                
            if(a.x > 0) accelText = '+' + String(ac);
            else accelText = String(ac);
        
            // Use parameter x to move paddle
            if (BB.paddle !== null) {
              if (BB.paddle.accel / ac > 2.0) {
                
              } else if (BB.paddle.accel / ac > 0) {
                BB.paddle.accel += ac * SETTINGS_PADDLE_ACCEL;
              } else {
                BB.paddle.accel = ac * SETTINGS_PADDLE_ACCEL;
              }
            }
            
            BB.accelLabel.setText(accelText);
        },

        // Reset current game and start new one
        reset: function() {
            //Reset (remove all children in the stage if exists)
            for (var i = BB.stage.children.length - 1; i >= 0; i--) {
                BB.stage.removeChildAt(i);
            }
            
            BB.balls = [];
            BB.blocks = [];
            BB.setMap();
            for (var i = 0; i < SETTINGS_BALL_NUM; i++) {
                BB.addBall();
            }
            BB.addPaddle();
            
            var resetLabel = new PIXI.Text("RESET", {font: "24px/1.2 vt", fill: "red"});
            resetLabel.position.x = 18;
            resetLabel.position.y = BB.renderer.height - 52;
            BB.stage.addChild(resetLabel);
            resetLabel.buttonMode = true;
            resetLabel.interactive = true;
            resetLabel.click = resetLabel.tap = function(data) {
                BB.reset();  
            };
            setTimeout(function() {
                resetLabel.setText("RESET"); //for Android
            }, 1000, resetLabel);
            
            var label = new PIXI.Text("SCORE:", {font: "24px/1.2 vt", fill: "red"});
            label.position.x = 20;
            label.position.y = 20;
            BB.stage.addChild(label);
            setTimeout(function() {
                label.setText("SCORE:"); //for Android
            }, 1000, label);
            
            BB.scoreLabel = new PIXI.Text("0", {font: "24px/1.2 vt", fill: "white"});
            BB.scoreLabel.position.x = 90;
            BB.scoreLabel.position.y = 20;
            BB.stage.addChild(BB.scoreLabel);
            BB.setScore(0);
            
            /*
            var label = new PIXI.Text("ACCEL:", {font: "24px/1.2 vt", fill: "red"});
            label.position.x = 160;
            label.position.y = 20;
            BB.stage.addChild(label);
            label.setText("ACCEL:"); //for Android
            
            BB.accelLabel = new PIXI.Text("0", {font: "24px/1.2 vt", fill: "white"});
            BB.accelLabel.position.x = 230;
            BB.accelLabel.position.y = 20;
            BB.stage.addChild(BB.accelLabel);
            */
            
            BB.gameState = GAMESTATE_PLAY;
        },
        
        /**
         * Check whether the ball hits the object
         * @param {PIXI.Sprite} ball
         * @param {PIXI.Sprite} obj target object
         */
        isBallHit: function(ball, obj) {
            return (ball.position.x > (obj.position.x - (obj.width * 0.5))) &&
                (ball.position.x < (obj.position.x + (obj.width * 0.5))) &&
                (ball.position.y > (obj.position.y - (obj.height * 0.5))) &&
                (ball.position.y < (obj.position.y + (obj.height * 0.5)));
        },
        
        // Game Over        
        endGame: function() {
            BB.gameState = GAMESTATE_STOP;
            vibrate();
        },
        
        // Game Clear
        clearGame: function() {
            if(typeof navigator.notification !== 'undefined') navigator.notification.alert("Cleared!", function(){}, "Congraturations");
            else alert("Cleared!");
            
            BB.gameState = GAMESTATE_STOP;
        }
    }
    ...


When this page is loading, ``init()`` function is called when Cordova is fully loaded or when it's failed to detect the type of the device. 

.. code-block:: javascript

    ...
    window.onload = function() {
        if(getUa() === false) init();
        else document.addEventListener("deviceready", init, false);
    }
    ...


Here is the code of ``init()`` function. In this function, BB object is rendered according to the type of device you are using. Then, events listeners related the paddle are added. Also, it renders the paddle position according to each event.

.. code-block:: javascript

    ...
    function init() {
        // Accelerometer
        /*
        if (typeof navigator.accelerometer !== 'undefined' && !accelerationWatch) {
            accelerationWatch = navigator.accelerometer.watchAcceleration(
                BB.updateAcceleration, 
                function(ex) {
                    alert("accel fail (" + ex.name + ": " + ex.message + ")");
                }, 
                {frequency: SETTINGS_ACCELEROMETER_RELOAD_FREQ}
            );
        }
        */
        BB.screenSize = setBound();
     
        BB.renderer = (getUa() === "Android") ? new PIXI.CanvasRenderer(BB.screenSize.width, BB.screenSize.height) : new PIXI.autoDetectRenderer(BB.screenSize.width, BB.screenSize.height),
        BB.renderer.transparent = false;
        document.body.appendChild(BB.renderer.view);
        
        setScale(BB.screenSize);
        
        BB.reset();
        
        // Event listeners to control the paddle
        window.addEventListener("touchmove", function(e) {
            BB.paddle.position.x = e.touches[0].clientX / BB.screenSize.zoom;
        });
        
        window.addEventListener("mousedown", function(e) {
            BB.isMouseDown = true;
        });
        
        window.addEventListener("mouseup", function(e) {
            BB.isMouseDown = false;
        });
        
        window.addEventListener("mousemove", function(e) {
            if(BB.isMouseDown) BB.paddle.position.x = e.clientX;
        });
        
        window.addEventListener("keydown", function(e) {
            switch (e.which) {
                case 37:
                    BB.paddle.position.x -= 4;
                    BB.paddle.accel += (SETTINGS_PADDLE_ACCEL * 0.1);
                    break;
                case 39:
                    BB.paddle.position.x += 4;
                    BB.paddle.accel -= (SETTINGS_PADDLE_ACCEL * 0.1);
                    break;
                case 38:
                    BB.paddle.position.y -= 1;
                    break;
            }
        });

        requestAnimFrame(animate);
    }
    ...




``getUa()`` function is used to detect the type of the device. It will return ``false`` when it failed to get this information.

.. code-block:: javascript

    ...
    function getUa() {
        if ((navigator.userAgent.indexOf('iPhone') > 0 && navigator.userAgent.indexOf('iPad') == -1) || navigator.userAgent.indexOf('iPod') > 0 ) {
            return 'iPhone'; 
        } else if(navigator.userAgent.indexOf('iPad') > 0) {
            return 'iPad';
        } else if(navigator.userAgent.indexOf('Android') > 0) {
            return 'Android';
        } else return false;
    }
    ...
