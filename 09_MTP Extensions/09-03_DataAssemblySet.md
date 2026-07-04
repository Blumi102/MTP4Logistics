## MTP Extension of the DataAssemblySet
This chapter specifies all identified extensions of the *DataAssemblySet* and integrates them into the existing MTP specification [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3).

### Übersicht
#### Extension of the IndicatorElements
According to Chapters~[Reportwerte](#sec:Reportwerte) and [Lea Hmi](#sec:LeaHmi), the two interface definitions *SUC StructView* and *SUC ArrayView* are required for value displays in LEA HMIs and for mapping report values on LEA services. According to Section~[Prozesswerte](#sec:Prozesswerte), *StructView* is also required for process-value outputs of structured data types. As shown in Figure~[Extension of the DataAssemblySet for Implementing Structured and Array-Based IndicatorElements](#fig:ErweiterungIndicatorElement), *SUC StructView* and *SUC ArrayView*, together with all other interface definitions for report values, are derived from the interface definition *SUC IndicatorElement* according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3) and organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangDataAssemblySetSchnittstellen). This extension, as a result of this dissertation, has already been adopted into the profile *ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0* of the MTP specification [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3).

![Extension of the DataAssemblySet for Implementing Structured and Array-Based IndicatorElements](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/IndicatorElement/Klassendiagramm.drawio.png)
*Extension of the DataAssemblySet for Implementing Structured and Array-Based IndicatorElements*

#### Extension of the OperationElements
According to Section~[Lea Hmi](#sec:LeaHmi), the new interface definitions *SUC StructMan*, *SUC StructManInt*, *SUC ArrayMan*, and *SUC ArrayManInt* are required for operator-driven value manipulation in LEA HMIs. As shown in Figure~[Extension of the DataAssemblySet for Implementing Structured and Array-Based OperationElements](#fig:ErweiterungOperationElement), *SUC StructMan* and *SUC ArrayMan*, together with all other interface definitions for value manipulation, are derived from the interface definition *SUC OperationElement* according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). *SUC StructManInt* is derived from *SUC StructMan*, and *SUC ArrayManInt* from *SUC ArrayMan*. All four interface definitions are organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangDataAssemblySetSchnittstellen). This extension, as a result of this dissertation, has already been adopted into the profile *ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0* of the MTP specification [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3).

![Extension of the DataAssemblySet for Implementing Structured and Array-Based OperationElements](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/OperationElement/Klassendiagramm.drawio.png)
*Extension of the DataAssemblySet for Implementing Structured and Array-Based OperationElements*

#### Extension of DINT-Based Interfaces with Time Formats
According to Section~[Schnittstelle Transportdienst](#subsec:SchnittstelleTransportdienst), report values in a time format are required for the timestamps of a transport service. For this purpose, *RC HasTimeFormat* is introduced. As shown in Figure~[Extension of the DataAssemblySet for Interpreting DINT Values in a Time Format](#fig:ErweiterungTimeFormat), this RC can be added as an SRC to all DINT-based interface definitions, in particular to *SUC DIntView*, *SUC DIntMan*, *SUC DIntServParam*, and *SUC DIntProcessValueIn*. *RC HasTimeFormat* is organized in the newly introduced *RCL MTPDataAssemblyRCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangDataAssemblySetSchnittstellen). 

*RC HasTimeFormat* uses a new *AT TimeFormatAttributeType* to specify the time format in which a DINT value is to be interpreted. As shown in Figure~[Extension of the DataAssemblySet for Interpreting DINT Values in a Time Format](#fig:ErweiterungTimeFormat), this AT is organized in *ATL MTPDataAssemblyATLib*. The detailed specification is provided in Appendix~[Model Definitions](#subsec:AnhangDataAssemblySetModelle).

These extensions are assigned to the newly introduced profile *ModuleTypePackage:DataAssemblySet.Time V2.0.0*.[^1]

![Extension of the DataAssemblySet for Interpreting DINT Values in a Time Format](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Zeitformate/Klassendiagramm.drawio.png)
*Extension of the DataAssemblySet for Interpreting DINT Values in a Time Format*

### Interface Definitions
#### Specification of the System Unit Class StructView
*SUC StructView* (Table~[Data Assembly Suc Struct View](#tab:DataAssemblySucStructView)) is used by an LOL to display an LEA variable of a user-defined structured data type.

<a id="tab:DataAssemblySucStructView"></a>
**Table: Interface Definition of *SUC StructView***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>StructView</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="5">System Unit Class (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="5">generic interface for displaying a value of structured data following the rules of modelling complex data types</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/IndicatorElement/StructView</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/IndicatorElement</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="4">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="4">-</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Attributes</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Access</th>
		<th>Type</th>
		<th>Description</th>
		<th>Attribute-Type Reference</th>
		<th>Base Function</th>
	</tr>
	<tr>
		<td>V</td>
		<td>LOL &lt;- LEA</td>
		<td>{VType}</td>
		<td>Value</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>VType</td>
		<td>MTP</td>
		<td>&lt;empty&gt;</td>
		<td>Type Definition of the Value</td>
		<td>{AT of StructuredDataType}</td>
		<td>Complex-Type</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="6">-</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="5">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="5">(no further constraints given)</td>
	</tr>
</table>

The distinctive feature of this interface definition is the use of a user-defined structured data type. Figure~[Modeling of a User-Defined Data Type](#fig:CustomDatatypeModellierung) shows how such a data type can be modeled. For this purpose, the rules for modeling complex data types from [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51) are applied.

%TODO @Format: Bild schärfer machen!
![Modeling of a User-Defined Data Type](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Parameter/Modelling_Custom_Datatype.png)
*Modeling of a User-Defined Data Type*

The complex data type used must be derived from *AT StructuredDataType* defined in [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51). When this interface is used, a user-defined ATL must be created, here: CompanyAAttributeLib. Within this ATL, the structured data type that is later to be used in the IE of *SUC StructView* must be specified. By assigning this user-defined AT to the attribute *VType* of *SUC StructView*, the structured data type used is defined. This data type is then expected in the variable *V*. 

**Note:** If the *StructView* interface is used as a report value, it can be "frozen" by the variable *ReportValueFreeze* at the *ServiceControl* interface according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). Optionally, it can be extended by a *MissedValue* variable by assigning *RC MissedValueFlag*. 

#### Specification of the System Unit Class ArrayView
*SUC ArrayView* (Table~[Data Assembly Suc Array View](#tab:DataAssemblySucArrayView)) is used by the LOL to display the value at a specific position of an array located in an LEA.

<a id="tab:DataAssemblySucArrayView"></a>
**Table: Interface Definition of *SUC ArrayView***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>ArrayView</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">generic interface for displaying a value at a specific position of an array located in a PEA by a POL</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/IndicatorElement/ArrayView</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/IndicatorElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>OSLevel</td><td>LOL -> LEA</td><td>BYTE</td><td>OSLevel variable</td><td>-</td><td>OSLevel</td></tr>
	<tr><td>IndexSel</td><td>LOL -> LEA</td><td>DINT</td><td>Index Select Value</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexMin</td><td>LOL <- LEA</td><td>DINT</td><td>Low Limit of the Index</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexMax</td><td>LOL <- LEA</td><td>DINT</td><td>High Limit of the Index</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexCur</td><td>LOL <- LEA</td><td>DINT</td><td>Current Index Value</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>V</td><td>LOL <- LEA</td><td>{VType}</td><td>Output Value</td><td>-</td><td>-</td></tr>
	<tr><td>VType</td><td>MTP</td><td><sup>a)</sup></td><td>Type Definition of the Values</td><td>{AT derived from BaseData-Type}</td><td>Complex-Type</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6"><sup>a)</sup> Type shall be &lt;empty&gt; in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

The challenge of this interface definition is that it must access an array inside the LEA that may have an arbitrary length. In common automation solutions, this is often impossible or possible only under certain conditions because of predefined types. Therefore, a multiplexing mechanism is used that enables access to an array of arbitrary length via a structurally static interface. 

By means of the *OSLevel* variable, it can be defined according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3) whether the interface is currently operated by the LOL or locally at the LEA. The variable *IndexSel* selects the array position to be displayed, similar to a pointer. The variables *IndexMin* and *IndexMax* specify the lower and upper limits of the array. The variable *IndexCur* specifies the currently selected index. The value of the array at this position is displayed in *V*. 

*VType* defines the data type shared by all array elements. This may be a primitive data type or a user-defined structured data type according to the description of *SUC StructView*.

**Note 1:** If the *ArrayView* interface is used as a report value, it can be "frozen" by the variable *ReportValueFreeze* at the *ServiceControl* interface according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). In this case, the entire array must be frozen, not only the currently selected value. Individual frozen values of the array can then be displayed by selecting the indices. Optionally, the *ArrayView* interface can be extended by a *MissedValue* variable by assigning *RC MissedValueFlag*. 

**Note 2:** If the *ArrayView* interface is used as a report value and several or all values of an array are to be read for documentation purposes, several or all indices between *IndexMin* and *IndexMax* must be entered successively by the LOL at the *ArrayView* interface. The values of the individual array elements can then be stored one after another. This must also work in the frozen state.

#### Specification of the System Unit Class StructMan
*SUC StructMan* (Table~[Data Assembly Suc Struct Man](#tab:DataAssemblySucStructMan)) is used by the LOL to manipulate an LEA variable of a user-defined structured data type.

<a id="tab:DataAssemblySucStructMan"></a>
**Table: Interface Definition of *SUC StructMan***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>StructMan</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">generic interface for manipulating a value of structured data type following the rules of modelling complex data types</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OperationElement/StructMan</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OperationElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>VOut</td><td>LOL <- LEA</td><td>{VType}</td><td>Value Output</td><td>-</td><td>-</td></tr>
	<tr><td>VMan</td><td>LOL -> LEA</td><td>{VType}</td><td>Manual Value</td><td>-</td><td>-</td></tr>
	<tr><td>VRbk</td><td>LOL <- LEA</td><td>{VType}</td><td>Readback Value</td><td>-</td><td>Readback</td></tr>
	<tr><td>VFbk</td><td>LOL <- LEA</td><td>{VType}</td><td>Feedback</td><td>-</td><td>Feedback</td></tr>
	<tr><td>VType</td><td>MTP</td><td>&lt;empty&gt;</td><td>Type Definition of the Value</td><td>{AT of StructuredDataType}</td><td>Complex-Type</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

*VMan* is used to enter the desired value of the variable. Analogous to the concept described in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3), *VRbk* is used to verify the communication between an LOL and the *StructMan* interface within an LEA and indicates the raw value communicated to the LEA. *VOut* indicates the value passed to a further LEA-internal block, possibly with applied constraints. The variable *VFbk* is used to display the current value of the structure influenced by the *StructMan* interface. 

The distinctive feature of this interface definition is the use of a user-defined structured data type. The modeling and use of such a type have already been described in connection with *SUC StructView* and are applied in the same way for *SUC StructMan*. This data type is then expected behind the variables *VOut*, *VMan*, *VRbk*, and *VFbk*. 

#### Specification of the System Unit Class StructManInt
*SUC StructManInt* (Table~[Data Assembly Suc Struct Man Int](#tab:DataAssemblySucStructManInt)) is used to manipulate an LEA variable of a user-defined structured data type within the LEA or by the LOL.

<a id="tab:DataAssemblySucStructManInt"></a>
**Table: Interface Definition of *SUC StructManInt***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>StructManInt</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">generic interface for manipulating a value of structured data type following the rules of modelling complex data types by the LOL or from inside the LEA</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OperationElement/StructMan/StructManInt</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OperationElement/StructMan</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>WQC</td><td>LOL <- LEA</td><td>BYTE</td><td>Worst Quality Code variable</td><td>-</td><td>WQC</td></tr>
	<tr><td><em>VMan <sup>a)</sup></em></td><td><em>LOL -> LEA</em></td><td><em>{VType}</em></td><td><em>(relevant, if SrcManAct is true, see SourceMode) Manual Value</em></td><td><em>-</em></td><td><em>-</em></td></tr>
	<tr><td>VInt</td><td>LOL <- LEA</td><td>{VType}</td><td>(relevant, if SrcIntAct is true, see SourceMode) Internal Value</td><td>-</td><td>-</td></tr>
	<tr><td>SrcChannel</td><td>LOL <- LEA</td><td>BOOL</td><td>SourceMode channel; 0: operator (*Op) shall be used; 1: automatic (*Aut) shall be used</td><td>-</td><td>SourceMode</td></tr>
	<tr><td>SrcManAut</td><td>LOL <- LEA</td><td>BOOL</td><td>Request SourceMode to Manual by automatic (if SrcChannel is true); 1: request manual; 0: no operation</td><td>-</td><td>SourceMode</td></tr>
	<tr><td>SrcIntAut</td><td>LOL <- LEA</td><td>BOOL</td><td>Request SourceMode to Internal by automatic (if SrcChannel is true); 1: request internal; 0: no operation</td><td>-</td><td>SourceMode</td></tr>
	<tr><td>SrcIntOp</td><td>LOL -> LEA</td><td>BOOL</td><td>Request SourceMode to Internal by operator (if SrcChannel is false); 1: request internal; 0: no operation</td><td>-</td><td>SourceMode</td></tr>
	<tr><td>SrcManOp</td><td>LOL -> LEA</td><td>BOOL</td><td>Request SourceMode to Manual by operator (if SrcChannel is false); 1: request manual; 0: no operation</td><td>-</td><td>SourceMode</td></tr>
	<tr><td>SrcIntAct</td><td>LOL <- LEA</td><td>BOOL</td><td>1: internal mode active</td><td>-</td><td>SourceMode</td></tr>
	<tr><td>SrcManAct</td><td>LOL <- LEA</td><td>BOOL</td><td>1: manual mode active</td><td>-</td><td>SourceMode</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6"><sup>a)</sup> VMan is inherited from the StructMan interface. However, its meaning changes slightly in this case since it is only used when the SourceMode is set to manual.</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

The *StructManInt* interface extends the *StructMan* interface by internal value specification and a *SourceMode* according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). If the internal access channel is selected, an internal LEA value is used instead of the external value specification. Otherwise, the function of this interface is identical to that of the *StructMan* interface.

#### Specification of the System Unit Class ArrayMan
*SUC ArrayMan* (Table~[Data Assembly Suc Array Man](#tab:DataAssemblySucArrayMan)) is used by the LOL to manipulate a value at a specific position of an array located in an LEA.

<a id="tab:DataAssemblySucArrayMan"></a>
**Table: Interface Definition of *SUC ArrayMan***
<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>ArrayMan</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">generic interface for the POL to manipulate a value at a specific position of an array located in a LEA</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OperationElement/ArrayMan</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OperationElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>IndexSel</td><td>LOL -> LEA</td><td>DINT</td><td>Index Select Value</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexMin</td><td>LOL <- LEA</td><td>DINT</td><td>Low Limit of the Index</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexMax</td><td>LOL <- LEA</td><td>DINT</td><td>High Limit of the Index</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexCur</td><td>LOL <- LEA</td><td>DINT</td><td>Current Index Value</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>VMan</td><td>LOL -> LEA</td><td>{VType}</td><td>Manual Value</td><td>-</td><td>-</td></tr>
	<tr><td>VRbk</td><td>LOL <- LEA</td><td>{VType}</td><td>Readback Value</td><td>-</td><td>Readback</td></tr>
	<tr><td>VFbk</td><td>LOL <- LEA</td><td>{VType}</td><td>Feedback</td><td>-</td><td>Feedback</td></tr>
	<tr><td>VOut</td><td>LOL <- LEA</td><td>{VType}</td><td>Value Output</td><td>-</td><td>-</td></tr>
	<tr><td>VType</td><td>MTP</td><td><sup>a)</sup></td><td>Type Definition of the Values</td><td>{AT derived from BaseData-Type}</td><td>Complex-Type</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6"><sup>a)</sup> Type shall be &lt;empty&gt; in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

As already described for the *ArrayView* interface, the challenge of this interface lies in accessing an array within an LEA that may have an arbitrary length. As described in the context of *SUC ArrayView*, access to this array is also index-based in the case of the *ArrayMan* interface.

The array position to be modified is selected via the variable *IndexSel*. The variables *IndexMin* and *IndexMax* specify the lower and upper limits of the array. The variable *IndexCur* specifies the currently selected index of the variable to be manipulated. The variable *VMan* is used to enter the desired value for the variable to be manipulated. Analogous to the concept specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3), *VRbk* is used to verify the communication between an LOL and the *ArrayMan* interface within an LEA and indicates the raw value of the variable communicated to the LEA. When a new index is selected, the variables *VMan* and *VRbk* are set to the value at the selected position in the array. *VOut* indicates the value passed to a further LEA-internal block, possibly with limitations. The variable *VFbk* is used to display the current value of the structure affected by the *ArrayMan* interface. *VType* defines the data type shared by all array elements. This may be a primitive data type or a user-defined structured data type.

#### Specification of the Role Class HasTimeFormat
*RC HasTimeFormat* (Table~[Data Assembly Rc Has Time Format](#tab:DataAssemblyRcHasTimeFormat)) indicates that a DINT-based interface is to be interpreted in a time format. This RC can be assigned as an SRC to the interface definitions *SUC DIntView*, *SUC DIntMan*, *SUC DIntServParam*, and *SUC DIntProcessValueIn*. *RC HasTimeFormat* provides different formats for interpreting DINT values as time values, encoded in the variable *TimeFormat*. The meaning of the values of this variable is shown in Table~[Zeitformate](#tab:Zeitformate).

% Schnittstellendefinition RC HasTimeFormat
<a id="tab:DataAssemblyRcHasTimeFormat"></a>
**Table: Interface Definition of *RC HasTimeFormat***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>HasTimeFormat</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="5">Role Class (RC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="5">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="5">Role Class to assign a time format interpretation to a DINT-based interface</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblyRCLib/HasTimeFormat</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:DataAssemblySet.Time V2.0.0</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="4">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="4">-</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Attributes</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Access</th>
		<th>Type</th>
		<th>Description</th>
		<th>Attribute-Type Reference</th>
		<th>Base Function</th>
	</tr>
	<tr>
		<td>TimeFormat</td>
		<td>LOL &lt;- LEA</td>
		<td>BYTE</td>
		<td>Time format as defined in Table~[Zeitformate](#tab:Zeitformate)</td>
		<td>TimeFormat-Attribute-Type</td>
		<td>-</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="6">-</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Annotations</th>
		<td colspan="5">IE of SUC DIntView as SRC<br>IE of SUC DIntMan as SRC<br>IE of SUC DIntServParam as SRC<br>IE of SUC DIntProcessValueIn as SRC</td>
	</tr>
</table>

% Zeitformate
<a id="tab:Zeitformate"></a>
**Table: Encoding of Time Formats**

<table>
	<tr>
		<th>ID</th>
		<th>Name</th>
		<th>Beschreibung</th>
	</tr>
	<tr>
		<td>0</td>
		<td>None</td>
		<td>kein Format</td>
	</tr>
	<tr>
		<td>1</td>
		<td>TIME</td>
		<td>DINT-Wert gibt eine Zeitspanne in Millisekunden (ms) an</td>
	</tr>
	<tr>
		<td>2</td>
		<td>TIME_OF_DAY (TOD)</td>
		<td>DINT-Wert gibt die Tageszeit in Millisekunden seit Mitternacht an</td>
	</tr>
	<tr>
		<td>3</td>
		<td>DATE</td>
		<td>DINT-Wert gibt das Datum als Anzahl der Tage seit dem 01.01.1990 an</td>
	</tr>
</table>

#### Extension of the System Unit Class DIntView
*SUC DIntView* (Table~[Data Assembly Suc D Int View](#tab:DataAssemblySucDIntView)) is used to display DINT values of an LEA. This interface definition is already specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3) and is extended in this dissertation by the capability to annotate *RC HasTimeFormat* as an SRC.[^2]

% Schnittstellendefinition SUC DIntView
<a id="tab:DataAssemblySucDIntView"></a>
**Table: Interface Definition of *SUC DIntView***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>DIntView</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="5">System Unit Class (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="5">class used to display a double integer value of the LEA</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/IndicatorElement/DIntView</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/IndicatorElement</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">[0..1] MTPTextRCLib/HasTextReference/HasEnumDefinition (SRC)<br>[0..1] MTPDataAssemblyRCLib/HasTimeFormat (SRC)</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:DataAssemblySet.Time V2.0.0</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="4">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="4">-</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Attributes</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Access</th>
		<th>Type</th>
		<th>Description</th>
		<th>Attribute-Type Reference</th>
		<th>Base Function</th>
	</tr>
	<tr>
		<td>V</td>
		<td>LOL &lt;- LEA</td>
		<td>DINT</td>
		<td>Value</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>VSclMin</td>
		<td>LOL &lt;- LEA</td>
		<td>DINT</td>
		<td>Value Scale Low Limit</td>
		<td>-</td>
		<td>Scale Settings</td>
	</tr>
	<tr>
		<td>VSclMax</td>
		<td>LOL &lt;- LEA</td>
		<td>DINT</td>
		<td>Value Scale High Limit</td>
		<td>-</td>
		<td>Scale Settings</td>
	</tr>
	<tr>
		<td>VUnit</td>
		<td>LOL &lt;- LEA</td>
		<td>INT</td>
		<td>Value Unit</td>
		<td>-</td>
		<td>Unit Settings</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="6">-</td>
	</tr>
	<tr>
		<td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="5">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="5">(no further constraints given)</td>
	</tr>
</table>

### Model Definitions
#### Specification of the Attribute Type TimeFormatAttributeType
*AT TimeFormatAttributeType* (Table~[At Time Format Attribute Type](#tab:AtTimeFormatAttributeType)) defines the format for interpreting DINT values as time values. This AT is derived from *AT StaticValueAttributeType*.

% Modelldefinition AT TimeFormatAttributeType
<a id="tab:AtTimeFormatAttributeType"></a>
**Table: Model Definition of *AT TimeFormatAttributeType***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>TimeFormatAttributeType</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">Attribute Type (AT)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">attribute type for time format information</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPDataAssemblyATLib/TimeFormatAttributeType</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPATLib/StaticValueAttributeType</td>
	</tr>
	<tr>
		<th>Data Type</th>
		<td colspan="3">BYTE</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:DataAssemblySet.Time V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Attributes</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th>Description</th>
		<th>AttributeType Reference</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="4">-</td>
	</tr>
</table>



[^1]: It is recommended to incorporate *RC HasTimeFormat* and the associated *AT TimeFormatAttributeType* into the base profile *ModuleTypePackage:DataAssemblySet.Base* in the future.
[^2]: Since only the extension of *SUC DIntView* is used in this dissertation, only this case is described here. *SUC DIntMan*, *SUC DIntServParam*, and *SUC DIntProcessValueIn* must be extended in the same way by assigning *RC HasTimeFormat*.
