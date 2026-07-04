## MTP Extension of the ProcessValueSet {#sec:AnhangProcessValueSet}
This chapter specifies all identified extensions of the *ProcessValueSet* and integrates them into the existing MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

### Übersicht {#subsec:AnhangProcessValueSetUebersicht}
#### Extension of the ProcessValueInputs
According to Section~[Prozesswerte](#sec:Prozesswerte), the interface definitions *SUC StructProcessValueIn* and *SUC ArrayProcessValueIn* are intended to specify process-value inputs for structured data types and array data types. As shown in Figure~[Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Inputs](#fig:ErweiterungProcessValueInputs), *SUC StructProcessValueIn* and *SUC ArrayProcessValueIn*, together with all other interface definitions for process-value inputs, are derived from the interface definition *SUC InputElement* according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) and organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangProcessValueSetSchnittstellen). This extension, as a result of this dissertation, has already been adopted into the profile *ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0* of the MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

![Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Inputs](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Prozesswerte/Prozesswerteingänge/Klassendiagramm.drawio.png)
*Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Inputs* {#fig:ErweiterungProcessValueInputs}

#### Extension of the ProcessValueOutputs
According to Section~[Prozesswerte](#sec:Prozesswerte), interface definitions for process-value outputs of structured data types and array data types are to be specified. For process-value outputs of structured data types, the associated *IndicatorElement*, i.e. *SUC StructView*, can be used as for all other MTP data types according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). For array-based process-value outputs, a separate interface definition *SUC ArrayProcessValueOut* is provided because, unlike *SUC ArrayView*, it does not require an *OSLevel* variable for access control. An *ArrayProcessValueOut* interface is always accessed by another LEA and not by an operator or LOL. Following the principles of the MTP concept, *SUC ArrayProcessValueOut* is derived from an abstract *SUC OutputElement*. *SUC OutputElement*, in turn, is derived from *SUC DataAssembly* specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). The newly introduced interface definitions are shown in Figure~[Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Outputs](#fig:ErweiterungProcessValueOutputs) and organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangProcessValueSetSchnittstellen). This extension, as a result of this dissertation, has already been adopted into the profile *ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0* of the MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

![Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Outputs](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Prozesswerte/Prozesswertausgänge/Klassendiagramm.drawio.png)
*Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Outputs* {#fig:ErweiterungProcessValueOutputs}

### Interface Definitions {#subsec:AnhangProcessValueSetSchnittstellen}
#### Specification of the System Unit Class StructProcessValueIn
*SUC StructProcessValueIn* (Table~[Data Assembly Suc Struct Process Value In](#tab:DataAssemblySucStructProcessValueIn)) is used by an LEA to access the value of a variable with a structured data type from another LEA.

% Schnittstellendefinition SUC StructProcessValueIn
<a id="tab:DataAssemblySucStructProcessValueIn"></a>
**Table: Interface Definition of *SUC StructProcessValueIn***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>StructProcessValueIn</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">generic interface for accessing a value of structured data type from another LEA</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/InputElement/StructProcess-ValueIn</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/InputElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>V</td><td>LOL -> LEA</td><td>{VType}</td><td>Value</td><td>-</td><td>-</td></tr>
	<tr><td>VType</td><td>MTP</td><td>&lt;empty&gt;</td><td>Type Definition of the Value</td><td>{AT of Structured-DataType}</td><td>Complex-Type</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

The required value is transferred in the variable *V* according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). The distinctive feature of this interface definition is the use of a user-defined structured data type. The modeling and use of such a type have already been described in connection with *SUC StructView* and are applied in the same way for *SUC StructProcessValueIn*. This data type is then expected behind the variable *V*. 

#### Specification of the System Unit Class ArrayProcessValueIn
*SUC ArrayProcessValueIn* (Table~[Data Assembly Suc Array Process Value In](#tab:DataAssemblySucArrayProcessValueIn)) is used by an LEA to access a value at a specific position of an array in another LEA.

% Schnittstellendefinition SUC ArrayProcessValueIn
<a id="tab:DataAssemblySucArrayProcessValueIn"></a>
**Table: Interface Definition of *SUC ArrayProcessValueIn***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>ArrayProcessValueIn</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">generic interface for accessing a value of array data type from another PEA</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/InputElement/ArrayProcess-ValueIn</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/InputElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>IndexSel</td><td>LOL <- LEA</td><td>DINT</td><td>Index Value</td><td>-</td><td>Multiplexing for Process Values</td></tr>
	<tr><td>IndexMin</td><td>LOL -> LEA</td><td>DINT</td><td>Low Limit of the Index</td><td>-</td><td>Multiplexing for Process Values</td></tr>
	<tr><td>IndexMax</td><td>LOL -> LEA</td><td>DINT</td><td>High Limit of the Index</td><td>-</td><td>Multiplexing for Process Values</td></tr>
	<tr><td>IndexCur</td><td>LOL -> LEA</td><td>DINT</td><td>Current Index Value</td><td>-</td><td>Multiplexing for Process Values</td></tr>
	<tr><td>V</td><td>LOL -> LEA</td><td>{VType}</td><td>Output Value</td><td>-</td><td>-</td></tr>
	<tr><td>VType</td><td>MTP</td><td>a)</td><td>Type Definition of the Values</td><td>{AT of BaseDataType}</td><td>Complex-Type</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6"><sup>a)</sup> Type shall be &lt;empty&gt; in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

Ähnlich wie bei der *SUC ArrayView* besteht die Herausforderung bei dieser Schnittstelle darin, auf ein Array innerhalb einer LEA zuzugreifen, das eine beliebige Länge haben kann. Wie bei der *SUC ArrayView* soll der Zugriff auf dieses Array auch im Falle der *SUC ArrayProcessValueIn* indexbasiert erfolgen.

The array position to be displayed is selected via the variable *IndexSel*. The variables *IndexMin* and *IndexMax* specify the lower and upper limits of the array. The variable *IndexCur* specifies the currently selected index, and the value of the array at this position is displayed in *V*. *VType* defines the data type shared by all array elements. This may be a primitive data type or a structured data type.

**Note:** This interface definition differs from all other interfaces derived from the *InputElement* interface definition because it also includes information flows from the LEA to the LOL. This had not previously been envisaged.

#### Specification of the System Unit Class OutputElement
*SUC OutputElement* (Table~[Data Assembly Suc Output Element](#tab:DataAssemblySucOutputElement)) is an abstract interface from which specific process-value outputs of different data types can be derived. The interface definition itself serves only an organizational purpose and provides a variable for transmitting a *Worst Quality Code (WQC)*.

% Schnittstellendefinition SUC OutputElement
<a id="tab:DataAssemblySucOutputElement"></a>
**Table: Interface Definition of *SUC OutputElement***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>OutputElement</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">abstract</td></tr>
	<tr><th>Description</th><td colspan="5">abstract interface from which specific process value outputs can be derived</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OutputElement</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>WQC</td><td>LOL <- LEA</td><td>BYTE</td><td>Worst Quality Code variable</td><td>-</td><td>WQC</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

**Note:** For greater clarity in modeling and with regard to possible future developments, MTP standardization should consider explicitly modeling *ProcessValueOutputs* of all MTP data types, including structured data types, and also deriving them from the newly specified *OutputElement*.

#### Specification of the System Unit Class ArrayProcessValueOut
*SUC ArrayProcessValueOut* (Table~[Data Assembly Suc Array Process Value Out](#tab:DataAssemblySucArrayProcessValueOut)) is used by an LEA to provide the values of an LEA-internal array to another LEA.

% Schnittstellendefinition SUC ArrayProcessValueOut
<a id="tab:DataAssemblySucArrayProcessValueOut"></a>
**Table: Interface Definition of *SUC ArrayProcessValueOut***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>ArrayProcessValueOut</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">generic interface for making available a value of array data type to another LEA</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OutputElement/ArrayProcessValueOut</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/OutputElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>IndexSel</td><td>LOL -> LEA</td><td>DINT</td><td>Index Value</td><td>-</td><td>Multiplexing for Process Values</td></tr>
	<tr><td>IndexMin</td><td>LOL <- LEA</td><td>DINT</td><td>Low Limit of the Index</td><td>-</td><td>Multiplexing for Process Values</td></tr>
	<tr><td>IndexMax</td><td>LOL <- LEA</td><td>DINT</td><td>High Limit of the Index</td><td>-</td><td>Multiplexing for Process Values</td></tr>
	<tr><td>IndexCur</td><td>LOL <- LEA</td><td>DINT</td><td>Current Index Value</td><td>-</td><td>Multiplexing for Process Values</td></tr>
	<tr><td>V</td><td>LOL <- LEA</td><td>{VType}</td><td>Output Value</td><td>-</td><td>-</td></tr>
	<tr><td>VType</td><td>MTP</td><td>a)</td><td>Type Definition of the Values</td><td>{AT of BaseDataType}</td><td>Complex-Type</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6"><sup>a)</sup> Type shall be &lt;empty&gt; in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

The interface definition *SUC ArrayProcessValueOut* corresponds to the interface definition *SUC ArrayView*. The only difference is that *SUC ArrayProcessValueOut* does not contain an *OSLevel* variable because it is always controlled by another LEA.


