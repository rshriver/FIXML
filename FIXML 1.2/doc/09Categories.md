FIXML Categories 
=================

Each message category defined within the FIX specification has its own pair of schema files (a base and an implementation schema file). This provides a granular level of usage for applications only requiring access to one message category. The message category schema files contain the component and message definitions that belong to a specific message category defined within the FIX Protocol. Examples of message categories include: Indications, Market Data, Positions, Allocation, etc. A complete list of the category files for FIXML is provided in the FIXML Schema File Summary section.

Category base file
------------------

The category base schema file includes the standard FIX components and messages that are coded for the category. Category messages and components are defined following a similar pattern defined above for components. Messages will include an additional element for the abbreviated message name.

The following is an example of the New Order Single message from the fixml-order-base-5-0-SP2.xsd FIXML schema file:

&lt;xs:group name="NewOrderSingleElements"&gt;

&lt;xs:sequence&gt;

&lt;xs:element name="Pty" type="Parties\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="TgtPty" type="TargetParties\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="PreAll" type="PreAllocGrp\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="MtchgInst" type="MatchingInstructions\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="DsplyInstr" type="DisplayInstruction\_Block\_t" minOccurs="0"/&gt;

&lt;xs:element name="DisclsrInst" type="DisclosureInstructionGrp\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="TrdSes" type="TrdgSesGrp\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="Instrmt" type="Instrument\_Block\_t"/&gt;

&lt;xs:element name="FinDetls" type="FinancingDetails\_Block\_t" minOccurs="0"/&gt;

&lt;xs:element name="Undly" type="UndInstrmtGrp\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="Stip" type="Stipulations\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="OrdQty" type="OrderQtyData\_Block\_t"/&gt;

&lt;xs:element name="TrgrInstr" type="TriggeringInstruction\_Block\_t" minOccurs="0"/&gt;

&lt;xs:element name="SprdBnchmkCurve" type="SpreadOrBenchmarkCurveData\_Block\_t" minOccurs="0"/&gt;

&lt;xs:element name="Yield" type="YieldData\_Block\_t" minOccurs="0"/&gt;

&lt;xs:element name="Comm" type="CommissionData\_Block\_t" minOccurs="0"/&gt;

&lt;xs:element name="PegInstr" type="PegInstructions\_Block\_t" minOccurs="0"/&gt;

&lt;xs:element name="DiscInstr" type="DiscretionInstructions\_Block\_t" minOccurs="0"/&gt;

&lt;xs:element name="StrtPrmGrp" type="StrategyParametersGrp\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;xs:element name="TrdRegTS" type="TrdRegTimestamps\_Block\_t" minOccurs="0" maxOccurs="unbounded"/&gt;

&lt;/xs:sequence&gt;

&lt;/xs:group&gt;

&lt;xs:attributeGroup name="NewOrderSingleAttributes"&gt;

&lt;xs:attribute name="ID" type="ClOrdID\_t" use="required"/&gt;

&lt;xs:attribute name="OrdReqID" type="OrderRequestID\_t" use="optional"/&gt;

&lt;xs:attribute name="ID2" type="SecondaryClOrdID\_t" use="optional"/&gt;

&lt;xs:attribute name="LnkID" type="ClOrdLinkID\_t" use="optional"/&gt;

&lt;xs:attribute name="OrignDt" type="TradeOriginationDate\_t" use="optional"/&gt;

&lt;xs:attribute name="TrdDt" type="TradeDate\_t" use="optional"/&gt;

&lt;xs:attribute name="Acct" type="Account\_t" use="optional"/&gt;

&lt;xs:attribute name="AcctIDSrc" type="AcctIDSource\_t" use="optional"/&gt;

&lt;xs:attribute name="AcctTyp" type="AccountType\_t" use="optional"/&gt;

&lt;xs:attribute name="DayBkngInst" type="DayBookingInst\_t" use="optional"/&gt;

&lt;xs:attribute name="BkngUnit" type="BookingUnit\_t" use="optional"/&gt;

&lt;xs:attribute name="PreallocMeth" type="PreallocMethod\_t" use="optional"/&gt;

&lt;xs:attribute name="AllocID" type="AllocID\_t" use="optional"/&gt;

&lt;xs:attribute name="SettlTyp" type="SettlType\_t" use="optional"/&gt;

&lt;xs:attribute name="SettlDt" type="SettlDate\_t" use="optional"/&gt;

&lt;xs:attribute name="CshMgn" type="CashMargin\_t" use="optional"/&gt;

&lt;xs:attribute name="ClrFeeInd" type="ClearingFeeIndicator\_t" use="optional"/&gt;

&lt;xs:attribute name="HandlInst" type="HandlInst\_t" use="optional"/&gt;

&lt;xs:attribute name="ExecInst" type="ExecInst\_t" use="optional"/&gt;

&lt;xs:attribute name="AuctInst" type="AuctionInstruction\_t" use="optional"/&gt;

&lt;xs:attribute name="MinQty" type="MinQty\_t" use="optional"/&gt;

&lt;xs:attribute name="MinQtyMeth" type="MinQtyMethod\_t" use="optional"/&gt;

&lt;xs:attribute name="MtchInc" type="MatchIncrement\_t" use="optional"/&gt;

&lt;xs:attribute name="MxPxLvls" type="MaxPriceLevels\_t" use="optional"/&gt;

&lt;xs:attribute name="MaxFloor" type="MaxFloor\_t" use="optional"/&gt;

&lt;xs:attribute name="MktSegID" type="MarketSegmentID\_t" use="optional"/&gt;

&lt;xs:attribute name="ExDest" type="ExDestination\_t" use="optional"/&gt;

&lt;xs:attribute name="ExDestIDSrc" type="ExDestinationIDSource\_t" use="optional"/&gt;

&lt;xs:attribute name="ProcCode" type="ProcessCode\_t" use="optional"/&gt;

&lt;xs:attribute name="PrevClsPx" type="PrevClosePx\_t" use="optional"/&gt;

&lt;xs:attribute name="Side" type="Side\_t" use="required"/&gt;

&lt;xs:attribute name="SMEInd" type="ShortMarkingExemptIndicator\_t" use="optional"/&gt;

&lt;xs:attribute name="ShrtSaleExmptnRsn" type="ShortSaleExemptionReason\_t" use="optional"/&gt;

&lt;xs:attribute name="LocReqd" type="LocateReqd\_t" use="optional"/&gt;

&lt;xs:attribute name="TxnTm" type="TransactTime\_t" use="required"/&gt;

&lt;xs:attribute name="QtyTyp" type="QtyType\_t" use="optional"/&gt;

&lt;xs:attribute name="Typ" type="OrdType\_t" use="required"/&gt;

&lt;xs:attribute name="PxTyp" type="PriceType\_t" use="optional"/&gt;

&lt;xs:attribute name="Px" type="Price\_t" use="optional"/&gt;

&lt;xs:attribute name="PxPrtScp" type="PriceProtectionScope\_t" use="optional"/&gt;

&lt;xs:attribute name="StopPx" type="StopPx\_t" use="optional"/&gt;

&lt;xs:attribute name="Ccy" type="Currency\_t" use="optional"/&gt;

&lt;xs:attribute name="TrdPxNegottnMeth" type="TradePriceNegotiationMethod\_t" use="optional"/&gt;

&lt;xs:attribute name="UpfrontPxTyp" type="UpfrontPriceType\_t" use="optional"/&gt;

&lt;xs:attribute name="UpfrontPx" type="UpfrontPrice\_t" use="optional"/&gt;

&lt;xs:attribute name="ComplianceID" type="ComplianceID\_t" use="optional"/&gt;

&lt;xs:attribute name="ComplianceTxt" type="ComplianceText\_t" use="optional"/&gt;

&lt;xs:attribute name="EncComplianceTxt" type="EncodedComplianceText\_t" use="optional"/&gt;

&lt;xs:attribute name="SolFlag" type="SolicitedFlag\_t" use="optional"/&gt;

&lt;xs:attribute name="IOIID" type="IOIID\_t" use="optional"/&gt;

&lt;xs:attribute name="QID" type="QuoteID\_t" use="optional"/&gt;

&lt;xs:attribute name="TmInForce" type="TimeInForce\_t" use="optional"/&gt;

&lt;xs:attribute name="EfctvTm" type="EffectiveTime\_t" use="optional"/&gt;

&lt;xs:attribute name="ExpireDt" type="ExpireDate\_t" use="optional"/&gt;

&lt;xs:attribute name="ExpireTm" type="ExpireTime\_t" use="optional"/&gt;

&lt;xs:attribute name="GTBkngInst" type="GTBookingInst\_t" use="optional"/&gt;

&lt;xs:attribute name="ExpsreDur" type="ExposureDuration\_t" use="optional"/&gt;

&lt;xs:attribute name="ExpsreDurUnit" type="ExposureDurationUnit\_t" use="optional"/&gt;

&lt;xs:attribute name="Cpcty" type="OrderCapacity\_t" use="optional"/&gt;

&lt;xs:attribute name="Rstctions" type="OrderRestrictions\_t" use="optional"/&gt;

&lt;xs:attribute name="TrdgCpcty" type="TradingCapacity\_t" use="optional"/&gt;

&lt;xs:attribute name="PrTrdAnon" type="PreTradeAnonymity\_t" use="optional"/&gt;

&lt;xs:attribute name="TrdPubInd" type="TradePublishIndicator\_t" use="optional"/&gt;

&lt;xs:attribute name="CustCpcty" type="CustOrderCapacity\_t" use="optional"/&gt;

&lt;xs:attribute name="ForexReq" type="ForexReq\_t" use="optional"/&gt;

&lt;xs:attribute name="SettlCcy" type="SettlCurrency\_t" use="optional"/&gt;

&lt;xs:attribute name="BkngTyp" type="BookingType\_t" use="optional"/&gt;

&lt;xs:attribute name="Txt" type="Text\_t" use="optional"/&gt;

&lt;xs:attribute name="SettlDt2" type="SettlDate2\_t" use="optional"/&gt;

&lt;xs:attribute name="Qty2" type="OrderQty2\_t" use="optional"/&gt;

&lt;xs:attribute name="Px2" type="Price2\_t" use="optional"/&gt;

&lt;xs:attribute name="ClrAcctTyp" type="ClearingAccountType\_t" use="optional"/&gt;

&lt;xs:attribute name="PosEfct" type="PositionEffect\_t" use="optional"/&gt;

&lt;xs:attribute name="Covered" type="CoveredOrUncovered\_t" use="optional"/&gt;

&lt;xs:attribute name="MaxShow" type="MaxShow\_t" use="optional"/&gt;

&lt;xs:attribute name="TgtStrategy" type="TargetStrategy\_t" use="optional"/&gt;

&lt;xs:attribute name="TgtStrategyParameters" type="TargetStrategyParameters\_t" use="optional"/&gt;

&lt;xs:attribute name="ParticipationRt" type="ParticipationRate\_t" use="optional"/&gt;

&lt;xs:attribute name="CxllationRights" type="CancellationRights\_t" use="optional"/&gt;

&lt;xs:attribute name="MnyLaunderingStat" type="MoneyLaunderingStatus\_t" use="optional"/&gt;

&lt;xs:attribute name="RegistID" type="RegistID\_t" use="optional"/&gt;

&lt;xs:attribute name="Designation" type="Designation\_t" use="optional"/&gt;

&lt;xs:attribute name="ManOrdInd" type="ManualOrderIndicator\_t" use="optional"/&gt;

&lt;xs:attribute name="CustDrctdOrd" type="CustDirectedOrder\_t" use="optional"/&gt;

&lt;xs:attribute name="RcvdDptID" type="ReceivedDeptID\_t" use="optional"/&gt;

&lt;xs:attribute name="CustOrdHdlInst" type="CustOrderHandlingInst\_t" use="optional"/&gt;

&lt;xs:attribute name="OrdHndlInstSrc" type="OrderHandlingInstSource\_t" use="optional"/&gt;

&lt;xs:attribute name="OrdOrigntn" type="OrderOrigination\_t" use="optional"/&gt;

&lt;xs:attribute name="OrigntngDeptID" type="OriginatingDeptID\_t" use="optional"/&gt;

&lt;xs:attribute name="RcvgDeptID" type="ReceivingDeptID\_t" use="optional"/&gt;

&lt;xs:attribute name="OwnerTyp" type="OwnerType\_t" use="optional"/&gt;

&lt;xs:attribute name="RefOrdID" type="RefOrderID\_t" use="optional"/&gt;

&lt;xs:attribute name="RefOrdIDSrc" type="RefOrderIDSource\_t" use="optional"/&gt;

&lt;xs:attribute name="ThrttlInst" type="ThrottleInst\_t" use="optional"/&gt;

&lt;xs:attribute name="RefClOrdID" type="RefClOrdID\_t" use="optional"/&gt;

&lt;xs:attribute name="AuctTyp" type="AuctionType\_t" use="optional"/&gt;

&lt;xs:attribute name="AuctPct" type="AuctionAllocationPct\_t" use="optional"/&gt;

&lt;/xs:attributeGroup&gt;

&lt;xs:complexType name="NewOrderSingle\_message\_t" final="\#all"&gt;

&lt;xs:annotation&gt;

&lt;xs:documentation xml:lang="en"&gt;NewOrderSingle can be found in Volume 4 of the

specification&lt;/xs:documentation&gt;

&lt;xs:appinfo&gt;

&lt;fm:Xref Protocol="FIX" name="NewOrderSingle" ComponentType="Message" MsgID="14" Section="Trade" Category="SingleGeneralOrderHandling"/&gt;

&lt;/xs:appinfo&gt;

&lt;/xs:annotation&gt;

&lt;xs:complexContent&gt;

&lt;xs:extension base="Abstract\_message\_t"&gt;

&lt;xs:sequence&gt;

&lt;xs:group ref="NewOrderSingleElements"/&gt;

&lt;/xs:sequence&gt;

&lt;xs:attributeGroup ref="NewOrderSingleAttributes"/&gt;

&lt;/xs:extension&gt;

&lt;/xs:complexContent&gt;

&lt;/xs:complexType&gt;

&lt;xs:element name="Order" type="NewOrderSingle\_message\_t" substitutionGroup="Message" final="\#all"/&gt;

Category implementation file
----------------------------

The category implementation file simply includes the category base file. The implementation file is where modifications (restrictions or extensions) would be made to the category components and messages.
