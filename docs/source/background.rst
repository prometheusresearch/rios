**********
Background
**********

.. contents:: Table of Contents


Overview
========
Electronic data capture (EDC) systems have increasingly replaced paper-based
methods of collecting research data. As EDC systems have proliferated, however,
so has the number of incompatible formats for storing EDC instruments (form
configurations). The lack of interoperability among EDC formats makes it
difficult to reuse, share, or find previously configured instruments unless
they were configured for the same EDC system. Ideally, each research instrument
would need to be configured only once, would be stored in an easily accessible
place for others to use, and would work seamlessly with its users’ EDC tools.

The Research Instrument Open Standard (RIOS) brings this ideal closer to
reality by laying the groundwork for an interoperable ecosystem of research
instruments. All EDC instruments have at least four types of properties:
content (e.g., text of questions and response options), structure (e.g.,
ordering, grouping of questions), internal logic (e.g., skip logic, validation
rules), and method of display (e.g., pagination, form controls used to collect
responses). RIOS is an open metadata standard for representing research
instruments. It offers a generic, well-defined schema for representing the
content, structure, logic, and display properties shared by all EDC
instruments, without relying on the idiosyncratic representations of EDC
systems.

By moving to a standard research instrument definition, researchers can begin
to develop converters to move instrument configurations between EDC systems.
Prototype converters for moving to and from the RIOS standard and `Qualtrics`_
and `REDCap`_ EDC formats are available at
https://www.rexdb.org/rios-converter/.  Applications built on the open-source
RexDB platform (e.g., `RexStudy`_) natively support the RIOS standard. More
information about the RexDB project can be found at https://www.rexdb.org/.

.. _`Qualtrics`: https://www.qualtrics.com/
.. _`REDCap`: http://projectredcap.org/
.. _`RexStudy`: http://www.prometheusresearch.com/rexstudy


About the Authors
=================
With funding from the NIH (Grant #1R43-MH106225), the informatics experts at
Prometheus Research authored the freely-available, universal standard called
RIOS and initial set of conversion tools for the exchange, reuse, and storage
of EDC metadata configurations. The original implementation of the standard was
referred to as "PRISMH" for the "Portable Research Instrument Standard for
Mental Health" and later renamed due to its applicability to domains outside of
mental and behavioral health. Webinar(s) and other resources about RIOS are
freely available on Prometheus' website: http://www.prometheusresearch.com. For more
Prometheus'-authored works, visit `FigShare`_.

.. _`FigShare`: https://figshare.com/search?q=prometheus+research

