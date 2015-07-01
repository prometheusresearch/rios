********
Overview
********

.. contents:: Table of Contents


Introduction
============

The PRISMH specification describe a collection of configuration files that are
used to define the process of data collection in an open and transportable way.


Major Components
================

Instrument
----------
:doc:`Instrument Definition </instrument_specification>` are the base of the
PRISMH specification. They contain the definition of **what** data is to be
collected. At its heart, it is a list of field definitions that specify the
name, data type, and type constraints.  There is no information or instruments
on **how** the data is to be retrieved or collected -- only **what** data needs
to be collected.


Assessment
----------
:doc:`Assessment Documents </assessment_specification>` are individual units of
collected data that satisfy the rules defined in an `Instrument`_. They are a
field-for-field listing of each data point, and can optionally contain metadata
about the data or the means that were used to collect it.


Calculation Set
---------------
:doc:`Calculation Set Definitions </calculation_set_specification>` are a means
of augmenting an `Instrument`_ with additional fields that can be
programmatically calculated using the data collected in an `Assessment`_. These
calculated values are then stored in their corresponding `Assessment`_ Document
as metadata.


Web Form
--------
:doc:`Web Form Configurations </web_form_specification>` are a generic way of
describing **how** the data described by an `Instrument`_ should be collected
when the desired tool is a Web-based form. It describes what order the
questions are presented in, how they're paginated, what text is used to guide
or prompt the user, and what web components are used to enter the data.


SMS Interaction
---------------
In much the same way that `Web Form`_ Configurations describe how to collect an
`Instrument`_'s data via a web page, :doc:`SMS Interaction Configurations
</sms_interaction_specification>` describe how to collect the data via an
interactive SMS text message exchange. It describes what order the questions
are presented in and what text is used to guide or prompt the user.

