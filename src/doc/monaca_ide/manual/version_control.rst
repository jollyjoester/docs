================================================
Version Control (GitHub)
================================================


Introduction
================================================

Version control is a management tool that helps manage the changes to your project's source code and other collections of information. Usually, changes are determined by a revision code which is comprised of numbers and/or letters.  With version control, revision history can easily be tracked, compared against, restored and merged to control the whole set of your source code.  Additionally, version control systems provide is the ability to allow multiple team members or individuals to collaborate and maintain tracking over the source code.

Version Control is now available within Monaca Cloud IDE with user-friendly interface. There are many version control systems; however, currently Monaca Cloud IDE supports the integration of one of the most popular Git services called `GitHub <https://github.com>`_. If you integrate your Monaca project to your repository, you can simply manage your source code right away from Monaca Cloud IDE.

In this section, we will guide you on how to integrate your GitHub account with your Monaca account and configuring your Monaca project with a GitHub repository.

.. note:: Generally, you can only connect to public repositories. However, with valid Monaca subscription plan, you can additionally connect to private repositories. Please refer to `Pricing <https://monaca.mobi/en/pricing>`_.


Prerequisites
================================================

In order to use version control in Monaca Cloud IDE, you will need:

- a GitHub account. Register `here <https://github.com/join>`_.
- a Monaca account. Register `here <https://monaca.mobi/en/register/start>`__. 


GitHub Integration
===============================================================

.. _link_monaca_to_github:

Link Monaca Account to GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Log into `Monaca Cloud IDE <https://monaca.mobi/en/login>`_ with your Monaca account.

2. Go to :menuselection:`Your profile name --> GitHub Integration`.

  .. figure:: images/version_control/1.png
    :width: 320px   
    :align: left

  .. rst-class:: clear


3. Click on :guilabel:`Link` button. You are required to login with your GitHub account before being redirected to GitHub's Authorize Application page.

  .. figure:: images/version_control/2.png
    :width: 600px   
    :align: left

  .. rst-class:: clear

4. In the Authorize Application page, you will be asked to authorize the application in order to link Monaca account to GitHub. Click on :guilabel:`Authorize application` to proceed.

  .. figure:: images/version_control/3.png
    :width: 600px   
    :align: left

  .. rst-class:: clear


5. Now your Monaca account is successfully linked to your GitHub account.

  .. figure:: images/version_control/4.png
    :width: 600px   
    :align: left

  .. rst-class:: clear


.. warning:: Please note that you can only link one GitHub account to a Monaca account. If you try to link with multiple accounts, you will encounter an error.


Unlink Monaca Account from GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you want to unlink your Monaca account from GitHub, just click on :guilabel:`Unlink` button in Link to GitHub page.

.. figure:: images/version_control/4.png
  :width: 600px   
  :align: center

.. rst-class:: clear


Unable to Re-link to GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you accidentally revoke Monaca access with Github account, attempt to re-link with the steps described in :ref:`link_monaca_to_github` will not be possible. You will see the following error:

.. figure:: images/version_control/14.png
  :width: 600px   
  :align: center

.. rst-class:: clear


Therefore, in order to re-link your account in this case, please do as follows:

1. Logout from Monaca Cloud IDE.

2. Go to `Monaca Login <https://monaca.mobi/en/login>`_ page and choose :guilabel:`Sign in with GitHub`.

  .. figure:: images/version_control/15.png
    :width: 395px   
    :align: left

  .. rst-class:: clear

3. Fill in your GitHub account information.

4. Then, you will be redirected to GitHub's Authorize Application page. Click on :guilabel:`Authorize application` to proceed.

  .. figure:: images/version_control/3.png
    :width: 600px   
    :align: left

  .. rst-class:: clear

5. After this, your Monaca account should be successfully linked to GitHub account. You can confirm in the Link to GitHub page. It should appear like this: 

  .. figure:: images/version_control/4.png
    :width: 600px   
    :align: left

  .. rst-class:: clear


Version Control Configuration
===============================================================

Assuming that you have successfully integrated your Monaca account to GitHub account, you need to do some configurations in Monaca Cloud IDE in order to connect your project to your repository.

Please follow the configuration instruction below:

1. Log into `Monaca Cloud IDE <https://monaca.mobi/en/login>`_ with your Monaca account.

2. Open a project you want to connect to a repository. 

3. From Monaca Cloud IDE menu, go to :menuselection:`Version Control --> Configure...`.

4. Then, Monaca will list all of your empty GitHub repositories. If you do not have any empty repositories yet, you will be asked to create one.

  .. note:: Only an empty repository can be used to connect to a Monaca project. Please be aware that you cannot change to another repository after configuration.

  .. figure:: images/version_control/7.png
    :width: 600px   
    :align: left

  .. rst-class:: clear

5. Once you have an empty repository in GitHub, you are now able to select your remote repository. Then, click on :guilabel:`Initialize` button to save the configuration.

  .. figure:: images/version_control/8.png
    :width: 600px   
    :align: left

  .. rst-class:: clear

6. Your project is then being uploaded to your new repository in GitHub. By default, your working branch will be configured as master. If you want to switch to another working branch, please go to Version Control Configuration page (:menuselection:`Version Control --> Configure...`).

.. _version_control_import_project_github:

Import Existing Project from GitHub Repository
===============================================================

Once you have linked your Monaca account with GitHub, you can import any existing projects from GitHub repositories to Monaca Cloud IDE.

1. Log into `Monaca Cloud IDE <https://monaca.mobi/en/login>`_ with your Monaca account.

2. From Dashboard, go to :menuselection:`New Project --> Import Project`.

3. In Import Project dialog, fill in the necessary information and choose ``Import from GitHub Repository``. Then, select the repository and click on :guilabel:`Import` button.

  .. figure:: images/version_control/10.png
    :width: 500px   
    :align: left

  .. rst-class:: clear

4. If the import is successful, the new project will be added to Monaca Dashboard. By default, master branch will be applied to the imported project. You can switch the current working branch in the Version Control Configuration page (:menuselection:`Version Control --> Configure...`).


Working with Remotes
===============================================================

Once you have successfully connected your project with a repository, you can start working on the same project with your team members and keep it synchronized to the latest updates in Monaca Cloud IDE.

Monaca Cloud IDE provides a very user-friendly interface supporting version control of your code. Without learning Git from the scratch, you can still perform some basic Git commands directly from the IDE.


Checkout Current Working Branch
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you have more than one branch and want to switch the current working branch, please do as follows:

1. From Monaca Cloud IDE menu, go to :menuselection:`Version Control --> Configure`.

2. Choose the branch you want to switch to from current working branch, and click :guilabel:`Save` button.

  .. figure:: images/version_control/11.png
    :width: 600px   
    :align: left

  .. rst-class:: clear

.. note:: You will get an error message if you try to checkout to a new branch while you have not committed changes on the current working branch yet. Please push your changes to current branch first before checking out to another branch.


Retrieve Changes from Remotes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you are familiar with Git commands, retrieve changes from remotes here refers to ``git pull`` command. In order to retrieve the changes from remotes, from Monaca Cloud IDE menu, go to :menuselection:`Version Control --> Pull`. If there are changes in your remotes, you will receive those updates in your working branch.

.. note:: When you create a project in IDE, Monaca keeps all the files in :guilabel:`www` folder. Files outside of this folder are also synced even though they will not appear in the IDE.



Commit Changes to Remotes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After making changes in the current working branch, you are able to commit them back to your remote repository. To commit your changes, please do as follows:

1. From Monaca Cloud IDE menu, go to :menuselection:`Version Control --> Commit`. 

2. Fill in your commit message and check files you want to commit. Then, click on :guilabel:`Commit` button.

3. Once you are ready to push those updates to the remote repository, select :menuselection:`Version Control --> Push`. Once it is successfully pushed, your remotes will contain latest changes made in Monaca Cloud IDE.


Show Remote Commit History
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In order to see full history of your previous commits in remote repository, go to :menuselection:`Version Control --> Show Remote History`. You will be redirected to the remote Git service provider's website showing a commit history of your current branch.


Show Local Commit History
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Every commit you made in your Monaca Cloud IDE is called Local Commit. You are able to view your local commit history through :menuselection:`Version Control --> Show Commit History`. To view the changes in each commit, click on the commit on the left panel.


