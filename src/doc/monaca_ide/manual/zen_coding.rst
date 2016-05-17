.. _emmet:

================================================
Emmet 
================================================

.. rst-class:: right-menu


What is Emmet?
================================================

`Emmet (formerly Zen Coding) <http://docs.emmet.io/>`_  is an editor plugin for high-speed CSS, HTML (or any other structured code format) coding and editing. It was formerly called as Zen Coding. Monaca Emmet plugin contains a powerful abbreviation engine which allows you to expand expressions (similar to CSS selectors) into HTML code. For example, type the following line in ``<body>`` tag of an HTML file on the Monaca Cloud IDE and then press :kbd:`tab`  key.


::

  div#index>div.content+ul#navigation>li*4>a
  

After pressing the :kbd:`tab`  key, the above line will be expanded into:

::

  <div id="index">
    <div class="content"></div>
    <ul id="navigation">
      <li><a href=""></a></li>
      <li><a href=""></a></li>
      <li><a href=""></a></li>
      <li><a href=""></a></li>
    </ul>
  </div>


The following Emmet actions along with keyboard shortcuts are supported in Monaca:

- :ref:`expandAbbr`
- :ref:`wrapAbbr`
- :ref:`matchTag`
- :ref:`matchTagInward`.

Please note that almost every action highly depends on current cursor position inside the editor.

.. _expandAbbr:

Expand Abbreviation (TAB)
================================================
It searches abbreviation from your current cursor position and expands it into HTML or CSS code. Here is a syntax list of properties and operators supported by Emmet:


======================== ======================================= ==============================
Syntax                    Description                             Example
======================== ======================================= ==============================
``E``                     :ref:`elementName`                      ``div``
``E#id``                  :ref:`elementId`                        ``div#content``
``E.class``               :ref:`elementClass`                     ``div.header``
``E#id.class``            :ref:`elementIdClass`                   ``div#content.column.width``
``E>N``                   :ref:`childElement`                     ``div>p``
``E+N``                   :ref:`siblingElement`                   ``h1+p``
``E*N``                   :ref:`elementMult`                      ``ul#nav>li*5>a``
``E$*N``                  :ref:`itemNum`                          ``ul#nav>li.item-$*5``
``E[attr]``               :ref:`elementAttr`                      ``p[title]``
``E|filter``              :ref:`elementFilter`                    ``p.title|e``
``P:V (CSS)``             :ref:`propertyValues`                   ``fl:r+d:b+w:300+h:600``
======================== ======================================= ==============================



.. _elementName:

.. rst-class:: function-reference

Element Name
^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax 
  :dfn:`E`

Example
  ====================================== ======================================
  ``div``, ``p``, ``h1``, etc.
  ====================================== ======================================

  ::

      h1
  
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <h1></h1>

.. rst-class:: function-reference

.. _elementId:

Element with Identifier
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax 
  :dfn:`E#id`

Example
  ============================================================================ ======================================
  ``div#content``, ``p#intro``, ``span#error``, etc.
  ============================================================================ ======================================

  ::

      p#intro

  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <p id="intro"></p>


.. rst-class:: function-reference

.. _elementClass:

Element with Class
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax
  :dfn:`E.class`

Example
  ======================================================= =====================
  ``div.header``, ``p.error.critial``, etc.
  ======================================================= =====================

  ::

      p.error.critial
      
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <p class="error critial"></p>

.. rst-class:: function-reference

.. _elementIdClass:

Element with ID and Class
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax
  :dfn:`E#id.class`

Example
  ======================================================= =====================
  ``div#content.column.width``, etc.
  ======================================================= =====================

  ::

      div#content.column.width
      
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <div id="content" class="column width"></div>

.. rst-class:: function-reference

.. _childElement:

Child Element
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax
  :dfn:`E>N`

Example
  ======================================================= =====================
  ``div>p``, ``div#footer>p>span``, etc.
  ======================================================= =====================

  ::

      div#footer>p>span
      
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <div id="footer">
        <p>
          <span></span>
        </p>
      </div>


.. rst-class:: function-reference

.. _siblingElement:

Sibling Element
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax
  :dfn:`E+N`


Example
  ======================================================= =====================
  ``h1+p``, ``div#header+div#content+div#footer``, etc.
  ======================================================= =====================

  ::

     div#header+div#content+div#footer
      
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <div id="header"></div>
      <div id="content"></div>
      <div id="footer"></div>

.. rst-class:: function-reference

.. _elementMult:

Element Multiplication
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax
  :dfn:`E*N`

Example
  ======================================================= =====================
  ``ul#nav>li*5>a``, etc.
  ======================================================= =====================
  
  ::

      ul#nav>li*5>a
      
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <ul id="nav">
        <li><a href=""></a></li>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
      </ul>     

.. rst-class:: function-reference

.. _itemNum:

Item Numbering
^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax
  :dfn:`E$*N`

Example
  ======================================================= =====================
  ``ul#nav>li.item-$*5``, etc.
  ======================================================= =====================

  ::

      ul#nav>li.item-$*5
      
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <ul id="nav">
        <li class="item-1"></li>
        <li class="item-2"></li>
        <li class="item-3"></li>
        <li class="item-4"></li>
        <li class="item-5"></li>
      </ul>

.. rst-class:: function-reference

.. _elementAttr:

Element with Attribute
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax
  :dfn:`E[attr]`

Example
  ============================================================================ ==========================
  ``p[title]``, ``td[colspan=2]``, ``span[title="Hello" rel]``, etc.
  ============================================================================ ==========================

  ::

      td[colspan=2]
      
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      <td colspan="2"></td> 

.. rst-class:: function-reference

.. _elementFilter:

Element with Filter
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For more information about ``Filter``, please refer to `Zen Coding Filter Wiki  <https://code.google.com/p/zen-coding/wiki/Filters>`_ .

Syntax
  :dfn:`E|filter`

Example
  ======================================================= =====================
  ``p.title|e``, etc.
  ======================================================= =====================

  ::

      p.title|e
      
  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      &lt;p class="title"&gt;&lt;/p&gt;  


  ``<`` and ``>`` was escaped into HTML Entities, such as``&lt;`` and ``&gt;``.

.. rst-class:: function-reference

.. _propertyValues:

CSS Abbreviation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Syntax
  :dfn:`P:V`

Example

  ======================================================= =====================
  ``fl:r+d:b+w:300+h:600``, etc.
  ======================================================= =====================

  After pressing the :kbd:`tab`  key, the above line will be expanded into:

  ::

      float: right;display: block;width: 300px;height: 600px;


  For more information about ``CSS Abbreviation``, please refer to `Zen Coding CSS Wiki  <https://code.google.com/p/zen-coding/wiki/ZenCSSPropertiesEn>`_ .

.. _wrapAbbr:

Wrap with Abbreviation (CTRL+SHIFT+A)
================================================

.. warning:: Currently, this action work correctly only with Windows.

It boosts coding speed with proper coding indentation. It takes Emmet abbreviation, expands it and places currently selected content or current cursor position in the last element of expanded abbreviation. For example, we have the following HTML code:

::

  <body>
    <div class="lesson">
      <h1>Introduction to Monaca</h1>
      <p>In this page, we will take a brief look at Monaca.</p>
    </div>
  </body>

  
We want to wrap ``<h1>`` into a class called "chapter1". With Emmet, we can either select the whole ``<h1></h1>`` tag or put the cursor inside ``<h1>`` tag and press ``CTRL+SHIFT+A``. Then, an input form will appear asking us to input the Emmet abbreviation. Please input "div.chapter1" and press "OK". The following snippet is the result of this action:

::

  <body>
    <div class="lesson">
      <div class="chapter1">
        <h1>Introduction to Monaca</h1>
      </div>
      <p>In this page, we will take a brief look at Monaca.</p>
    </div>
  </body>


However, if you select ``<h1>`` content only or the current cursor is inside the content, then only the content is wrapped inside the class "chapter1" under ``<h1>`` tag.

::

  <body>
    <div class="content">     
      <h1>
        <div class="chapter1">
          Introduction to Monaca
        </div>
      </h1>
      <p>In this page, we will take a brief look at Monaca.</p>
    </div>
  </body>


.. _matchTag:

Match Tag Pair (CTRL+D)
================================================


It selects the whole content of the element which contains the current cursor.


.. _matchTagInward:

Match Tag Pair Inward (CTRL+SHIFT+D)
================================================


It selects the whole content of the child element insides the element which contains the current cursor.

