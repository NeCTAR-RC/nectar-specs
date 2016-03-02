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


Use Case
---------
NeCTAR, or a member node is made aware of a compomised instance. A support
person performs some actions to determine a possible cause of the compromise,
and then locks the instance.

The tool will automate the process of:
 1. Locking the instance
 2. Gather all the OpenStack instance, user, etc information
 3. Create a ticket in FreshDesk with all applicable information
 4. Add user to newly created ticket as a CC
 5. Send an email to the user to inform them that their instance has been
    compromised and locked.

The actual process of engaging with the user will be determined once we have a
better understanding of how to use the FreshDesk API and its limitations.


Project Priority
-----------------
This project is low priority.


Proposed change
===============
A new hivemind extension will be added, called *security*.

This extension will add the following commands:

 * **hivemind security.lock_instance**
    - Used for the full process of dealing with a compromised instance
    - Will lock, gather information, create ticket and alert user
 * **hivemind security.unlock_instance**
    - Unlock an instance only
 * **hivemind security.instance_info**
    - Print instance/tenant information to the console (this is the same
      information that will be added to the FD ticket, as part of the lock
      process)


Alternatives
------------
UoM node have some shell scripts they use, but are out of date and have a
different focus. They do have some scripts to extract the image from the
underlying storage for the user to download on request.


Security impact
---------------
Unknown


Notification impact
-------------------
NeCTAR support people should be made aware of this tool and it should be
documented and incorporated into the support manual.


Implementation
==============

Assignee(s)
-----------
Primary assignee:
  Andy Botting
  andrew.botting@unimelb.edu.au


Work Items
----------
 1. Develop security.instance_info tool
 2. Investigate FreshDesk API
 3. Add lock/unlock tools


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

