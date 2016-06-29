FIXML Root Element
==================

The FIXML root element is used to support versioning requirements and the ability to batch messages.

FIXML Versionin Attributes
--------------------------

The FIXML root element &lt;FIXML&gt; includes several optional attributes that can be used to identify the application and FIXML version details. The FIXML root element is defined in the fixml-components-base-5-0-SP2.xsd schema file. The table below illustrates the root level version attributes.

Table 1 FIXML Versioning Attributes

|           |                                                                      |                     |            |
|-----------|----------------------------------------------------------------------|---------------------|------------|
| Attribute | Description                                                          | Field(Tag)/datatype | Example    |
| v         | FIX Version                                                          | ApplVerID(1128)     | FIX.5.0SP2 |
| r         | FIX Version release date (Deprecated)                                | xs:string           |            |
| xv        | FIX Extension Pack number                                            | ApplExtID(1156)     | 192        |
| cv        | Custom functionality, support of which required bilateral agreement. | CstmApplVerID(1129) |            |
| xr        | FIX Extension release date (Deprecated)                              | xs:string           |            |
| s         | FIXML Schema Release                                                 | xs:date (Fixed)     | 2014-05-07 |

**Example:**

&lt;FIXML v="FIX.5.0SP2" xv="192" s="2014-05-07"&gt; … &lt;/FIXML&gt;

Batching FXIML messages
-----------------------

The FIXML root element &lt;FIXML&gt; supports the ability to include either a single or a batch of FIXML application messages. Batch capability is provided to support groups of messages, such as post trade confirms or position reports at the end of a trading session.

### Batching Structure

The entity relationship diagram below illustrates the message batching elements and design.

Figure 5 - FIXML Message Batching Entity Relationship Diagram

The figure below illustrates the high level FIXL structure for a single FIX message compared to a batch of FIX messages. For greater detail, refer to the detailed examples included later in this document.

| Single Message Usage | Batch Message Usage |
|----------------------|---------------------|
| &lt;FIXML&gt;        
 >                     
 > &lt;Order&gt;       
 >                     
 > &lt;Hdr/&gt;        
 >                     
 > &lt;/Order&gt;      
 >                     
 > &lt;/FIXML&gt;      | &lt;FIXML&gt;       
                        >                    
                        > &lt;Batch&gt;      
                        >                    
                        > &lt;Hdr/&gt;       
                        >                    
                        > &lt;Order&gt;      
                        >                    
                        > &lt;Hdr/&gt;       
                        >                    
                        > &lt;/Order&gt;     
                        >                    
                        > &lt;Order&gt;      
                        >                    
                        > &lt;Hdr/&gt;       
                        >                    
                        > &lt;/Order&gt;     
                        >                    
                        > &lt;/Batch&gt;     
                        >                    
                        > &lt;/FIXML&gt;     |

Figure 6 - Single versus Batch FIXML messages

### Batch Attributes

The capability to indicate several optional batch attributes was added in FIX 5.0 SP2 EP128. These additional batch attributes include:

-   BacthID(50000) @ID (String)

-   BatchProcessMode(50001) @ProcMode (int)

-   BatchTotalMessages(50002) @TotMsg (int)

@ID is a unique identifier for a batch of messages.

@ProcMode indicates the processing mode for a batch f messages.

> Valid values include:
>
> 0 – Incremental update (default if not specified)
>
> 1 – Snapshot (The batch of messages is a complete set)

@TotMsg indicates the total number of messages in the batch.

FIXML Single Message Example
----------------------------

This example is a New Order Single FIXML message sent individually.

&lt;FIXML v="FIX.5.0SP2" xv="192" s="2014-05-07" &gt;

&lt;Order ID="123456" Side="2" TxnTm="2001-09-11T09:30:47-05:00" Typ="2" Px="93.25" Acct="26522154"&gt;

&lt;Instrmt Sym="IBM" ID="459200101" Src="1"/&gt;

&lt;OrdQty Qty="1000"/&gt;

&lt;/Order&gt;

&lt;/FIXML&gt;

FIXML Batch Message Example
---------------------------

This example shows a batch of position reports.

Note that the header is provided for the entire batch of messages. The batch attribute @TotMsg is an optional batch attribute indicating the number of messages included in the batch.

&lt;FIXML v="FIX.5.0SP2" xv="192" s="2014-05-07"&gt;

&lt;Batch ID="11212" TotMsg="3"&gt;

&lt;Hdr Snt="2001-12-17T09:30:47-05:00" SID="OCC" TID="Firm"/&gt;

&lt;PosRpt RptID="541386431" Rslt="0" BizDt="2003-09-10" Acct="1" AcctTyp="1" SetPx="0.00" SetPxTyp="1" PriSetPx="0.00" ReqTyp="0" Ccy="USD"&gt;

&lt;Pty ID="OCC" R="21"/&gt;

&lt;Pty ID="99999" R="4"/&gt;

&lt;Pty ID="C" R="38"&gt;

&lt;Sub ID="ZZZ" Typ="2"/&gt;

&lt;/Pty&gt;

&lt;Instrmt Sym="AOL" ID="KW" Src="J" CFI="OCASPS" MMY="20031122" MatDt="2003-11-22" StrkPx="47.50" StrkCcy="USD" Mult="100"/&gt;

&lt;Qty Typ="SOD" Long="35" Short="0"/&gt;

&lt;Qty Typ="FIN" Long="20" Short="10"/&gt;

&lt;Qty Typ="IAS" Long="10"/&gt;

&lt;Amt Typ="FMTM" Amt="0.00"/&gt;

&lt;/PosRpt&gt;

&lt;PosRpt RptID="541386536" Rslt="0" BizDt="2003-09-10" Acct="1" AcctTyp="1" SetPx="0.00" SetPxTyp="1" PriSetPx="0.00" ReqTyp="0" Ccy="USD"&gt;

&lt;Pty ID="OCC" R="21"/&gt;

&lt;Pty ID="99999" R="4"/&gt;

&lt;Pty ID="C" R="38"&gt;

&lt;Sub ID="ZZZ" Typ="2"/&gt;

&lt;/Pty&gt;

&lt;Instrmt Sym="AOL" ID="KW" Src="J" CFI="OCASPS" MMY="20031122" MatDt="2003-11-22" StrkPx="47.50" StrkCcy="USD" Mult="100"/&gt;

&lt;Qty Typ="SOD" Long="35" Short="0"/&gt;

&lt;Qty Typ="FIN" Long="20" Short="10"/&gt;

&lt;Qty Typ="IAS" Long="10"/&gt;

&lt;Amt Typ="FMTM" Amt="0.00"/&gt;

&lt;/PosRpt&gt;

&lt;PosRpt RptID="541386678" Rslt="0" BizDt="2003-09-10" Acct="1" AcctTyp="1" SetPx="0.00" SetPxTyp="1" PriSetPx="0.00" ReqTyp="0" Ccy="USD"&gt;

&lt;Pty ID="OCC" R="21"/&gt;

&lt;Pty ID="99999" R="4"/&gt;

&lt;Pty ID="C" R="38"&gt;

&lt;Sub ID="ZZZ" Typ="2"/&gt;

&lt;/Pty&gt;

&lt;Instrmt Sym="AOL" ID="KW" Src="J" CFI="OCASPS" MMY="20031122" MatDt="2003-11-22" StrkPx="47.50" StrkCcy="USD" Mult="100"/&gt;

&lt;Qty Typ="SOD" Long="35" Short="0"/&gt;

&lt;Qty Typ="FIN" Long="20" Short="10"/&gt;

&lt;Qty Typ="IAS" Long="10"/&gt;

&lt;Amt Typ="FMTM" Amt="0.00"/&gt;

&lt;/PosRpt&gt;

&lt;/Batch&gt;

&lt;/FIXML&gt;
