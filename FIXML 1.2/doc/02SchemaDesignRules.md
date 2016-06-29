FIXML Schema Design Rules
=========================

The FIXML schema may be used to validate FIXML messages. The FIXML schema is generated from the FPL Repository. The FIXML schema may be extended to include enhancements and restrictions of the FIX application messaging standard.

The following design rules support the design objectives for the FIXML Schema and the FIXML instance documents.

1.  FIXML naming

    1.  Use meaningful abbreviations for element and attribute names wherever possible. Use standard abbreviations for common words (e.g., Price = Px, Currency = Ccy, etc.).

    2.  Field name prefixes that were used in FIX tag=value format for uniqueness shall be removed – thus creating a contextual abbreviation.

2.  The FIXML root element may include version identifiers (see section on version attributes below).

3.  The FIXML root element will include a single FIXML message or a batch of FIXML messages (see section on batching FIXML messages below).

4.  FIX messages are implemented as an XML element.

    1.  The FIXML element name is the abbreviated name of the message.

    2.  The FIXML element is implemented with a complexType unique for each message.

        1.  The message complexType name is a concatenation of the message name and the string “\_message\_t”.

        2.  The message complex type is extended by the complexType Abstract\_message\_t.

        3.  The message complexType includes a group with a sequence consisting of the message elements (see component instances implemented as elements below).

        4.  The message complexType includes the attributeGroup for the message (see field instances implemented as attributes below).

    3.  FIXML elements are not generated for messages that are coded in the repository with NotReqXML=1. These messages are generally not application level messages and include session level messages such as Logon(35=A), Logout(35=5), etc.).

5.  FIX field instances within a message or a component are implemented as an attribute within an attribute group for the message or component.

    1.  The FIXML attribute name is the abbreviated name of the field or a separate abbreviated name within a category as coded in the FIX repository.

    2.  The FIXML attribute Type is implemented as the field simpleType (see FIX fields implemented as a simpleType below).

    3.  The FIXML attribute Use is set to required or optional based on whether or not the field instance is required within the message or component.

    4.  The FIXML attributeGroup name is based on concatenation of the message or component name and the string “Attributes” (e.g. AllocationInstructionAttributes for the AllocationInstruction message)

    5.  The FIXML attribute is not generated for those fields coded as NotReqXML=“1”. These fields are generally those that are needed in the Tag=value syntax and not needed in FIXML (e.g. fields that are coded with the NumInGroup data type).

6.  FIX component instances within a message or another component are implemented as an XML element in a sequence of elements for the message or parent component.

    1.  The FIXML component instance element name is the abbreviated name of the FIX component.

    2.  The FIXML component instance element type is implemented as the component complexType (see FIXML components implemented as a complexType below).

    3.  The FIXML component instance element minOccurs=“1” for components coded as required and minOccurs=”0” for components coded as not required in the FIX repository.

    4.  The FIXML component instance element maxOccurs=”1” for components with the type of Block (or ImplicitBlock) in the FIX repository and maxOccurs=”unbounded” for components with the type BlockRepeating (or ImplicitBlockRepeating) in the FIX repository.

    5.  A FIXML component instance element that is coded as inlined in the FIX repository will not be generated. Attributes of this component will be appended to the attributes of the parent component or message. Elements of this inlined component will be appended to the element sequence for the parent component or message.

    6.  The FIXML elements for components are not generated for components that are coded in the repository with NotReqXML=1. The StandardTrailer component is an example of a component that is not generated in FIXML.

7.  FIX components are implemented as a complexType.

    1.  The FIXML complexType name is a concatenation of the FIX component name and the string “\_Block\_t”.

    2.  The FIXML component complexType includes a group with a sequence consisting of the component elements. The name of the group is a concatenation of the component name and the string “Elements”.

    3.  The FIXML component complexType includes an attributeGroup. The attributeGroup name is a concatenation of the component name with the string “”Attributes”.

8.  FIX fields are implemented as a simpleType.

    1.  The FIXML field simpleType name is a concatenation of the FIX field name and the string “\_t” (e.g. Account\_t).

    2.  The FIXML field simpleType is restricted by the FIX field data type or in the case of an enumerated field, by the FIXML field enumeration simpleType (see FIX field enumerations implemented as a simpleType below).

    3.  The FIXML field simpleType includes the FIX field description as documentation.

    4.  The FIXML field simpleType includes the FIX field name, component type tag, data type and abbreviated name as application information to cross reference.

9.  FIX field enumerations are implemented as a simpleType.

    1.  The FIXML field enumeration simpleType name is a concatenation of the field name and the string “\_enum\_t” (e.g. AdvSide\_enum\_t).

    2.  The FIXML field enumeration simpleType is restricted by the FIX field data type.

    3.  The FIXML field enumeration simpleType includes the enumeration values for the FIX field.

    4.  The FIXML field enumeration simpleType includes the enumeration descriptions for each FIX field enumeration value.

10. FIX Categories are used to organize FIXML schema files.

    1.  The FIXML filename

    2.  Categories coded with NotReqXML=1 are not used in FIXML schema generation (e.g. Session category).

    3.  FIX Category Sections are used to generate the pre-trade, trade, post-trade and infrastructure FIXML schema files.

11. FIX datatypes are mapped to the closest XML Schema datatype whenever possible, thus making FIXML more compatible with standard XML toolsets.

12. The complex type Abstrace\_message\_t includes the attributes and elements of the StandardHeader component.
