..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

==========================================
Example Spec - The title of your blueprint
==========================================

Introduction paragraph -- why are we doing anything? A single paragraph of
prose that operators can understand. The title and this first paragraph
should be used as the subject line and body of the commit message
respectively.

Some notes about the nectar-spec and blueprint process:

* The aim of this document is first to define the problem we need to solve,
  and second agree the overall approach to solve that problem.

Some notes about using this template:

* Your spec should be in ReSTructured text, like this template.

* Please wrap text at 79 columns.

* Please do not delete any of the sections in this template. If you have
  nothing to say for a whole section, just write: None

* For help with syntax, see http://sphinx-doc.org/rest.html

* If you would like to provide a diagram with your spec, ascii diagrams are
  recommended (http://asciiflow.com/ is a very nice tool to assist with making
  ascii diagrams). png and/or jpeg formatted files can be included and
  embedded in a spec, however these won't provide the same integrated review
  capabilities as full ascii inside gerrit. If you do embed external images
  then please also provide the original image/diagram source (preferably in a
  readily usable format (i.e., not relying on some expensive proprietary tool)
  so that it can be edited by others.


Problem description
===================

A detailed description of the problem. What problem is this blueprint
addressing?

Use Cases
----------

What use cases does this address? What impact on actors does this change have?
Ensure you are clear about the actors in each use case: Developer, End User,
Deployer etc.

Project Priority
-----------------

Does this blueprint fit under one of EIF or NCRIS Work Packages, is it a
priority for your Node, is it just nice to have? If so please mention it here.

Proposed change
===============

Here is where you cover the change you propose to make in detail. How do you
propose to solve this problem?

If this is one part of a larger effort make it clear where this piece ends. In
other words, what's the scope of this effort?

At this point, if you would like to just get feedback on if the problem and
proposed change fit in NeCTAR, you can stop here and post this for review to
get preliminary feedback. If so please say:
Posting to get preliminary feedback on the scope of this spec.

Alternatives
------------

What other ways could we do this thing? Why aren't we using those? This doesn't
have to be a full literature review, but it should demonstrate that thought has
been put into why the proposed solution is an appropriate one.


Security impact
---------------

Describe any potential security impact on the system.


Notification impact
-------------------

Please specify any notifications that need to happen and to who. Users,
operators, Node heads, NeCTAR directorate etc.


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

What is the impact on the docs from this change?


References
==========

Please add any useful references here. You are not required to have any
reference. Moreover, this specification should still make sense when your
references are unavailable. Examples of what you could include are:

* Links to mailing list or IRC discussions

* Links to notes from a summit session

* Links to relevant research, if appropriate

* Anything else you feel it is worthwhile to refer to

