..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

========================================================================
Enable SameHostFilter and DifferentHostFilter for all Availability Zones
========================================================================

Add SameHostFilter and DifferentHostFilter to nova-scheduler in all AZs.

Problem description or motivation
=================================

When a user boots an instance, nova-scheduler selects a host to launch the
instance on. By default, the user has no control over this selection.

In some cases, there is a need to make sure instances are launched on
different hosts.

Use Cases
----------

#. High Availability Cluster

    In a HA cluster, it will be a good idea to make sure instances are launched
    on different compute hosts. This will protect against a single hypervisor
    failure bringing down all the nodes in the cluster.

#. High Performance Computing

   In a HPC scenario, it will be useful to launch instances on different
   compute hosts, to take advantage of unused CPU cycles across hosts. This is
   particularly important since many nodes have CPU oversubscription in place.


Project Priority
-----------------

This is a non-urgent continuous improvement.

Proposed change
===============

The change will add `SameHostFilter,DifferentHostFilter` to
`scheduler_default_filters` in `/etc/nova/nova.conf`.

After the change is implemented, a user can boot an instance with a 'hint' to
be on the same or different host as an existing instance. For example: `nova
boot --hint different_host=<uuid> <new_instance>`

Alternatives
------------

Other alternatives have not been explored since the solution is pretty clear

Security impact
---------------

No security impact is expected.

Notification impact
-------------------

Node Operators will need to be informed, to implement the change.

Users should also be notified of the new functionality, so that they can make
use of it.

Deployer impact
---------------

Node Operators will need to execute the change, e.g. update hiera variables.

Implementation
==============

Assignee(s)
-----------

Primary assignee:
  Jake Yip <jake.yip@unimelb.edu.au>

Work Items
----------

#. Create this spec.

#. Create a page in wiki detailing hiera values to edit.

#. Create new Change item for Operators to tick off when done.

Dependencies
============

None at this point in time.

Documentation Impact
====================

A 'Continous Improvement' announcement on FreshDesk will be useful to notify
users.

Change Management
=================

A change item will be prepared and linked to at https://wiki.rc.nectar.org.au/wiki/Changes

References
==========

#. http://docs.openstack.org/liberty/config-reference/content/section_compute-scheduler.html
