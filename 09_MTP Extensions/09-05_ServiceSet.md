## MTP Extension of the ServiceSet {#sec:AnhangServiceSet}
This chapter specifies all identified extensions of the *ServiceSet* and integrates them into the existing MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

### Übersicht {#subsec:AnhangServiceSetUebersicht}
#### Semantic Description of LEA Services
To distinguish the CES and SES procedures introduced in Section~[Lea Dienste](#sec:LeaDienste) for an LOL, a semantic identifier in the form of *FunctionClassificationAttributes* is added to them. Tables~[Function Classification Ces](#tab:FunctionClassificationCes) and [Function Classification Ses](#tab:FunctionClassificationSes) specify the corresponding *FunctionClassificationAttributes*. "2.0" denotes the version in major-minor format and can be incremented accordingly when changes are made to the *FunctionClassificationAttributes*.  

% FunctionClassificationAttribute CES
<a id="tab:FunctionClassificationCes"></a>
**Table: FunctionClassificationAttribute of a Cyclic Execution Service Procedure**

<table>
	<tr>
		<td colspan="2"><strong>FunctionClassificationAttribute for CES</strong></td>
	</tr>
	<tr>
		<th>Standard</th>
		<td>ModuleTypePackage:Logistics</td>
	</tr>
	<tr>
		<th>Level</th>
		<td>Machine</td>
	</tr>
	<tr>
		<th>Type</th>
		<td>CES</td>
	</tr>
	<tr>
		<th>IRDI</th>
		<td>ModuleTypePackage:Logistics:CES:2.0</td>
	</tr>
</table>

% FunctionClassificationAttribute SES
<a id="tab:FunctionClassificationSes"></a>
**Table: FunctionClassificationAttribute of a Single Execution Service Procedure**

<table>
	<tr>
		<td colspan="2"><strong>FunctionClassificationAttribute for SES</strong></td>
	</tr>
	<tr>
		<th>Standard</th>
		<td>ModuleTypePackage:Logistics</td>
	</tr>
	<tr>
		<th>Level</th>
		<td>Machine</td>
	</tr>
	<tr>
		<th>Type</th>
		<td>SES</td>
	</tr>
	<tr>
		<th>IRDI</th>
		<td>ModuleTypePackage:Logistics:SES:2.0</td>
	</tr>
</table>

#### Semantic Description of Service Parameters
To enable a semantic description of service parameters, the model definition *ServiceParameter* is extended by the capability to append *FunctionClassificationAttributes*. The detailed specification is provided in Appendix~[Model Definitions](#subsec:AnhangServiceSetModelle). This extension, as a result of this dissertation, has already been adopted into the base profile *ModuleTypePackage:ServiceSet.Base V2.0.0* of the MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

Tables~[Function Classification Product Id](#tab:FunctionClassificationProductId) to [Function Classification Packaging Data Set](#tab:FunctionClassificationPackagingDataSet) specify *FunctionClassificationAttributes* for the parameters *ProductId*, *LogisticsObjectStatus*, *ProductDataSet*, *PackagingId*, and *PackagingDataSet* introduced in Section~[Parametrierngsmech](#subsec:Parametrierngsmech). "2.0" denotes the version in major-minor format and can be incremented accordingly when changes are made to the *FunctionClassificationAttributes*.

% FunctionClassificationAttribute ProductId
<a id="tab:FunctionClassificationProductId"></a>
**Table: FunctionClassificationAttribute of a Procedure Parameter for Setting a ProductId**

<table>
	<tr>
		<td colspan="2"><strong>FunctionClassificationAttribute for ProductId</strong></td>
	</tr>
	<tr>
		<th>Standard</th>
		<td>ModuleTypePackage:Logistics</td>
	</tr>
	<tr>
		<th>Level</th>
		<td>Service Parameter</td>
	</tr>
	<tr>
		<th>Type</th>
		<td>ProductId Procedure Parameter</td>
	</tr>
	<tr>
		<th>IRDI</th>
		<td>ModuleTypePackage:Logistics:ProductId:2.0</td>
	</tr>
</table>

% FunctionClassificationAttribute LogisticsObjectStatus
<a id="tab:FunctionClassificationLogisticsObjectStatus"></a>
**Table: FunctionClassificationAttribute of a Procedure Parameter for Setting a LogisticsObjectStatus**

<table>
	<tr>
		<td colspan="2"><strong>FunctionClassificationAttribute for LogisticsObjectStatussObjectStatus</strong></td>
	</tr>
	<tr>
		<th>Standard</th>
		<td>ModuleTypePackage:Logistics</td>
	</tr>
	<tr>
		<th>Level</th>
		<td>Service Parameter</td>
	</tr>
	<tr>
		<th>Type</th>
		<td>LogisticsObjectStatussObjectStatus Procedure Parameter</td>
	</tr>
	<tr>
		<th>IRDI</th>
		<td>ModuleTypePackage:Logistics:LogisticsObjectStatus:2.0</td>
	</tr>
</table>

% FunctionClassificationAttribute ProductDataSet
<a id="tab:FunctionClassificationProductDataSet"></a>
**Table: FunctionClassificationAttribute of a Configuration Parameter for Accessing a ProductDataSet**

<table>
	<tr>
		<td colspan="2"><strong>FunctionClassificationAttribute for ProductDataSet</strong></td>
	</tr>
	<tr>
		<th>Standard</th>
		<td>ModuleTypePackage:Logistics</td>
	</tr>
	<tr>
		<th>Level</th>
		<td>Service Parameter</td>
	</tr>
	<tr>
		<th>Type</th>
		<td>ProductDataSet Configuration Parameter</td>
	</tr>
	<tr>
		<th>IRDI</th>
		<td>ModuleTypePackage:Logistics:ProductDataSet:2.0</td>
	</tr>
</table>

% FunctionClassificationAttribute PackagingId
<a id="tab:FunctionClassificationPackagingId"></a>
**Table: FunctionClassificationAttribute of a Procedure Parameter for Setting a PackagingId**

<table>
	<tr>
		<td colspan="2"><strong>FunctionClassificationAttribute for PackagingId</strong></td>
	</tr>
	<tr>
		<th>Standard</th>
		<td>ModuleTypePackage:Logistics</td>
	</tr>
	<tr>
		<th>Level</th>
		<td>Service Parameter</td>
	</tr>
	<tr>
		<th>Type</th>
		<td>PackagingId Procedure Parameter</td>
	</tr>
	<tr>
		<th>IRDI</th>
		<td>ModuleTypePackage:Logistics:PackagingId:2.0</td>
	</tr>
</table>

% FunctionClassificationAttribute PackagingDataSet
<a id="tab:FunctionClassificationPackagingDataSet"></a>
**Table: FunctionClassificationAttribute of a Configuration Parameter for Accessing a PackagingDataSet**

<table>
	<tr>
		<td colspan="2"><strong>FunctionClassificationAttribute for PackagingDataSet</strong></td>
	</tr>
	<tr>
		<th>Standard</th>
		<td>ModuleTypePackage:Logistics</td>
	</tr>
	<tr>
		<th>Level</th>
		<td>Service Parameter</td>
	</tr>
	<tr>
		<th>Type</th>
		<td>PackagingDataSet Configuration Parameter</td>
	</tr>
	<tr>
		<th>IRDI</th>
		<td>ModuleTypePackage:Logistics:PackagingDataSet:2.0</td>
	</tr>
</table>

#### Extension of the ParameterElements
According to Section~[Lea Parameter](#sec:LeaParameter), the two new interface definitions *SUC StructServParam* and *SUC ArrayServParam* are required for the parameterization of LEA services. As shown in Figure~[Extension of the ServiceSet for Implementing Structured and Array-Based Service Parameters](#fig:ErweiterungParam), *SUC StructServParam* and *SUC ArrayServParam*, together with all other interface definitions for service parameters, are derived from the interface definition *SUC ParameterElement* according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) and organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Anhang Service Set Schnittstellen](#subsec:AnhangServiceSetSchnittstellen). This extension, as a result of this dissertation, has already been adopted into the profile *ModuleTypePackage:ServiceSet.ComplexTypes V2.0.0* of the MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

![Extension of the ServiceSet for Implementing Structured and Array-Based Service Parameters](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Parameter/Klassendiagramm.drawio.png)
*Extension of the ServiceSet for Implementing Structured and Array-Based Service Parameters* {#fig:ErweiterungParam}

#### Specification of the LogisticsInteraction {#subsec:LogisticsInteraction}
Section~[Lea Parameter](#sec:LeaParameter) and Section~[Ermittlung Next Node](#subsec:ErmittlungNextNode) introduce the LEA requests to an LOL shown in Table~[Arten Logistics Interaction](#tab:ArtenLogisticsInteraction).

% Arten der LogisticsInteraction
<a id="tab:ArtenLogisticsInteraction"></a>
**Table: Possible Requests from an LEA to a Logistics Orchestration Layer**

<table>
	<tr>
		<th>Name</th>
		<th>Beschreibung</th>
	</tr>
	<tr>
		<td>ProductParameter-Request</td>
		<td>Mit dieser Anfrage bezieht eine LEA unter Angabe einer *ProductId* und eines *LogisticsObjectStatus* einen produktspezifischen Parametersatz vom LOL.</td>
	</tr>
	<tr>
		<td>Packaging-ParameterRequest</td>
		<td>Mit dieser Anfrage bezieht eine LEA unter Angabe einer *PackagingId* einen verpackungsspezifischen Parametersatz vom LOL.</td>
	</tr>
	<tr>
		<td>ProductParameter-UpdatedInfo</td>
		<td>Mit dieser Anfrage informiert eine LEA den LOL, dass sich der produktspezifische Parametersatz an einem definierten Arrayindex seines *ProductDataSet* geändert hat.</td>
	</tr>
	<tr>
		<td>Packaging-ParameterUpdated-Info</td>
		<td>Mit dieser Anfrage informiert eine LEA den LOL, dass sich der verpackungsspezifische Parametersatz an einem definierten Arrayindex seines *PackagingDataSet* geändert hat.</td>
	</tr>
	<tr>
		<td>TransportNode-Request</td>
		<td>Mit dieser Anfrage bezieht eine LEA unter Angabe einer *TransportId* den nächsten anzufahrenden Transportknoten für einen Transportauftrag vom LOL.</td>
	</tr>
</table>

These requests are implemented on the basis of service-operator interaction according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) and may occur once or not at all in an LEA. If they occur, they always follow the same sequence and always allow the same responses by an LOL. It is therefore appropriate to standardize these concrete service-operator interactions as logistics-specific interactions, hereafter called *LogisticsInteractions*. This allows an LEA MTP to model whether the corresponding *LogisticsInteractions* occur, while the structure of the *Questions* and *Answers* is standardized and does not need to be remodeled for every specific LEA type.
 
Figure~[Extension of the ServiceSet for Implementing Logistics Interactions](#fig:LogisticsInteractionKonzept) shows the interface and model definitions newly introduced for *LogisticsInteraction*.

![Extension of the ServiceSet for Implementing Logistics Interactions](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/Klassendiagramm.drawio.png)
*Extension of the ServiceSet for Implementing Logistics Interactions* {#fig:LogisticsInteractionKonzept}

<!-- Als Grundlage für die Standardisierung wird die Struktur der Dienst-Bediener-Interaktion gemäß \cite{PNO.2025.Part4} übernommen. Die Basis bildet die \emph{SUC LogisticsInteraction}, die mittels einer \emph{RC HasLogisticsInteraction} der \emph{SUC Service} einer LEA zugeordnet werden kann. Die \emph{RC HasLogisticsInteraction} ist abgeleitet von der in der \cite{PNO.2025.Part1} spezifizierten \emph{RC HasTextReference} und verweist mittels \emph{TextReference} auf die \emph{LogisticsInteraction}. Sie wird der \emph{SUC Service} als RR annotiert, da einem Dienst mehrere von der \emph{RC HasTextReference} abgeleitete RCs zugeordnet werden können. 

Die \emph{SUC LogisticsInteraction} ist von der \emph{SUC Text Definition} gemäß \cite{PNO.2025.Part4} abgeleitet und organisiert alle logistikspezifischen Fragen (\emph{SUC LogisticsQuestions}) einer LEA. Die \emph{SUC LogisticsQuestion} ist eine abstrakte Klasse, die von der in der \cite{PNO.2025.Part1} spezifizierten \emph{SUC Text} abgeleitet ist. Als konkrete Ausprägungen werden die \emph{SUC ProductParameterRequest}, die \emph{SUC PackagingParameterRequest}, die \emph{SUC ProductParameterUpdatedInfo}, die \emph{SUC PackagingParameterUpdatedInfo} und die \emph{SUC TransportNodeRequest} spezifiziert. Eine LEA kann jede dieser \emph{LogisticsQuestions} entweder gar nicht oder genau einmal untergeordnet zu seiner \emph{SUC LogisticsInteraction} bereitstellen. Die Charakteristik dieser Anfragen wird im Anhang~\ref{subsec:AnhangServiceSetModelle} beschrieben. Aus dieser Beschreibung geht auch hervor, dass für die Interaktion eine \emph{LogisticsQuestionId}, zwei \emph{LogisticsQuestionParams}, eine \emph{LogisticsAnswerId} und ein \emph{LogisticsAnswerTimeout} an der \emph{ServiceControl}-Schnittstelle verwendet werden. Diese werden der \emph{SUC ServiceControl} \cite{PNO.2025.Part4} mittels der \emph{RC LogisticsInteractionExtension} hinzugefügt. Diese RC wird als SRC modelliert, da sie der \emph{SUC ServiceControl} nur maximal einmal zugeordnet werden kann.

Die \emph{SUC LogisticsInteraction} und die \emph{SUC LogisticsQuestion} (inkl. ihrer Ableitungen) werden in der \emph{SUCL MTPTextSUCLib} organisiert. Die \emph{RC HasLogisticsInteraction} ist Teil der \emph{RCL MTPTextRCLib} und die \emph{RC LogisticsInteractionExtension} ist Teil der \emph{RCL MTPServiceRCLib}. Die Detailspezifikation erfolgt im Anhang~\ref{subsec:AnhangServiceSetModelle}.

Diese Definitionen werden einem neuen Profil \emph{ModuleTypePackage:ServiceSet.Logistics V2.0.0} zugeordnet.

\subsection{Schnittstellendefinitionen}
\label{subsec:AnhangServiceSetSchnittstellen}

\subsubsection{Spezifikation der System Unit Class StructServParam}

Die \emph{SUC StructServParam} (Tabelle~\ref{tab:DataAssemblySucStructServParam}) wird verwendet, um Parameter eines benutzerdefinierten strukturierten Datentyps von einem LOL an eine LEA zu übertragen. -->

% Schnittstellendefinition SUC StructServParam
<a id="tab:DataAssemblySucStructServParam"></a>
**Table: Interface Definition of *SUC StructServParam***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>StructServParam</strong></td>
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
		<td colspan="5">generic parameter interface for a structured data type following the rules of modelling complex data types</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ServiceElement/ParameterElement/StructServParam</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ServiceElement/ParameterElement</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:ServiceSet.ComplexTypes V2.0.0</td>
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
		<td>VExt</td>
		<td>LOL -> LEA</td>
		<td>{VType}</td>
		<td>External Value</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>VInt</td>
		<td>LOL <- LEA</td>
		<td>{VType}</td>
		<td>Internal Value</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>VOp</td>
		<td>LOL -> LEA</td>
		<td>{VType}</td>
		<td>Operator Value</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>VReq</td>
		<td>LOL <- LEA</td>
		<td>{VType}</td>
		<td>Requested Value</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>VOut</td>
		<td>LOL <- LEA</td>
		<td>{VType}</td>
		<td>Output Value</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>VFbk</td>
		<td>LOL <- LEA</td>
		<td>{VType}</td>
		<td>Feedback Value</td>
		<td>-</td>
		<td>-</td>
	</tr>
	<tr>
		<td>VType</td>
		<td>MTP</td>
		<td>&lt;empty&gt;</td>
		<td>Type Definition of the Values</td>
		<td>{AT of Structured-DataType}</td>
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

The setting of a parameter of *SUC StructServParam* is performed via the access channels *Automatic Internal*, *Automatic External*, or *Operator* in the same way as for all other service parameters defined in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

The distinctive feature of this interface definition is the use of a user-defined structured data type. The modeling and use of such a type have already been described in connection with *SUC StructView* and are applied in the same way for *SUC StructServParam*. This data type is then expected behind the variables *VExt*, *VInt*, *VOp*, *VReq*, and *VOut*. 

#### Specification of the System Unit Class ArrayServParam
*SUC ArrayServParam* (Table~[Data Assembly Suc Array Serv Param](#tab:DataAssemblySucArrayServParam)) is used by the LOL to write data to an array or read data from an array managed in an LEA.

% Schnittstellendefinition SUC ArrayServParam
<a id="tab:DataAssemblySucArrayServParam"></a>
**Table: Interface Definition of *SUC ArrayServParam***

<table>
	<tr>
		<td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="5"><strong>ArrayServParam</strong></td>
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
		<td colspan="5">generic parameter interface for an array data type following the rules of modelling complex data types</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ServiceElement/ParameterElement/ArrayServParam</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ServiceElement/ParameterElement</td>
	</tr>
	<tr>
		<th>Role Classes</th>
		<td colspan="5">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="5">ModuleTypePackage:ServiceSet.ComplexTypes V2.0.0</td>
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
	<tr><td>IndexExt</td><td>LOL -> LEA</td><td>DINT</td><td>External Index Value</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexInt</td><td>LOL <- LEA</td><td>DINT</td><td>Internal Index Value</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexOp</td><td>LOL -> LEA</td><td>DINT</td><td>Operator Index Value</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexMin</td><td>LOL <- LEA</td><td>DINT</td><td>Low Limit of the Index</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexMax</td><td>LOL <- LEA</td><td>DINT</td><td>High Limit of the Index</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>IndexCur</td><td>LOL <- LEA</td><td>DINT</td><td>Current Index Value</td><td>-</td><td>Multiplexing for Arrays</td></tr>
	<tr><td>VExt</td><td>LOL -> LEA</td><td>{VType}</td><td>External Value</td><td>-</td><td>-</td></tr>
	<tr><td>VInt</td><td>LOL <- LEA</td><td>{VType}</td><td>Internal Value</td><td>-</td><td>-</td></tr>
	<tr><td>VOp</td><td>LOL -> LEA</td><td>{VType}</td><td>Operator Value</td><td>-</td><td>-</td></tr>
	<tr><td>VReq</td><td>LOL <- LEA</td><td>{VType}</td><td>Requested Value</td><td>-</td><td>-</td></tr>
	<tr><td>VOut</td><td>LOL <- LEA</td><td>{VType}</td><td>Output Value</td><td>-</td><td>-</td></tr>
	<tr><td>VFbk</td><td>LOL <- LEA</td><td>{VType}</td><td>Feedback Value</td><td>-</td><td>-</td></tr>
	<tr><td>VType</td><td>MTP</td><td><sup>a)</sup></td><td>Type Definition of the Values</td><td>{AT of BaseDataType}</td><td>Complex-Type</td></tr>
	<tr>
		<td colspan="6"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="6"><sup>a)</sup> Type shall be &lt;empty&gt; in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.</td>
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

As with the *ArrayView* interface definition, the challenge for *SUC ArrayServParam* is to access an array within an LEA that may have an arbitrary length. As introduced in connection with *SUC ArrayView*, access to this array is also index-based in the case of *SUC ArrayServParam*.

The variables *IndexExt*, *IndexInt*, and *IndexOp* are used to select an array element depending on the operating mode. According to the active access channel, one of these three values is transferred to the variable *IndexCur*. The variables of all three access channels are checked to determine whether they lie within the range between *IndexMin* and *IndexMax*. If an index outside this range is set, the last valid index remains active and the *Worst Quality Code (WQC)* is set to "Out of Specification" according to [NAMUR NE 184](../98_References/README.md#namur-ne-184).

According to the value of the variable *IndexCur*, the array element at the corresponding index is selected for processing. It can then be processed according to the parameter-transfer mechanisms specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). *VOut* always indicates the configured value of the array element located at the position in the array defined by *IndexCur*. This value does not necessarily have to match the parameter value currently used in the LEA.

*VType* defines the data type shared by all array elements. This may be a primitive data type or a user-defined structured data type according to the description of *SUC StructView*.

#### Specification of the Role Class LogisticsInteractionExtension
*RC LogisticsInteractionExtension* (Table~[Data Assembly Rc Logistics Interaction Extension](#tab:DataAssemblyRcLogisticsInteractionExtension)) extends the *ServiceControl* interface definition according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) by the variables required for logistics interactions. If a *LogisticsInteraction* is provided in the LEA, exactly one *LogisticsInteractionExtension* must be assigned as an SRC to the *ServiceControl* interface; otherwise none.

% Schnittstellendefinition RC LogisticsInteractionExtension
<a id="tab:DataAssemblyRcLogisticsInteractionExtension"></a>
**Table: Interface Definition of *RC LogisticsInteractionExtension***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>LogisticsInteractionExtension</strong></td></tr>
	<tr><th>Type</th><td colspan="5">Role Class (RC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">sealed</td></tr>
	<tr><th>Description</th><td colspan="5">interface definition extending the ServiceControl interface for logistice interaction</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPServiceRCLib/LogisticsInteractionExtension</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">AutomationMLBaseRoleClassLib/AutomationMLBaseRole</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Access</th><th>Type</th><th>Description</th><th>Attribute-Type Reference</th><th>Base Function</th></tr>
	<tr><td>Logistics-QuestionID</td><td>LOL <- LEA</td><td>DINT</td><td>Identifier of a currently pending logistics question</td><td>-</td><td></td></tr>
	<tr><td>Logistics-QuestionParam1</td><td>LOL <- LEA</td><td>STRING</td><td>Question parameter 1 of a currently pending logistics question (e.g., ProductId)</td><td>-</td><td></td></tr>
	<tr><td>Logistics-QuestionParam2</td><td>LOL <- LEA</td><td>STRING</td><td>Question parameter 2 of a currently pending logistics question (e.g., LogisticsObjectStatus)</td><td>-</td><td></td></tr>
	<tr><td>Logistics-AnswerID</td><td>LOL -> LEA</td><td>DINT</td><td>Identifier of a currently given answer to a pending question</td><td>-</td><td></td></tr>
	<tr><td>Logistics-AnswerTimeout</td><td>LOL -> LEA</td><td>TIME_OF_DAY</td><td>Timeout for a LEA to wait for an answer from a LOL; 0: timeout function deactivated; &gt; 0: timeout in s</td><td>-</td><td></td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Annotations</th><td colspan="5">IE of SUC ServiceControl as SRC</td></tr>
</table>

A *LogisticsInteraction* follows a principle similar to the service-operator interaction described in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). However, for the IDs of the questions, *LogisticsQuestionID*, and answers, *LogisticsAnswerID*, values from the DINT range, instead of DWORD, are used, where the value 0 and negative values may also be valid IDs. The value "-1" indicates that currently no question or answer is pending. By means of *LogisticsQuestionParam1* and *LogisticsQuestionParam2*, analogous to *InteractAddInfo* from [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), additional information can be attached to a request, for example *ProductId* and *LogisticsObjectStatus* for *ProductParameterRequest*. The variable *LogisticsAnswerTimeout* allows the entry of a time period that specifies how long an LEA should wait for the response of an LOL. After this time has elapsed, the LEA may execute an alternative program flow without the LOL response. Setting the timeout to 0 is interpreted as deactivation of the timeout function.

#### Extension of the System Unit Class ServiceControl
*SUC ServiceControl* (Table~[Data Assembly Suc Service Control](#tab:DataAssemblySucServiceControl)) defines the base class for controlling MTP services. This interface definition was already defined in the MTP specification and is extended in this dissertation by the capability to connect a RoleClass of type *RC LogisticsInteractionExtension* as an SRC.

% Schnittstellendefinition SUC ServiceControl
<a id="tab:DataAssemblySucServiceControl"></a>
**Table: Interface Definition of *SUC ServiceControl***

<table>
	<tr><td colspan="6"><strong>▶ Module Type Package - DataAssembly Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="5"><strong>ServiceControl</strong></td></tr>
	<tr><th>Type</th><td colspan="5">System Unit Class (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="5">-</td></tr>
	<tr><th>Description</th><td colspan="5">service control interface definition</td></tr>
	<tr><th>AutomationML Path</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ServiceElement/ServiceControl</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="5">MTPDataAssemblySUCLib/DataAssembly/ServiceElement</td></tr>
	<tr><th>Role Classes</th><td colspan="5">[0..1] MTPServiceRCLib/LogisticsInteractionExtension (SRC)</td></tr>
	<tr><th>Version</th><td colspan="5">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="4">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="4">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><td colspan="6"><em>The list of AutomationML Attributes is left out here. Please refer to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) for the complete specification.</em></td></tr>
	<tr><td colspan="6"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="6">-</td></tr>
	<tr><td colspan="6"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="5">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="5">(no further constraints given)</td></tr>
</table>

### Model Definitions {#subsec:AnhangServiceSetModelle}
#### Extension of the System Unit Class ServiceParameter
*SUC ServiceParameter* (Table~[Suc Service Parameter](#tab:SucServiceParameter)) defines the base class for MTP service parameters of all data types. This model definition was already defined in the MTP specification and is extended in this dissertation by the attribute *Classification* for representing semantic information in the form of *FunctionClassificationAttributes*.

% Modelldefinition SUC ServiceParameter
<a id="tab:SucServiceParameter"></a>
**Table: Model Definition of *SUC ServiceParameter***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>ServiceParameter</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">abstract</td></tr>
	<tr><th>Description</th><td colspan="3">base model definition of service parameter</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPServiceSUCLib/ServiceParameter</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPSUCLib/LinkedObject</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">-</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Base V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>Classification</td><td>&lt;empty&gt;</td><td>list of child attributes of AttributeType FunctionClassificationAttribute</td><td>OrderedListType</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">(no children allowed)</td></tr>
</table>

#### Specification of the System Unit Class LogisticsInteraction
*SUC LogisticsInteraction* (Table~[Suc Logistics Interaction](#tab:SucLogisticsInteraction)) organizes all model definitions required for the logistics interaction between an LEA and an LOL. It is derived from *SUC TextDefinition* specified in [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). *SUC LogisticsInteraction* is linked to the model definition *SUC HasLogisticsInteraction* via a *TextRef*. *SUC LogisticsInteraction* follows a principle similar to *SUC ServiceInteraction* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), with the difference that it contains predefined *LogisticsQuestions*, which are specified below.

% Modelldefinition SUC LogisticsInteraction
<a id="tab:SucLogisticsInteraction"></a>
**Table: Model Definition of *SUC LogisticsInteraction***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>LogisticsInteraction</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">-</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for logistics-specific service interaction</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPTextSUCLib/TextDefinition</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">-</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>-</td><td>-</td><td>-</td><td>-</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">[1..*] IEs of SUC LogisticsQuestion</td></tr>
</table>

#### Specification of the System Unit Class LogisticsQuestion
*SUC LogisticsQuestion* (Table~[Suc Logistics Question](#tab:SucLogisticsQuestion)) is an abstract class derived from *SUC Text* from [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) and represents a logistics-specific question that an LEA can ask an LOL. Five specific questions have so far been derived from *LogisticsQuestion*: *ProductParameterRequest*, *PackagingParameterRequest*, *ProductParameterUpdatedInfo*, *PackagingParameterUpdatedInfo*, and *TransportNodeRequest*. Each of these questions may occur either not at all or exactly once in an LEA.

% Modelldefinition SUC LogisticsQuestion
<a id="tab:SucLogisticsQuestion"></a>
**Table: Model Definition of *SUC LogisticsQuestion***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>LogisticsQuestion</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">abstract</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for an abstract question for logistics-specific service interactions</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPTextSUCLib/Text</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">-</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>Name</td><td>xs:string</td><td colspan="2">unique number of the question (&gt;0)</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>-</td><td>-</td><td>-</td><td>-</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">IE of SUC LogisticsInteraction</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">(no children allowed)</td></tr>
</table>

#### Specification of the System Unit Class ProductParameterRequest
*SUC ProductParameterRequest* (Table~[Suc Product Parameter Request](#tab:SucProductParameterRequest)) is derived from *SUC LogisticsQuestion* and is used to request product-specific parameter sets from an LOL. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC ProductParameterRequest*. Instead, a value in the DINT range is expected as the response. Values greater than or equal to 0 specify the index at which the LOL has written the requested parameter set into the *ProductDataSet* of the LEA. The array limits, minimum and maximum index, must not be exceeded or undershot. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC ProductParameterRequest
<a id="tab:SucProductParameterRequest"></a>
**Table: Model Definition of *SUC ProductParameterRequest***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>ProductParameterRequest</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">sealed</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for requesting product parameter sets from a Logistics Orchestration Layer</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion/ProductParameterRequest</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">-</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>-</td><td>-</td><td>-</td><td>-</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">(no further constraints given)</td></tr>
</table>

The standard sequence of a *ProductParameterRequest* is shown in Figure~[Sequence of the Logistics Interaction of a ProductParameterRequest](#fig:ProductParameterRequest).

![Sequence of the Logistics Interaction of a ProductParameterRequest](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/ProductParameterRequest.png)
*Sequence of the Logistics Interaction of a ProductParameterRequest* {#fig:ProductParameterRequest}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 1$, the LEA sends a *ProductParameterRequest* to the LOL and transfers *ProductId* as *LogisticsQuestionParam1* and *LogisticsObjectStatus* as *LogisticsQuestionParam2*. The LOL then determines the required parameter set and writes it into the *ProductDataSet* of the LEA via the corresponding *ArrayServParm* interface. If the parameterization is successful, the LOL returns a *LogisticsAnswer-ID* $>= 0$, here: *LogisticsAnswerID* $= 3$, to the LEA, reflecting the index of the *ProductDateSet* to which the new parameter set was written. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question and no answer are currently pending. *LogisticsQuestionParam1* and *LogisticsQuestionParam2* are reset.

#### Specification of the System Unit Class PackagingParameterRequest
*SUC PackagingParameterRequest* (Table~[Suc Packaging Parameter Request](#tab:SucPackagingParameterRequest)) is derived from *SUC LogisticsQuestion* and is used to request packaging-specific parameter sets from an LOL. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC PackagingParameterRequest*. Instead, a value in the DINT range is expected as the response. Values greater than or equal to 0 specify the index at which the LOL has written the requested parameter set into the *PackagingDataSet* of the LEA. The array limits, minimum and maximum index, must not be exceeded or undershot. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC PackagingParameterRequest
<a id="tab:SucPackagingParameterRequest"></a>
**Table: Model Definition of *SUC PackagingParameterRequest***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>PackagingParameterRequest</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">sealed</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for requesting packaging parameter sets from a Logistics Orchestration Layer</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion/PackagingParameterRequest</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">-</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>-</td><td>-</td><td>-</td><td>-</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">(no further constraints given)</td></tr>
</table>

The standard sequence of a *PackagingParameterRequest* is shown in Figure~[Sequence of the Logistics Interaction of a PackagingParameterRequest](#fig:PackagingParameterRequest).
 
![Sequence of the Logistics Interaction of a PackagingParameterRequest](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/PackagingParameterRequest.png)
*Sequence of the Logistics Interaction of a PackagingParameterRequest* {#fig:PackagingParameterRequest}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 2$, the LEA sends a *PackagingParameterRequest* to the LOL and transfers *PackagingId* as *LogisticsQuestionParam1*. The LOL then determines the required parameter set and writes it into the *PackagingDataSet* of the LEA via the corresponding *ArrayServParm* interface. If the parameterization is successful, the LOL returns a *LogisticsAnswerID* $>= 0$, here: *LogisticsAnswerID* $= 2$, to the LEA, reflecting the index of the *PackagingDateSet* to which the new parameter set was written. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question and no answer are currently pending. *LogisticsQuestionParam1* is reset.

#### Specification of the System Unit Class ProductParameterUpdatedInfo
*SUC ProductParameterUpdatedInfo* (Table~[Suc Product Parameter Updated Info](#tab:SucProductParameterUpdatedInfo)) is derived from *SUC LogisticsQuestion* and is used to inform an LOL that a parameter set in the *ProductDataSet* of an LEA has changed. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC ProductParameterUpdatedInfo*. Instead, the value "1" is expected as confirmation that the LOL has acknowledged the parameter change. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC ProductParameterUpdatedInfo
<a id="tab:SucProductParameterUpdatedInfo"></a>
**Table: Model Definition of *SUC ProductParameterUpdatedInfo***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>ProductParameterUpdatedInfo</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">sealed</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for informing a LOL of a change in a product parameter set</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion/ProductParameterUpdatedInfo</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">-</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>-</td><td>-</td><td>-</td><td>-</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">(no further constraints given)</td></tr>
</table>
 
The standard sequence of a *ProductParameterUpdatedInfo* is shown in Figure~[Sequence of the Logistics Interaction of a ProductParameterUpdatedInfo](#fig:ProductParameterUpdatedInfo).

![Sequence of the Logistics Interaction of a ProductParameterUpdatedInfo](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/ProductParameterUpdatedInfo.png)
*Sequence of the Logistics Interaction of a ProductParameterUpdatedInfo* {#fig:ProductParameterUpdatedInfo}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 3$, the LEA sends a *ProductParameterUpdatedInfo* to the LOL and transfers the array index, here: array index $= 5$, of the changed parameter set in the *ProductDataSet* as *LogisticsQuestionParam1*. The LOL parameter management then determines whether the corresponding product parameter data set is also to be adapted in the LOL, if necessary by user request, and updates the parameter set if required. The LOL acknowledges the parameter change by sending *LogisticsAnswerID*~$= 1$ to the LEA. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question and no answer are currently pending. *LogisticsQuestionParam1* is reset.

#### Specification of the System Unit Class PackagingParameterUpdatedInfo
*SUC PackagingParameterUpdatedInfo* (Table~[Suc Packaging Parameter Updated Info](#tab:SucPackagingParameterUpdatedInfo)) is derived from *SUC LogisticsQuestion* and is used to inform an LOL that a parameter set in the *PackagingDataSet* of an LEA has changed. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC PackagingParameterUpdatedInfo*. Instead, the value "1" is expected as confirmation that the LOL has acknowledged the parameter change. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC PackagingParameterUpdatedInfo
<a id="tab:SucPackagingParameterUpdatedInfo"></a>
**Table: Model Definition of *SUC PackagingParameterUpdatedInfo***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>PackagingParameterUpdatedInfo</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">sealed</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for informing a LOL of a change in a packaging parameter set</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion/PackagingParameterUpdatedInfo</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">-</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>-</td><td>-</td><td>-</td><td>-</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">(no further constraints given)</td></tr>
</table>
 
The standard sequence of a *PackagingParameterUpdatedInfo* is shown in Figure~[Sequence of the Logistics Interaction of a PackagingParameterUpdatedInfo](#fig:PackagingParameterUpdatedInfo).

![Sequence of the Logistics Interaction of a PackagingParameterUpdatedInfo](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/PackagingParameterUpdatedInfo.png)
*Sequence of the Logistics Interaction of a PackagingParameterUpdatedInfo* {#fig:PackagingParameterUpdatedInfo}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 4$, the LEA sends a *PackagingParameterUpdatedInfo* to the LOL and transfers the array index, here: array index $= 4$, of the changed parameter set in the *PackagingDataSet* as *LogisticsQuestionParam1*. The LOL parameter management then determines whether the corresponding product parameter data set is also to be adapted in the LOL, if necessary by user request, and updates the parameter set if required. The LOL acknowledges the parameter change by sending *LogisticsAnswerID*~$= 1$ to the LEA. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question and no answer are currently pending. *LogisticsQuestionParam1* is reset.

#### Specification of the System Unit Class TransportNodeRequest
*SUC TransportNodeRequest* (Table~[Suc Transport Node Request](#tab:SucTransportNodeRequest)) is derived from *SUC LogisticsQuestion* and is used to request the next transport node to be approached from an LOL. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC TransportNodeRequest*. Instead, a value in the DINT range is expected as the response. Values greater than 0 directly specify the ID of the next transport node to be approached. This eliminates the need for a separate parameter interface to configure the next transport node to be approached. Only values corresponding to the ID of a transport node in the respective MLS may be returned as a response. The value "0" indicates that the *FinalTargetNode* specified in the transport service interface is to be used as the next transport node. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC TransportNodeRequest
<a id="tab:SucTransportNodeRequest"></a>
**Table: Model Definition of *SUC TransportNodeRequest***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>TransportNodeRequest</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">sealed</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for requesting the next transport node to be approached from a Logistics Orchestration Layer</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPLogisticsSUCLib/LogisticsInteraction/LogisticsQuestion/TransportNodeRequest</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPLogisticsSUCLib/LogisticsInteraction/LogisticsQuestion</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">-</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>-</td><td>-</td><td>-</td><td>-</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">(no further constraints given)</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">(no further constraints given)</td></tr>
</table>

The standard sequence of a *TransportNodeRequest* is shown in Figure~[Sequence of the Logistics Interaction of a TransportNodeRequest](#fig:TransportNodeRequest).

![Sequence of the Logistics Interaction of a TransportNodeRequest](Inhalt/Abbildungen/08_Bereichs-Automatisierung/TransportNodeRequest.png)
*Sequence of the Logistics Interaction of a TransportNodeRequest* {#fig:TransportNodeRequest}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 5$, the LEA sends a *TransportNodeRequest* to the LOL and transfers the *TransportId* of the associated transport service as *LogisticsQuestionParam1*. The LOL then determines the required next transport node. If the next transport node is successfully determined, the LOL returns a *LogisticsAnswerID* $>= 0$ to the LEA. This response directly reflects the ID of the next transport node to be approached. A *LogisticsAnswerID* $= 0$ indicates that the *FinalTargetNode* of the transport service is to be used. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question or answer is currently pending. *LogisticsQuestionParam1* and *LogisticsQuestionParam2* are reset. The information received about the next transport node is transferred by the LEA to the procedure parameter *NextNode* in the corresponding transport service.

#### Specification of the Role Class HasLogisticsInteraction
*RC HasLogisticsInteraction* (Table~[Rc Has Logistics Interaction](#tab:RcHasLogisticsInteraction)) is derived from *RC HasTextReference* specified in [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). *SUC HasLogisticsInteraction* is used to assign a *LogisticsInteraction* to the model definition *SUC Service*, specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). For this purpose, a *SUC LogisticsInteraction* model definition is referenced by means of *TextRef*. If a *LogisticsInteraction* is provided in an LEA, exactly one *SUC HasLogisticsInteraction* must be assigned to the LEA service as a RoleRequirement; otherwise none.

% Modelldefinition RC HasLogisticsInteraction
<a id="tab:RcHasLogisticsInteraction"></a>
**Table: Model Definition of *RC HasLogisticsInteraction***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>HasLogisticsInteraction</strong><sup>a)</sup></td></tr>
	<tr><th>Type</th><td colspan="3">Role Class (RC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">sealed</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for assigning a logistics interaction to a service</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPTextRCLib/HasTextReference/HasLogisticsInteraction</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPTextRCLib/HasTextReference</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>-</td><td>-</td><td>-</td><td>-</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4"><sup>a)</sup> The usage of the HasLogisticsInteraction is allowed exactly once at a ServiceElement.</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Annotations</th><td colspan="3">IE of SUC Services as RR</td></tr>
</table>

#### Extension of the System Unit Class Service
*SUC ServiceParameter* (Table~[Suc Service](#tab:SucService)) defines the base class for modeling MTP services. This model definition was already defined in the MTP specification and is extended in this dissertation by the capability to connect a RoleClass of *RC HasLogisticsInteraction* as an RR.

% Modelldefinition SUC Service 
<a id="tab:SucService"></a>
**Table: Model Definition of *SUC Service***

<table>
	<tr><td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td></tr>
	<tr><th>Name</th><td colspan="3"><strong>Service</strong></td></tr>
	<tr><th>Type</th><td colspan="3">SystemUnitClass (SUC)</td></tr>
	<tr><th>Modifier</th><td colspan="3">sealed</td></tr>
	<tr><th>Description</th><td colspan="3">model definition for a Service</td></tr>
	<tr><th>AutomationML Path</th><td colspan="3">MTPServiceSUCLib/Service</td></tr>
	<tr><th>AutomationML BaseRef</th><td colspan="3">MTPSUCLib/LinkedObject</td></tr>
	<tr><th>RoleClasses</th><td colspan="3">[0..1] MTPTextRCLib/HasTextReference/HasServicePosition (RR)<br>[0..1] MTPTextRCLib/HasTextReference/HasServiceInteraction (RR)<br>[0..1] MTPTextRCLib/HasTextReference/HasLogisticsInteraction (RR)</td></tr>
	<tr><th>Version</th><td colspan="3">ModuleTypePackage:ServiceSet.Logistics V2.0.0</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Properties</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th colspan="2">Description</th></tr>
	<tr><td>-</td><td>-</td><td colspan="2">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Attributes</strong></td></tr>
	<tr><th>Name</th><th>Type</th><th>Description</th><th>AttributeType Reference</th></tr>
	<tr><td>Classification</td><td>&lt;empty&gt;</td><td>List of child attributes of AttributeTypes FunctionClassificationAttribute</td><td>OrderedListType</td></tr>
	<tr><td colspan="4"><strong>📌 Comment</strong></td></tr>
	<tr><td colspan="4">-</td></tr>
	<tr><td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td></tr>
	<tr><th>Allowed Parents</th><td colspan="3">IH to which an IE of SUC ServiceSet relates via EI of IC AspectSetReference</td></tr>
	<tr><th>Allowed Children</th><td colspan="3">[1..*] IEs of SUC Procedure<br>[0..*] IEs of SUC ConfigurationParameter</td></tr>
</table>
 

