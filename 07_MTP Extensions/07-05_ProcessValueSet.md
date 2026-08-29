## 7.5 MTP Extension of the ProcessValueSet
This chapter specifies all identified extensions of the *ProcessValueSet* and integrates them into the existing [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

### 7.5.1 Overview
#### Extension of the ProcessValueInputs
DataAssembly definitions *SUC StructProcessValueIn* and *SUC ArrayProcessValueIn* are intended to specify process-value inputs for structured data types and array data types. As shown in [Figure 7.15](#figure-715-extension-of-the-processvalueset-for-implementing-structured-and-array-based-process-value-inputs), *SUC StructProcessValueIn* and *SUC ArrayProcessValueIn*, together with all other DataAssembly definitions for process-value inputs, are derived from the DataAssembly definition *SUC InputElement* according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) and are organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in [DataAssembly definitions](#752-dataassembly-definitions). This extension, as a result of this work, has already been adopted into the profile *ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0* of the [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

##### Figure 7.15: Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Inputs
![Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Inputs](./images/05_PVIn.drawio.svg)

#### Extension of the ProcessValueOutputs
DataAssembly definitions for process-value outputs of structured data types and array data types are to be specified. For process-value outputs of structured data types, the associated *IndicatorElement*, i.e. *SUC StructView*, shall be used as for all other MTP data types according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). For array-based process-value outputs, a separate DataAssembly definition *SUC ArrayProcessValueOut* is provided because, unlike *SUC ArrayView*, it does not require an *OSLevel* variable for access control. An *ArrayProcessValueOut* interface is always accessed by another LEA and not by an operator or LOL. Following the principles of the MTP concept, *SUC ArrayProcessValueOut* is derived from an abstract *SUC OutputElement*. *SUC OutputElement*, in turn, is derived from *SUC DataAssembly* specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). The newly introduced DataAssembly definitions are shown in [Figure 7.16](#figure-716-extension-of-the-processvalueset-for-implementing-structured-and-array-based-process-value-outputs) and organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in [DataAssembly definitions](#752-dataassembly-definitions). This extension, as a result of this work, has already been adopted into the profile *ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0* of the [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

##### Figure 7.16: Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Outputs
![Extension of the ProcessValueSet for Implementing Structured and Array-Based Process Value Outputs](./images/05_PVOut.drawio.svg)

### 7.5.2 DataAssembly definitions
#### Specification of the System Unit Class StructProcessValueIn
*SUC StructProcessValueIn* ([Table 7.43](#table-743-dataassembly-definition-of-suc-structprocessvaluein)) is used by a LEA to access the value of a variable with a structured data type from another LEA.

##### Table 7.43: DataAssembly definition of *SUC StructProcessValueIn*

<table>
	<tr><td colspan="6" align="left"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th align="left">Name</th><td colspan="5" align="left"><strong>StructProcessValueIn</strong></td></tr>
	<tr><th align="left">Type</th><td colspan="5" align="left">System Unit Class (SUC)</td></tr>
	<tr><th align="left">Modifier</th><td colspan="5" align="left">-</td></tr>
	<tr><th align="left">Description</th><td colspan="5" align="left">generic interface for accessing a value of structured data type from another LEA</td></tr>
	<tr><th align="left">AutomationML Path</th><td colspan="5" align="left">MTPDataAssemblySUCLib/DataAssembly/InputElement/StructProcessValueIn</td></tr>
	<tr><th align="left">AutomationML BaseRef</th><td colspan="5" align="left">MTPDataAssemblySUCLib/DataAssembly/InputElement</td></tr>
	<tr><th align="left">Role Classes</th><td colspan="5" align="left">-</td></tr>
	<tr><th align="left">Version</th><td colspan="5" align="left">ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th align="left">Name</th><th align="left">Type</th><th colspan="4" align="left">Description</th></tr>
	<tr><td align="left">-</td><td align="left">-</td><td colspan="4" align="left">-</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th align="left">Name</th><th align="left">Access</th><th align="left">Type</th><th align="left">Description</th><th align="left">AttributeType Reference</th><th align="left">Base Function</th></tr>
	<tr><td align="left">V</td><td align="left">LOL ⟶ LEA</td><td align="left">{VType}</td><td align="left">Value</td><td align="left">-</td><td align="left">-</td></tr>
	<tr><td align="left">VType</td><td align="left">MTP</td><td align="left">&lt;empty&gt;</td><td align="left">Type Definition of the Value</td><td align="left">{AT of StructuredDataType}</td><td align="left">ComplexType</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6" align="left">-</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th align="left">Allowed Parents</th><td colspan="5" align="left">(no further constraints given)</td></tr>
	<tr><th align="left">Allowed Children</th><td colspan="5" align="left">(no further constraints given)</td></tr>
</table>

The required value is transferred in the variable *V* according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). The distinctive feature of this DataAssembly definition is the use of a user-defined structured data type. The modeling and use of such a type have already been described in connection with [SUC StructView](./07-03_DataAssemblySet.md#specification-of-the-system-unit-class-structview) and are applied in the same way for *SUC StructProcessValueIn*. This data type is then expected behind the variable *V*.

#### Specification of the System Unit Class ArrayProcessValueIn
*SUC ArrayProcessValueIn* ([Table 7.44](#table-744-dataassembly-definition-of-suc-arrayprocessvaluein)) is used by a LEA to access a value at a specific position of an array in another LEA.

##### Table 7.44: DataAssembly definition of *SUC ArrayProcessValueIn*

<table>
	<tr><td colspan="6" align="left"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th align="left">Name</th><td colspan="5" align="left"><strong>ArrayProcessValueIn</strong></td></tr>
	<tr><th align="left">Type</th><td colspan="5" align="left">System Unit Class (SUC)</td></tr>
	<tr><th align="left">Modifier</th><td colspan="5" align="left">-</td></tr>
	<tr><th align="left">Description</th><td colspan="5" align="left">generic interface for accessing a value of array data type from another LEA</td></tr>
	<tr><th align="left">AutomationML Path</th><td colspan="5" align="left">MTPDataAssemblySUCLib/DataAssembly/InputElement/ArrayProcessValueIn</td></tr>
	<tr><th align="left">AutomationML BaseRef</th><td colspan="5" align="left">MTPDataAssemblySUCLib/DataAssembly/InputElement</td></tr>
	<tr><th align="left">Role Classes</th><td colspan="5" align="left">-</td></tr>
	<tr><th align="left">Version</th><td colspan="5" align="left">ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th align="left">Name</th><th align="left">Type</th><th colspan="4" align="left">Description</th></tr>
	<tr><td align="left">-</td><td align="left">-</td><td colspan="4" align="left">-</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th align="left">Name</th><th align="left">Access</th><th align="left">Type</th><th align="left">Description</th><th align="left">AttributeType Reference</th><th align="left">Base Function</th></tr>
	<tr><td align="left">IndexSel</td><td align="left">LOL ⟵ LEA</td><td align="left">DINT</td><td align="left">Index Value</td><td align="left">-</td><td align="left">Multiplexing for Process Values</td></tr>
	<tr><td align="left">IndexMin</td><td align="left">LOL ⟶ LEA</td><td align="left">DINT</td><td align="left">Low Limit of the Index</td><td align="left">-</td><td align="left">Multiplexing for Process Values</td></tr>
	<tr><td align="left">IndexMax</td><td align="left">LOL ⟶ LEA</td><td align="left">DINT</td><td align="left">High Limit of the Index</td><td align="left">-</td><td align="left">Multiplexing for Process Values</td></tr>
	<tr><td align="left">IndexCur</td><td align="left">LOL ⟶ LEA</td><td align="left">DINT</td><td align="left">Current Index Value</td><td align="left">-</td><td align="left">Multiplexing for Process Values</td></tr>
	<tr><td align="left">V</td><td align="left">LOL ⟶ LEA</td><td align="left">{VType}</td><td align="left">Output Value</td><td align="left">-</td><td align="left">-</td></tr>
	<tr><td align="left">VType</td><td align="left">MTP</td><td align="left">a)</td><td align="left">Type Definition of the Values</td><td align="left">{AT of BaseDataType}</td><td align="left">ComplexType</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6" align="left"><sup>a)</sup> Type shall be &lt;empty&gt; in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th align="left">Allowed Parents</th><td colspan="5" align="left">(no further constraints given)</td></tr>
	<tr><th align="left">Allowed Children</th><td colspan="5" align="left">(no further constraints given)</td></tr>
</table>

Similar to the [SUC ArrayView](./07-03_DataAssemblySet.md#specification-of-the-system-unit-class-arrayview), the challenge with this interface lies in accessing an array within a LEA that can have an arbitrary length. As with the *SUC ArrayView*, access to this array shall also be index-based in the case of the *SUC ArrayProcessValueIn*.

The array position to be displayed is selected via the variable *IndexSel*. The variables *IndexMin* and *IndexMax* specify the lower and upper limits of the array. The variable *IndexCur* specifies the currently selected index, and the value of the array at this position is displayed in *V*. *VType* defines the data type shared by all array elements. This may be a primitive data type or a structured data type.

**Note:** This DataAssembly definition differs from all other interfaces derived from the DataAssembly definition *SUC InputElement* because it also includes information flows from the LEA to the LOL. This had not previously been envisaged.

#### Specification of the System Unit Class OutputElement
*SUC OutputElement* ([Table 7.45](#table-745-dataassembly-definition-of-suc-outputelement)) is an abstract interface from which specific process-value outputs of different data types can be derived. The DataAssembly definition itself serves only an organizational purpose and provides a variable for transmitting a *Worst Quality Code (WQC)*.

##### Table 7.45: DataAssembly definition of *SUC OutputElement*

<table>
	<tr><td colspan="6" align="left"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th align="left">Name</th><td colspan="5" align="left"><strong>OutputElement</strong></td></tr>
	<tr><th align="left">Type</th><td colspan="5" align="left">System Unit Class (SUC)</td></tr>
	<tr><th align="left">Modifier</th><td colspan="5" align="left">abstract</td></tr>
	<tr><th align="left">Description</th><td colspan="5" align="left">abstract interface from which specific process value outputs can be derived</td></tr>
	<tr><th align="left">AutomationML Path</th><td colspan="5" align="left">MTPDataAssemblySUCLib/DataAssembly/OutputElement</td></tr>
	<tr><th align="left">AutomationML BaseRef</th><td colspan="5" align="left">MTPDataAssemblySUCLib/DataAssembly</td></tr>
	<tr><th align="left">Role Classes</th><td colspan="5" align="left">-</td></tr>
	<tr><th align="left">Version</th><td colspan="5" align="left">ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th align="left">Name</th><th align="left">Type</th><th colspan="4" align="left">Description</th></tr>
	<tr><td align="left">-</td><td align="left">-</td><td colspan="4" align="left">-</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th align="left">Name</th><th align="left">Access</th><th align="left">Type</th><th align="left">Description</th><th align="left">AttributeType Reference</th><th align="left">Base Function</th></tr>
	<tr><td align="left">WQC</td><td align="left">LOL ⟵ LEA</td><td align="left">BYTE</td><td align="left">Worst Quality Code variable</td><td align="left">-</td><td align="left">WQC</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6" align="left">-</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th align="left">Allowed Parents</th><td colspan="5" align="left">(no further constraints given)</td></tr>
	<tr><th align="left">Allowed Children</th><td colspan="5" align="left">(no further constraints given)</td></tr>
</table>

**Note:** For greater clarity in modeling and with regard to possible future developments, MTP standardization should consider explicitly modeling *ProcessValueOutputs* of all MTP data types, including structured and primitive data types, and also deriving them from the newly specified *OutputElement*.

#### Specification of the System Unit Class ArrayProcessValueOut
*SUC ArrayProcessValueOut* ([Table 7.46](#table-746-dataassembly-definition-of-suc-arrayprocessvalueout)) is used by a LEA to provide the values of a LEA-internal array to another LEA.

##### Table 7.46: DataAssembly definition of *SUC ArrayProcessValueOut*

<table>
	<tr><td colspan="6" align="left"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th align="left">Name</th><td colspan="5" align="left"><strong>ArrayProcessValueOut</strong></td></tr>
	<tr><th align="left">Type</th><td colspan="5" align="left">System Unit Class (SUC)</td></tr>
	<tr><th align="left">Modifier</th><td colspan="5" align="left">-</td></tr>
	<tr><th align="left">Description</th><td colspan="5" align="left">generic interface for making available a value of array data type to another LEA</td></tr>
	<tr><th align="left">AutomationML Path</th><td colspan="5" align="left">MTPDataAssemblySUCLib/DataAssembly/OutputElement/ArrayProcessValueOut</td></tr>
	<tr><th align="left">AutomationML BaseRef</th><td colspan="5" align="left">MTPDataAssemblySUCLib/DataAssembly/OutputElement</td></tr>
	<tr><th align="left">Role Classes</th><td colspan="5" align="left">-</td></tr>
	<tr><th align="left">Version</th><td colspan="5" align="left">ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th align="left">Name</th><th align="left">Type</th><th colspan="4" align="left">Description</th></tr>
	<tr><td align="left">-</td><td align="left">-</td><td colspan="4" align="left">-</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th align="left">Name</th><th align="left">Access</th><th align="left">Type</th><th align="left">Description</th><th align="left">AttributeType Reference</th><th align="left">Base Function</th></tr>
	<tr><td align="left">IndexSel</td><td align="left">LOL ⟶ LEA</td><td align="left">DINT</td><td align="left">Index Value</td><td align="left">-</td><td align="left">Multiplexing for Process Values</td></tr>
	<tr><td align="left">IndexMin</td><td align="left">LOL ⟵ LEA</td><td align="left">DINT</td><td align="left">Low Limit of the Index</td><td align="left">-</td><td align="left">Multiplexing for Process Values</td></tr>
	<tr><td align="left">IndexMax</td><td align="left">LOL ⟵ LEA</td><td align="left">DINT</td><td align="left">High Limit of the Index</td><td align="left">-</td><td align="left">Multiplexing for Process Values</td></tr>
	<tr><td align="left">IndexCur</td><td align="left">LOL ⟵ LEA</td><td align="left">DINT</td><td align="left">Current Index Value</td><td align="left">-</td><td align="left">Multiplexing for Process Values</td></tr>
	<tr><td align="left">V</td><td align="left">LOL ⟵ LEA</td><td align="left">{VType}</td><td align="left">Output Value</td><td align="left">-</td><td align="left">-</td></tr>
	<tr><td align="left">VType</td><td align="left">MTP</td><td align="left">a)</td><td align="left">Type Definition of the Values</td><td align="left">{AT of BaseDataType}</td><td align="left">ComplexType</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6" align="left"><sup>a)</sup> Type shall be &lt;empty&gt; in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.</td></tr>
	<tr><td colspan="6" align="left"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th align="left">Allowed Parents</th><td colspan="5" align="left">(no further constraints given)</td></tr>
	<tr><th align="left">Allowed Children</th><td colspan="5" align="left">(no further constraints given)</td></tr>
</table>

The DataAssembly definition *SUC ArrayProcessValueOut* corresponds to the DataAssembly definition [SUC ArrayView](./07-03_DataAssemblySet.md#specification-of-the-system-unit-class-arrayview). The only difference is that *SUC ArrayProcessValueOut* does not contain an *OSLevel* variable because it is always controlled by another LEA.
