:tocdepth: 1

.. note::

   **DRAFT**

   This document outlines each DM communication platform (including
   chat, ticketing, forums, technical notes and software
   documentation) and explains what need it fulfils in DM.  It also
   sketches out ways in which these platforms could support future
   project-wide communication strategies under various policies.

LSST Data Management uses a number of technical communication and
documentation platforms to address our needs, with the SQuaRE team
leading the management (and development, when necessary) of these
platforms.  Each platform addresses a specific niche of audience (DM,
Project or our science community), synchronicity (real-time,
asynchronous, or broadcast), and task (e.g., work ticketing,
documenting designs, manuals).

In this document we outline SQuaRE's communication support services
and speculate now they could be used to support a project-wide
communication strategy.  Note, however, that while we have chosen some
of these platforms for their ability to support a wider outreach into
the project and the community, they can all be restricted to their
current audiences if project policy demands it.

DM's communications platform strategy has evolved rapidly since Summer
2015 with the appointment of our Documentation Engineer, so this
document also takes the opportunity to foreshadow platform migrations
that are underway.

How tools are selected
======================

With all communication tools, there is always a balance of providing
users a diversity of tools that they want to use and consolidating
tools so that information does not fragment.  We have found that the
parameter space of task, synchronicity and audience do require
multiple tools, but we favor only having one supported tool for each
locus in that space.

How do we select that tool? We weigh in a number of factors:

- Ease of development with the tool (*Can we build the services we
  need around this tool?*).

- Quality of support for the tool (rate of bug fixes, new features,
  for example).

- User preference within the project (polling, discussions).

- Prevailing usage outside the project (do our collaborators or shared
  staff use this tool in their other projects?).

- Cost (after seeking open source or non-profit discounting).

- Cost/Benefit of effort required for migration, when a previous tool
  has already been used in that space.

.. _overview:

Overview
========

This table is a summary of the DM communication platforms, along with
our current understanding of how the various tools and platforms cover
the audience space.

.. _platforms:

.. table:: DM Communication Platforms and Intended Audiences

   +-------------------------------+----------------------------+
   |                               | Audience                   |
   |                               +-------+---------+----------+
   | Platform                      | DM    | Project | External |
   +======+========================+=======+=========+==========+
   | Chat | HipChat                | Y     | ~       | N        |
   |      +------------------------+-------+---------+----------+
   |      | Slack (RFC-140)        | Y     | ~       | possible |
   +------+------------------------+-------+---------+----------+
   | Community                     | Y     | Y       | Y        |
   +-------------------------------+-------+---------+----------+
   | Confluence                    | Y     | Y       | read     |
   +-------------------------------+-------+---------+----------+
   | JIRA Tickets                  | Y     | Y       | read     |
   +-------------------------------+-------+---------+----------+
   | GitHub Issues                 | N     | N       | Y        |
   +-------------------------------+-------+---------+----------+
   | GitHub Pull Requests          | Y     | Y       | Y        |
   +-------------------------------+-------+---------+----------+
   | Request for Comments (RFC)    | Y     | ~       | read     |
   +---------------+---------------+-------+---------+----------+
   | Design        | LSST the Docs | Y     | read    | read     |
   | Documentation +---------------+-------+---------+----------+
   |               | Docushare     | Y     | Y       | ?        |
   +---------------+---------------+-------+---------+----------+
   | Technical Notes               | Y     | ?       | read     |
   +-------------------------------+-------+---------+----------+
   | Developer Guide               | Y     | read    | read     |
   +-------------------------------+-------+---------+----------+
   | Software Docs                 | Y     | read    | read     |
   +-------------------------------+-------+---------+----------+
   | Documentation Index           | read  | read    | read     |
   +-------------------------------+-------+---------+----------+
   | NASA/SAO ADS                  | ~     | ~       | read     |
   +-------------------------------+-------+---------+----------+
   | Zenodo                        | write | ~       | ~        |
   +-------------------------------+-------+---------+----------+
   | Docushare                     | write | Y       | ~        |
   +-------------------------------+-------+---------+----------+

On a moment-by-moment basis, DM team members use Chat, JIRA tickets
and GitHub Pull Request threads to collaborate.  More asynchronously,
we use the Community forum to have long-form conversations and
broadcast announcements, use the Confluence wiki for posting ad-hoc
information, and use Request for Comments (RFC) to make decisions.
Finally, we use the LSST the Docs platform to document designs (Design
Documents) and processes (Developer Guides), report on work and
experiments (Technical Notes), and document our software for both
internal and external users.  Document indices, such as the DM
Documenation Index and the NASA/SAO Astrophysics Data System ensure
that DM communications are discoverable.  Finally, we use archives
such as Zenodo and Docushare, though these are not intended to be
user-facing services.

Communication and documentation as a shared DM responsibility
-------------------------------------------------------------

There are no communication gatekeepers within Data Management.  Every
team member can participate in, and is responsible for, communicating
and documenting DM work.  We use a regular review process to vet
documentation, either with peers or a Technical Control Team for
controlled documents.

Traditionally, many organization create participation barriers to
their communication platforms through the complexity of systems that
publish to the web or elsewhere.  As the maintainer and developer of
DM's communication platforms, SQuaRE is committed to making our
platforms accessible and easy to use through automation.  For example,
our aim is to allow a team member to publish a new technical note to
the web immediately, or update software documentation without any
effort beyond writing the content itself.

Making information accessible outside Data Management
-----------------------------------------------------

As an open source software organization, Data Management is culturally
aligned with making information openly available beyond the team.
This is why the community is granted at least read access to nearly
all DM communication platforms listed in :numref:`platforms`.  While
all of these artifacts (JIRA tickets, technical notes, Zenodo
depositions and so on) make sense in their authoring context, we
recognize that the external community needs a simpler view into LSST
Data Management information.  Our strategy is to treat only two DM
platforms as entry points; all other information should be
discoverable from these platforms.

The first entry point is the Community forum.  Questions on the forum
will be answered with links to documents deeper in the DM information
hierarchy, such as pages in software documentation, technical notes,
and so forth.  The community forum, in essence becomes an interactive
search engine into LSST's documentation, in addition to being a space
to discover gaps in our documentation and draft new content.  :ref:`We
specifically discusss the Community forum later in this technical
note. <community>`.

(Also, since DM's information is accessible on the open web---without
login walls---we also organically benefit from web search and social
media entry points.  DM's documentation, itself, is also highly
self-referential.)

The second entry point is a *planned* Data Management Documentation
Index web site.  Where the Community forum is highly contextual and
serendipitous, the Documentation Index support systematic and
comprehensive documentation discovery.  We will allow readers to
browse DM documents by type (software documentation, design document,
technical note, presentation, paper, source code), subject area, as
well as full-text search.  The Documentation Index will also have
curated categories to highlight new and key information for user
groups.  The Documentation Index will kept up-to-date by hooking into
the LSST the Docs, Zenodo, and ADS platforms that host or archive DM's
artifacts.  :ref:`We discuss the Documentation Index later in this
technical note. <doc-index>`.

Again, the advantage of this architecture is that DM only needs to
promote two URLs to the community to effectively market our entire
information portfolio.

.. _chat:

Chat (HipChat → Slack)
======================

DM makes extensive use of chat (currently the HipChat service by
Atlassian) as a replacement to hallway and office conversations that
would happen naturally in a co-located organization, and locally as a
way to seek near-synchronous help without disturbing someone who is
busy.  HipChat is currently considered to be an internal DM platform,
through there is some participation from other subsystems.

Our Chat platform is divided into several rooms to scope the
conversations.  For example, the 'Data Management' room hosts generic
DM conversations, while the 'SQuaRE' room is primarily used to debug
software build and developer services issues in real-time (and is the
most popular room as a result).  Rooms can also be created organically
to host different working groups (for example, the 'Astropy
Integration' room).

Chat systems are rightly considered invaluable for software
development teams.  They are the most efficient way of troubleshooting
a problem, and by their informality, provide a vital social lubricant
and culture propagation medium in what is a dispersed
multi-institutional team.  The advantage of chat over other platforms
such as email is that the entire team can passively monitor
conversations and stay generally aware of issues without feeling like
they have to read every message, tuning in and out as they would to a
discussion between two teammates in the hallway.

At the same time, we recognize that Chat can be a distraction, and not
all team members are always available to participate in key
discussions (that may potentially yield design decisions).  For this
reason we are building a culture that redirects chat complex or
important chat conversations to better venues:

- Data Management category in the Community forum for complex yet
  informal discussions

- The Request for Discussion (|rfd|) to schedule a time slot for a
  video conference-based discussion

- The Request for Comments (|rfc|) to formally propose and gain
  feedback on a proposal that has design or process ramifications.

- Problems reported on Chat are often fixed in real time. When it is
  not possible to do so, a work ticket is filed.

It is important to note that while Chat is a stunningly effective
platform for mentoring and in-team troubleshooting, it does not scale
as a support medium in many circumstances, particularly it lacks the
StackOverflow effect: you can't easily come to find an answer, realize
that someone has already asked it and gotten a pertinent answer, and
leave satisfied without even having had to disturb a DM developer.

However we do foresee that there will be members of the scientific
community who will wish to engage with DM as developers rather than
passive users.  So our recommendation is to adopt platforms that make
it easy and cheap to an external users to the chat system, while at
the same time treating the chat system for those users as a last
resort.

ChatOps
-------

We also use Chat for real time monitoring of software builds and tests
and to automatically broadcast announcements of |rfc|\ s/|rfd|\ s.
This is a basic form of *ChatOps,* where infrastructure is controlled
through a chat interface.  Companies like GitHub, for example, use
ChatOps to control servers and react to operational events.  The
advantage of doing this is that diverse and geographically distributed
teams can collaborate in real-time.  DM and SQuaRE would like to
expand our use of Chat into ChatOps, likely with `StackStorm and Hubot
<http://stackstorm.com/2015/06/08/enhanced-chatops-from-stackstorm/>`_,
though this work is not yet planned.

ChatOps services always require some level of development for bots
that interface in-house services to the chat system.  This is why the
standard and level of maturity of APIs and available off-the-shelf
integrations is of high interest to SQuaRE, who is the most likely
source of effort for this development.

.. _slack:

Motivation for the transition to Slack
--------------------------------------

Due to the aforementioned considerations as well as expressed user
preference and prevailing usage, SQuaRE is proposing that DM move its
Chat implementation from HipChat to Slack.  The proposal (which
received a lot of enthusiasm and scant opposition) can be found at the
relevant RFC - see `RFC-140
<https://jira.lsstcorp.org/browse/RFC-140>`_.

.. _community:

Community forum and Mailing Lists
=================================

DM launched the Community forum (https://community.lsst.org or *c.l.o*
for short in DM parlance) in August 2015 as a hub for asynchronous
discussions within LSST teams, while also being open to participation
from the community.

Community is hosted on the Discourse web forum platform, which is
modern, open source and being activity developed.  The adoption of the
Discourse platform was proposed in `RFC-85
<https://jira.lsstcorp.org/browse/RFC-85>`_.

When Community was launched, it was intended to replace mailing lists
as DM's platform for long-form asynchronous discussions and
announcements to the community.  Community was also a response to the
desire of the senior DM scientists to reach out to important
scientific collaborations with which DM has obvious common topics of
interest (e.g., the DESC collaboration).

We see Community growing into a larger role by first servicing more
LSST project subsystems, and ultimately becoming a place where
astronomers from the community congregate to discuss the use of LSST
data and software with project staff and amongst themselves.

Key qualities of Community as an asynchronous forum implementation
are:

- *Native to the web.* This allows individual topics and posts to be
  linked to from documents and social media.  Search engines such also
  Google also index the conversations on Community.


- *A delightful user experience.* Whereas JIRA and Confluence are
  powerful platforms, they lack Discourse's sensitivity to the
  difficulty of building a community on the web.  Examples of
  Discourse's user experience affordances include markdown for
  formatting, support for linking topic threads together, effective
  search, and a granular notification system that can keep peripheral
  stakeholders aware of activity on the forum.

- *An open platform.* Anyone can create an account on Community and
  participate in discussions (although an account is not necessary to
  read content) without going through a gatekeeper.  The Discourse
  platform protects itself from spam with a graduated system, although
  DM allows project members to short-cut the trust accrual algorithm
  by assigning project members to specific groups.  And although
  Community is not meant to be a highly secure and private platform,
  certain categories can be made viewable and/or writeable to only
  certain user groups.

- *Support for categories* so that different types of conversations
  can be segregated, while still making it easy to see all
  conversations happening on the forum.

- *Support for marking solutions.* Discourse was made by the same
  group that built StackOverflow, an immensely successful
  community-driven question-and-answer site.  Although Discourse is
  more conversation-oriented, an 'Accepted answers' plugin allows for
  Q&A type categories where the ultimate solution to an issue posed by
  an original poster is clearly marked.

Categories and the organization of conversations
------------------------------------------------

`Announcements <https://community.lsst.org/c/announce>`_ For major
   announcements.  Originally this category was intended to be
   equivalent to the ``dm-announce@lists.lsst.org`` mailing list to
   announce software releases.  As the scope of Community has grown,
   the scope of Announcements has also grown to be more
   Project-holistic.  This is an area where DM collaboration with LSST
   Communications would be beneficial.

`Data Management <https://community.lsst.org/c/dm>`_ Conversations
   within the DM team, open to the public.

   ``Data Management`` also includes several sub-categories:

   `DM Notifications
      <https://community.lsst.org/c/dm/dm-notifications>`_ Brief
      broadcasts within the DM to alert team members of new features
      or changes to the software stack and infrastructure.

      DM Notifications also hosts our weekly `DM Activity Highlights
      series <https://community.lsst.org/tags/dm-highlights>`_ series
      that summarizes DM activity at very technical level.
   
   DM Team A category visible only to members of the ``LSSTDM`` group
      (seldom used given our policy of open communication)

`Support <https://community.lsst.org/c/qa>`_ Question-and-answer
   category for users of LSST Software and Data to resolve issues
   (with DM Staff and other community members).  Accepted solutions
   are marked to organically build a knowledge base for other users.

`Simulations <https://community.lsst.org/c/sims>`_ Conversations
   within the Simulations team, open to the public.

`Camera <https://community.lsst.org/c/camera>`_ Conversations within
   the Camera team, open to the public.  This category is not actively
   used.

`Cross-System Discussions <https://community.lsst.org/c/systems>`_
   This category hosts sub-categories for conversations between LSST
   subsystems to work on interfaces.

LSST Project This category is only visible to LSST project members
   (``LSST`` group).  It has been used to debrief conferences and
   offer frank discussions.

Planned and Possible Categories
-------------------------------

Ask LSST
   This category, sponsored by the Project Science Team, will provide
   the science collaborations, and the astronomy community in general,
   a venue to ask questions about how LSST will operate and serve
   their science goals and receive official answers from the project.
   Such a Q&A venue will offer an appealing alternative to getting
   answers through our technical documentation or through one-on-one
   conversations that don't scale.  Technically, this category will
   operate similarly to the Support category.

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
discussion on https://community.lsst.org.  Echoing forum activity to
an e-mail gateway has been common practice since the early days of the
Internet.  SQuaRE uses Mandrill, by Mailchimp, to send these emails.

Project group management
------------------------

As discussed, we assign project staff to 'groups' within Community
that offer higher Discourse trust levels and access to private
categories.  Currently this assignment is managed manually by SQuaRE
and DM T/CAMs.  As Community's use grows across the project, this may
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
developers, and is hard to maintain.  We are in the process of
migrating all software documentation from Confluence to other, better
harnesses.

The DM Developer Guide formerly published on Confluence has been
officially migrated to the new DM Developer Guide at
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
previous wiki, TRAC.  This migration is a background activity across
DM that occasionally sees fits of progress.

.. _tickets:

Work Ticketing
==============

JIRA Tickets
------------

DM uses JIRA to plan, track and report on work.  Thus it is a medium
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
tightly coupled to the code.  Also, Pull Requests is how a non-LSST
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

Our current policy is to to triage these GitHub issues into JIRA
tickets.

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

See the `RFC page in the Developer Guide <http://developer.lsst.io/en/latest/processes/decision_process.html#request-for-comments-rfc-process>`_ for more information.

.. _RFD:

Request for Discussion (RFD)
============================

Although DM has regular meetings for specific individuals, there is
often a need to host *ad hoc* video conference meetings to discuss an
issue more expeditiously than on Community, while still ensuring the
availability of key team members.  For this need we use the Request
for Discussion process (RFD).  RFDs meetings are held in a standing
weekly time slot, with a JIRA project being used to reserve that time
slot.

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
delivery service.  The name *LSST the Docs" is in reference to the
highly popular documentation service *Read the Docs*---we explain
below why we could not just us that service off the shelf (which is
normally our preference).


ReStructuredText
----------------

ReStructuredText is a plain-text markup language, similar to Markdown
and LaTeX.  We specifically chose reStructuredText because it *the*
standard markup language in the Python community (in which DM
participates) and because it is explicitly designed to be
user-extensible.  These extensions come from both the open source
community (including rich tools for writing Math and documenting
application programming interfaces) and DM itself (such as a
short-hand for referencing other DM documents, or a system for citing
astronomical literature, among other possibilities).

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
  deep links to specific sections).  There is no dissonance from
  switching from searching for a document on the web and then reading
  reading it elsewhere in a PDF viewer.

- Web-based documentation naturally builds an organic network of
  internal links that improve content wayfinding.

- Websites are rendered equally well on small and large screens,
  thanks to responsive design practices.

- Websites can include interactive elements, such as dynamic figures
  or Python notebooks to test code.

- Websites can be updated continuously.

In *LSST the Docs*, PDF is treated as an archival format, while the
web site is the reader-facing product.

Continuous documentation delivery with LSST the Docs
----------------------------------------------------

Continuous delivery describes a process where documentation is ready
for publication whenever content is changed, thanks to a highly
automated pipeline.  When revised documentation content is pushed to
GitHub, it is built, tested, and made available in a staging
environment to the team.  When a team choses (usually by merging
changes to the GitHub master), the new content to automatically
published.

`Read the Docs <https://readthedocs.org/>`_ is a popular continuous
delivery service for Sphinx documentation, and we have used it widely
for technical notes and design documents.  However, Read the Docs
limits our ability to provision new documentation projects through an
well-defined API, and more fundamentally, limits our ability to
control the build environment for documentation.  LSST software
documentation requires that the software itself be built, which
demands a customized build environment.  To solve these issues, we
have built a service described in `SQR-006: Documentation Deployment
Service for LSST's Eups-based Software <http://sqr-006.lsst.io/>`_.
We anticipate that all DM reStructuredText/Sphinx-based documentation
projects will be served by LSST the Docs rather than Read the Docs in
order to leverage automations and efficiencies built into LSST the
Docs.

Domains: lsst.org/codes/io
--------------------------

For the convenience of our users, we generate a unique domain-name for
each published document, e.g. the developer guide can be found at
`developer.lsst.io <http://developer.lsst.io>`_.  The .io top-level
domain is in common use with tech sector organisations and using a
documentation-specific domain that is managed automatically keeps any
accidents away from the main, human-curated website.  Unlike the
lsst.org website, lsst.io is not a point of entry; everything hosted
under it will be referenced in the documentation index.

For similar reasons, SQuaRE cloud-based services aimed at DM
developers are hosted under the domain lsst.codes.  There is no
public-facing material in the lsst.codes services.

Change-Controlled Design Documents
==================================

LSST archives copies of all change-controlled documents in Docushare.
Irrespective of the source and development flow of our documents (be
they reStructuredText or LaTeX or Word), we continue to do so.
However our users are unhappy with the Docushare user experience,
hence why we do not depend on it as be the sole index of our
documentation.  (See :ref:`Archives <archives>`, below.)

The LSST the Docs platform was adopted by DM for several design
documents.  The ability to use a standard GitHub-based workflow for
collaboration and review, as well as the ability to see the document
drafts live on the web, makes LSST the Docs particularly appealing.
We hope that these design documents will see more frequent updates
than the previous generated of Word-based documents.  When updates to
these documents are approved by by the relevant boards, a release tag
will be made in the document's GitHub repository and a PDF rendering
of the document will be archived in Docushare.  Because of the
advantages of web-native documents, the 'unofficial' version of the
document published by LSST the Docs will continue to be the primary
way that the design document is viewed, even when it has been archived
in Docushare.

Some change-controlled documents are also published as LaTeX
documents, under the reasoning that they may be published to arXiv.org
or otherwise re-purposed into academic literature.  We intend to
provide some level of continuous integration and web delivery for
these documents that are already offered to the reStructuredText-based
LSST the Docs-published documents, though we are still planning how to
do this most effectively.

Technical Notes
===============

Technotes grew out of an organic need to have standalone documents
like Change-controlled Design Documents, but that could be used more
flexibly and informally to report on DM work.  For example, Technotes
have been used to describe back-end services provided by SQuaRE.  They
have also been used to draft designs for DM system (that are outside
the direct scope of change-control); this mode of design improves
schedules, improves the quality of the final product, and also
facilitates better cross-team collaboration.  Finally, Technotes have
been used to report on data processing experiments with the LSST
Stack.

In addition to building upon the web-native and GitHub-based
collaboration features of LSST the Docs, Technotes are meant to be
visible to the astronomical literature.  Released versions of
technotes are archived in Zenodo (:ref:`see below <archives>`), which
assigns a Digital Object Identifier (DOI) to the document.  In
partnership with ADS, the Astrophysics Data System, we are able to
list LSST Technotes in the primary astronomy bibliography.  Our
intention is to make more DM work directly citeable in the literature,
rather than relying solely on umbrella Project papers and "personal
communication" statements.

We plan to improve the Technote platform as it currently exists.
Potential improvements include:

- Improved visual design and print (PDF) layout.
- BibTeX-like citation system for reStructuredText that interacts with
  online bibliographies, such as ADS.
- Integration of Jupyter notebooks with Technotes.
- Integration of Technotes with the Community forum to facilitate
  discussions surrounding a technote.
- Improved automation of Technote provisioning.

See `SQR-000: The LSST DM Technical Note Publishing Platform
<http://sqr-000.lsst.io/en/master/>`_ for more information.

Developer Guide
===============

The DM Developer Guide is a key document for DM developers that
encapsulates our development policies and practices.  This Developer
Guide is especially important for on-boarding new team members.  It is
published with LSST the Docs at https://developer.lsst.io.

Although some information published in the developer guide could
qualify as technical notes or ad hoc pages in the DM Confluence wiki,
we encourage developers to write anything related to DM processes and
policies in the Developer Guide so that the information can be quickly
discovered by browsing the Developer Guide's table of contents.  The
failure to do this was one reason why the Developer Guide's original
incarnation as a Confluence space was unsuccessful.  That Confluence
space was poorly organized and in some cases Developer Guide-like
material existed in the Data Management confluence space, rather than
the Developer Guide confluence space.

..  Software and Data Documentation ===============================
  
  [do we need to talk about this?]

.. _archives:

Digital Archives: Docushare & Zenodo
====================================

DM makes use of Docushare and Zenodo are archival services for our released documentation artifacts.

Docushare
---------

As is standard practice in LSST, Docushare is used to archive all
approved changed-controlled documents.  Our standard practice is to
generate and deposit PDFs of the original web document into Docushare.

Zenodo
------

Zenodo is a digital archive operated by CERN that provides reasonable
assurances of data longevity such that it can issue Digital Object
Identifiers (DOIs).  DOIs allow digital artifacts to be cited in
academic literature.  DM uses Zenodo to archive released versions of
our documents that are relevant to scientific literature, such as
technical notes, presentations, software, and software documentation.
Note that the LSST Publication Board has also adopted Zenodo as an
archive for LSST presentations.

Any researcher can upload artifacts to Zenodo and receive a DOI.
Curation occurs when an artifact is submitted to a Zenodo Community.
We curate an `LSST Data Management (lsst-dm) community
<http://zenodo.org/lsst-dm>`_ on Zenodo that *can* be browsed.

Metadata preparation is a barrier to uploading to Zenodo.  We are
building a Python tool, Zenodio <http://zenodio.lsst.io>`_, to help
automate the process of completing deposition metadata and uploading
to Zenodo.  Our technical note and design document repositories, for
instance, include user-editable metadata files that are used by LSST
the Docs and Zenodio tools.  We also expect that Zenodo will make it
possible for Community curators to edit the metadata of accepted
artifacts.

Archives as band-end services
-----------------------------

Although these archives serve necessary and useful functions, we do
not promote these Docushare or Zenodo as user-facing points of entry
for DM documentation.  We do not believe that Docushare, nor Zenodo,
provide the types of document search, curation and discovery
affordances.  It is also desirable to view a document in its original,
web native form rather than a static PDF deposited in an archive.
Thus we treat Docushare and Zenodo largely as back-end services
necessary for fulfilling archival requirements set by the LSST project
or academic publishers.

.. _doc-index:

A Documentation Index
=====================

*This section describes future work.*

LSST's documentation, as described above, consists of a constellation
of design documents, technical notes, and documentation sites for
specific software projects and data releases.  In addition, DM also
produces presentations, conference proceedings and published academic
articles.  For these to documents to be effective, they need to be
discoverable.

We intend to solve the documentation discovery problem with a highly
useable, well publicized, central documentation landing page.

- Dynamically updated when new documents are published by LSST the
  Docs, or made available in ADS/Zenodo.
- Full-text search
- Browse by content type, and also by subject
- Curated collections of documents (e.g, top documentation for
  scientists).
- Awareness of documentation versions; ability to choose a version of
  the document
- Landing page should be curated to get readers to top documents, such
  as the Science Pipelines documentation.

We anticipate that the Documentation Index will be integrated into the
Data Management homepage at dm.lsst.org.  Together with the Community
forum, the Documentation Index is the public-facing point of entry
into LSST Data Management information.

NASA/SAO Astrophysics Data System (ADS)
=======================================

*This section descries future work.*

In addition to our own Document Index, we also also push documents to
the NASA/SAO Astrophysics Data System.  ADS is an immensely successful
literature database for astronomy such that being part of the
astronomical literature is synonymous with being listed on ADS.  Thus
we list DM technical notes on ADS so that they can be cited in
literature.  Note that Zenodo is key to this process since Zenodo
furnishes the DOI and archival assurances required by ADS.

.. |clo| replace:: Community_

.. |rfc| replace:: RFC_

.. |rfd| replace:: RFD_

.. |ltd| replace:: LTD_

