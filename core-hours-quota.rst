..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

================
Core Hours Quota
================

Currently the NeCTAR RC sets quota based on the max number of instances and
cores a user can have at one time. To make better use of our resources and
plan allocations capacity we should move to a quota system that includes a
consumable such as core hours.


Problem description
===================

Use Cases
---------

When making an allocation request users estimate their core hour requirements
as an indication of total usage required for their project, e.g., over a six
month period they may require 100 cores for 3 weeks. For capacity planning and
allocation purposes this is very different to a potential usage of 100 cores
for six months, which is the status quo.

Project Priority
----------------

This blueprint is related to the NCRIS2013 WP8 on allocations, however it is
being treated as BAU improvement work by Core Services.


Proposed change
===============

For all new and updated allocations we would not assign any quota, instead we would
check daily the core hours of the project and handle things like the project trials.

Notifications would be sent out when certain thresholds were met:
 * 80% - warning email
 * 100% - prevent project from creating new resources (set quota to 0)
 * 120% - Suspend all resources

1 month after suspension all resources would be archived then deleted.
Archived resources would be kept for 3 months and then permanetly deleted.

Alternatives
------------

Keep it the way it is

Security impact
---------------

None

Notification impact
-------------------

This is a major change and Users, operators, Node heads, NeCTAR directorate
will need to be notified.

Deployer impact
---------------

Discuss things that will affect how you deploy and configure OpenStack
that have not already been mentioned, such as:

* What config options are being added?

* Is this a change that takes immediate effect after its merged, or is it
  something that has to be explicitly enabled?

* If this change is a new binary, how would it be deployed?

* Please state anything that those doing continuous deployment, or those
  upgrading from the previous release, need to be aware of. Also describe
  any plans to deprecate configuration values or features. For example, if we
  change the directory name that instances are stored in, how do we handle
  instance directories created before the change landed? Do we move them? Do
  we have a special case in the code? Do we assume that the operator will
  recreate all the instances in their cloud?


Implementation
==============

Assignee(s)
-----------

Who is leading this effort

If more than one person is working on the implementation, please designate the
primary author and contact.

Primary assignee:
  <email or None>

Other contributors:
  <email or None>

Work Items
----------

Work items or tasks -- break the feature up into the things that need to be
done to implement it. Those parts might end up being done by different people,
but we're mostly trying to understand the timeline for implementation.


Dependencies
============

* Include specific references to specs that this one either depends on or
  is related to.


Documentation Impact
====================

The process for PT expiry on the support site will need to be updated to cover
this change. General information about allocations will also need to be
updated and a news item placed on the support site.


References
==========

Please add any useful references here. You are not required to have any
reference. Moreover, this specification should still make sense when your
references are unavailable. Examples of what you could include are:

* Links to mailing list or IRC discussions

* Links to notes from a summit session

* Links to relevant research, if appropriate

* Anything else you feel it is worthwhile to refer to

