FIXML Fields
============

FIXML fields are defined in the base and impl files:

-   Fields base file (fixml-fields-base-5-0-SP2.xsd)

-   Fields implementation file (fixml-fields-impl-5-0-SP2.xsd)

Fields base file
----------------

The fixml-fields-base-5-0-SP2.xsd file contains simple type definitions for all FIX application level fields and session level fields that are used as part of the FIXML header. All fields are defined as simple types. The simple type name is derived from the full FIX field name appended with a “\_t”. All fields with enumerations are defined as simple types. The enumeration simple type name is derived from the full FIX field name appended with the string “enum\_t”.

The following is an example of a field definition for the AvgPx(6) field:

&lt;xs:simpleType name="AvgPx\_t"&gt;

&lt;xs:annotation&gt;

&lt;xs:documentation&gt;Calculated average price of all fills on this order.

For Fixed Income trades AvgPx is always expressed as percent-of-par, regardless of the PriceType (423) of LastPx (31). I.e., AvgPx will contain an average of percent-of-par values (see LastParPx (669)) for issues traded in Yield, Spread or Discount.&lt;/xs:documentation&gt;

&lt;xs:appinfo&gt;

&lt;fm:Xref Protocol="FIX" name="AvgPx" ComponentType="Field" Tag="6" Type="Price" AbbrName="AvgPx"/&gt;

&lt;/xs:appinfo&gt;

&lt;/xs:annotation&gt;

&lt;xs:restriction base="Price"/&gt;

&lt;/xs:simpleType&gt;

The following is an example of the CommType(13) enumerated field:

&lt;xs:simpleType name="CommType\_enum\_t"&gt;

&lt;xs:annotation&gt;

&lt;xs:documentation&gt;Commission type&lt;/xs:documentation&gt;

&lt;xs:appinfo&gt;

&lt;fm:Xref Protocol="FIX" name="CommType" ComponentType="Field" Tag="13" Type="char" AbbrName="CommTyp"/&gt;

&lt;/xs:appinfo&gt;

&lt;xs:appinfo&gt;

&lt;fm:EnumDoc value="1"&gt;Per Unit (implying shares, par, currency, etc.)&lt;/fm:EnumDoc&gt;

&lt;fm:EnumDoc value="2"&gt;Percent&lt;/fm:EnumDoc&gt;

&lt;fm:EnumDoc value="3"&gt;Absolute (total monetary amount)&lt;/fm:EnumDoc&gt;

&lt;fm:EnumDoc value="4"&gt;Percentage waived - cash discount (for CIV buy orders)&lt;/fm:EnumDoc&gt;

&lt;fm:EnumDoc value="5"&gt;Percentage waived -= enhanced units (for CIV buy orders)&lt;/fm:EnumDoc&gt;

&lt;fm:EnumDoc value="6"&gt;Points per bond or contract (supply ContractMultiplier (231) in the &lt;Instrument&gt; component block if the object security is denominated in a size other than the industry default - 1000 par for bonds)&lt;/fm:EnumDoc&gt;

&lt;/xs:appinfo&gt;

&lt;/xs:annotation&gt;

&lt;xs:restriction base="char"&gt;

&lt;xs:enumeration value="1"/&gt;

&lt;xs:enumeration value="2"/&gt;

&lt;xs:enumeration value="3"/&gt;

&lt;xs:enumeration value="4"/&gt;

&lt;xs:enumeration value="5"/&gt;

&lt;xs:enumeration value="6"/&gt;

&lt;/xs:restriction&gt;

&lt;/xs:simpleType&gt;

Fields implementation file
--------------------------

In order to support extension and restriction of enumerations, there is a slightly different approach for use of the base and implementation file for these fields. The enumeration simple type is located in the base file and the standard field simple type referencing the enumeration is located in the implementation file. As shown above, the fixml-fields-base -5-0-SP2.xsd file defines each enumerated field as a simple type named fieldname\_enum\_t. This enumerated type is then used to restrict the corresponding field type in the fixml-fields-impl-5-0-SP2.xsd schema file named fieldname\_t. It is this fieldname\_t type that is referenced in subsequent schema files (fixml-components-5-0-SP2.xsd and the message category schema files). This approach is needed to provide a mechanism to extend enumerations. The fieldname\_t can be modified in the fixml-fields-impl file to include additional enumerations. The fieldname\_t can be restricted by redefining the fieldname\_enum\_t simple type within the fixml-fields-impl-5-0-SP2.xsd file.

The following is an example of the FIX standard CommType(13) field definition in the implementation file.

&lt;xs:simpleType name="CommType\_t"&gt;

&lt;xs:restriction base="CommType\_enum\_t"/&gt;

&lt;/xs:simpleType&gt;
