:tocdepth: 1

.. note::

   ***DRAFT***

   This document outlines each DM communication platform (including
   chat, ticketing, forums, technical notes and software
   documentation) and explains what need it fulfils in DM. It also
   sketches out ways in which these platforms could support future
   project-wide communication strategies under various policies. 

LSST Data Management uses a number of technical communication and
documentation platforms to address our needs, with the SQuaRE team
leading the management (and development, when necessary) of these
platforms.  Each platform addresses a specific niche of audience (DM,
Project or our science community), synchronicity (real-time,
asynchronous, or broadcast), and task (e.g., work ticketing,
documenting designs, manuals, etc).

In this document we outline SQuaRE's communication support services
and speculate now they could be used to support a project-wide
communication strategy. Note, however, that while we have chosen some
of these platforms for their ability to support a wider outreach into
the project and the community, they can all be restricted to their
current audiences if project policy demands it.

DM's communications platform strategy has evolved rapidly since Summer
2015 with the appointment of our Documentation Engineer, so this
document also takes the opportunity to foreshadow platform migrations
that are underway.

How are tools selected
========================

With all communication tools, there is always a balance of providing
users a diversity of tools that they want to use and consolidating
tools so that information does not fragment and to boost the network
effect. We have found that the parameter space of task, synchronicty
and audience do require multiple tools, but we favour only having one
supported tool for each locus in that space.

How do we select that tool? We weigh in a number of factors:

- Ease of development with the tool (can we build the services we need
  around this tool)

- Quailty of supprt for the tool (rate of bugfixes, new features etc)

- User preference within the project (polling, discussions)

- Prevailing usage outside the project (do our collaborators or shared
  staff use this tool in their other projects?)

- Cost (after seeking open source or non-profit discounting)

- Cost/Benefit of effort required for migration, when a previous tool
  has already been used in that space. 

.. _overview:

Overview
========

This is an overview of our current understanding of how the various
tools and platforms cover the audience space. 

.. table:: DM Communication Platforms and Intended Audiences

   +--------------------------------------+-------------------------+
   |                                      | Audience                |
   |                                      +----+---------+----------+
   | Platform                             | DM | Project | External |
   +======+===============================+====+=========+==========+
   | Chat | HipChat                       | Y  | ~       | N        |
   |      +-------------------------------+----+---------+----------+
   |      | Slack (RFC-140)               | Y  | ~       | possible |
   +------+-------------------------------+----+---------+----------+
   | Community                            | Y  | Y       | Y        |
   +--------------------------------------+----+---------+----------+
   | Confluence                           | Y  | Y       | read     |
   +--------------------------------------+----+---------+----------+
   | JIRA Tickets                         | Y  | Y       | read     |
   +--------------------------------------+----+---------+----------+
   | GitHub Issues                        | N  |  N      | Y        |
   +--------------------------------------+----+---------+----------+
   | GitHub Pull Requests                 | Y  | Y       | Y        |
   +----------------------+---------------+----+---------+----------+
   | Design Documentation | LSST the Docs | Y  | read    | read     |
   |                      +---------------+----+---------+----------+
   |                      | Docushare     | Y  | Y       | ?        |
   +----------------------+---------------+----+---------+----------+
   | Technical Notes                      | Y  | ?       | read     |
   +--------------------------------------+----+---------+----------+
   | Developer Guide                      | Y  | read    | read     |
   +--------------------------------------+----+---------+----------+
   | Software Docs                        | Y  | read    | read     |
   +--------------------------------------+----+---------+----------+
   | Documentation Index                  | Y  | read    | read     |
   +--------------------------------------+----+---------+----------+

.. _chat:

Chat (HipChat → Slack)
======================

DM makes extensive use of chat (currently the HipChat service by
Atlassian) as a replacement to hallway and office conversations that
would happen naturally in a co-located organization, and locally as a
way to seek near-synchronous help without disturbing someone who is
busy.  Hipchat is currently considered to be an internal DM platform,
through there is some participation from other subsystems.

Our Chat platform is divided into several rooms to scope the
conversations. For example, the 'Data Management' room hosts generic
DM conversations, while the 'SQuaRE' room is primarily used to debug
software build and developer services issues in real-time (and is the
most popular room as a result). Rooms can also be created organically
to host different working groups (for example, the 'Astropy
Integration' room).

Chat systems are rightly considered invaluable for software
development teams. They are the most efficient way of troubleshooting
a problem, and by their informality, provide a vital social lubricant
and culture propagation medium in what is a dispersed
multi-institutional team.

The advantage of chat over other platforms such as email is that the
entire team can passively monitor conversations and stay generally
aware of issues without feeling like they have to read every message,
tuning in and out as they would to a discussion between two teammates
in the hallway.

At the same time, we recognize that Chat can be a distraction, and not
all team members are always available to participate in key
discussions (that may potentially yield design decisions).

For this reason we are building a culture that redirects chat complex
or important chat conversations to better venues:

- Data Management category in the Community forum for
  complex yet informal discussions

- The Request for Discussion (|rfd|) to schedule a time slot for a
  video conference-based discussion

- The Request for Comments (|rfc|) to formally propose and gain
  feedback on a proposal that has design or process ramifications.

- Problems reported on Chat are often fixed in real time. When it is
  not possible to do so, a work ticket is filed.

It is important to note that while Chat is a stunningly effective
platform for mentoring and in-team troubleshooting, it does not scale
as a support medium in many circumstances, particularly it lacks the
StackOverflow effect: you can't easily come to find an answer, realise
that someone has already asked it and gotten a pertinent answer, and
leave satisfied without even having had to disturb a DM developer.

However we do foresee that there will be members of the scientific
community who will wish to engage with DM as developers rather than
passive users. So our recommendation is to adopt platforms that make
it easy and cheap to an external users to the chat system, while at
the same time treating the chat system for those users as a last
resort.

ChatOps
-------

We also use Chat for real time monitoring of software builds and tests
and to automatically broadcast announcements of |rfc|\
s/|rfd|\ s. This is a basic form of *ChatOps,* where infrastructure is
controlled through a chat interface.  Companies like GitHub, for
example, use ChatOps to control servers and react to operational
events.  The advantage of doing this is that diverse and
geographically distributed teams can collaborate in real-time.  DM and
SQuaRE would like to expand our use of Chat into ChatOps, likely with
`StackStorm and Hubot
<http://stackstorm.com/2015/06/08/enhanced-chatops-from-stackstorm/>`_,
though this work is not yet planned.

ChatOps services always require some level of development for bots
that interface in-house services to the chat system. This is why the
standard and level of maturity of APIs and available off-the-shelf
integrations is of high interest to SQuaRE, who is the most likely
source of effort for this development. 

.. _slack:

Motivation for the transition to Slack
--------------------------------------

Due to the aforementioned considerations as well as expressed user
preference and prevailing usage, SQuaRE is proposing that DM move its
Chat implementation from Hipchat to Slack. The proposal (which
received a lot of enthusiasm and scant opposition) can be found at the
relevant RFC - see `RFC-140
<https://jira.lsstcorp.org/browse/RFC-140>`_.

.. _community:

Community forum and Mailing Lists
=================================

DM launched the Community forum (https://community.lsst.org or c.l.o
for short in DM parlance) in August 2015 as a hub for asynchronous
discussions within LSST teams, while also being open to participation
from the community.

Community is hosted on the Discourse web forum platform, which is
modern, open source and being activity developed. The adoption of the
Discourse platform was proposed in `RFC-85
<https://jira.lsstcorp.org/browse/RFC-85>`_

When Community was launched, it was intended to replace mailing lists
as DM's platform for long-form asynchronous discussions and
announcements to the community. Community was also a response to the
desire of the senior DM scientists to reach out to important
scientific collaborations with which DM has obvious common topics of
interest (eg. the DESC collaboration).

We see Community growing into a larger role by first servicing more
LSST project subsystems, and ultimately becoming a place where
astronomers from the community congregate to discuss the use of LSST
data and software with project staff and amongst themselves.

Key qualities of Community as an asynchronous forum implementation
are:

- *Native to the web.* This allows individual topics and posts to be
  linked to from documents and social media. Search engines such also
  Google also index the conversations on Community.


- *A delightful user experience.* Whereas JIRA and Confluence are
  powerful platforms, they lack Discourse's sensitivity to the
  difficulty of building a community on the web. Examples of
  Discourse's user experience affordances include markdown for
  formatting, support for linking topic threads together, effective
  search, and a granular notification system that can keep peripheral
  stakeholders aware of activity on the forum.

- *An open platform.* Anyone can create an account on Community and
  participate in discussions (although an account is not necessary to
  read content) without going through a gatekeeper. The Discourse
  platform protects itself from spam with a graduated system, although
  DM allows project members to short-cut the trust accrual algorithm
  by assigning project members to specific groups. And although
  Community, certain categories can be made viewable and/or writeable
  to only certain user groups.

- *Support for categories* so that different types of conversations
  can be segregated, while still making it easy to see all
  conversations happening on the forum.

- *Support for marking solutions.* Discourse was made by the same
   group that built StackOverflow, an immensely successful
   community-driven question-and-answer site. Although Discourse is
   more conversation-oriented, an 'Accepted answers' plugin allows for
   Q&A type categories where the ultimate solution to an issue posed
   by an original poster is clearly marked.

Categories and the organization of conversations
------------------------------------------------

`Announcements <https://community.lsst.org/c/announce>`_
   For major announcements. Originally this category was intended to be equivalent to the ``dm-announce@lists.lsst.org`` mailing list to announce software releases. As the scope of Community has grown, the scope of Announcements has also grown to be more Project-holistic. This is an area where DM collaboration with LSST Communications would be beneficial.

`Data Management <https://community.lsst.org/c/dm>`_
   Conversations within the DM team, open to the public.

   ``Data Management`` also includes several sub-categories:

   `DM Notifications <https://community.lsst.org/c/dm/dm-notifications>`_
      Brief broadcasts within the DM to alert team members of new features or changes to the software stack and infrastructure.

      DM Notifications also hosts our weekly `DM Activity Highlights series <https://community.lsst.org/tags/dm-highlights>`_ series that summarizes DM activity at very technical level.
   
   DM Team
      A category visible only to members of the ``LSSTDM`` group (seldom used given our policy of open communication)

`Support <https://community.lsst.org/c/qa>`_
   Question-and-answer category for users of LSST Software and Data to resolve issues (with DM Staff and other community members). Accepted solutions are marked to organically build a knowledge base for other users.

`Simulations <https://community.lsst.org/c/sims>`_
   Conversations within the Simulations team, open to the public.

`Camera <https://community.lsst.org/c/camera>`_
   Conversations within the Camera team, open to the public. This category is not actively used.

`Cross-System Discussions <https://community.lsst.org/c/systems>`_
   This category hosts sub-categories for conversations between LSST subsystems to work on interfaces.

LSST Project
   This category is only visible to LSST project members (``LSST`` group). It has been used to debrief conferences and offer frank discussions.

Planned and Possible Categories
-------------------------------

Ask LSST
   This category, sponsored by the Project Science Team, will provide the science collaborations, and the astronomy community in general, a venue to ask questions about how LSST will operate and serve their science goals and receive official answers from the project.
   Such a Q&A venue will offer an appealing alternative to getting answers through our technical documentation or through one-on-one conversations that don't scale.
   Technically, this category will operate similarly to the Support category.

Broadcasting to mailing lists (Community Mailbot)
-------------------------------------------------

Community was intended to replace DM's mailing lists, and it has:
conversations no longer occur on the ``dm-devel`` and ``dm-user``
mailing lists.  However, we also recognized that these mailing lists
have value in reliably reaching an audience which prefers e-mail.
Thus we built the `Community Mailbot
<https://github.com/lsst-sqre/community_mailbot>`_ to forward new
topics in select categories to the existing DM mailing lists.  The
forwarded email contains the text of the original topic post along
with an unambiguous button inviting readers to participate in the
discussion on https://community.lsst.org. Echoing forum activity to an
e-mail gateway has been common practice since the early days of the Internet. 

SQuaRE uses Mandrill, by Mailchimp, to send these emails.

Project group management
------------------------

As discussed, we assign project staff to 'groups' within Community
that offer higher Discourse trust levels and access to private
categories. Currently this assignment is managed manually by SQuaRE
and DM T/CAMs. As Community's use grows across the project, this may
arrangement will scale poorly.

SQuaRE is highly desirous of interfacing to the LSST Contacts via a
standard programmatic API, which is not possible with the current
Contacts DB implementation in order to ensure that group access in
Community and other SQuaRE services is kept in sync with the Project's
master list. 

.. _confluence:

Confluence Wiki
===============

DM uses Confluence wikis, although their role is being diminished with
the introduction of |clo| and the |ltd| publishing paradigm (including
Technical Notes, the new Developer Guide and software documentation).

SQuaRE dissuades software documentation in wikis, since it cannot be
managed with standard software release tools, cannot be tested by our
continuous integration harness, is "out of sight out of mind" for the
developers, and is hard to maintain. We are in the process of
migrating all software documentation from Confluence to other, better
harnesses.

The DM Developer Guide formerly published on Confluence has
been officially migrated to the new DM Developer Guide at
https://developer.lsst.io.

The LSST Software User Guide will be replaced by software
documentation published through |ltd|.

In our view, acceptable uses for the Wikis include:

- Meeting notes, especially with action-item assignment (although
  there is an emerging preference to summarize conferences and |rfd|
  meetings on |clo|.

- Ad hoc collaboration, such as planning (although again, many groups
  will use |clo| for these activities).

Unfortunately, DM never completed its migration to Confluence from its
previous wiki, TRAC. This migration is a background activity across DM
that occasionally sees fits of progress.

.. _tickets:

Work Ticketing
==============

JIRA Tickets
------------

DM uses JIRA to plan, track and report on work. Thus it is a medium
that bridges DM developers to DM technical managers to DM management
to Project auditing.  See the Developer Guide for a complete overview
of how tickets are used to report work, and the relationships between
work.

There is no foreseeable need to consider alternatives to JIRA during
construction or beyond.


Pull Requests
-------------

During a code review, conversations relating to a work ticket shift to
GitHub's pull request platform, as described in the `Developer Guide
<http://developer.lsst.io/en/latest/processes/workflow.html#code-review-discussion>`_.

We do this because GitHub Pull Requests allow conversations that are
tightly coupled to the code. Also, Pull Requests is how a non-LSST
developer would send us code contributions anyway, so for a project
that aspires to be openly developed, they are inevitable. 


GitHub Issues and Community-driven bug reporting
------------------------------------------------

By policy we do *not* use GitHub issues within DM since they would
conflict with the JIRA system upon which our project management system
is built.

However, we have left GitHub issues available since they are a part of
the fabric of the open source software community---without GitHub
issues, an external user would likely not make the effort to find out
how to report a bug.

Our current policy is to to triage these GitHub issues into JIRA tickets.

See also `RFC-147 'Best practices to report an issue with DM system'
<https://jira.lsstcorp.org/browse/RFC-147>`_ for discussion
surrounding how to support bug reports from the community.

.. _RFC:

Request for Comments (RFC)
==========================

The RFC process is a core part of DM's decision making process and a
vital foundation of the team's culture.  We use RFCs to allow anyone
in the team to propose work that has ramifications across DM while
also giving all team members an opportunity to comment if they are
affected.  RFCs may be issued for changes in third-party dependencies,
changes to designs and interfaces within the DM software, or changes
to our developer processes.  The RFC platform is hosted on JIRA so
that decision status and linkage to work tickets can be tracked.

See the `Developer Guide <http://developer.lsst.io/en/latest/processes/decision_process.html#request-for-comments-rfc-process>`_ for more information.

.. _RFD:

Request for Discussion (RFD)
============================

Although DM has regular meetings for specific individuals, there is often a need to host *ad hoc* video conference meetings to discuss an issue more expeditiously than on Community, while still ensuring the availability of key team members.
For this need we use the Request for Discussion process (RFD).
RFDs meetings are held in a standing weekly time slot, with a JIRA project being used to reserve that time slot.

See the `Developer Guide <http://developer.lsst.io/en/latest/processes/decision_process.html#request-for-discussion-rfd-process>`_ for more information.

.. _LTD:

LSST the Docs Publishing Platform
=================================

*LSST the Docs* is a publishing platform and ecosystem that underpins
DM's various flavors of technical documentation: change-controlled
documents, technical notes, the Developer Guide, and software/data
documentation.  The platform is intended to give our development team
a set of common tools to write documents in a consistent style, while
using best practices to deploy (publish) documentation.  This allows
our development team to communicate effectively and efficiently, and
benefit from a core technical base built by the DM team and the open
source community.

*LSST the Docs* can be summarized by a stack of technologies:
reStructuredText, GitHub, Sphinx, and the *LSST the Docs* continuous
delivery service. The name *LSST the Docs" is in reference to the
highly popular documentation service *Read the Docs* - we explain
below why we could not just us that service off the shelf (which is
normally our preference).


ReStructured Text
-----------------

ReStructuredText is a plain-text markup language, similar to Markdown and LaTeX.
We specifically chose reStructuredText because it *the* standard markup language in the Python community (in which DM participates) and because it is explicitly designed to be user-extensible.
These extensions come from both the open source community (including rich tools for writing Math and documenting application programming interfaces) and DM itself (such as a short-hand for referencing other DM documents, or a system for citing astronomical literature, among other possibilities).

GitHub collaboration
--------------------

Since they are simple plain text files, reStructuredText documents are managed GitHub and benefit from DM's regular `development workflow <http://developer.lsst.io/en/latest/processes/workflow.html>`_ (including ticketing and reviews).
This collaboration model is not possible with Confluence wiki pages or word processor files.

Sphinx and web-native documentation
-----------------------------------

By writing in reStructuredText, we also benefit from the `Sphinx
<http://www.sphinx-doc.org/en/stable/>`_ tool for building
documentation websites.  Natively publishing documents to the web, as
opposed to static PDF files, is fundamental to successful, modern
documentation.

- Information is discoverable through search and hyperlinks (including
  deep links to specific sections). There is no dissonance from
  switching from searching for a document on the web and then reading
  reading it elsewhere in a PDF viewer.

- Web-based documentation naturally builds an organic network of
  internal links that improve content wayfinding.

- Websites are rendered equally well on small and large screens,
  thanks to responsive design practices.

- Websites can include interactive elements, such as dynamic figures or Python notebooks to test code.

- Websites can be updated continuously.

In *LSST the Docs*, PDF is treated as an archival format, while the
web site is the reader-facing product.

Continuous documentation delivery with LSST the Docs
----------------------------------------------------

Continuous delivery describes a process where documentation is ready
for publication whenever content is changed, thanks to a highly
automated pipeline.  When revised documentation content is pushed to
GitHub, it is built, tested, and made available in a staging
environment to the team.  When a team choses (using my merging changes
to the GitHub master), the new content to automatically published.

`Read the Docs <https://readthedocs.org/>`_ is popular continuous
delivery service for Sphinx documentation, and we have used it widely
for technical notes and design documents.  However, Read the Docs
limits our ability to provision new documentation projects through an
well-defined API, and more fundamentally, limits our ability to
control the build environment for documentation.  LSST software
documentation requires that the software itself be built, which
demands a customized build environment.  To solve these issues, we
have built a service described in `SQR-006: Documentation Deployment
Service for LSST's Eups-based Software <http://sqr-006.lsst.io/>`_.

Domains: lsst.org/codes/io
--------------------------

For the convenience of our users, we generate a unique domain-name for
each published document, eg. the developer guide can be found at
developer.lsst.io. The .io top-level domain is in common use with tech
sector organisations and using a documentation-specific domain that is
managed automatically keeps any accidents away from the main,
human-curated website. Unlike the lsst.org website, lsst.io is not a
point of entry; everything hosted under it will be referenced in the
documentation index.

For similar reasons, SQuaRE cloud-based services aimed at DM
developers are hosted under the domain lsst.codes. There is no
public-facing material in the lsst.codes services.


Change-Controlled Design Documents
==================================

LSST stores deposits copies of all change-controlled documents in
Docushare. Irrespective of the source and development flow of our
documents (be they RST or LaTeX or Word), we continue to do
so. However our users are unhappy with the Docushare user experience,
hence why we do not depend it to be the sole index of our documentation.

While we support authors who wish to write documents in the LSST the Doc platform, 

Technical Notes
===============

Technical notes provide a very quick, very lightweight way of writing
a short document in the editor of your choice and publishing it.

See `SQR-000: The LSST DM Technical Note Publishing Platform <http://sqr-000.lsst.io/en/master/>`_ for more information.

Developer Guide
===============

The DM developer guide is a key document for DM developers as it
encapsulates our development policies and practices.

https://developer.lsst.io


Software Documentation
======================

[do we need to talk about this?]

A Documentation Index
=====================

[This section describes future work]

LSST's documentation, as described above, consists of a constellation
of design documents, technical notes, and documentation sites for
specific software projects and data releases.

In addition, DM also produces presentations, conference proceedings
and published academic articles.

For these to documents to be effective, they need to be discoverable.

We intend to solve the documentation discovery problem with a highly
useable, well publicized, central documentation landing page.

- Dynamically updated when new documents are published by LSST the Docs, or made available in ADS/Zenodo.
- Full-text search
- Browse by content type, and also by subject
- Curated collections of documents (e.g top documentation for scientists).
- Awareness of documentation versions; ability to choose a version of the document
- Landing page should be curated to get readers to top documents, such as the Science Pipelines documentation.

.. |clo| replace:: Community_

.. |rfc| replace:: RFC_

.. |rfd| replace:: RFD_

.. |ltd| replace:: LTD_

