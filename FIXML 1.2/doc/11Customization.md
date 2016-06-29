FIXML Customization
===================

The FIXML schema files have been organized to support extension. Implementation versions of each schema file (with the exception of the datatypes and main schema files) are provided to permit users to redefine the standard (base) FIXML schema. This section provides guidelines for customizing the FIXML schema files.

Even though a considerable amount of work has gone into making FIXML extensible, users are strongly encouraged to minimize modifications, in order to promote more consistent usage of the FIXML syntax within the industry. Obviously, the less customization, the easier it is to connect to counterparties.

If customization is required, you are encouraged to communicate your requirements that are not being met by FIX to the FPL Global Technical Committee. There you may find out that there is a technique to meet your business requirement. Or, you may find that the Technical Committee has already addressed the issue for a planned future release. At a minimum you will receive coaching and assistance in how to extend FIXML in such a way as to make the new feature a part of a future version of FIX.

Defining a custom field
-----------------------

New fields can be defined as an XML simpleType in the fixml-fields-impl-5-0-SP2.xsd schema file. It is recommended to add the field to the end of the schema document. It is also strongly encouraged to include XML comments to define the reason the new field must be added and there is not already a standard FIX field with the same meaning and use.

The field reference is added to the component or message where it is to be used.

If the field will be added to a standard message or component contained in a base file, the message or component must be redefined in the correct impl schema file. For Common components, this would be the fixml-components-impl-5-0-SP2.xsd file.

Adding a field reference to a component or message contained in one of the message categories is done using the correct category impl schema file (e.g. fixml-marketdata-impl-5-0-SP2.xsd). The component or message must be redefined in the impl schema file.

It is encouraged to append new enhancements to the end of the schema files.

Restricting enumeration values for a FIX field
----------------------------------------------

Restricting enumeration values is done by modifying the type definition in the fixml-fields-impl 5-0-SP2.xsd schema file.

Extending enumeration values for a FIX field
--------------------------------------------

Extending enumeration values is done by creating a union of the original enumeration type definition with new enumeration values.

Making an optional field required
---------------------------------

Making an optional field required is done by redefining the optional attribute group, modifying the usage of the field from “optional” to “required”. This redefinition is done within the implementation file for either the components for Common components or the implementation file for a particular message category (e.g. fixml-marketdata-impl-5-0-SP2.xsd).

Making a required field optional
--------------------------------

It is not possible to make a required field optional without modifying the original required element or attribute group. Making required fields optional does go against the standard base definition of FIX and should be avoided.

Adding a custom message
-----------------------

Custom messages are added by creating a message structure within the category to which the custom message belongs. Required and optional element and attribute groups should be created for the custom message.
