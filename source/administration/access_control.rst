.. index::
  single: access

=============================
Access Control
=============================

.. index::
  pair: access control; users cannot update org validator

Create a Group Having No Ability to Update the Org Validator
------------------------------------------------------------

Requirements: You will need the UNSUPPORTED knife-acl plugin and a little time.

1) We are going to create a new group in the Private Chef webUI named anything that makes sense in your org. The one I created was named **no-update-validator**

2) Next, we will install the knife-acl knife plugin, preferrably in a new rbenv/rvm gemset, to avoid possibly trashing a working ruby gems setup.

  .. code-block:: bash

	$ gem install knife-acl

3) Then, using knife-acl, we can manage the permissions on the Nodes container for a given org in our Private Chef installation.

  For example, with a .chef/knife.rb configured properly and pointing at the organization where I just created the "no-update-validator" group, I can execute the following command and see the permissions on the top-level Nodes container for this org. Objects inherit the permissions of their container, if not manually assigned any others after creation.

  .. code-block:: bash

    $ knife acl show containers nodes  

  ::

    create: 
      actors:  []
      groups: 
	  admins
	  users
	  clients
	  no-update-validator
    delete: 
      actors:  ["pivotal"]
      groups: 
	  admins
	  users
    grant:  
      actors:  ["pivotal"]
      groups:  ["admins"]
    read:   
      actors:  []
      groups: 
	  admins
	  users
	  clients
	  no-update-validator
    update: 
      actors:  ["pivotal"]
      groups: 
	  admins
	  users  

  .. code-block:: bash

    $ knife acl add containers nodes delete group no-update-validator

  .. code-block:: bash

    $ knife acl add containers nodes update group no-update-validator

  .. code-block:: bash

    $ knife acl show containers nodes  

  ::

    create: 
      actors:  []
      groups: 
	  admins
	  users
	  clients
	  no-update-validator
    delete: 
      actors:  ["pivotal"]
      groups: 
	  admins
	  users
	  no-update-validator
    grant:  
      actors:  ["pivotal"]
      groups:  ["admins"]
    read:   
      actors:  []
      groups: 
	  admins
	  users
	  clients
	  no-update-validator
    update: 
      actors:  ["pivotal"]
      groups: 
	  admins
	  users
	  no-update-validator

  And we see that the no-update-validator group now has update and delete permissions on the nodes container.

4) Finally, continue on with the other permissions for the Nodes container, and the other permissions for the other containers needed, like Environments, Users, and so on.

.. note::
	  
	  The permissions above can be understood more completely by referring to http://wiki.opscode.com/display/chef/Hosted+Chef+Authorization
