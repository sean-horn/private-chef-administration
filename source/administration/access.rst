.. index::
  single: access

=============================
Access
=============================

.. index::
  pair: access; ssh_nagios

SSH Access to Nagios
--------------------

In order to access Nagios on the primary/standalone backend with only a SSH connection, make your SSH connection this way

.. code-block:: bash

  $ ssh -L9671:localhost:9671 USERNAME@PRIVATE_CHEF_BACKEND_FQDN

And then in a browser location line enter the URL: http://localhost:9671/nagios

.. note::

   The default username/password for Nagios in a Private Chef installation can be found at :ref:`Nagios Auth Settings <configuration-nagios-auth>`

SSH Access to CouchDB/Futon
---------------------------

In order to access CouchDB or Futon on the primary/standalone backend with only a SSH connection, make your SSH connection this way

.. code-block:: bash

  $ ssh -L5984:localhost:5984 USERNAME@PRIVATE_CHEF_BACKEND_FQDN

And then in a browser location line enter the URL: http://localhost:5984/_utils
