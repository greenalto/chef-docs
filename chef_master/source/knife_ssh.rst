=====================================================
knife ssh
=====================================================

.. include:: ../../includes_knife/includes_knife_ssh.rst

**Syntax**

.. include:: ../../includes_knife/includes_knife_ssh_syntax.rst

**Options**

.. note:: Review the list of :doc:`common options </knife_common_options>` available to this (and all) |knife| subcommands and plugins.

.. include:: ../../includes_knife/includes_knife_ssh_options.rst

**knife.rb File Settings**

.. include:: ../../includes_knife/includes_knife_using_knife_rb.rst

..note:: See :doc:`knife.rb </config_rb_knife>` for more information about how to add optional settings to the |knife rb| file.

.. include:: ../../includes_knife/includes_knife_ssh_settings.rst

**Examples**

For example, to query for all nodes that have the "webserver" role and then use |ssh| to run the command "sudo chef-client", enter:

.. code-block:: bash

   $ knife ssh "role:webserver" "sudo chef-client"

.. include:: ../../step_knife/step_knife_ssh_run_chef_client_on_all_nodes.rst

To upgrade all nodes, enter:

.. code-block:: bash

   $ knife ssh name:* "sudo aptitude upgrade -y"

To find the uptime of all of your Web servers running |ubuntu| on the |amazon ec2| platform, enter:

.. code-block:: bash

   $ knife ssh "role:web" "uptime" -x ubuntu -a ec2.public_hostname

to return something like:

.. code-block:: bash

   ec2-174-129-127-206.compute-1.amazonaws.com  13:50:47 up 1 day, 23:26,  1 user,  load average: 0.25, 0.18, 0.11
   ec2-67-202-63-102.compute-1.amazonaws.com    13:50:47 up 1 day, 23:33,  1 user,  load average: 0.12, 0.13, 0.10
   ec2-184-73-9-250.compute-1.amazonaws.com     13:50:48 up 16:45,  1 user,  load average: 0.30, 0.22, 0.13
   ec2-75-101-240-230.compute-1.amazonaws.com   13:50:48 up 1 day, 22:59,  1 user,  load average: 0.24, 0.17, 0.11
   ec2-184-73-60-141.compute-1.amazonaws.com    13:50:48 up 1 day, 23:30,  1 user,  load average: 0.32, 0.17, 0.15

To force a |chef client| run on all of your Web servers running |ubuntu| on the |amazon ec2| platform, enter:

.. code-block:: bash

   $ knife ssh "role:web" "sudo chef-client" -x ubuntu -a ec2.public_hostname
   
to return something like:

.. code-block:: bash

   ec2-67-202-63-102.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:37 +0000] INFO: Starting Chef Run (Version 0.9.10)
   ec2-174-129-127-206.compute-1.amazonaws.com [Fri, 22 Oct 2010 14:18:37 +0000] INFO: Starting Chef Run (Version 0.9.10)
   ec2-184-73-9-250.compute-1.amazonaws.com    [Fri, 22 Oct 2010 14:18:38 +0000] INFO: Starting Chef Run (Version 0.9.10)
   ec2-75-101-240-230.compute-1.amazonaws.com  [Fri, 22 Oct 2010 14:18:38 +0000] INFO: Starting Chef Run (Version 0.9.10)
   ec2-184-73-60-141.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:38 +0000] INFO: Starting Chef Run (Version 0.9.10)
   ec2-174-129-127-206.compute-1.amazonaws.com [Fri, 22 Oct 2010 14:18:39 +0000] INFO: Chef Run complete in 1.419243 seconds
   ec2-174-129-127-206.compute-1.amazonaws.com [Fri, 22 Oct 2010 14:18:39 +0000] INFO: cleaning the checksum cache
   ec2-174-129-127-206.compute-1.amazonaws.com [Fri, 22 Oct 2010 14:18:39 +0000] INFO: Running report handlers
   ec2-174-129-127-206.compute-1.amazonaws.com [Fri, 22 Oct 2010 14:18:39 +0000] INFO: Report handlers complete
   ec2-67-202-63-102.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:39 +0000] INFO: Chef Run complete in 1.578265 seconds
   ec2-67-202-63-102.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:39 +0000] INFO: cleaning the checksum cache
   ec2-67-202-63-102.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:39 +0000] INFO: Running report handlers
   ec2-67-202-63-102.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:39 +0000] INFO: Report handlers complete
   ec2-184-73-9-250.compute-1.amazonaws.com    [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Chef Run complete in 1.638884 seconds
   ec2-184-73-9-250.compute-1.amazonaws.com    [Fri, 22 Oct 2010 14:18:40 +0000] INFO: cleaning the checksum cache
   ec2-184-73-9-250.compute-1.amazonaws.com    [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Running report handlers
   ec2-184-73-9-250.compute-1.amazonaws.com    [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Report handlers complete
   ec2-75-101-240-230.compute-1.amazonaws.com  [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Chef Run complete in 1.540257 seconds
   ec2-75-101-240-230.compute-1.amazonaws.com  [Fri, 22 Oct 2010 14:18:40 +0000] INFO: cleaning the checksum cache
   ec2-75-101-240-230.compute-1.amazonaws.com  [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Running report handlers
   ec2-75-101-240-230.compute-1.amazonaws.com  [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Report handlers complete
   ec2-184-73-60-141.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Chef Run complete in 1.502489 seconds
   ec2-184-73-60-141.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:40 +0000] INFO: cleaning the checksum cache
   ec2-184-73-60-141.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Running report handlers
   ec2-184-73-60-141.compute-1.amazonaws.com   [Fri, 22 Oct 2010 14:18:40 +0000] INFO: Report handlers complete



