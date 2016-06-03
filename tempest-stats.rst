..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

==========================================
Tempest Tests Statistics
==========================================
Add the ability to collect Tempest test logs and statistics, and graph statistics over time.

Problem description or motivation
=================================

NeCTAR runs tempest tests mimicking users' action to check if services are
working. It is useful to graph how long these tests take, so that we can see
trends over time.

Use Cases
----------

#. Upgrades

    Core Services and Node Operators can compare run times of tests before and
    after an upgrade, to see if performance has been impacted or improved in
    any way. An example test might be time taken to launch an instance (for
    nova upgrade), or time taken to attach a snapshot (for cinder upgrade).

#. Trends

    Operators can monitor graphs for trends, so that abnormalities like
    spikes in tests' run times can be seen. This can be a good indication /
    warning of impending doom.

#. History

    Users feedback that 'snapshots are taking very long'. Historical
    information can be consulted to see if snapshots really are taking longer,
    or is just a figment of the users' imagination.

Project Priority
-----------------

This is a non-urgent, business-as-usual improvement.

Proposed change
===============

The change will be split into different phases for implementation

Phase 1
#. Jenkins will trigger Tempest tests.
#. Test output will be output as a subunit stream.
#. Subunit stream will be split, one copy will be passed to subunit-trace and
   output to stdout.
#. Another copy of the stream will be sent to a gnocchi script, parsed and
   uploaded to gnocchi.

Phase 2
#. Data in gnocchi can be retrieved and graphed using grafana.

Phase 3
#. Graphs can be monitored for trends. An example is a sudden spike in test
   completion time.

Alternatives
------------

An alternative implementation will be sending the output of tests directly to
Nagios (Step 3 of proposed change). We can still get alerts but miss the trends
over time.

Security impact
---------------

OpenStack credentials to post to gnocchi needs to be secured. We will keep it
in an internal repo.

Graphing frontend needs to be secured too. We can front it using the mon box
and allow certain AAF users, like how we are doing for Melbourne nodes's
grafana.

Notification impact
-------------------

Node Operators may be made aware of this monitoring system so that they can use it
for themselves.


Deployer impact
---------------

None.

Implementation
==============

Assignee(s)
-----------
Primary assignee:
  jake.yip@unimelb.edu.au

Other contributors:
  andrew.botting@unimelb.edu.au

Work Items
----------

#. Tempest tests will be modified to be triggered via Jenkins timer.

#. Test Suites will be modified to output a subunit stream (in addition to
   pretty output).

#. Split the subunit stream and send a copy of it to be processed into gnocchi

#. Graph it using grafana, grafana-gnocchi plugin

#. Monitoring (TBD???). Possible solutions will be via gnocchi API, or via influxdb.

Dependencies
============

None at this point in time.


Documentation Impact
====================

The implementation will be documented as part of this work.


Change Management
=================

None at this point in time.

References
==========

None at this point in time.
