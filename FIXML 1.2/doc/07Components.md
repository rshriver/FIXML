FIXML Components
================

Component FIXML schema files are used to define the Common category reusable components in the FIX application standard. There are two Common components files

-   fixml-components-base-5-0-SP2.xsd – components base file

-   fixml-components-impl-5-0-SP2.xsd – components implementation file

Components base file 
---------------------

The fixml-components-base-5-0-SP2.xsd file contains the definitions for all FIX Common category components. The FIXML root element, FIXML headers, the batch element, and the abstract message type are also defined within this file.

Components (and messages) are defined using element groups and attribute groups. The advantage of these groups is that you can redefine the groups (using either restriction or extension) to change the overall structure of the component (or message).

These groups are defined for each component.

|                           |                                                                                             |
|---------------------------|---------------------------------------------------------------------------------------------|
| *componentName*Elements   | A group that contains a list of elements contained in the component.                        |
| *componentName*Attributes | An attribute group that contains a list of Attributes contained in the component.           |
| *componentName*\_Block\_t | Defines the component with the attributes of the attribute group and the group of elements. |

The Parties Component block is shown below. Notice the overall definition pattern. This pattern is followed for all component blocks and message definitions.

&lt;xs:group name="PartiesElements"&gt;

&lt;xs:sequence&gt;

&lt;xs:element name="Sub" type="PtysSubGrp\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;/xs:sequence&gt;

&lt;/xs:group&gt;

&lt;xs:attributeGroup name="PartiesAttributes"&gt;

&lt;xs:attribute name="ID" type="PartyID\_t" use="optional"/&gt;

&lt;xs:attribute name="Src" type="PartyIDSource\_t" use="optional"/&gt;

&lt;xs:attribute name="R" type="PartyRole\_t" use="optional"/&gt;

&lt;xs:attribute name="Qual" type="PartyRoleQualifier\_t" use="optional"/&gt;

&lt;/xs:attributeGroup&gt;

&lt;xs:complexType name="Parties\_Block\_t"&gt;

&lt;xs:annotation&gt;

&lt;xs:appinfo&gt;

&lt;fm:Xref Protocol="FIX" name="Parties" ComponentType="BlockRepeating" Category="Common"/&gt;

&lt;/xs:appinfo&gt;

&lt;/xs:annotation&gt;

&lt;xs:sequence&gt;

&lt;xs:group ref="PartiesElements"/&gt;

&lt;/xs:sequence&gt;

&lt;xs:attributeGroup ref="PartiesAttributes"/&gt;

&lt;/xs:complexType&gt;

Components implementation file
------------------------------

The fixml-components-impl-5-0-SP2.xsd file simply includes the components-base file. This is the file where modifications (restrictions or extensions) would be made to Common components (components not coded to a specific Category) used in the FIX protocol.
