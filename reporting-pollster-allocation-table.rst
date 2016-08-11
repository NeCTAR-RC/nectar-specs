..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

=========================================
Add allocation data to reporting pollster
=========================================

The UoM requires reporting of allocation data that is not currently present in
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
* The extra layer of indirection improves the security of the primary data

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
:code:`rcallocation_allocation` dashboard table. The new table will contain the
following columns:

* tenant uuid as project id - to know which project the allocation is for
* contact email - needed to work out which faculty a project belongs to
* modified time - the date the allocation was last edited

This table will contain only the last edited copy of an allocation request
in the :code:`rcallocation_allocation` table. It will not attempt to keep
track of changes in time. Hence the tenant uuid / project id will be unique
and used as the primary key.

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

Security Impact
---------------

The extra layer of indirection created by going through the reporting database
gives greater security than that given by the alternate approach.

Deployer Impact
---------------

The reporting pollster will have to add the dashboard database to the
collection of databases that it draws on. Hence there will be changes
to its configuration file.

The puppet file that manages the reporting user will have to have read only 
access to the dashboard database granted.

The reporting pollster will have a schema change to its database. This 
schema change may have to be manually applied.

The pollster application should automatically populate the new table
once it is created. However, if this proves difficult to implement it
might be required that a one off query be run to prepopulate the table.

No components of OpenStack are affected.

Implementation
==============

Assignee(s)
-----------

Primary assignee:

* Martin Paulo <martin.paulo@unimelb.edu.au>

Other contributors:

* None

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
to the reporting `swagger api <http://swagger.io/>`_ as documentation. So:

* None

Change Management
=================

The changes will fit into the existing life cycle of the reporting application.


References
==========

* None




