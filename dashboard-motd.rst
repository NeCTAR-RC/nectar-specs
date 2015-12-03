..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

==========================================
Dashboard Message Of The Day
==========================================

Ability to post short announcements somewhere we know Research Cloud users
will see them - the Dashboard.

This will complement, not replace, existing communications such as email.

Problem description or motivation
=================================

By comparison with the existing email notifications, these MOTDs will be:

* More timely, as email transmission/reading delay will be eliminated;
* More targeted to the users of the research cloud, as the MOTD
  will be visible to everyone using the Dashboard, not merely to the
  owner of an instance.
* More efficient and more clear, as it will be easily updatable
  as situations evolve, so that superceded information can be corrected
  or removed.

Use Cases / User Stories
------------------------

1. Sam the Sysadmin notifies end users of a technical problem

Sam is a Research Cloud sysadmin. Sam notices a technical problem in the RC,
which he believes may have impact on end users. Sam therefore decides
to notify end users of the problem, of its impacts, and of fix progress.

Sam opens a web browser and goes to a certain bookmarked URL. He is presented
with a simple and easy-to-use (key success criterion) HTML form.
Sam types (or pastes) a notification to end users that there is a problem
into the form, then submits it. Sam receives confirmation that his message
has been received and will be displayed to end users.

Sam works on the technical problem for some time, and makes some progress,
such that he now has an accurate idea of the time remaining to resolution.
Sam communicates this projected resolution time to end users using the same
HTML form as previously, but this time with an updated message.

After some further time, the issue is resolved. Sam uses the form a third time
to write a notification to end users that the issue has been resolved.

2. Edgar the End User receives notification of a problem

Edgar is a busy user of the Research Cloud. Edgar does not have time to read
email.
Edgar's work using the Research Cloud has unfortunately been interrupted
due to a technical problem with the research cloud.
Edgar notices the impact of the problem, and decides to use the Dashboard
to investigate it. Edgar does not read any email he may have received.
Edgar therefore opens his web browser and goes to the Dashboard URL.

Before he is able to begin using the Dashboard to investigate the problem
(key success criterion: impossible to accidentally not notice messaging),
Edgar is presented with a message explaining exactly what the problem is,
what its impacts on him will be, and the estimated time to resolution.
Edgar realises that he will be unable to use the research cloud in the
presence of this problem, so he decides to wait until after the expected
resolution time before resuming use of the cloud.

Half-way to the expected resolution time, Edgar becomes impatient.
He therefore re-opens his web browser, and again visits the Dashboard.
Edgar is again presented with a salient message, which now contains
additional and different information to that in the first message.

Edgar does not become confused by presentation of multiple conflicting
messages, some of which supercede others (key success criterion).
Edgar does not receive an ugly and confusing multitude of messages (also key).

After some time has passed, Edgar ceases to be presented with such messages
when he uses the Dashboard, without his having taken any explicit action
to accomplish this. Key success criterion: Edgar will not be annoyed
by being forced to manually dismiss the messages presented to him in order to
use the Dashboard.

Project Priority
-----------------

This is a non-urgent, business-as-usual improvement.

Proposed change
===============

The intention is to leverage Twitter for all parts of this change, from
initial message insertion using a tweet through to display of the message
to end users using one of the existing Twitter display widgets.

Message creation
----------------

By tweeting to a Twitter feed created especially for use by this feature,
using one of the many existing Twitter UIs.

Message modification
--------------------

By editing of a previous tweet using an existing Twitter UI.

Message display
---------------

By use of a Twitter "embedded timeline widget" as documented at:

https://dev.twitter.com/web/embedded-timelines

There shall be a fixed upper limit to the number of messages the widget will
display. This limit will be controllable via modifications to the Dashboard.

Message appearance
------------------

The appearance of messages is fairly tightly restricted by Twitter:

https://about.twitter.com/company/display-requirements

Message expiry
--------------

There shall be a maximum age of message; tweets older than this will
not be displayed by the widget. Thus, all messages will eventually
expire automatically, so will not need to be manually deleted.
This age limit will be controllable via modifications to the Dashboard.

Message deletion
----------------

By deletion of the tweet using an existing Twitter UI.

Graceful Degradation
--------------------

The Dashboard shall degrade gracefully in the face of unavailability of
Twitter services and/or content.

Authentication and Authorisation
--------------------------------

The ability to post messages using this feature shall be limited to a set of
trusted individuals.
It is anticipated that Twitter's existing authentication and authorisation
systems will be sufficient for this purpose.

Alternatives
------------

Alternatives considered include:

* Use of a Content Management System, such as Drupal or Wordpress.
  The existing Drupal site may be decommissioned, so was rejected.
  CMSs in general are a heavy hammer with which to crack this nut.

* Creation of a simple CMS-like facility within Dashboard.
  This would be wheel-reinvention.

Security impact
---------------

A new set of credentials for the Twitter account will be generated.
These will need to be securely stored and transmitted to those who
require them in order to post messages.

Notification impact
-------------------

No notifications required.

Deployer impact
---------------

None anticipated.

Implementation
==============

Assignee(s)
-----------

Primary assignee:
  matthew.sanderson@anu.edu.au

Work Items
----------

1. Move existing Proof of Concept widget to somewhere publicly visible for review.
   Could just email it around, as it's a small static HTML page.

2. Fine-tune appearance of widget, while still conforming to Twitter guidelines.

3. Agree on and implement max-message-count and maximum-age configuration.

4. Submit widget as a change to Dashboard.

Dependencies
============

Correct functioning of the Twitter APIs, and connectivity to them from
the end user's web browser.

Documentation Impact
====================

New documentation atefacts to be delivered as part of this work:

* Process documentation: How do end users add, modify and remove messages?
  This to include pointers to existing Twitter documentation.


Change Management
=================

Not required.

References
==========

There are rumours of existing design work, but this author has never seen it.
