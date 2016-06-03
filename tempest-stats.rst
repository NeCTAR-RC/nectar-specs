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

NeCTAR runs tempest tests mimicking users' action to check if services are working. It is useful to graph how long these tests take, so that we can see trends over time.

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

#. Jenkins will trigger Tempest tests
#. Test output will be logged, and converted to a reasonable format (junitxml?).
#. Junitxml will be parsed and send to a collection backend (graphite / influxdb?)
#. Monitor graphs for trends

Alternatives
------------

An alternative implementation will be sending the output of tests directly to
Nagios (Step 3 of proposed change). We can still get alerts but miss the trends
over time.

Security impact
---------------

Test Results database needs to be secured.

Notification impact
-------------------

None

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

#. Tempest tests will be modified to be triggered Jenkins.

    Adds ability for operators to trigger tests and also look at test output.

#. Test Suites will be modified to output a subunit stream (in addition to
   pretty output).
   
#. The subunit stream will be converted to a junitxml report. An example output looks like this::

    <testsuite errors="0" failures="0" name="" tests="8" time="300.144">
    <testcase classname="tempest.api.compute.servers.test_create_server.ServersTestJSON" name="test_host_name_is_same_as_server_name[id-ac1ad47f-984b-4441-9274-c9079b7a0666]" time="26.109"/>
    <testcase classname="tempest.api.compute.servers.test_create_server.ServersTestJSON" name="test_list_servers_with_detail[id-585e934c-448e-43c4-acbf-d06a9b899997]" time="0.259"/>
    <testcase classname="tempest.api.compute.servers.test_create_server.ServersTestJSON" name="test_verify_created_server_vcpus[id-cbc0f52f-05aa-492b-bdc1-84b575ca294b]" time="0.448"/>
    <testcase classname="tempest.api.compute.servers.test_create_server.ServersTestJSON" name="test_verify_server_details[id-5de47127-9977-400a-936f-abcfbec1218f,smoke]" time="0.000"/>
    <testcase classname="tempest.api.compute.volumes.test_attach_volume.AttachVolumeTestJSON" name="test_attach_detach_volume[id-52e9045a-e90d-4c0d-9087-79d657faffff]" time="133.440"/>
    <testcase classname="tempest.api.compute.volumes.test_attach_volume.AttachVolumeTestJSON" name="test_list_get_volume_attachments[id-7fa563fe-f0f7-43eb-9e22-a1ece036b513]" time="54.991"/>
    <testcase classname="tempest.api.compute.volumes.test_volume_snapshots.VolumesSnapshotsTestJSON" name="test_volume_snapshot_create_get_list_delete[id-cd4ec87d-7825-450d-8040-6e2068f2da8f]" time="10.323"/>
    <testcase classname="tempest.api.compute.volumes.test_volumes_get.VolumesGetTestJSON" name="test_volume_create_get_delete[id-f10f25eb-9775-4d9d-9cbe-1cf54dae9d5f]" time="5.257"/>

#. A script will parse the XML to send metrics to a database backend.

    The choice of backend to be determined. Candidates are graphite, or influxdb.

    The backend should preferably be a time-series database, and also stored
    multiple key-value pairs (*testname*, *hostname*, *availability_zone*)

#. The same script can also directly trigger alerts. (**TBD**?).

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
