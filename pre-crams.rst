..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

================================================
Urgent pre-CRAMS NeCTAR application form changes
================================================

The NeCTAR NCRIS 2013 Allocations Work Package (WP8) has been funded by NeCTAR
to build a new generalised allocations system for the Research Cloud. This
new system, named CRAMS (Cloud Resource Allocation Management System), is
expected to replace the existing NeCTAR allocations system that is built into
the NeCTAR dashboard.

Whilst work on CRAMS has already started, the NeCTAR Nodes and Directorate
have identified a set of urgent changes required to the existing application
form used to apply for resources through the NeCTAR dashboard. The primary
motivations for these changes are threefold:

 * To help applicants complete a request more easily,
 * To ensure Merit Allocation Committee members have the information they
   require to make a timely decision, and
 * To ensure Nodes have the information required to manage their service
   offerings and support their business models.

This spec is concerned with these prioritised changes to the existing forms.


Problem description or motivation
=================================

The primary motivation of the changes outlined in this document is to ensure
applicants, Merit Allocation Committe Members and Nodes do not need to wait
until CRAMS development and deployment is complete before *quick wins* can
be achieved.

Use Cases
----------

The proposed changes will:

1. Make it easier for applicants to complete a request for resources by
   improving field names and help text, limiting options (such as end-dates) to
   allowed values, and adding fields that will assist in the expedited
   processing of their application.
2. Ensure Merit Allocation Committee members have the information they require
   to make a timely decision --- this includes the ability to mark an
   allocation as primarily belonging to a particular node, and capturing
   information relvant to assessing the merit of a request.
3. Ensure Nodes have the information required to manage their service offerings
   and support their business models before the CRAMS system becomes
   available.

Project Priority
-----------------

This project follows on from the NCRIS funded NeCTAR Allocations Work Package
(Work Package 8), and is funded with EIF money earmarked to implement the Cloud
Resource Allocation Management System (CRAMS). The CRAMS budget has a component
reserved for implementing changes to the current NeCTAR Allocation request form
that are required prior to the release of CRAMS.


Proposed change
===============

To achieve the goals of this work, fields will be changed and help text updated
so that it is easier for applicants to understand and complete a request;
additional fields will be added to capture information required to process
requests faster and assess the merit of requests; and additional fields will be
added to caputure information required by Nodes to support their business
models.

Alternatives
------------

The CRAMS project will replace the current NeCTAR Allocation form, and is
scheduled to go-live by the end of 2015. However, there are a number of urgent
changes required by the Nodes before this date that necessitated an update of
the current request form.

Security impact
---------------

These changes should not have any significant impact on security. Current
security controls will remain unchanged. Additional data gathered as
part of each request is not more sensitive than the existing information.

Notification impact
-------------------

Allocations approvers, DHD and rc-ops will all need to be notified of the
changes as users may have new questions regarding the new fields. End-user
notification other than a support news article (also useful for DHD reference)
is unnecessary.

Deployer impact
---------------

Implementation
==============

Assignee(s)
-----------

Primary assignee:
  Sebastian Barney <sebastian.barney@monash.edu>

Other contributors:
  Rafi Feroze <mohamed.feroze@monash.edu>
  Simon Yu <xiaoming.yu@monash.edu>
  Blair Bethwaite <blair.bethwaite@monash.edu>
  NeCTAR Core Services & User Support

Work Items
----------

CRAM-7
    As a researcher submitting a request I want the help text more clearly
	linked to the field to which it applies.
	
	An information icon has been added next to each field heading with help
	text. The help text appears in a frame on click.

CRAM-4
    As a researcher I want the purpose of the *Research title* field to be
	clearer so I provide the information required by the allocation committee.
	
	This field has been relabeled to *Research description* as recommended by
	the NeCTAR Directorate.

CRAM-15
    As the NeCTAR Directorate we want to simplify the options for selecting a
	project end-date so that people understand the use of this information.
	
	The *end date* field has been replaced with an *Estimated project duration*
	field, with options of 1-month, 3-months, 6-months and 12-months. Help text
	indicates that projects are approved for a maximum 12-month period, but can
	be extended once approved.

CRAM-5
    As a researcher I want to better understand what is required of the
	*Geographic requirements* field so I can have the best change with my
	request.
	
	A drop-down list has been added allowing an applicant to request the
	resources of a particular NeCTAR Node or select *National/Unallocated*.
	
CRAMS-68
	As a researcher submitting a request I want consistent terminology so I can
	complete the form confidently.
	
	The word *Institution* has replaced *University* and *Organisation*.
	
CRAMS-71
	As a researcher submitting a request I want a date picker so that I can
	select my start date more easily.
	
	Date picker now used for start date.
	
CRAMS-73
	As an applicant I want support completing the core-hours so that I can
	answer correctly and get the resources I need.
	
	The default number of core hours is now calculated to the number of cores
	requested multiplied by the period of time estimated multiplied by 0.5.

CRAM-2
    As an Allocation Committee Member I want to know the intended primary
	location of a request so that I can review applications most relevant to my
	node.
	
	A column listing the information provided in the *Geographic requirements*
	field has been added to the list of requests for approval, so that
	approvers can easily identify the requests relevant to their node.
	
CRAM-6
    As an Allocation Committee member I want to be able to change the requested
	*Allocation home* so that the request goes in the queue of the correct
	member.
	
	Allocation Committee Members are able to change the *Allocation home* on a
	request without approving or denying so that it is seen and processed by
	the appropriate Allocation Committee Member.
	
CRAM-25
    As a Allocation Committee Member I want to know the Chief Investigator for
	a project so I can better assess the academic merit of a request.
	
	Fields have been added to the request form to gather information on the
	Chief Investigator.

CRAM-18
    As an Allocation Committee Member I want to know which institutions will be
	supported by an application.
	
	A field has been added to collect information on the institutions supported
	by the request.

CRAM-31
    As a Allocation Committee Member I want to know how many people will be
	using an allocation so I can determine the merit of the request.
	
	A field has been added to collect the number of people using an allocation.

CRAM-49
    As a Allocation Committee Member I want a list of publications for each
	project so that I can assess the merit of an allocation request.
	
	Fields have been added to capture information on related publications.

CRAM-41
    As a Allocation Committee Member I want to know if a project has received
	grants so that I can assess the merit of the request.
	
	Fields have been added to capture information on related grants.

CRAM-65
    BUG: Approvers could edit approved requests, which caused conflicts.
	
	Approvers can no longer edit approved requests.
	
CRAM-64
	As a Node I want to know the split between Nationally funded and node
	funded allocations so I can manage my resources more effectively.
	
	Fields have been added on the approval page to indicate the percentage an
	allocation is funded under the National Merit Scheme, with a dropdown list
	to select the node that will be funding any difference.


Dependencies
==============

No known dependencies.


Documentation Impact
====================

There is no known documentation impacted by these changes.

The current user support documentation does not need to be extended. Help is
provided on the form for all fields as appropriate.


Change Management
=================

All changes will be communicated to the current Allocation Committee Members
for feedback and to ensure they are understood prior to the changes being
implemented.

The implementation of these changes will be undertaken in coordination with the
core services team.


References
==========

The requirements for development and associated development tasks are
documented in Monash University's JIRA instance:
https://jira-vre.its.monash.edu.au/browse/CRAM-52

The original requirements for urgent changes and their priorities, as described
by representatives of all NeCTAR Nodes and the NeCTAR Directorate:
https://docs.google.com/document/d/1CXFnxewMzdGPu3aXRkFLkmJZ7mTqn7zbEKaGJleMJWc


Additional feedback received
https://docs.google.com/document/d/1to68OvrorMabAxvZsDnLQXDrtbXyPIYO6SYtVmb3wW4
