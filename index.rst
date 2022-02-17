..
  Technote content.

  See https://developer.lsst.io/restructuredtext/style.html
  for a guide to reStructuredText writing.

  Do not put the title, authors or other metadata in this document;
  those are automatically added.

  Use the following syntax for sections:

  Sections
  ========

  and

  Subsections
  -----------

  and

  Subsubsections
  ^^^^^^^^^^^^^^

  To add images, add the image file (png, svg or jpeg preferred) to the
  _static/ directory. The reST syntax for adding the image is

  .. figure:: /_static/filename.ext
     :name: fig-label

     Caption text.

   Run: ``make html`` and ``open _build/html/index.html`` to preview your work.
   See the README at https://github.com/lsst-sqre/lsst-technote-bootstrap or
   this repo's README for more info.

   Feel free to delete this instructional comment.

:tocdepth: 1

.. Please do not modify tocdepth; will be fixed when a new Sphinx theme is shipped.

.. sectnum::

.. note::

This technical note describes the deliverables of the First-look Analysis and Feedback Functionality Breakout Group, Charge #2.
This is the working draft and is not yet finalized.

Context
========
To commission and operate the observatory, project is currently developing numerous tools to perform analysis of system performance, data acquisition, and display.
There exist multiple solutions of where and when these analyses could be performed.
This new charge is for the FAFF group to better identify the needs of the analyses, then determine how the computing resources and capabiilties should be distributed to meet the needs.
The expanded scope of this charge in comparison to the original is the difference in relevant timescale for performing analyses and producing results.
This charge expands the timescale from minutes to approximately 24 hours to facilitate the ability to perform round-the-clock commissioning activities including on-sky observation planning, execution, and preparation for the following night taking into account the previous nights' results.

Motivation
==========
The previous FAFF report made several recommendations regarding how to perform analyses and create artifacts for display to operators.
The bigger-picture infrastructure that would facilitate this work was considered out-of-scope and not addressed.
Other aspects of the image display, specifically in regards to functionality required not on-the-fly but shortly thereafter were also not in scope.
This charge is to deal with these issues to develop the implementation side of the original recommendations, as well as a small number of related issues.
Commissioning has now started with regular auxTel observing, and these tools would already be in use if they existed.
These tools, workflows and infrastructures need to be in regular use and well developed before moving into the on-sky commissioning period with ComCam.

Scope and Deliverables
======================

.. _SITCOM-173: https://jira.lsstcorp.org/browse/SITCOM-173
.. _SITCOM-174: https://jira.lsstcorp.org/browse/SITCOM-174
.. _SITCOM-180: https://jira.lsstcorp.org/browse/SITCOM-180

This group is being assembled to review the current strategies and tooling of the project, and evaluate the approach against a series of typical use-cases that demonstrate critical functionalities to observatory commissioning and operations.
The group will report the finding and make a series of recommendations to augment the current tools and possibly design and develop new tools to address the use-cases.

As mentioned in the `Context`_, the scope of this charge is limited to timescales of minutes up to approximately 24 hours. 
This is to enable day-to-day and night-to-night commissioning activity where the next night is able to benefit from the previous day's analyses.

Several of the following charge assignments are related to specific Jira tickets that resulted from a Missing Capabilities mini-workshop. 
The relationship between the question and charge is indicated by the link preceding the charge question (TBC).

The following items shall be delivered by the group:

#. (`SITCOM-174`_, `SITCOM-173`_, `SITCOM-180`_) A series of use-cases where image data analysis is required on short timescales. 
   A reduced set of use-cases should be created as a regular reference throughout the charge.
   A set of required turn-around time(s) should be defined and assigned to each case where applicable.

    - Use-cases should be complete, including which inputs are required and from where they will originate (e.g. SAL Script, EFD, LFA, external source), desired manipulations, logic-based operations/calculations, and if/how the desired artefacts are presented to the user (e.g. display images and/or graphs).

#. (`SITCOM-180`_, `SITCOM-173`_) Define which metrics, analyses and artifacts must be calculated and on what timescale they must be evaluated and reported to support commissioning/operations. 
   This is to evaluate if a "rapid processing" of data is required, what specific calulations are required.
   This list should include the relevant camera specific calculations (which are currently performed by the EO testing data reduction).
   This is expected to inform the answer to the next charge task.

#. (`SITCOM-174`_, `SITCOM-173`_) Define how users will interact with each aspect of the previously listed metrics, analyses and artifacts; classify them indicating where can could calculated.
   This includes tasks defined for the catcher, OCPS jobs, AuxTel/ComCam/LSSTCam processing, and the rendez-vous of data from multiple sources (DIMM, all-sky etc).

#. (`SITCOM-180`_) Provide a list of required non-scalar metrics are required and cannot be computed with faro. 
   Suggest a mechanism (work flow) to perform the measurement, document the finding, evaluate any trend (if applicable), then present it to the stakeholders.

#. (`SITCOM-174`_) Using the responses to questions 1-4, propose a management & maintenance structure for the Camera Diagnostic & Commissioning Clusters.
   This includes identifying what processes require specific hardware and/or infrastructure, identifying the more generalized analyses that may benefit from a common infrastructure, and evaluating possible solutions that can ease duplication of effort.

#. Develop a plan and scope estimate to expand the Camera Visualization Tool to support the full commissioning effort.
   This includes identifying libraries/packages/dependencies that require improvements (e.g. Seadragon) and fully scoping what is required to implement the tool with DM tooling such as the Butler. 
   The scope estimate may propose the use of in-kind contribution(s) to this effort if and where applicable.
  
#. Work with project software teams to and implement an initial version of the Catcher CSC and supporting functionality.
   An initial description of required functionality was delivered in the first FAFF charge. 
   This deliverable is to implement (at least) two use-cases; one which uses image data and the other which does not.
   Subsequently, suggest a developer and/or in-kind contributor continue development.

#. Design user-level training bootcamps and materials, aimed at the level of an in-kind contributor.
   These bootcamps will be used as the initial training materials.
   It is expected that In-kind contributors and/or other delegates can augment the content, provide improvements, and eventually take over some of the training.
   
#. A prioritized list of tasks to build-out the new functionalities with recommended end-dates. 
   Wheere possible, these dates shall correspond to integration milestones.


Timeline
========
This group is to provide an initial report including suggested immediate actions on July 1st, 2022. 
The final report shall be delivered by September 1st, 2022.

Aspects Considered Out-Of-Scope
===============================

This working group is aimed at identifying the needs to perform routine night-to-night commissioning and analyses that require longer turn-arounds are generally out-of-scope.
This is not a sufficiently well-defined line. 
To provide further context, the following items are aspects which are considered out-of-scope for this group and should be addressed elsewhere.

#. Evaluation of deep coadds and required tooling requiring advanced image visualization.
#. Definition of logging tool(s)
#. Interaction(s) with the observatory logging system (associating logging comments with images, tagging of images etc)
#. Communication and workflows (e.g. How the daily calibration products get reported to the summit crews)
#. Generation of a nightly summary report.
#. Data analyses regarding templates and/or coadd generation
#. Investigation of pipeline performance
#. Generation of verification artifacts
#. Ability to re-process data with different pipeline configurations


Participants
============

- Patrick Ingraham (chair): Calibration Systems Engineer

- Keith Bechtol: Commissioning Scientist and Associate Professor at the University of Wisconsin

- Tony Johnson: Camera Control Software Lead

- ?: SQuaRE Science Participant

- ?: DM Software Representative

- Robert Lupton: Calibration Scientist

- Tiago Ribeiro: T&S Software Architect and Scheduler Scientist


.. Add content here.
.. Do not include the document title (it's automatically added from metadata.yaml).

.. .. rubric:: References

.. Make in-text citations with: :cite:`bibkey`.

.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa
