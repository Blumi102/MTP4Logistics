## MTP Specification of the ChoreographySet {#sec:AnhangChoreoAspekt}
This chapter specifies the *ChoreographySet* as a new aspect of the MTP specification that contains all elements identified in the conceptual chapter~[Art2 LL](#chap:Art2LL).
 
### Übersicht {#subsec:AnhangChoreographySetUebersicht}
According to Chapter~[Art2 LL](#chap:Art2LL), a series of new model and interface definitions is required to represent choreography-relevant information in the MTP of an LEA. Figure~[Specification of the ChoreographySet for Implementing Choreography-Based Logistics Lines](#fig:AnhangUebersichtChoreoAspekt) provides an overview of these newly specified definitions.

![Specification of the ChoreographySet for Implementing Choreography-Based Logistics Lines](Inhalt/Abbildungen/99_Anhang/Spezifikation_Choreografie/Klassendiagramm.drawio.png)
*Specification of the ChoreographySet for Implementing Choreography-Based Logistics Lines* {#fig:AnhangUebersichtChoreoAspekt}

#### Interface Definitions
On the interface-definition side, *SUC ChoreographyParticipantManager* is introduced as an interface for configuring configurable logic, and *SUC CommunicationManager* is introduced as an interface for configurable communication. *SUC CommunicationManager* is an abstract interface definition that fundamentally allows the use of different communication technologies through different derivations. For implementation based on OPC~UA client/server, the derived *SUC OpcUaClientServerManager* is introduced. A convention in the MTP specifications provides that interface definitions belonging together in terms of content are derived from a common interface definition with the suffix **Element*. Accordingly, in this case *SUC ChoreographyElement*, derived from *SUC DataAssembly* [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3), is introduced, from which *SUC ChoreographyParticipantManager* and *SUC CommunicationManager* are derived.

For individual values exchanged and processed within a choreography, *SUC UnionElement*, derived from *SUC DataAssembly* [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1), is introduced according to Section~[Union Type](#subsec:UnionType) to display a value with configurable data type. For the communication variant of active writing, *SUC WritableUnionElements*, derived from *SUC UnionElement*, is additionally provided[^1] and enables write access to a value with configurable data type. 

These interface definitions are organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangChoreographySetSchnittstellen). 

#### Model Definitions
On the model-definition side, *SUC ChoreographySet* is introduced as a new aspect set for organizing all choreography-related models and is derived from the abstract *SUC MTPSet* according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). The *ChoreographySet* always contains exactly one IE of *SUC ChoreographyParticipant*, derived from *SUC LinkedObject* [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). It indicates that an LEA has the capability to participate in a choreography and is linked to a *ChoreographyParticipantManager* interface. The input list and output list of the choreography participant are represented by the subordinate *SUC InputList* and *SUC OutputList*. These lists can contain any number of IEs of *SUC InputElemente* and *SUC OutputElement*. They are derived from *SUC LinkedObject* and represent incoming or outgoing system variables. According to Section~[Choreo Konfiguration](#subsec:ChoreoKonfiguration), the classes *SUC FixedInputElement*, *SUC ConfigurableInputElement*, *SUC WritableInputElement*, *SUC FixedOutputElement*, and *SUC ConfigurableOutputElement* are provided as concrete derivations of *SUC InputElemente* and *SUC OutputElement*. Almost all *InputElements* and *OutputElements* are linked to a *UnionElement* interface via LinkedObject relations. An exception is formed by *WritableInputElements*, each of which is assigned to a *WritableUnionElement* interface. In the case of *ConfigurableInputElements* and *ConfigurableOutpuElements*, an ID link relation to a *CommunicationManager* interface also exists, which handles value transfer in the sense of configurable communication. The model definitions are organized in the newly introduced library *SUCL MTPChoreographySUCLib*. The detailed specification is provided in Appendix~[Model Definitions](#subsec:AnhangChoreographySetModelle).

All model and interface definitions required for the *ChoreographySet* are assigned to the new profile *ModuleTypePackage:ChoreographySet.Base V2.0.0*.[^2]

### Interface Definitions {#subsec:AnhangChoreographySetSchnittstellen}
#### Specification of the System Unit Class UnionElement
*SUC UnionElement* (Table~[Data Assembly Suc Union Element](#tab:DataAssemblySucUnionElement)) is used to display the value of an *InputElement* or an *OutputElement*. Accordingly, a *UnionElement* interface is assigned to these model definitions via a LinkedObject relation.

% Schnittstellendefinition SUC UnionElement
<a id="tab:DataAssemblySucUnionElement"></a>
**Table: Interface Definition of *SUC UnionElement***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>UnionElement</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-<sup>a)</sup></td></tr>
	<tr><th>Description</th><td colspan="5">interface for displaying a value with datatype defined at runtime</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/UnionElement</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ChoreographySet.Base V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>VQC</td><td>LOL <- LEA</td><td>BYTE</td><td>quality Code of the value</td><td>-</td><td>-</td></tr>
	<tr><td>DataType</td><td>LOL <- LEA</td><td>BYTE</td><td>identifier of selected data type<br/>(0 : None, 1: VReal, 2: VDInt, 3: VDWord, 4: VBool, 5: VString)</td><td>-</td><td>-</td></tr>
	<tr><td>VReal</td><td>LOL <- LEA</td><td>REAL</td><td>Real Value<br/>(Type: 1)</td><td>-</td><td>-</td></tr>
	<tr><td>VDInt</td><td>LOL <- LEA</td><td>DINT</td><td>Double Integer Value (Type: 2)</td><td>-</td><td>-</td></tr>
	<tr><td>VDWord</td><td>LOL <- LEA</td><td>DWORD</td><td>Double Word Value (Type: 3)</td><td>-</td><td>-</td></tr>
	<tr><td>VBool</td><td>LOL <- LEA</td><td>BOOL</td><td>Boolean Value (Type: 4)</td><td>-</td><td>-</td></tr>
	<tr><td>VString</td><td>LOL <- LEA</td><td>STRING</td><td>String Value<br/>(Type: 5)</td><td>-</td><td>-</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6"><sup>a)</sup> Bei der <em>SUC UnionElement</em> könnten zukünftig noch andere Datentypen ergänzt werden. Alle weiteren Schnittstellen, die die <em>SUC UnionElement</em> nutzen, sollte folglich auch Erweiterungen erlauben und nicht <em>sealed</em> sein.</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

The variables *VReal*, *VDInt*, *VDWord*, *VBool*, and *VString * are used to display the desired value. The variable *DataType* indicates which data type is currently active and which of the previously mentioned variables is therefore to be interpreted. *UnionElement* can thus display only one value of one defined data type at a time. *VQC* provides information about the quality and trustworthiness of the displayed value.

#### Specification of the System Unit Class WritableUnionElement
*SUC WritableUnionElement* (Table~[Data Assembly Suc Writable Union Element](#tab:DataAssemblySucWritableUnionElement)) is derived from *UnionElement* and is used to write a value into a *WritableInputElement*. Accordingly, a *WritableUnionElement* interface is always assigned to a *WritableInputElement* via a LinkedObject relation. 

% Schnittstellendefinition SUC WritableUnionElement
<a id="tab:DataAssemblySucWritableUnionElement"></a>
**Table: Interface Definition of *SUC WritableUnionElement***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>WritableUnionElement</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">interface for writing a value with datatype defined at runtime</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/UnionElement/WritableUnionElement</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/UnionElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ChoreographySet.Base V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>VQC</td><td>LOL -> LEA</td><td>BYTE</td><td>quality Code of the value</td><td>-</td><td>-</td></tr>
	<tr><td>DataType</td><td>LOL -> LEA</td><td>BYTE</td><td>identifier of selected data type (0 : None, 1: VReal, 2: VDInt, 3: VDWord, 4: VBool, 5: VString)</td><td>-</td><td>-</td></tr>
	<tr><td>VReal</td><td>LOL -> LEA</td><td>REAL</td><td>Real Value (Type: 1)</td><td>-</td><td>-</td></tr>
	<tr><td>VDInt</td><td>LOL -> LEA</td><td>DINT</td><td>Double Integer Value (Type: 2)</td><td>-</td><td>-</td></tr>
	<tr><td>VDWord</td><td>LOL -> LEA</td><td>DWORD</td><td>Double Word Value (Type: 3)</td><td>-</td><td>-</td></tr>
	<tr><td>VBool</td><td>LOL -> LEA</td><td>BOOL</td><td>Boolean Value (Type: 4)</td><td>-</td><td>-</td></tr>
	<tr><td>VString</td><td>LOL -> LEA</td><td>STRING</td><td>String Value (Type: 5)</td><td>-</td><td>-</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

The variables *VReal*, *VDInt*, *VDWord*, *VBool*, and *VString* are used to enter the desired value. The variable *DataType* indicates which data type is currently active and which of the previously mentioned variables is to be used in the LEA program. *WritableUnionElement* thus accepts only one value of one defined data type at a time. *VQC* can be used to transmit information about the quality and trustworthiness of the entered value.

#### Specification of the System Unit Class ChoreographyElement
*SUC ChoreographyElement* (Table~[Data Assembly Suc Choreography Element](#tab:DataAssemblySucChoreographyElement)) is an abstract class derived from *SUC DataAssembly* specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). The choreography-relevant interface definitions *ChoreographyParticipantManager* and *CommunicationManager* are derived from *ChoreographyElement*.

% Schnittstellendefinition SUC ChoreographyElement
<a id="tab:DataAssemblySucChoreographyElement"></a>
**Table: Interface Definition of *SUC ChoreographyElement***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>ChoreographyElement</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">abstract</td></tr>
	<tr><th>Description</th><td colspan="5">root interface class for choreography-related interface definitions</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ChoreographySet.Base V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>WQC</td><td>LOL <- LEA</td><td>BYTE</td><td>Worst Quality Code</td><td>-</td><td>WQC</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

#### Specification of the System Unit Class ChoreographyParticipantManager
*SUC ChoreographyParticipantManager* (Table~[Data Assembly Suc Choreography Participant Manager](#tab:DataAssemblySucChoreographyParticipantManager)) is derived from *SUC ChoreographyElement* and is used to configure the configurable logic of a choreography participant. In addition, it provides information for type, version, and instance verification of choreographed logistics lines, see also Appendix~[Workflows](#subsec:AnhangManifestWorkflows). This interface definition is assigned to an *SUC ChoreographyParticipant* in the *ChoreographySet* via a LinkedObject relation.

% Schnittstellendefinition SUC ChoreographyParticipantManager
<a id="tab:DataAssemblySucChoreographyParticipantManager"></a>
**Table: Interface Definition of *SUC ChoreographyParticipantManager***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>ChoreographyParticipantManager</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">configuration interface for a choreography participant</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement/ChoreographyParticipantManager</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ChoreographySet.Base V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>ComposedTypeCode</td><td>LOL -> LEA</td><td>STRING</td><td>identifier of the choreography type</td><td>-</td><td>-</td></tr>
	<tr><td>ComposedTypeRevision</td><td>LOL -> LEA</td><td>STRING</td><td>version of the choreography type</td><td>-</td><td>-</td></tr>
	<tr><td>RoleIdent</td><td>LOL -> LEA</td><td>STRING</td><td>identifier of the participant role within the choreography</td><td>-</td><td>-</td></tr>
	<tr><td>ViewSel</td><td>LOL -> LEA</td><td>BOOL</td><td>selection to view prepared configuration (false) or active configuration (true)</td><td>-</td><td>-</td></tr>
	<tr><td>ViewCur</td><td>LOL <- LEA</td><td>BOOL</td><td>currently selected view: false = prepared, true = active</td><td>-</td><td>-</td></tr>
	<tr><td>RestoreDefaultEn</td><td>LOL <- LEA</td><td>BOOL</td><td>enable flag to restore default configuration</td><td>-</td><td>-</td></tr>
	<tr><td>RestoreDefault</td><td>LOL -> LEA</td><td>BOOL</td><td>restores the default config of all inputs, logics, and outputs</td><td>-</td><td>-</td></tr>
	<tr><td>ExecuteEn</td><td>LOL <- LEA</td><td>BOOL</td><td>enable flag to execute the configurable logic</td><td>-</td><td>-</td></tr>
	<tr><td>ExecuteOn</td><td>LOL -> LEA</td><td>BOOL</td><td>trigger to apply the current configuration and start the execution</td><td>-</td><td>-</td></tr>
	<tr><td>ExecuteOff</td><td>LOL -> LEA</td><td>BOOL</td><td>trigger to quit the execution, outputs are set to default value</td><td>-</td><td>-</td></tr>
	<tr><td>ExecuteAct</td><td>LOL <- LEA</td><td>BOOL</td><td>flag which indicates the active execution</td><td>-</td><td>-</td></tr>
	<tr><td>ExecuteErr</td><td>LOL <- LEA</td><td>BOOL</td><td>flag which indicates min. one processing error</td><td>-</td><td>-</td></tr>
	<tr><td>InputCnt</td><td>LOL <- LEA</td><td>UINT</td><td>number of input configurations (maximum index of input configurations = InputCnt-1)</td><td>-</td><td>-</td></tr>
	<tr><td>InputIndexSel</td><td>LOL -> LEA</td><td>UINT</td><td>index of the desired input configuration to be shown</td><td>-</td><td>-</td></tr>
	<tr><td>InputIndexCur</td><td>LOL <- LEA</td><td>UINT</td><td>index of the currently selected input configuration</td><td>-</td><td>-</td></tr>
	<tr><td>Input_VQC</td><td>LOL <- LEA</td><td>BYTE</td><td>value quality code of the currently selected input</td><td>-</td><td>-</td></tr>
	<tr><td>Input_DataType</td><td>LOL <- LEA</td><td>BYTE</td><td>data type of the currently selected input</td><td>-</td><td>-</td></tr>
	<tr><td>Input_VReal</td><td>LOL <- LEA</td><td>REAL</td><td>real value of the currently selected input</td><td>-</td><td>-</td></tr>
	<tr><td>Input_VDInt</td><td>LOL <- LEA</td><td>DINT</td><td>double Integer value of the currently selected input</td><td>-</td><td>-</td></tr>
	<tr><td>Input_VDWord</td><td>LOL <- LEA</td><td>DWORD</td><td>double Word value of the currently selected input</td><td>-</td><td>-</td></tr>
	<tr><td>Input_VBool</td><td>LOL <- LEA</td><td>BOOL</td><td>boolean value of the currently selected input</td><td>-</td><td>-</td></tr>
	<tr><td>Input_VString</td><td>LOL <- LEA</td><td>STRING</td><td>string value of the currently selected input</td><td>-</td><td>-</td></tr>
	<tr><td>LogicCnt</td><td>LOL <- LEA</td><td>UINT</td><td>number of logic configurations (maximum index of logic configurations = LogicCnt-1)</td><td>-</td><td>-</td></tr>
	<tr><td>LogicIndexSel</td><td>LOL -> LEA</td><td>UINT</td><td>index of the desired logic configuration to be shown</td><td>-</td><td>-</td></tr>
	<tr><td>LogicIndexCur</td><td>LOL <- LEA</td><td>UINT</td><td>index of the currently selected logic configuration</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_FuncTypeSel</td><td>LOL -> LEA</td><td>UINT</td><td>function type selector of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Source</td><td>LOL -> LEA</td><td>SINT</td><td>source of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Index</td><td>LOL -> LEA</td><td>UINT</td><td>index of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Const_VQC</td><td>LOL -> LEA</td><td>BYTE</td><td>constant value quality code of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Const_DataTypeSel</td><td>LOL -> LEA</td><td>BYTE</td><td>constant data type of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Const_VReal</td><td>LOL -> LEA</td><td>REAL</td><td>constant Real value of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Const_VDInt</td><td>LOL -> LEA</td><td>DINT</td><td>constant Double Integer value of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Const_VDWord</td><td>LOL -> LEA</td><td>DWORD</td><td>constant double word value of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Const_VBool</td><td>LOL -> LEA</td><td>BOOL</td><td>constant boolean value of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In0_Const_VString</td><td>LOL -> LEA</td><td>STRING</td><td>constant String value of input 0 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Source</td><td>LOL -> LEA</td><td>SINT</td><td>source of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Index</td><td>LOL -> LEA</td><td>UINT</td><td>index of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Const_VQC</td><td>LOL -> LEA</td><td>BYTE</td><td>constant value quality code of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Const_DataTypeSel</td><td>LOL -> LEA</td><td>BYTE</td><td>constant data type of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Const_VReal</td><td>LOL -> LEA</td><td>REAL</td><td>constant Real value of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Const_VDInt</td><td>LOL -> LEA</td><td>DINT</td><td>constant Double Integer value of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Const_VDWord</td><td>LOL -> LEA</td><td>DWORD</td><td>constant double word value of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Const_VBool</td><td>LOL -> LEA</td><td>BOOL</td><td>constant boolean value of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In1_Const_VString</td><td>LOL -> LEA</td><td>STRING</td><td>constant String value of input 1 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Source</td><td>LOL -> LEA</td><td>SINT</td><td>source of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Index</td><td>LOL -> LEA</td><td>UINT</td><td>index of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Const_VQC</td><td>LOL -> LEA</td><td>BYTE</td><td>constant value quality code of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Const_DataTypeSel</td><td>LOL -> LEA</td><td>BYTE</td><td>constant data type of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Const_VReal</td><td>LOL -> LEA</td><td>REAL</td><td>constant Real value of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Const_VDInt</td><td>LOL -> LEA</td><td>DINT</td><td>constant Double Integer value of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Const_VDWord</td><td>LOL -> LEA</td><td>DWORD</td><td>constant double word value of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Const_VBool</td><td>LOL -> LEA</td><td>BOOL</td><td>constant boolean value of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In2_Const_VString</td><td>LOL -> LEA</td><td>STRING</td><td>constant String value of input 2 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Source</td><td>LOL -> LEA</td><td>SINT</td><td>source of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Index</td><td>LOL -> LEA</td><td>UINT</td><td>index of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Const_VQC</td><td>LOL -> LEA</td><td>BYTE</td><td>constant value quality code of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Const_DataTypeSel</td><td>LOL -> LEA</td><td>BYTE</td><td>constant data type of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Const_VReal</td><td>LOL -> LEA</td><td>REAL</td><td>constant Real value of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Const_VDInt</td><td>LOL -> LEA</td><td>DINT</td><td>constant Double Integer value of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Const_VDWord</td><td>LOL -> LEA</td><td>DWORD</td><td>constant double word value of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Const_VBool</td><td>LOL -> LEA</td><td>BOOL</td><td>constant boolean value of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_In3_Const_VString</td><td>LOL -> LEA</td><td>STRING</td><td>constant String value of input 3 of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_Out_VQC</td><td>LOL <- LEA</td><td>BYTE</td><td>constant value quality code of output of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_Out_DataType</td><td>LOL <- LEA</td><td>BYTE</td><td>constant data type of output of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_Out_VReal</td><td>LOL <- LEA</td><td>REAL</td><td>constant Real value of output of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_Out_VDInt</td><td>LOL <- LEA</td><td>DINT</td><td>constant Double Integer value of output of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_Out_VDWord</td><td>LOL <- LEA</td><td>DWORD</td><td>constant Double Word value of output of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_Out_VBool</td><td>LOL <- LEA</td><td>BOOL</td><td>constant Boolean value of output of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_Out_VString</td><td>LOL <- LEA</td><td>STRING</td><td>constant String value of output of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>Logic_Ret</td><td>LOL <- LEA</td><td>UINT</td><td>return value of the currently selected logic element</td><td>-</td><td>-</td></tr>
	<tr><td>OutputCnt</td><td>LOL <- LEA</td><td>UINT</td><td>number of output configurations (maximum index of output configurations = OutputCnt-1)</td><td>-</td><td>-</td></tr>
	<tr><td>OutputIndexSel</td><td>LOL -> LEA</td><td>UINT</td><td>index of the desired output configuration to be shown</td><td>-</td><td>-</td></tr>
	<tr><td>OutputIndexCur</td><td>LOL <- LEA</td><td>UINT</td><td>index of the currently selected output configuration</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Source</td><td>LOL -> LEA</td><td>SINT</td><td>source of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Index</td><td>LOL -> LEA</td><td>UINT</td><td>index of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_DataType</td><td>LOL -> LEA</td><td>BYTE</td><td>data type of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Const_VQC</td><td>LOL -> LEA</td><td>BYTE</td><td>constant value quality code of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Const_DataTypeSel</td><td>LOL -> LEA</td><td>BYTE</td><td>constant data type of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Const_VReal</td><td>LOL -> LEA</td><td>REAL</td><td>constant Real value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Const_VDInt</td><td>LOL -> LEA</td><td>DINT</td><td>constant Double Integer value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Const_VDWord</td><td>LOL -> LEA</td><td>DWORD</td><td>constant Double Word value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Const_VBool</td><td>LOL -> LEA</td><td>BOOL</td><td>constant Boolean value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Const_VString</td><td>LOL -> LEA</td><td>STRING</td><td>constant String value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Value_VQC</td><td>LOL -> LEA</td><td>BYTE</td><td>value quality code of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Value_DataTypeSel</td><td>LOL -> LEA</td><td>BYTE</td><td>data type of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Value_VReal</td><td>LOL -> LEA</td><td>REAL</td><td>real value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Value_VDInt</td><td>LOL -> LEA</td><td>DINT</td><td>double integer value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Value_VDWord</td><td>LOL -> LEA</td><td>DWORD</td><td>double word value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Value_VBool</td><td>LOL -> LEA</td><td>BOOL</td><td>boolean value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Value_VString</td><td>LOL -> LEA</td><td>STRING</td><td>string value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td>Output_Ret</td><td>LOL <- LEA</td><td>UINT</td><td>return value of the currently selected output</td><td>-</td><td>-</td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

#### Specification of the System Unit Class CommunicationManager
*SUC CommunicationManager* (Table~[Data Assembly Suc Communication Manager](#tab:DataAssemblySucCommunicationManager)) is an abstract class derived from *SUC ChoreographyElement*. It is to be understood as a generic interface definition for configuring the configurable communication of a choreography participant. To use this interface definition, a concrete manager for a specific communication technology must be derived from it. So far, only *OpcUaClientServerManager* has been implemented for configuring OPC~UA client/server connections; additional derivations can be developed in the future. The derivations of *SUC CommunicationManager* are assigned to the model definitions of *SUC ConfigurableInputElements* and *SUC ConfigurableOutputElements* in the *ChoreographySet* via an ID link relation, variable *ManagerLink*. In addition, each model definition specifies a *ManagerIndex* that refers to a concrete communication element within the *CommunicationManager*.

<a id="tab:DataAssemblySucCommunicationManager"></a>
**Table: Interface Definition of *SUC CommunicationManager***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>CommunicationManager</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="5">System Unit Class (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="5">abstract</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="5">abstract interface definition for the communication between different choreography participants</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement/Commu-nicationManager</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
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
		<td>-</td>
		<td>-</td>
		<td>-</td>
		<td>-</td>
		<td>-</td>
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
		<th>Allowed Parents</th>
		<td colspan="5">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="5">(no further constraints given)</td>
	</tr>
</table>

#### Specification of the System Unit Class OpcUaClientServerManager
*SUC OpcUaClientServerManager* (Table~[Data Assembly Suc Opc Ua Client Server Manager](#tab:DataAssemblySucOpcUaClientServerManager)) is derived from the abstract *SUC CommunicationManager*. It is used to configure OPC~UA client/server communication of an LEA with other LEAs participating in a choreography. *SUC OpcUaClientServerManager* is assigned to the model definitions of *SUC ConfigurableInputElements* and *SUC ConfigurableOutputElements* in the *ChoreographySet* via an ID link relation, variable *ManagerLink*. Each model definition specifies a *ManagerIndex* that refers to a concrete communication element within the *CommunicationManager*. In the case of *OpcUaClientServerManager*, these communication elements are the *UaReader* and *UaWriter* managed by the manager, which are referenced via their index. The *UaReader* are each assigned to a *ConfigurableInputElement*, and the *UaWriter* are each assigned to a *ConfigurableOutputElement*. For the communication variant of active writing, *SUC OpcUaClientServerManager* manages the existing *ValueFields* of an LEA that can be written by other LEAs. 

<!-- Start Table -->

<table>
	<tr><td colspan="6"><strong>&#9654; Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>OpcUaClientServerManager</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">interface for managing the OPC UA connections, readers, writers and value fields of a choreography participant</td></tr>
	<tr><td colspan="6"><strong>&#128204; AutomationML Properties</strong></td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement/CommunicationManager/OpcUaClientServerManager</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement/CommunicationManager</td></tr>
	<tr><th>Role Classes</th><td colspan="5">-</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ChoreographySet.Base V2.0.0</td></tr>
	<tr><td colspan="6"><strong>&#128204; AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>ConnectionViewSel</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>selection to view prepared configuration (false) or active configuration (true)</td><td>-</td><td>-</td></tr>
	<tr><td>ConnectionViewCur</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>currently selected view: false = prepared, true = active</td><td>-</td><td>-</td></tr>
	<tr><td>ConnectionCnt</td><td>LOL &lt;- LEA</td><td>BYTE</td><td>number of connection configurations (maximum index = ConnectionCnt-1)</td><td>-</td><td>-</td></tr>
	<tr><td>ConnectionCntActive</td><td>LOL &lt;- LEA</td><td>BYTE</td><td>number of active connections</td><td>-</td><td>-</td></tr>
	<tr><td>ConnectionCntInactive</td><td>LOL &lt;- LEA</td><td>BYTE</td><td>number of inactive but configured connections</td><td>-</td><td>-</td></tr>
	<tr><td>ConnectionCntError</td><td>LOL &lt;- LEA</td><td>BYTE</td><td>number of failed connections</td><td>-</td><td>-</td></tr>
	<tr><td>ConnectionIndexSel</td><td>LOL -&gt; LEA</td><td>BYTE</td><td>index of the desired connection configuration to be shown</td><td>-</td><td>-</td></tr>
	<tr><td>ConnectionIndexCur</td><td>LOL &lt;- LEA</td><td>BYTE</td><td>index of the currently selected connection configuration</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_RestoreDefaultEn</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>enable flag to restore default configuration of the currently selected connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_RestoreDefault</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>restore default configuration of the currently selected connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_ConnectEn</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>enable flag to connect the currently selected connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_Connect</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>apply the configuration and establish the currently selected connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_ConnectAct</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>indication whether the currently selected connection is established</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_ConnectErr</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>indication whether the currently selected connection has an error</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_DisconnectEn</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>enable flag to disconnect the currently selected connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_Disconnect</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>disconnect the currently selected connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_Reset</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>reset the currently selected connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_Active</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>indicates that the selected connection is activated to be used</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_ServerUrl</td><td>LOL -&gt; LEA</td><td>STRING</td><td>server URL for the connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_NamespaceUriCnt</td><td>LOL -&gt; LEA</td><td>BYTE</td><td>number of namespace URIs</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_NamespaceUri_1</td><td>LOL -&gt; LEA</td><td>STRING</td><td>namespace URI 1</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_NamespaceUri_2</td><td>LOL -&gt; LEA</td><td>STRING</td><td>namespace URI 2</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_NamespaceUri_3</td><td>LOL -&gt; LEA</td><td>STRING</td><td>namespace URI 3</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_NamespaceUri_4</td><td>LOL -&gt; LEA</td><td>STRING</td><td>namespace URI 4</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_NamespaceUri_5</td><td>LOL -&gt; LEA</td><td>STRING</td><td>namespace URI 5</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_SessionName</td><td>LOL -&gt; LEA</td><td>STRING</td><td>name of the session assigned by the client (when empty, then generated by the server)</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_ApplicationName</td><td>LOL -&gt; LEA</td><td>STRING</td><td>readable name of the OPC UA client application</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_SecurityMsgMode</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>enum UASecurityMsgMode</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_SecurityPolicy</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>enum UASecurityPolicy</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_ServerUri</td><td>LOL -&gt; LEA</td><td>STRING</td><td>defines the URI of the server, coded in ASCII</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_CheckServerCertificate</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>flag indicating if the server certificate should be checked</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_TransportProfile</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>enum UATransportProfile</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_UserIdentityTokenType</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>enum UAUserIdentityTokenType</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_UserTokenParam1</td><td>LOL -&gt; LEA</td><td>STRING</td><td>meaning according to UserIdentityTokenType, e.g., username</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_UserTokenParam2</td><td>LOL -&gt; LEA</td><td>STRING</td><td>meaning according to UserIdentityTokenType, e.g., password</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_CertificateID</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>certificate identifier</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_SessionTimeout</td><td>LOL -&gt; LEA</td><td>TIME</td><td>timeout for the session in case of connection loss</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_MonitorConnection</td><td>LOL -&gt; LEA</td><td>TIME</td><td>interval time to check the connection</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_LocaleID_1</td><td>LOL -&gt; LEA</td><td>STRING</td><td>optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_LocaleID_2</td><td>LOL -&gt; LEA</td><td>STRING</td><td>optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_LocaleID_3</td><td>LOL -&gt; LEA</td><td>STRING</td><td>optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_LocaleID_4</td><td>LOL -&gt; LEA</td><td>STRING</td><td>optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_SessionInfo_LocaleID_5</td><td>LOL -&gt; LEA</td><td>STRING</td><td>optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.</td><td>-</td><td>-</td></tr>
	<tr><td>Connection_Status</td><td>LOL &lt;- LEA</td><td>DWORD</td><td>status of current connection</td><td>-</td><td>-</td></tr>
	<tr><td>ReaderViewSel</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>selection to view prepared configuration (false) or active configuration (true)</td><td>-</td><td>-</td></tr>
	<tr><td>ReaderViewCur</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>currently selected view: false = prepared, true = active</td><td>-</td><td>-</td></tr>
	<tr><td>ReaderCnt</td><td>LOL &lt;- LEA</td><td>UINT</td><td>number of reader configurations (maximum index of reader configurations = ReaderCnt-1)</td><td>-</td><td>-</td></tr>
	<tr><td>ReaderCntInUse</td><td>LOL &lt;- LEA</td><td>UINT</td><td>number of readers in use</td><td>-</td><td>-</td></tr>
	<tr><td>ReaderCntError</td><td>LOL &lt;- LEA</td><td>UINT</td><td>number of readers with failures</td><td>-</td><td>-</td></tr>
	<tr><td>ReaderIndexSel</td><td>LOL -&gt; LEA</td><td>UINT</td><td>index of the desired reader configuration to be shown</td><td>-</td><td>-</td></tr>
	<tr><td>ReaderIndexCur</td><td>LOL &lt;- LEA</td><td>UINT</td><td>index of the currently selected reader configuration</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_RestoreDefaultEn</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>enable Flag to restore the default configuration of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_RestoreDefault</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>restore the default configuration of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_Reset</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>reset the reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_ConnectionIndex</td><td>LOL -&gt; LEA</td><td>INT</td><td>connection index the currently selected reader should use</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_InputIndex</td><td>LOL &lt;- LEA</td><td>UINT</td><td>indicates the index of the Input List the reader refers to</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_DataTypeSel</td><td>LOL -&gt; LEA</td><td>BYTE</td><td>data type of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_Timeout</td><td>LOL -&gt; LEA</td><td>TIME</td><td>timeout for the used OPC UA operations</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_MaxTryCount</td><td>LOL -&gt; LEA</td><td>BYTE</td><td>number of tries for an OPC UA operation until the Reader transitions into the error state</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_CycleSel</td><td>LOL -&gt; LEA</td><td>TIME</td><td>target cycle for the read operation</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_CycleCur</td><td>LOL &lt;- LEA</td><td>TIME</td><td>actual read cycle</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_Error</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>true, if the reader is in the error state</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_Status</td><td>LOL &lt;- LEA</td><td>DWORD</td><td>status of the Reader (e.g., status codes of OPC UA operations in case of an error)</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_Value_NamespaceIndex</td><td>LOL -&gt; LEA</td><td>UINT</td><td>namespace index of the value of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_Value_Identifier</td><td>LOL -&gt; LEA</td><td>STRING</td><td>identifier of the value of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_Value_IdentifierType</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>identifier type of the value of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_QC_NamespaceIndex</td><td>LOL -&gt; LEA</td><td>UINT</td><td>namespace index of the quality code of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_QC_Identifier</td><td>LOL -&gt; LEA</td><td>STRING</td><td>identifier of the quality code of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>Reader_QC_IdentifierType</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>identifier type of the quality code of the currently selected reader</td><td>-</td><td>-</td></tr>
	<tr><td>WriterViewSel</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>selection to view prepared configuration (false) or active configuration (true)</td><td>-</td><td>-</td></tr>
	<tr><td>WriterViewCur</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>currently selected view: false = prepared, true = active</td><td>-</td><td>-</td></tr>
	<tr><td>WriterCnt</td><td>LOL &lt;- LEA</td><td>UINT</td><td>number of writer configurations (maximum index of writer configurations = WriterCnt-1)</td><td>-</td><td>-</td></tr>
	<tr><td>WriterCntInUse</td><td>LOL &lt;- LEA</td><td>UINT</td><td>number of writers in use</td><td>-</td><td>-</td></tr>
	<tr><td>WriterCntError</td><td>LOL &lt;- LEA</td><td>UINT</td><td>number of writers with failures</td><td>-</td><td>-</td></tr>
	<tr><td>WriterIndexSel</td><td>LOL -&gt; LEA</td><td>UINT</td><td>index of the desired writer configuration to be shown</td><td>-</td><td>-</td></tr>
	<tr><td>WriterIndexCur</td><td>LOL &lt;- LEA</td><td>UINT</td><td>index of the currently selected writer configuration</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_RestoreDefaultEn</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>enable Flag to restore the default configuration of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_RestoreDefault</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>restore the default configuration of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_Reset</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>reset the writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_ConnectionIndex</td><td>LOL -&gt; LEA</td><td>INT</td><td>connection index the currently selected writer should use</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_OutputIndex</td><td>LOL &lt;- LEA</td><td>UINT</td><td>indicates the index of the Output List the writer refers to</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_DataTypeSel</td><td>LOL -&gt; LEA</td><td>BYTE</td><td>data type of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_Timeout</td><td>LOL -&gt; LEA</td><td>TIME</td><td>timeout for the used OPC UA operations</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_MaxTryCount</td><td>LOL -&gt; LEA</td><td>BYTE</td><td>number of tries for an OPC UA operation until the writer transitions into the error state</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_CycleSel</td><td>LOL -&gt; LEA</td><td>TIME</td><td>target cycle for the write operation</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_CycleCur</td><td>LOL &lt;- LEA</td><td>TIME</td><td>actual write cycle</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_Error</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>true, if the writer is in the error state</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_Status</td><td>LOL &lt;- LEA</td><td>DWORD</td><td>status of the Writer (e.g., status codes of OPC UA operations in case of an error)</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_Value_NamespaceIndex</td><td>LOL -&gt; LEA</td><td>UINT</td><td>namespace index of the value of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_Value_Identifier</td><td>LOL -&gt; LEA</td><td>STRING</td><td>identifier of the value of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_Value_IdentifierType</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>identifier type of the value of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_QC_NamespaceIndex</td><td>LOL -&gt; LEA</td><td>UINT</td><td>namespace index of the quality code of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_QC_Identifier</td><td>LOL -&gt; LEA</td><td>STRING</td><td>identifier of the quality code of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>Writer_QC_IdentifierType</td><td>LOL -&gt; LEA</td><td>UDINT</td><td>identifier type of the quality code of the currently selected writer</td><td>-</td><td>-</td></tr>
	<tr><td>ValueFieldViewSel</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>selection to view prepared configuration (false) or active configuration (true)</td><td>-</td><td>-</td></tr>
	<tr><td>ValueFieldViewCur</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>currently selected view: false = prepared, true = active</td><td>-</td><td>-</td></tr>
	<tr><td>ValueFieldApply</td><td>LOL -&gt; LEA</td><td>BOOL</td><td>variable for applying the data type configuration of all value fields</td><td>-</td><td>-</td></tr>
	<tr><td>ValueFieldCnt</td><td>LOL &lt;- LEA</td><td>UINT</td><td>number of value fields (maximum index of value fields = ValueFieldCnt-1)</td><td>-</td><td>-</td></tr>
	<tr><td>ValueFieldIndexSel</td><td>LOL -&gt; LEA</td><td>UINT</td><td>index of the desired value field to be shown</td><td>-</td><td>-</td></tr>
	<tr><td>ValueFieldIndexCur</td><td>LOL &lt;- LEA</td><td>UINT</td><td>index of the currently selected value field</td><td>-</td><td>-</td></tr>
	<tr><td>ValueField_InputIndex</td><td>LOL &lt;- LEA</td><td>UINT</td><td>indicates the index of the Input List the selected value field refers to</td><td>-</td><td>-</td></tr>
	<tr><td>ValueField_DataTypeSel</td><td>LOL -&gt; LEA</td><td>BYTE</td><td>data type of the currently selected value field</td><td>-</td><td>-</td></tr>
	<tr><td>ValueField_VQC</td><td>LOL &lt;- LEA</td><td>BYTE</td><td>value quality code of the currently selected value field</td><td>-</td><td>-</td></tr>
	<tr><td>ValueField_VReal</td><td>LOL &lt;- LEA</td><td>REAL</td><td>Real value of the currently selected value field</td><td>-</td><td>-</td></tr>
	<tr><td>ValueField_VDInt</td><td>LOL &lt;- LEA</td><td>DINT</td><td>Double Integer value of the currently selected value field</td><td>-</td><td>-</td></tr>
	<tr><td>ValueField_VDWord</td><td>LOL &lt;- LEA</td><td>DWORD</td><td>Double Word value of the currently selected value field</td><td>-</td><td>-</td></tr>
	<tr><td>ValueField_VBool</td><td>LOL &lt;- LEA</td><td>BOOL</td><td>Boolean value of the currently selected value field</td><td>-</td><td>-</td></tr>
	<tr><td>ValueField_VString</td><td>LOL &lt;- LEA</td><td>STRING</td><td>String value of the currently selected value field</td><td>-</td><td>-</td></tr>
	<tr><td colspan="6"><strong>&#128204; Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>&#128204; AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

<!-- End Table -->

### Model Definitions {#subsec:AnhangChoreographySetModelle}
#### Specification of the Instance Hierarchy Choreography
*IH Choreography* (Table~[Ih Choreography](#tab:IhChoreography)) is the entry point for the choreography-related information model in the instance hierarchy of an MTP.

<a id="tab:IhChoreography"></a>
**Table: Model Definition of *IH Choreography***

<table>
	<tr>
		<td colspan="3"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="2"><strong>Choreography</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="2">Instance Hierarchy (IH)</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="2">root element for the choreography-related information model of n MTP</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="2">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="3"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>ID</td>
		<td>xs:string</td>
		<td>Identifier of the Instance Hierarchy</td>
	</tr>
	<tr>
		<td colspan="3"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<td colspan="3"><strong>📌 AutomationML Object - Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="2">[1] IE of SUC ChoreographyParticipant</td>
	</tr>
</table>

#### Specification of the System Unit Class Library MTPChoreographySUCLib
*SUCL MTPChoreographySUCLib* (Table~[Sucl MTP Choreography SUC Lib](#tab:SuclMTPChoreographySUCLib)) contains the System Unit Classes of the *ChoreographySet* of a Module Type Package.

<a id="tab:SuclMTPChoreographySUCLib"></a>
**Table: Library Definition of *SUCL MTPChoreographySUCLib***

<table>
	<tr>
		<td colspan="3"><strong>▶ Module Type Package - Library Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="2"><strong>MTPChoreographySUCLib</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="2">SystemUnitClassLibrary (SUCL)</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="2">Library containing the Choreography-related SUC model definitions of an MTP</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="2">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="3"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td colspan="3"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="3">-</td>
	</tr>
</table>

#### Specification of the System Unit Class ChoreographySet
The *SUC ChoreographySet* (Table~[Suc Choreography Set](#tab:SucChoreographySet)), as a new aspect set of the MTP specification, is derived from *SUC MTPSet* according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) and organizes all model definitions required to describe an LEA as a participant in a choreography.

<a id="tab:SucChoreographySet"></a>
**Table: Model Definition of *SUC ChoreographySet***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>ChoreographySet</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for choreography aspect set</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/ChoreographySet</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPSUCLib/MTPSet</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">[1] EI of IC AspectSetReference which refers via ID to an IH containing [1]~IE of SUC ChoreographyParticipant</td>
	</tr>
</table>

#### Specification of the System Unit Class ChoreographyParticipant
*SUC ChoreographyParticipant* (Table~[Suc Choreography Participant](#tab:SucChoreographyParticipant)) describes an LEA as a choreography participant. The interface definition *SUC ChoreographyParticipantManager* is assigned to this model definition via a LinkedObject relation.

<a id="tab:SucChoreographyParticipant"></a>
**Table: Model Definition of *SUC ChoreographyParticipant***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>ChoreographyParticipant</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for choreography participant</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/ChoreographyParticipant</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPSUCLib/LinkedObject</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">IH to which an IE of SUC ChoreographySet relates via EI of IC AspectSet-Reference</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">[1] IE of SUC InputList<br>[1] IE of SUC OutputList</td>
	</tr>
</table>

#### Specification of the System Unit Class InputList
*SUC InputList* (Table~[Suc Input List](#tab:SucInputList)) organizes all incoming system variables relevant to the configurable logic of a choreography participant. The MTP of a choreography participant always contains exactly one *InputList*.

<a id="tab:SucInputList"></a>
**Table: Model Definition of *SUC InputList***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>InputList</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for the list of input elements of a choreography participant</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/ChoreographyParticipant/InputList</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">[1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC)</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">IE of SUC ChoreographyParticipant</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">[0..*] IE of SUC InputElement</td>
	</tr>
</table>

#### Specification of the System Unit Class InputElement
*SUC InputElement* (Table~[Suc Input Element](#tab:SucInputElement)) describes an incoming system variable relevant to the configurable logic of a choreography participant. This may be a statically defined internal process variable of the participant or a process variable received by the participant from another participant.

<a id="tab:SucInputElement"></a>
**Table: Model Definition of *SUC InputElement***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>InputElement</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">abstract</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for an input element of a choreography participant</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/InputElement</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPSUCLib/LinkedObject</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>Name</td>
		<td>xs:string</td>
		<td colspan="2">unique Number as index in the InputList (beginning at 0)</td>
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
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">IE of SUC InputList</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no children allowed)</td>
	</tr>
</table>

#### Specification of the System Unit Class FixedInputElement
*SUC FixedInputElement* (Table~[Suc Fixed Input Element](#tab:SucFixedInputElement)) is derived from *SUC InputElement* and describes a statically defined incoming system variable provided by the choreography participant itself. A *FixedInputElement* is assigned to a *UnionElement* interface via a LinkedObject relation.

<a id="tab:SucFixedInputElement"></a>
**Table: Model Definition of *SUC FixedInputElement***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>FixedInputElement</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for a statically defined input element</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/InputElement/FixedInputElement</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPChoreographySUCLib/InputElement</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
</table>

#### Specification of the System Unit Class ConfigurableInputElement
*SUC ConfigurableInputElement* (Table~[Suc Configurable Input Element](#tab:SucConfigurableInputElement)) is derived from *SUC InputElement* and describes a configurable incoming system variable received by the choreography participant from another choreography participant. A *ConfigurableInputElement* is assigned to a derivation of the *CommunicationManager* interface via an ID link relation using the variable *ManagerLink*. A *ManagerIndex* is used to refer to a specific communication element within the *CommunicationManager*. In this way, the communication is configured such that the required system variable is exchanged. The interpretation of *ManagerIndex* depends on the derivation of *CommunicationManager* used. In the case of *OpcUaClientServerManager*, this is the index of the reader used.

<a id="tab:SucConfigurableInputElement"></a>
**Table: Model Definition of *SUC ConfigurableInputElement***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>ConfigurableInputElement</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for a configurable input element</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/InputElement/ConfigurableInputElement</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPChoreographySUCLib/InputElement</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
		<td>ManagerLink</td>
		<td>xs:string</td>
		<td>object identifier of the associated CommunicationManager interface</td>
		<td>IDLinkAttribute-Type</td>
	</tr>
	<tr>
		<td>ManagerIndex</td>
		<td>xs:unsignedInt</td>
		<td>index of the incoming configurable communication entity within the communication manager</td>
		<td>-</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="4">-</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
</table>

#### Specification of the System Unit Class WritableInputElement
*SUC WritableInputElement* (Table~[Suc Writable Input Element](#tab:SucWritableInputElement)) is derived from *SUC InputElement* and describes an incoming system variable into which values can be written by another choreography participant. A *WritableInputElement* is assigned to a *WritableUnionElement* interface definition via a LinkedObject relation.

<a id="tab:SucWritableInputElement"></a>
**Table: Model Definition of *SUC WritableInputElement***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>WritableInputElement</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for a writable input element</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/InputElement/WritableInputElement</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPChoreographySUCLib/InputElement</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
		<td>ManagerLink</td>
		<td>xs:string</td>
		<td>object identifier of the associated CommunicationManager interface</td>
		<td>IDLinkAttribute-Type</td>
	</tr>
	<tr>
		<td>ManagerIndex</td>
		<td>xs:unsignedInt</td>
		<td>index of the field the value is written to within the communication manager</td>
		<td>-</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="4">-</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
</table>

#### Specification of the System Unit Class OutputList
*SUC OutputList* (Table~[Suc Output List](#tab:SucOutputList)) organizes all outgoing system variables relevant to the configurable logic of a choreography participant. The MTP of a choreography participant always contains exactly one *OutputList*.

<a id="tab:SucOutputList"></a>
**Table: Model Definition of *SUC OutputList***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>OutputList</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for the list of output elements of a choreography participant</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/ChoreographyParticipant/OutputList</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">[1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC)</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">IE of SUC ChoreographyParticipant</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">[0..*] IE of SUC OutputElement</td>
	</tr>
</table>

#### Specification of the System Unit Class OutputElement
*SUC OutputElement* (Table~[Suc Output Element](#tab:SucOutputElement)) describes an outgoing system variable relevant to the configurable logic of a choreography participant. This may be a statically defined internal process variable of the participant or a configurable process variable received by the participant from another participant. An *OutputElement* is always assigned to a *UnionElement* interface via a LinkedObject relation.

<a id="tab:SucOutputElement"></a>
**Table: Model Definition of *SUC OutputElement***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>OutputElement</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">abstract</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for an output element of a choreography participant</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/OutputElement</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPSUCLib/LinkedObject</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>Name</td>
		<td>xs:string</td>
		<td colspan="2">unique Number as Index in the Output List (beginning at 0)</td>
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
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">IE of SUC OutputList</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no children allowed)</td>
	</tr>
</table>

#### Specification of the System Unit Class FixedOutputElement
*SUC FixedOutputElement* (Table~[Suc Fixed Output Element](#tab:SucFixedOutputElement)) is derived from *SUC OutputElement* and describes a statically defined outgoing system variable used by the internal program of the choreography participant.

<a id="tab:SucFixedOutputElement"></a>
**Table: Model Definition of *SUC FixedOutputElement***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>FixedOutputElement</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for a statically defined output element</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/OutputElement/FixedOutputElement</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPChoreographySUCLib/OutputElement</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
</table>

#### Specification of the System Unit Class ConfigurableOutputElement
*SUC ConfigurableOutputElement* (Table~[Suc Configurable Output Element](#tab:SucConfigurableOutputElement)) is derived from *SUC OutputElement* and describes a configurable outgoing system variable sent by the choreography participant to another choreography participant. A *ConfigurableOutputElement* is assigned to a derivation of the *CommunicationManager* interface via an ID link relation using the variable *ManagerLink*. A *ManagerIndex* is used to refer to a specific communication element within the *CommunicationManager*. In this way, the communication is configured such that the required system variable is exchanged. The interpretation of *ManagerIndex* depends on the derivation of *CommunicationManager* used. In the case of *OpcUaClientServerManager*, this is the index of the writer used.

<a id="tab:SucConfigurableOutputElement"></a>
**Table: Model Definition of *SUC ConfigurableOutputElement***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>ConfigurableOutputElement</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">SystemUnitClass (SUC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">model definition for a configurable output element</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPChoreographySUCLib/OutputElement/ConfigurableOutputElement</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPChoreographySUCLib/OutputElement</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:ChoreographySet.Base V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th colspan="2">Description</th>
	</tr>
	<tr>
		<td>-</td>
		<td>-</td>
		<td colspan="2">-</td>
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
		<td>ManagerLink</td>
		<td>xs:string</td>
		<td>object identifier of the associated CommunicationManager interface</td>
		<td>IDLinkAttribute-Type</td>
	</tr>
	<tr>
		<td>ManagerIndex</td>
		<td>xs:unsignedInt</td>
		<td>index of the outcoming configurable communication entity within the CommunicationManager</td>
		<td>-</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="4">-</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no further constraints given)</td>
	</tr>
</table>



[^1]: This derivation is possible because a write access always includes reading back the written value. A write access is therefore an extension of a read access.
[^2]: *SUC CommunicationManager* and the derived *SUC OpcUaClientServerManager* can in principle also be used for configurable communication independently of choreographies, for example in decentralized orchestrations. Since such approaches are not yet provided in the MTP specification, these interface definitions are initially assigned to the *ChoreographySet*. For future cross-cutting use cases, a shift into the *ServerAssemblySet* [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51) may be appropriate.
