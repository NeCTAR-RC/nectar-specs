..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

=======================================
Hivemind extension for security actions
=======================================
This will be a tool to support NeCTAR operators and support staff in dealing
with security incidents involving compromised user instances.


Problem description or motivation
=================================
NeCTAR operators and security staff have to manually execute commands to
address security incidents. Having a tool to automate these commands in one
place will save time and ensure no critical information is missing and the
proper procedure has been followed.

We hope that this tool will also expedite the process of dealing with security
issues caused by compromised instances, and provide insight and help us
establish possible trends between security incidents.

This extension will automate the following actions:
 * Lock instance
 * Pause instance
 * Add metadata to the instance
 * Create a FreshDesk ticket (and apply 'security' tag)
 * Add instance information to the ticket
 * Add email addresses for tenant manager(s) and instance owner to the ticket
 * Send email with standard template to tenant managers/users
 * Deleting the exploited instance

These actions will be available indvidually as separate commands, but there will
also be a 'big_red_button' command to fully automate the process.

Use Case
---------
NeCTAR, or a member node is made aware of a compromised instance. A support
person performs some actions to determine a possible cause of the compromise,
and then pauses and locks the instance.

The tool will automate the process of:
 #. Stopping and locking the instance
 #. Gather all the OpenStack instance, user, etc information
 #. Create a ticket in FreshDesk with all applicable information
 #. Add user to newly created ticket as a CC
 #. Send an email to the user to inform them that their instance has been
    compromised and locked
 #. Delete the exploited instance

The actual process of engaging with the user will be determined once we have a
better understanding of how to use the FreshDesk API and its limitations.


Proposed change
===============
A new hivemind extension will be added, called *security*.

This extension will add the following commands:

 * **hivemind security.takedown**
    - Used for the full process of dealing with a compromised instance
    - Will pause, lock, gather information, create ticket and then add
      tenant manager(s) and owner to ticket for receiving future
      correspondance

 * **hivemind security.lock_instance**
    - Will pause and lock an instance
    - Will create an initial ticket to track instance information by staff,
      but not add tenant/owner to ticket at this stage.

 * **hivemind security.instance_info**
    - Print instance/tenant information to the console (this is the same
      information that will be added to the ticket, as part of the lock
      process).

 * **hivemind security.unlock_instance**
    - Unlock an instance only and update ticket

 * **hivemind security.delete_instance**
    - Delete an instance and update ticket

Metadata will be added to the instance to track the progress of security
process, and each step will add a new comment to the FreshDesk ticket.

Alternatives
------------
UoM node have some shell scripts they use, but are out of date and have a
different focus. They do have some scripts to extract the image from the
underlying storage for the user to download on request.


Security impact
---------------
Handling of compromised instances should be more consistant and quicker.


Notification impact
-------------------
NeCTAR support people should be made aware of this tool and it should be
documented and incorporated into the support manual.


Implementation
==============

Assignee(s)
-----------
Primary assignee:
 * Andy Botting <andrew.botting@unimelb.edu.au>


Work Items
----------
 #. Develop security.instance_info tool
 #. Investigate FreshDesk API
 #. Add lock/unlock commands
 #. Add logic for adding tenant manager(s) and owners to tickets for
    receiving correspondance.


Documentation Impact
====================
The Hivemind security tool will require a small amount of documentation, but the
majority of work should be around incorporating this into the support manual and
processes.


Change Management
=================
This tool should be included into the new process of dealing with compromised
instances. All NeCTAR support staff should be made aware of it.

References
==========
None

