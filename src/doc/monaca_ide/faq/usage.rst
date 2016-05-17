Usage
===================================================================================================


.. _faq05~001:

Tell me about the steps to develop applications for mobile devices using Monaca. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Monaca was designed to work on the cloud, everything is happened in web browser via Internet. Therefore, there is no need of installing any development environments and other specific softwares in your PC or Mac. The following steps are the mobile app development steps using Monaca:

* Register user in Monaca. 
* Write HTML5/CSS3/JavaScript with Editor on Monaca Cloud IDE. 
* If needed, check application operations using Monaca Debugger. 
* Build the application using Monaca Cloud IDE. 
* Download and install the built application file (.app/.apk) in a smartphone device. 

Moreover, note that in order to install the built application on iPhone or iPad, you need to register iOS Developer Program. For more details, please refer to  :doc:`../manual/build/ios/index/`. 


.. _faq05~002:

Can I create my own project template?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    
We do not offer a template function for the projects. 

.. _faq05~003:

The Code Editor's cursor on the Monaca Cloud IDE is shown to be off in its alignment. What should I do?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Code Editor on the Monaca Cloud IDE may not be able to handle the scale from the display function of your browser. Please use the Monaca Cloud IDE without using the browser's enlarge/reduce functions. (In many browsers, you can reset with Ctrl+0.)

.. _faq05~004:

I don't know how to write the program. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As references for app development using Monaca, we have prepared a tutorial, introductory guide, and sample apps. 
Each of these reference materials provides descriptions on how to write specific codes, so please do take a look. 
( :ref:`third_party_cordova_index` and :doc:`../sampleapp/index` )


.. _faq05~005:

When developing an app, is it necessary to own a server?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When developing an app with Monaca, you don't need to own a server because Monaca provides server functions with backend services. For more details, please refer to :ref:`monaca_backend_index`.

.. _faq05~006:

Does Monaca support team development?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, Monaca supports team development. Users can share their projects to other registered users using the team function in Monaca Cloud IDE. For more detail, please refer to :ref:`team_tab`. 

The usability of this function depends on your usage plan with Monaca.

If your plan is Gold, Platinum or Enterprise, team development allows you to:

1. Manage the team: add/remove members to the shared project.

2. Share the source code with multiple people (members are assigned as Developers):

  - The easiest way is to use Monaca's built-in "share" feature. Then, two or more people can open the same project in the IDE. However, if there is any conflict, the previous version will be overwritten (still remains in the file history). 

  - Another way is to set up a version control system and do the local development using Monaca Localkit or Monaca CLI. This requires a higher skill set, but more collaborative.

  - The last option is to use Monaca for Visual Studios. In this case, the files can be managed by VS's built in Team Explorer functionality. Git, TFS, Visual Studio Online and other supported version control system can be used in this case.

3. Let multiple people to test the project (members are assigned as Testers): Use Monaca's built-in "share" feature, and share the project with the test members.


However, if your usage plan is Basic or Personal, you can only chat and join a team as a Tester. For more information of the usage plan and its limitation, please refer to `Monaca Usage Plan <https://monaca.mobi/en/pricing>`_.

.. _faq05~007:

In Monaca, how is the security of development assets maintained?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  
Currently, for general use, each user's resources are controlled by each account on the same server. 
We can handle on an individual basis of strengthening the security such as having an independent location of each resource or enforcing source IP restrictions for access (fee-based). 
Please contact us `here <https://monaca.mobi/page/contact>`_. 

.. _faq05~08:

Are there any keyboard shortcuts or keybindings that can be used on the Monaca Cloud IDE? 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shortcuts that can be used on Monaca Cloud IDE are listed in  :doc:`../manual/development/monaca_ide/editor`. Also, Monaca can use keybindings like *vim*. You can set the keybinding from the Environment Settings of the File menu on the top of the page of Monaca Cloud IDE. 


.. _faq05~09:

I want to change the background color of the Splash screen. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 
For the changes to the Splash screen, you can configure from the "Splash Screen Settings" in :ref:`config_ios_app_monaca` and :ref:`config_android_app` for iOS and Android, respectively. 



