*******************************************
SMS Interaction Configuration Specification
*******************************************

.. contents:: Table of Contents


Overview
========
A PRISMH SMS Interaction Configuration is a standard means to augment an
Instrument Definition with additional configuration and meta-data that allows
the Instrument to be administered via an SMS text message-based application.


Format
======
SMS Interaction Configurations are stored and exchanged as `JSON`_ (JavaScript
Object Notation) objects. The structure of these objects must adhere to the
rules set forth in this document.

.. _`JSON`: http://json.org/


Structure
=========

Root Object
-----------
The Root Object of an SMS Interaction Configuration consists of several
properties:

``instrument``
    :Type: `Instrument Reference Object`_
    :Constraints: Required
    :Description: This property specifies which Instrument Definition the
                  Interaction is based on.

``defaultLocalization``
    :Type: String; Must be in the form of a `RFC5646`_ Language Tag
    :Constraints: Required
    :Description: This property specifies the localization that will be
                  available in every `Localized String Object`_ within the
                  Interaction Configuration.

``defaultTimeout``
    :Type: `Timeout Object`_
    :Description: This property specifies what the timeout behavior is for the
                  Interaction.

``steps``
    :Type: Array of `Step Object`_
    :Contraints: Required; Must contain at least one `Step Object`_
    :Description: This property lists the Steps of Questions (and/or other
                  Steps) that the Interaction is made up of. The order that
                  the Steps are placed in this property is the same order that
                  they will be executed.


Instrument Reference Object
---------------------------
An Instrument Reference Object is the means for an SMS Interaction
Configuration to reference the exact Instrument (and version of that
Instrument) that the responses contained within are in reference to.

``id``
    :Type: String
    :Constraints: Required; Must be a URI as described in `RFC3986`_

                  .. _`RFC3986`: http://tools.ietf.org/html/rfc3986
    :Description: This property is a reference to the ``id`` property on the
                  root object of an Instrument Definition. It is meant to
                  specify the exact Instrument this SMS Interaction
                  Configuration is based on.

``version``
    :Type: String
    :Constraints: Required
    :Description: This property is a reference the the ``version`` property on
                  the root object of an Instrument Definition. It is meant to
                  specify the exact revision of the Instrument this Interaction
                  Configuration is based on.


Timeout Object
--------------
A Timeout object describes what to do when a user doesn't respond for a period
of time. It must contain at least one of the following properties:

``warn``
    :Type: `Timeout Details Object`_
    :Description: This propery describes the warning phase of a timeout. When
                  the specified threshold is met, a message is sent to the user
                  to warn them about their impending timeout.

``abort``
    :Type: `Timeout Details Object`_
    :Description: This property describes the final phase of a timeout. When
                  the specified threshold is met, a message is sent to the user
                  telling them that the Interaction is being aborted, and the
                  system stops processing any further steps in the Interaction.


Timeout Details Object
----------------------

``theshold``
    :Type: Integer
    :Constraints: Required
    :Description: The number of seconds of idle time since the last action was
                  peformed.

``text``
    :Type: `Localized String Object`_
    :Constraints: Required
    :Description: The message to send when this timeout event occurs.


Step Object
-----------
A Step object represents a single piece of an Interaction. It consists of
several properties:

``type``
    :Type: Enumerated String
    :Constraints: Required
    :Description: This property indicates the type of step that is being
                  described.
    :PossibleValues: =========== ===========
                     Name        Description
                     =========== ===========
                     question    A Question that the user can respond to.
                     text        Some text that should be sent to the user.
                     =========== ===========

``options``
    :Type: Object
    :Description: This property is a container for whatever additional
                  parameters are needed for this particular Step.
    :PossibleValues: =============== ==================
                     Step Type       Applicable Options
                     =============== ==================
                     question        The options are in the form of a `Question Object`_.
                     text            The only option allowed is a single property named ``text`` that
                                     is a `Localized String Object`_. This property can be marked up.
                     =============== ==================


Question Object
---------------
A Question Object defines how a Field from an Instrument is presented to the
user so that they may provide a response.

``fieldId``
    :Type: String
    :Constraints: Required
    :Description: This property is a reference to the ID of a Field that is
                  defined in the associated Instrument Definition. A Field
                  ID can only be used in one Question Object in a given
                  Interaction. Interaction Questions can only represent 
                  Instrument Fields that are based on Simple Instrument data
                  types.

``text``
    :Type: `Localized String Object`_
    :Constraints: Required
    :Description: This property allows the Interaction author to provide a more
                  detailed description for the Question. Often, it is an
                  explicit question that is being asked of the Subject.
    :Example: What is the your age?

``error``
    :Type: `Localized String Object`_
    :Description: This property allows the Interaction author to supply text
                  that will be presented to the user when the value they've
                  input is not valid. This property is optional.

``enumerations``
    :Type: Array of `Descriptor Object`_
    :Constraints: Only applies to Questions for Fields of type ``enumeration``
                  or ``enumerationSet``
    :Description: This property contains the list of Enumerations that are
                  presented to the user for them to choose from. The order that
                  the Enumeration Objects are placed in this property is the
                  same order that they will be presented on the front end.


Descriptor Object
------------------
A Descriptor Object is the means with which an author defines the text of
simple facets of an Interaction such as Enumerations.

``id``
    :Type: String
    :Constraints: Required
    :Description: This property is a reference to the ID of an Enumeration or
                  Row on the Field that is defined in the associated Instrument
                  Definition.

``text``
    :Type: `Localized String Object`_
    :Constraints: Required
    :Description: This property allows the Interaction author to provide a more
                  detailed description for the Enumeration rather than
                  displaying a code. This text can be marked up.


Localized String Object
-----------------------
A Localized String Object is a generic container that allows the configuration
author to provide text for use in a Interaction that is accompanied with
localized (translated) versions of that text. This object contains one or more
properties, where each property is a `RFC5646`_ Language Tag. The values of all
the properties are the localized versions of the same text.

.. _`RFC5646`: http://tools.ietf.org/html/rfc5646

Example::

    {
        "en": "What is the subject's age?",
        "fr": "Quel est l'âge de l'objet?"
    }

Every Localized String Object within a given SMS Interaction Configuration must
contain at least one property that is keyed with the same Language Tag that is
defined in the defaultLocalization property of the `Root Object`_. This ensures
that the application responsible for displaying the Interaction can be
guaranteed to always have at least one known text string available to it.


Identifier
----------
Identifiers are strings that adhere to the following restrictions:

* Consists of 2 or more of the following characters:

  * Lowercase latin alphabetic characters ("a" through "z"; Unicode 0061
    through 007A)
  * Latin numeric digits ("0" through "9"; Unicode 0030 through 0039)
  * Underscore characters ("_"; Unicode 005F)

* The first character is an alphabetic character.
* The last character is not an underscore.
* Does not contain consecutive underscore characters.

Example Identifiers:

* page1
* grp_a
* ref_1_2_alpha

