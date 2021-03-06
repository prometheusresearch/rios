*******************
RIOS Change History
*******************


0.3.0 (2020-01-30)
==================

* Changed license to Apache v2.0.
* Clarified behavior of the ``length.min`` constraint with respect to
  ``required``.
* Clarified behavior of the ``required`` property with respect to
  ``recordList`` fields.
* Clarified behavior of the ``required`` property with respect to ``matrix``
  fields, their Rows, and their Columns.
* Clarified the values that should be provided for the ``min`` and ``max`` of
  the ``range`` constraint.
* Clarified behavior of the ``enumerations`` property in Question Objects.
* Clarified Web Form Event types that are applicable to ``audio`` elements.


0.2.0 (2015-12-28)
==================

* Changed name of standard to RIOS - Research Instrument Open Standard
* Removed ability to define Calculations with result types of ``enumeration``
  or ``enumerationSet``, as those types don't make sense without first defining
  the set of possible enumerations.
* Clarified that Form Element Tags cannot be the same as Page IDs or Instrument
  Field IDs.
* Clarified <<Parameter>> markup behavior with respect to null values.
* Clarified type inheritance with respect to overriding constraints.
* Added support for an ``identifiable`` flag on Calculations. This flag's
  meaning is the same as it is on Instrument fields.
* Added support for arbitrary metadata in Instruments, Calculation Sets, Forms,
  and Interactions via the ``meta`` property.


0.1.0 (2015-08-24)
==================

* Initial publication of PRIMSH for review.

