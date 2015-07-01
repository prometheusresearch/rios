**********************************
Example of a Simple Definition Set
**********************************

.. contents:: Table of Contents


Overview
========

The following examples illustrate a very simple Instrument and its accompanying
configurations. The Instrument defines two fields to be collected. There is a
Calculation Set definition that provides some post-Assessment calculations to
perform on the Assessment data. There are examples of how this Instrument can
be represented in both a Web Form and an SMS Interaction. Finally, there is an
example Assessment that could result from this Instrument.

It is not required to produce a full suite of configurations for every
Instrument; this is only an example of what is possible.


Instrument
==========

.. literalinclude:: simple-instrument.json
   :language: javascript


Calculation Set
===============

.. literalinclude:: simple-calculationset.json
   :language: javascript


Web Form
========

.. literalinclude:: simple-form.json
   :language: javascript


SMS Interaction
===============

.. literalinclude:: simple-interaction.json
   :language: javascript


Assessment
==========

.. literalinclude:: simple-assessment.json
   :language: javascript

