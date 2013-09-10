================================
Installing Ajenti & Wondershaper
================================

Ajenti and Wondershaper don't get installed via ./runansible in the standard DXS setup. (as of Aug 31, 2013) :-)

There are some steps required.

* There is a bug in the code which doesn't install gcc as one of the dependencies. 

::

    yum -y install gcc

* The Ajenti-Wondershaper-plugin pull request hasn't been merged at the time of writing this gist. Please check if it has been so the following instruction might be stale. We first need to pull in the changes to the dxs repo on the server.

::
    
    git checkout -b migonzalvar-issue4468-create-ajenti-wondershaper-plugin master
    git pull https://github.com/migonzalvar/dxs.git issue4468-create-ajenti-wondershaper-plugin

* Download and execute these two files to your ``dxs_repo_root``

    * https://gist.github.com/migonzalvar/7baa9663c13b30ab53f7/raw/ef4dcd38eb886441d46fd6d7e821be1525aa18cc/test.sh
    * https://gist.github.com/migonzalvar/7baa9663c13b30ab53f7/raw/275922b103014ebebaf18bd11fe1c6d8d655a446/test.yml
    * ``chmod a+x test.sh``
    * ``./test.sh``

* You should be able to login to ajenti after typing http://schoolserver:9990 in your browser. The user name is *root* and password is *admin*. Once you login, Ajenti will probably tell you something crashed. However, click the continue button to the main UI. You may also want to click the *wondershaper* link on the bottom of the left sidebar, change settings and test your uplink/downlink speeds.

.. note:: If for some reason, ajenti doesn't start after being installed, it might have a corrupted configuration. The most certain way to fix that is to remove ajenti by ``pip uninstall ajenti`` and do the whole setup again.
