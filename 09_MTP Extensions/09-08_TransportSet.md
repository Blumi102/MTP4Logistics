## MTP Specification of the TransportSet
This chapter specifies the *TransportSet* as a new aspect of the MTP specification that contains all elements identified in the conceptual chapter~[Art3 LA](#chap:Art3LA).

### Übersicht
#### Semantic Description of Transport Services
For semantic identification of the transport services introduced in Section~[Transportdienste](#sec:Transportdienste), a semantic identifier in the form of a *FunctionClassificationAttribute* is added to them. Table~[Function Classification Transportdienst](#tab:FunctionClassificationTransportdienst) specifies the corresponding *FunctionClassificationAttribute*. "2.0" denotes the version in major-minor format and can be incremented accordingly when changes are made to the *FunctionClassificationAttributes*.

<a id="tab:FunctionClassificationTransportdienst"></a>
**Table: FunctionClassificationAttribute of a Transport Service**

<table>
	<tr>
		<td colspan="2"><strong>▶ FunctionClassificationAttribute for Transport Service</strong></td>
	</tr>
	<tr>
		<th>Standard</th>
		<td>ModuleTypePackage:Logistics</td>
	</tr>
	<tr>
		<th>Level</th>
		<td>Transport-Management</td>
	</tr>
	<tr>
		<th>Type</th>
		<td>Transport</td>
	</tr>
	<tr>
		<th>IRDI</th>
		<td>ModuleTypePackage:Logistics:Transport:2.0</td>
	</tr>
</table>

#### Specification of the Transport Aspect
According to Chapter~[Art3 LA](#chap:Art3LA), a series of new model and interface definitions is required to represent transport-relevant information in the MTP of an LEA. Figure~[Specification of the TransportSet for Connecting Flexible Transport Systems to LEAs](#fig:AnhangUebersichtTransportAspekt) provides an overview of these newly specified definitions.
 
![Specification of the TransportSet for Connecting Flexible Transport Systems to LEAs](Inhalt/Abbildungen/99_Anhang/Spezifikation_Transport/Klassendiagramm.drawio.png)
*Specification of the TransportSet for Connecting Flexible Transport Systems to LEAs*

On the **interface-definition** side, *SUC TransportClientManager* is introduced as an interface definition for configuring and establishing a communication link between an LEA and transport management. It is an abstract interface definition that fundamentally allows the use of different communication technologies through different derivations. For implementation based on OPC~UA client/server, the derived *SUC OpcUaTransportClientManager* is introduced. In addition, *SUC TransportNodeManager* is introduced as an interface that enables the assignment of a transport node of an LEA to the associated TN proxy in transport management. A convention in the MTP specifications provides that interface definitions belonging together in terms of content are derived from a common interface definition with the suffix **Element*. Accordingly, in this case *SUC TransportElement*, derived from *SUC DataAssembly* [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3), is introduced, from which *SUC TransportClientManager* and *SUC TransportNodeManager* are derived. These interface definitions are organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangTransportSetSchnittstellen). 

On the **model-definition** side, *SUC TransportSet* is introduced as a new aspect set for organizing all transport-relevant models and is derived from the abstract *SUC MTPSet* according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). The *TransportSet* indicates that an LEA has the capability to be connected to a flexible transport system according to the concepts of this dissertation and contains all model definitions required for this purpose. In particular, this consists of any number of IEs of *SUC TransportNode*. The latter is an abstract class for representing transport nodes and is derived from *SUC LinkedObject*. The concrete derivations provided are *SUC InboundNode*, *SUC OutboundNode*, *SUC InOutboundNode*, *SUC ProcessingNode*, and *SUC OrderNode*. All *TransportNodes* are linked to one *TransportClientManager* interface each by means of an ID link relation and to one *TransportNodeManager* interface by means of LinkedObject relations. The model definitions are organized in the newly introduced library *SUCL MTPTransportSUCLib*. The detailed specification is provided in Appendix~[Model Definitions](#subsec:AnhangTransportSetModelle). 

All model and interface definitions required for the *TransportSet* are assigned to the new profile *ModuleTypePackage:TransportSet.Base V2.0.0*.
 
### Interface Definitions
#### Specification of the System Unit Class TransportElement
*SUC TransportElement* (Table~[Data Assembly Suc Transport Element](#tab:DataAssemblySucTransportElement)) is an abstract class derived from *SUC DataAssembly*. The transport-relevant interface definitions *SUC TransportClientManager* and *SUC TransportNodeManager* are derived from *SUC TransportElement*.

<a id="tab:DataAssemblySucTransportElement"></a>
**Table: Interface Definition of *SUC TransportElement***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>TransportElement</strong></td>
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
		<td colspan="5">root interface class for transport-related interface definitions</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/TransportElement</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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
		<td>WQC</td>
		<td>LOL <- LEA</td>
		<td>BYTE</td>
		<td>Worst Quality Code</td>
		<td>-</td>
		<td>WQC</td>
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

#### Specification of the System Unit Class TransportClientManager
*SUC TransportClientManager* (Table~[Data Assembly Suc Transport Client Manager](#tab:DataAssemblySucTransportClientManager)) is derived from *SUC TransportElement* and is an abstract interface definition for configuring the communication link between an LEA and a flexible transport system. To implement this interface definition, a concrete manager must be derived from it. So far, only *SUC OpcUaTransportClientManager* has been specified as a derivation. *SUC TransportClientManager*, and thus also its derivations, are assigned to a *TransportNode* model definition in the *TransportSet* via an ID link relation.

<a id="tab:DataAssemblySucTransportClientManager"></a>
**Table: Interface Definition of *SUC TransportClientManager***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>TransportClientManager</strong></td>
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
		<td colspan="5">abstract interface definition for configuring the communication of the Logistics Equipment Assembly to a transport management system</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/TransportElement/Transport-ClientManager</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/TransportElement</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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
		<td></td>
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

#### Specification of the System Unit Class OpcUaTransportClientManager
*SUC OpcUaTransportClientManager* (Table~[Data Assembly Suc Opc Ua Transport Client Manager](#tab:DataAssemblySucOpcUaTransportClientManager)) is derived from *SUC TransportClientManager* and is used to configure and establish an OPC~UA client/server communication link between the LEA and a flexible transport system. In addition, this interface contains the variable *LeaStateCur*, which enables transport management to determine the state of the LEA service. This is used to detect possible faults in the LEA and, if necessary, reroute transport services to this LEA.

<a id="tab:DataAssemblySucOpcUaTransportClientManager"></a>
**Table: Interface Definition of *SUC OpcUaTransportClientManager***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>OpcUaTransportClientManager</strong></td>
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
		<td colspan="5">configuration interface for an OPC~UA client communicating transport-relevant data</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/TransportElement/Transport-ClientManager/OpcUaTransportClientManager</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/TransportElement/Transport-ClientManager</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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
		<td>ConfigApplyEn</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Enable flag to apply the prepared configuration</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConfigApplyExt</td>
		<td>LOL -> LEA</td>
		<td>BOOL</td>
		<td>Apply the prepared configuration</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConnectEn</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Enable flag to establish connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConnectExt</td>
		<td>LOL -> LEA</td>
		<td>BOOL</td>
		<td>Establish connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>DisconnectEn</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Enable flag to remove connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>DisconnectExt</td>
		<td>LOL -> LEA</td>
		<td>BOOL</td>
		<td>Remove connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ResetExt</td>
		<td>LOL -> LEA</td>
		<td>BOOL</td>
		<td>Reset communication block</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConnectionAct</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Flag indicating an established connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConnectionErr</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Flag indicating a connection error</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ErrorId</td>
		<td>LOL <- LEA</td>
		<td>DWORD</td>
		<td>Identifier of the connection error</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>EndpointExt</td>
		<td>LOL -> LEA</td>
		<td>STRING</td>
		<td>Defines the server URL to connect with</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>NamespaceExt</td>
		<td>LOL -> LEA</td>
		<td>STRING</td>
		<td>Defines Namespace to be used</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>EndpointReq</td>
		<td>LOL <- LEA</td>
		<td>STRING</td>
		<td>Requested server URL</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>NamespaceReq</td>
		<td>LOL <- LEA</td>
		<td>STRING</td>
		<td>Requested namespace</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>EndpointCur</td>
		<td>LOL <- LEA</td>
		<td>STRING</td>
		<td>Currently configured server URL</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>NamespaceCur</td>
		<td>LOL <- LEA</td>
		<td>STRING</td>
		<td>Currently configured namespace</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>LeaStateCur</td>
		<td>LOL <- LEA</td>
		<td>DWORD</td>
		<td>MTP service state of the LEA service</td>
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

#### Specification of the System Unit Class TransportNodeManager
*SUC TransportNodeManager* (Table~[Data Assembly Suc Transport Node Manager](#tab:DataAssemblySucTransportNodeManager)) is derived from *SUC TransportElement* and is used to assign a TN proxy to a specific transport node in the LEA. This interface definition is assigned to a *TransportNode* model definition in the *TransportSet* via a LinkedObject relation.

<a id="tab:DataAssemblySucTransportNodeManager"></a>
**Table: Interface Definition of *SUC TransportNodeManager***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>TransportNodeManager</strong></td>
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
		<td colspan="5">configuration interface to assign transport nodes to transport proxies</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/TransportElement/Transport-NodeManager</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/TransportElement</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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
		<td>ConfigApplyEn</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Enable flag to apply the prepared configuration</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConfigApplyExt</td>
		<td>LOL -> LEA</td>
		<td>BOOL</td>
		<td>Apply the prepared configuration</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConnectEn</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Enable flag to establish connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConnectExt</td>
		<td>LOL -> LEA</td>
		<td>BOOL</td>
		<td>Establish connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>DisconnectEn</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Enable flag to remove connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>DisconnectExt</td>
		<td>LOL -> LEA</td>
		<td>BOOL</td>
		<td>Remove connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ResetExt</td>
		<td>LOL -> LEA</td>
		<td>BOOL</td>
		<td>Reset communication block</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConnectionAct</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Flag indicating an established connection</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ConnectionErr</td>
		<td>LOL <- LEA</td>
		<td>BOOL</td>
		<td>Flag indicating a connection error</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ErrorId</td>
		<td>LOL <- LEA</td>
		<td>DWORD</td>
		<td>Identifier of the connection error</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ProxyIdExt</td>
		<td>LOL -> LEA</td>
		<td>DINT</td>
		<td>Defines related proxy in the transportsystem</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ProxyIdReq</td>
		<td>LOL <- LEA</td>
		<td>DINT</td>
		<td>Requested transport proxy</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ProxyIdCur</td>
		<td>LOL <- LEA</td>
		<td>DINT</td>
		<td>Currently configured transport proxy</td>
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

### Model Definitions
#### Specification of the Instance Hierarchy Transports
*IH Transports* (Table~[Ih Transports](#tab:IhTransports)) is the entry point for the transport-related information model in the instance hierarchy of an MTP.

<a id="tab:IhTransports"></a>
**Table: Model Definition of *IH Transports***

<table>
	<tr>
		<td colspan="3"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="2"><strong>Transports</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="2">Instance Hierarchy (IH)</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="2">root element for the transport-related information model of an MTP</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="2">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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
		<td colspan="2">[1..*] IE of SUC TransportNode</td>
	</tr>
</table>

#### Specification of the System Unit Class Library MTPTransportSUCLib
*SUCL MTPTransportSUCLib* (Table~[Sucl MTP Transport SUC Lib](#tab:SuclMTPTransportSUCLib)) contains the System Unit Classes of the *TransportSet* of an MTP.

<a id="tab:SuclMTPTransportSUCLib"></a>
**Table: Library Definition of *SUCL MTPTransportSUCLib***

<table>
	<tr>
		<td colspan="3"><strong>▶ Module Type Package - Library Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="2"><strong>MTPTransportSUCLib</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="2">SystemUnitClassLibrary (SUCL)</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="2">Library containing the transport-related SUC model definitions of an MTP</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="2">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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

#### Specification of the System Unit Class TransportSet
*SUC TransportSet* (Table~[Suc Transport Set](#tab:SucTransportSet)), as a new aspect set of the MTP specification, contains all model definitions required to describe the transport-relevant information of an LEA.

<a id="tab:SucTransportSet"></a>
**Table: Model Definition of *SUC TransportSet***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>TransportSet</strong></td>
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
		<td colspan="3">Model definition for transport aspect set</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPTransportSUCLib/TransportSet</td>
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
		<td colspan="3">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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
		<td colspan="3">[1] EI of IC AspectSetReference which refers via ID to an IH containing<br>[1..*] IE of SUC TransportNode</td>
	</tr>
</table>

#### Specification of the System Unit Class TransportNode
*SUC TransportNode* (Table~[Suc Transport Node](#tab:SucTransportNode)) is an abstract model definition for describing a transport node available in an LEA. Currently, five concrete types of transport nodes are derived from this model definition: *SUC InboundNode*, *SUC OutboundNode*, *SUC InOutboundNode*, *SUC ProcessingNode*, and *SUC OrderNode*. A *SUC TransportNode* is assigned to the *TransportNodeManager* interface definition via a LinkedObject relation, which enables the assignment of the transport node to a TN proxy in transport management. In addition, *SUC TransportNode* is assigned to the *TransportClientManager* interface, which connects the LEA to transport management. For this assignment, the ID link mechanism and the variable *ClientLink* are used.

<a id="tab:SucTransportNode"></a>
**Table: Model Definition of *SUC TransportNode***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>TransportNode</strong></td>
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
		<td colspan="3">Model definition for a transport node of a transport-enabled Logistics Equipment Assembly</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode</td>
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
		<td colspan="3">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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
		<td>ClientLink</td>
		<td>xs:string</td>
		<td>object identifier of the associated TransportClientManager interface</td>
		<td>IDLinkAttribute-Type</td>
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
		<td colspan="3">IH to which an IE of SUC TransportSet relates via EI of IC AspectSetReference</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no children allowed)</td>
	</tr>
</table>

#### Specification of the System Unit Class InboundNode
*SUC InboundNode* (Table~[Suc Inbound Node](#tab:SucInboundNode)) is derived from *SUC TransportNode* and describes a transport node for transferring an LO from a flexible transport system to an LEA.

<a id="tab:SucInboundNode"></a>
**Table: Model Definition of *SUC InboundNode***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>InboundNode</strong></td>
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
		<td colspan="3">Model definition for a transport node transferring objects from a flexible transport system to the Logistics Equipment Assembly</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode/InboundNode</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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

#### Specification of the System Unit Class OutboundNode
*SUC OutboundNode* (Table~[Suc Outbound Node](#tab:SucOutboundNode)) is derived from *SUC TransportNode* and describes a transport node for transferring an LO from an LEA to a flexible transport system.

<a id="tab:SucOutboundNode"></a>
**Table: Model Definition of *SUC OutboundNode***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>OutboundNode</strong></td>
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
		<td colspan="3">model definition for a transport node transferring objects from the Logistics Equipment Assembly to a flexible transport system</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode/OutboundNode</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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

#### Specification of the System Unit Class InOutboundNode
*SUC InOutboundNode* (Table~[Suc In Outbound Node](#tab:SucInOutboundNode)) is derived from *SUC TransportNode* and describes a transport node for transferring LOs between an LEA and a flexible transport system in both directions.

<a id="tab:SucInOutboundNode"></a>
**Table: Model Definition of *SUC InOutboundNode***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>InOutboundNode</strong></td>
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
		<td colspan="3">model definition for a transport node transferring objects between the Logistics Equipment Assembly and a flexible transport system in both directions</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode/InOutboundNode</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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

#### Specification of the System Unit Class ProcessingNode
*SUC ProcessingNode* (Table~[Suc Processing Node](#tab:SucProcessingNode)) is derived from *SUC TransportNode* and describes a transport node for processing an LO without handing it over from the flexible transport system to an LEA.

<a id="tab:SucProcessingNode"></a>
**Table: Model Definition of *SUC ProcessingNode***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>ProcessingNode</strong></td>
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
		<td colspan="3">model definition for a transport node processing an object without transferring the object from the flexible transport system to the Logistics Equipment Assembly</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode/ProcessingNode</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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

#### Specification of the System Unit Class OrderNode
*SUC OrderNode* (Table~[Suc Order Node](#tab:SucOrderNode)) is derived from *SUC TransportNode* and describes a transport node for reporting transport demands and initiating corresponding transport processes.

<a id="tab:SucOrderNode"></a>
**Table: Model Definition of *SUC OrderNode***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>OrderNode</strong></td>
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
		<td colspan="3">model definition for a node to indicate transport demands and initialize corresponding transport processes</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode/OrderNode</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPTransportSUCLib/TransportNode</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:TransportSet.Base V2.0.0</td>
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


