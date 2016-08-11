..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

=========================================
Add allocation data to reporting pollster
=========================================

The UoM requires reporting of allocation_ data that is not currently present in
the reporting application database.


Problem description or motivation
=================================

The UoM wishes to know how much they have allocated to which faculty on any
given day. There are a number of options for procuring the data, but
going through the reporting database was felt to be the best approach, as:

* It means that the added table becomes available to other institutions
* The configuration and management of the 'hoovering' up of data is kept
  in a single well known location: making it simpler to manage and track.
* Once ingested the required allocations data can easily be combined with the
  runtime data currently stored in the reporting database

Use Case
--------

A UoM manager wishes to see how much is allocated. They go to the UoM
reporting application, and query it. It in turn goes to the reporting
database and fetches the required data for display to the manager.

Project Priority
----------------

This project is of great importance to UoM. So much so that they are funding
the resources to do the work.

Proposed Change
---------------

To add a table that contains the required allocation data taken from
:code:`rcallocation_allocationrequest` dashboard table. The new table will
contain the following columns:

* tenant uuid as project id - to know which project the allocation is for
* contact email - needed to work out which faculty a project belongs to
* modified time - the date the allocation was last edited

This table will contain only the last edited copy of an allocation request
in the :code:`rcallocation_allocationrequest` table. It will not attempt to
keep track of changes in time. Hence the tenant uuid / project id will be
unique and used as the primary key.

In addition to the table, code to populate and update it will need to be
added to the report pollster application.

Alternatives
------------

The alternative is to get and maintain read only connections to the following
databases:

* rcshib
* dashboard
* keystone
* nova

Or alternately, to the following two databases:

* rcshib
* reporting

Security Impact
---------------

* None

Deployer Impact
---------------

The reporting pollster will have to add the dashboard database to the
collection of databases that it draws on. Hence there will be changes
to its configuration file.

The reporting database user will have to have permissions to access the
dashboard database added in the puppet scripts that control them.

The reporting pollster will have a schema change to its database.
This will require a manual intervention to apply the schema change.

The pollster application will automatically populate the new table
once it is created.

No components of OpenStack are affected.

Implementation
==============

Assignee(s)
-----------

Primary assignee:

* Martin Paulo <martin.paulo@unimelb.edu.au>

Other contributors:

* Simon Fowler <simon.fowler@anu.edu.au>

Work Items
----------

#. Create new table definition
#. Add to schema
#. Update database
#. Update application configuration file
#. Write tests and code to populate and maintain the new table
#. Test
#. Deploy

Dependencies
============

* None

Documentation Impact
====================

The new table will be commented: those comments automatically flow through
to the reporting `swagger api <http://swagger.io/>`_ as documentation.

The NeCTAR wiki is be updated with a new reporting_ page being added
to describe both the application and its deployment.

The reporting_ wiki entry will contain a link to the original requirements_.

Change Management
=================

The changes will fit into the existing life cycle of the reporting application.

References
==========

.. _allocation: https://support.ehelp.edu.au/support/solutions/articles/6000055380-resources-available-to-you
.. _reporting: https://wiki.rc.nectar.org.au/wiki/Reporting
.. _requirements: https://drive.google.com/drive/folders/0B3_G7mPpWLltaVVpRTlCN01oQ1U
