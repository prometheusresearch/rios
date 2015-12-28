*******************
RIOS Change History
*******************


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

