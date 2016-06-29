<span id="_Toc352230334" class="anchor"><span id="_Ref362348255" class="anchor"><span id="_Toc410382667" class="anchor"></span></span></span>Introduction
=========================================================================================================================================================

The Financial Information Exchange (FIX) Protocol is a message standard developed to facilitate the electronic exchange of information related to securities transactions. It is intended for use between trading partners wishing to automate communications. FIXML is a technical standard for FIX application messages using XML syntax. This document defines the FIXML 1.0 technical standard.

Background
----------

The FPL FIXML working group began investigating the XML format in 1998 and published a white paper supporting an evolutionary approach to support the FIX Protocol using an XML format. The working group released an initial version of the FIXML DTDs on January 15th, 1999. There are DTDs based on FIX Protocol versions 4.1, 4.2 and 4.3. A FIXML Schema was established with the release of FIX 4.4. The working group then focused on optimizing and enhancing the use of XML technologies. The FIXML 1.0 standard is the result of these enhancements to optimizations for FIX messaging and has been available as part of the standard release process since FIX 5.0 SP2 (May 7, 2014).

<span id="_Toc410382669" class="anchor"><span id="_Toc352230335" class="anchor"></span></span>FIXML Features
------------------------------------------------------------------------------------------------------------

-   FIXML uses the FIX data dictionary and business logic from the FIX Repository.

-   FIXML is the XML representation and vocabulary for FIX application messages.

-   FIXML includes FIX application messages and does not include a session layer.

-   FIXML can be encapsulated within the FIX Session Protocol or within another protocol like, MQ Series, TIBCO, SOAP, etc.

FIXML 1.2 Enhancements
----------------------

Specification terms
-------------------

These key words in this document are to be interpreted as described [in Internet Engineering Task Force RFC 2119](http://www.apps.ietf.org/rfc/rfc2119.html). These terms indicate an absolute requirement for implementations of the standard: “**must**”, or “**required**”.

This term indicates an absolute prohibition: “**must not**”.

These terms indicate that a feature is allowed by the standard but not required: “**may**”, “**optional**”. An implementation that does not provide an optional feature must be prepared to interoperate with one that does.

These terms give guidance, recommendation or best practices: “**should**” or “**recommended**”. A recommended choice among alternatives is described as “**preferred**”.

These terms give guidance that a practice is not recommended: “**should not**” or “**not recommended**”.

Document format
---------------

In this document, examples of FIXML will appear with the FIXML root element enclosing elements, attributes and attribute values.

&lt;FIXML&gt;&lt;element attribute="attributeValue"/&gt;&lt;/FIXML&gt;

Field / Message / Component names

@ProcMode

BatchProcessMode(50002)
