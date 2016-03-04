:tocdepth: 1

.. note::

   In progress.

   This document is an overview of LSST DM's communication and documentation platforms, including: chat, ticketing, forums, technical notes and software documentation.

LSST Data Management uses a set of technical communication and documentation platforms to address our needs, with the SQuaRE team leading the management of these platforms.
Each platform addresses a specific niche of audience (DM, Project or community), synchronicity (real-time, asynchronous, or broadcast), and task (e.g., work ticketing, documenting designs and practices, and technical documentation for DM's software products).
This document outlines each DM communication platform, explains why and how it is used, differentiates how each platform is used in practice.
DM's communication platforms also exist within the greater context of LSST communications, and this document explores how platforms from these two LSST subsystems interface and coexist.
Finally, DM's communications platform strategy has evolved rapidly since Summer 2015, and this document reflects on the platform migrations that are underway.

.. _intro:

Introduction
============

.. table:: DM Communication Platforms and Intended Audiences

   +--------------------------------------+-------------------------+
   |                                      | Audience                |
   |                                      +----+---------+----------+
   | Platform                             | DM | Project | External |
   +======+===============================+====+=========+==========+
   | Chat | HipChat                       | Y  | ~       |          |
   |      +-------------------------------+----+---------+----------+
   |      | Slack (RFC-140)               | Y  | ~       | possible |
   +------+-------------------------------+----+---------+----------+
   | Community                            | Y  | Y       | Y        |
   +--------------------------------------+----+---------+----------+
   | Confluence                           | Y  | Y       |          |
   +--------------------------------------+----+---------+----------+
   | JIRA Tickets                         | Y  |         |          |
   +--------------------------------------+----+---------+----------+
   | GitHub Issues                        |    |         | Y        |
   +--------------------------------------+----+---------+----------+
   | GitHub Pull Requests                 | Y  |         | Y        |
   +----------------------+---------------+----+---------+----------+
   | Design Documentation | LSST the Docs | Y  |         | read     |
   |                      +---------------+----+---------+----------+
   |                      | Docushare     | Y  | Y       |          |
   +----------------------+---------------+----+---------+----------+
   | Technical Notes                      | Y  | ?       | read     |
   +--------------------------------------+----+---------+----------+
   | Developer Guide                      | Y  |         | read     |
   +--------------------------------------+----+---------+----------+
   | Software Docs                        | Y  |         | read     |
   +--------------------------------------+----+---------+----------+

.. _chat:

Chat (HipChat → Slack)
======================

DM makes extensive use of chat (through HipChat, by Atlassian) as a replacement to hallway and office conversations that would happen in a co-located organization.
Chat is currently considered to be an internal DM platform, through there is some participation from other subsystems.

Our Chat platform is divided into several rooms to scope the conversations.
For example, the 'Data Management' room hosts generic DM conversations, while the 'SQuaRE' room is primarily used to debug software build and infrastructure issues in real-time.
Rooms can also be created organically to host different working groups (for example, the 'Astropy Integration' room).
The advantage of chat over other platforms such as email is that the entire team can passively monitor conversations and stay generally aware of issues.

At the same time, we recognize that Chat can be a distraction, and not all team members are always available to participate in key discussions (that may potentially yield design decisions).
For this reason we are building a culture that redirects chat complex or important chat conversations to better venues:

- Data Management category in the Community forum for complex yet informal discussions
- The Request for Discussion (|rfd|) to schedule a time slot for a video conference-based discussion
- The Request for Comments (|rfc|) to formally propose and gain feedback on a proposal that has design or process ramifications.

We also use Chat for real time monitoring of software builds and tests and to automatically broadcast announcements of |rfc|\ s/|rfd|\ s.
This is a basic form of *ChatOps,* where infrastructure is controlled through a chat interface.
Companies like GitHub, for example, use ChatOps to control servers and react to operational events.
The advantage of doing this is that diverse and geographically distributed teams can collaborate in real-time.
DM and SQuaRE would like to expand our use of Chat into ChatOps, though there are no concrete plans at present.

.. _slack:

Motivation for the transition to Slack
--------------------------------------

There is no external participation because HipChat is tied to LSST's single sign-on.

.. _community:

Community forum and Mailing Lists
=================================

DM launched the Community forum (https://community.lsst.org) in August 2015 as a hub for asynchronous discussions within LSST teams, while also being open to participation from the community.
Community is hosted on the Discourse forum platform, which is modern, open source and being activity developed.
When Community was launched, it was intended to replace mailing lists as DM's platform for long-form asynchronous discussions and announcements to the community.
We see Community growing into a larger role by first servicing more LSST project subsystems, and ultimately becoming a place where astronomers from the community congregate to discuss the use of LSST data and software with project staff and amongst themselves.

Key qualities of Community are:

- *Native to the web.* This allows individual topics and posts to be linked to from documents and social media. Search engines such also Google also index the conversations on Community.
- *A delightful user experience.* Whereas JIRA and Confluence are powerful platforms, they lack Discourse's sensitivity to the difficulty of building a community on the web. Examples of Discourse's user experience affordances include markdown for formatting, support for linking topic threads together, effective search, and a granular notification system that can keep peripheral stakeholders aware of activity on the forum.
- *An open platform.* Anyone can create an account on Community and participate in discussions (although an account is not necessary to read content) without going through a gatekeeper. The Discourse platform protects itself from spam with a graduated system, although DM allows project members to short-cut the trust accrual algorithm by assigning project members to specific groups. And although Community, certain categories can be made viewable and/or writeable to only certain user groups.
- *Support for categories* so that different types of conversations can be segregated, while still making it easy to see all conversations happening on the forum.
- *Support for marking solutions.* Discourse was made by the same group that built StackOverflow, an immensely successful community-driven question-and-answer site. Although Discourse is more conversation-oriented, an 'Accepted answers' plugin allows for Q&A type categories where the ultimate solution to an issue posed by an original poster is clearly marked.

Categories and the organization of conversations
------------------------------------------------

Announcements
   For major announcements. Originally this category was intended to be equivalent to the ``dm-announce@lists.lsst.org`` mailing list to announce software releases. As the scope of Community has grown, the scope of Announcements has also grown to be more Project-holistic. This is an area where DM collaboration with LSST Communications would be beneficial.

Data Management
   Conversations within the DM team, open to the public.

   ``Data Management`` also includes several sub-categories:

   DM Notifications
      Brief broadcasts within the DM to alert team members of new features or changes to the software stack and infrastructure.

      DM Notifications also hosts our weekly `DM Activity Highlights series <https://community.lsst.org/tags/dm-highlights>`.
   
   DM Team
      A category visible only to members of the ``LSSTDM`` group (seldom used given our policy of open communication)

Support
   Question-and-answer category for users of LSST Software and Data to resolve issues (with DM Staff and other community members). Accepted solutions are marked to organically build a knowledge base for other users.

Simulations
   Conversations within the Simulations team, open to the public.

Camera
   Conversations within the Camera team, open to the public. This category is not actively used.

Cross-System Discussions
   This category hosts sub-categories for conversations between LSST subsystems to work on interfaces.

Project
   This category is only visible to LSST project members (``LSST`` group). It has been used to debrief conferences and offer frank discussions.

Planned and Possible Categories
-------------------------------

.. todo::

   'Ask LSST' category

Broadcasting to mailing lists (Community Mailbot)
-------------------------------------------------

Community was intended to replace DM's mailing lists, and it has: conversations no longer occur on the ``dm-devel`` and ``dm-user`` mailing lists.
However, we also recognized that these mailing lists have value in reliably reaching a large audience.

Project group management
------------------------

As discussed, we assign project staff to 'groups' within Community that offer higher Discourse trust levels and access to private categories.
Currently this assignment is managed manually by SQuaRE and DM T/CAMs.
As Community's use grows across the project, this may arrangement will scale poorly.
This would ultimately be solved if the Contacts DB, or its equivalent, could be accessed by a RESTful API.

.. _confluence:

Confluence Wiki
===============

DM uses Confluence wikis, although their role is being diminished with the introduction of |clo| and the |ltd| publishing paradigm (including Technical Notes, the new Developer Guide and software documentation).

Acceptable uses for the Wikis include:

- Meeting notes, especially with action-item assignment (although there is an emerging preference to summarize conferences and |rfd| meetings on |clo|.
- Ad hoc collaboration, such as planning (although again, many groups will use |clo| for these activities).

Note that our migration of content from Confluence is still underway.
The LSST Software User Guide will be replaced by software documentation published through |ltd|.
Note that the DM Developer Guide formerly published on Confluence has been officially migrated to the new DM Developer Guide at https://developer.lsst.io.
DM also has a dormant Trac ticketing system and wiki, and we intend to migrate relevant content from the Trac wiki into the software documentation or developer guide as appropriate.

.. _tickets:

Work Ticketing
==============

JIRA Tickets
------------

DM uses JIRA to report and track work.
Thus it is a medium that bridges DM to management and accounting.
See the Developer Guide for a complete overview of how tickets are used to report work, and the relationships between work.

Pull Requests
-------------

During a code review, conversations relating to a work ticket shift to GitHub's pull request platform, as described in the Developer Guide.
TODO: link.
We do this because GitHub Pull Requests allow conversations that are tightly coupled to the code.


GitHub Issues and Community-driven bug reporting
------------------------------------------------

We do *not* use GitHub issues within DM since they would conflict with the JIRA system upon which our accounting is built.
However, we have left GitHub issues available since they are a part of the fabric of the open source software community---without GitHub issues, an external user would likely not make the effort to find out how to report a bug.
Our current policy is to to triage these GitHub issues into JIRA tickets.
See also RFC-147 'Best practices to report an issue with DM system' for discussion surrounding how to support bug reports from the community.

.. _RFC:

Request for Comments (RFC)
==========================

The RFC process is a core part of DM's decision making process.
We use RFCs to allow anyone in the team to make proposals that have ramifications across DM while also giving all team members an opportunity to comment.
RFCs may be issued for changes in third-party dependencies, changes to designs and interfaces within the DM software, or changes to our developer processes.
The RFC platform is hosted on JIRA so that decision status and linkage to work tickets can be tracked.

See the Developer Guide for more information.

.. _RFD:

Request for Discussion (RFD)
============================

Although DM has regular meetings for specific individuals, there is often a need to host *ad hoc* video conference meetings to discuss an issue more expeditiously than on Community, while still ensuring the availability of key team members.
For this need we use the Request for Discussion process (RFD).
RFDs meetings are held in a standing weekly time slot, with a JIRA project being used to reserve that time slot.

See the Developer Guide for more information.

.. _LTD:

LSST the Docs Publishing Platform
=================================

Domains: lsst.org/codes/io
--------------------------

Change-Controlled Design Documents
==================================

Technical Notes
===============

Developer Guide
===============

Software Documentation
======================

Hello

.. |clo| replace:: Community_

.. |rfc| replace:: RFC_

.. |rfd| replace:: RFD_

.. |ltd| replace:: LTD_

