## MTP Extension of the Manifest {#sec:AnhangManifest}
This chapter specifies all identified extensions of the *Manifest* and integrates them into the existing MTP specification [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1).

### Overview {#subsec:AnhangManifestUebersicht}
#### Extension of the Manifest for Modeling Composed MTPs
According to Section~[Konzept Composed MTP](#sec:KonzeptComposedMTP), the two new model definitions *SUC ComposedModuleTypePackage* and *RC HasExternalMtpContext* are required for modeling Composed MTPs. As shown in Figure~[Extension of the Manifest for Modeling Composed MTPs](#fig:ErweiterungManifest), the model definition *SUC ComposedModuleTypePackage* is organized in *SUCL MTPSUCLib*. An *IH ModuleTypePackage* may contain either a *SUC ComposedModuleTypePackage* or a *SUC ModuleTypePackage*. In contrast to *SUC ModuleTypePackage*, *SUC ComposedModuleTypePackage* always contains a subordinate *AttachmentSet* and follows the structure described in Appendix~[Anhang Composed Mtp Aspekte](#subsec:AnhangComposedMtpAspekte). 

![Extension of the Manifest for Modeling Composed MTPs](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Manifest Composed/Klassendiagramm.drawio.png)
*Extension of the Manifest for Modeling Composed MTPs* {#fig:ErweiterungManifest}

*RC HasExternalMtpContext* is organized in the newly introduced library *RCL MTPRCLib*. It can be assigned to a *SUC LinkedObject* as an SRC, so *SUC LinkedObject* must be extended to enable this assignment.[^1] These extensions are specified in detail in Appendix~[Model Definitions](#subsec:AnhangManifestModelle) and are assigned to the new profile *ModuleTypePackage:Manifest.Composed V2.0.0*.

#### Extension of the Manifest for Verifying Choreographed Functions
According to Section~[Konzept Composed MTP](#sec:KonzeptComposedMTP), new workflows are required for type, version, and instance verification of choreographed functions and Composed MTPs. These extensions are specified in detail in Appendix~[Workflows](#subsec:AnhangManifestWorkflows) and are assigned to the new profile *ModuleTypePackage:Manifest.Composed V2.0.0*.

![Extension of the Manifest for Verifying Choreographed Functions](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Manifest Composed/KlassendiagrammAT.drawio.png)
*Extension of the Manifest for Verifying Choreographed Functions* {#fig:ErweiterungManifestAT}

For version verification, the variable *ComposedTypeRevision* of *SUC ComposedModuleTypePackage* is used. This variable has a specific format and interpretation that follow the rules of *Semantic Versioning* according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). According to the MTP modeling principles, a defined AttributeType must therefore be assigned to this variable. For this purpose, *AT ComposedTypeRevisionType* is introduced as shown in Figure~[Extension of the Manifest for Verifying Choreographed Functions](#fig:ErweiterungManifestAT); it describes the version of the communication-relevant interface content of a choreographed function.[^2] This AT is derived from *AT SemanticVersionAttributeType* and organized in *ATL MTPATLib*. This extension is specified in detail in Appendix~[Model Definitions](#subsec:AnhangManifestModelle) and is assigned to the new profile *ModuleTypePackage:Manifest.Composed V2.0.0*.

### Model Definitions {#subsec:AnhangManifestModelle}
#### Specification of the System Unit Class ComposedModuleTypePackage
*SUC ComposedModuleTypePackage* (Table~[Suc Composed Module Type Package](#tab:SucComposedModuleTypePackage)) is the entry point to the information model of a Composed MTP. It contains the table of contents of the Composed MTP, from which all contained aspects are referenced according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). A *SUC ComposedModuleTypePackage* always contains an *AttachmentSet* that references the MTP files on which the Composed MTP is based. *SUC ComposedModuleTypePackage* contains AutomationML properties and attributes used for type, version, and instance verification of choreographed types (see Appendix~[Workflows](#subsec:AnhangManifestWorkflows), type, version, and instance verification of choreographies). In addition, the variable *Version* specifies the version of the Composed MTP itself. In contrast to *ComposedTypeRevision*, *Version* also indicates non-communication-relevant changes that affect only the Composed MTP itself, for example changes to the line process picture.

<a id="tab:SucComposedModuleTypePackage"></a>
**Table: Model Definition of *SUC ComposedModuleTypePackage***

<table>
  <tr>
    <td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
  </tr>
  <tr>
    <th>Name</th>
    <td colspan="3"><strong>ComposedModuleTypePackage</strong></td>
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
    <td colspan="3">model definition for the entry point of a Composed Module Type Package</td>
  </tr>
  <tr>
    <th>AutomationML Path</th>
    <td colspan="3">MTPSUCLib/ComposedModuleTypePackage</td>
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
    <td colspan="3">ModuleTypePackage:Manifest.Composed V2.0.0</td>
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
    <td>ID</td>
    <td>xs:string</td>
    <td colspan="2">GUID-formatted ID of the object</td>
  </tr>
  <tr>
    <td>Name</td>
    <td>xs:string</td>
    <td colspan="2">name of the composed type (e.g., name of the choreography type)</td>
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
    <td>Version</td>
    <td>xs:string</td>
    <td>Composed Module Type Package version</td>
    <td>ModuleType-PackageRevision-Type</td>
  </tr>
  <tr>
    <td>ManufacturerUri</td>
    <td>xs:string</td>
    <td>creator of the composed type</td>
    <td>-</td>
  </tr>
  <tr>
    <td>ComposedType-Code</td>
    <td>xs:string</td>
    <td>identifier of the composed type</td>
    <td>-</td>
  </tr>
  <tr>
    <td>ComposedType-Revision</td>
    <td>xs:string</td>
    <td>version of the composed type</td>
    <td>ComposedType-RevisionType</td>
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
    <td colspan="3">IH ModuleTypePackage</td>
  </tr>
  <tr>
    <th>Allowed Children</th>
    <td colspan="3">[0..1] IE of each derivation of SUC MTPSet<br>[1] IE of SUC AttachmentSet</td>
  </tr>
</table>

#### Specification of the Attribute Type ComposedTypeRevisionType
*AT ComposedTypeRevisionType* (Table~[At Composed Type Revision Type](#tab:AtComposedTypeRevisionType)) defines the version information of the communication-relevant interface content of a Composed MTP according to the rules of *Semantic Versioning*. This AT is derived from *AT SemanticVersionAttributeType*.

<a id="tab:AtComposedTypeRevisionType"></a>
**Table: Model Definition of *AT ComposedTypeRevisionType***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>ComposedTypeRevisionType</strong></td>
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
		<td colspan="3">model definition of a composed type revision information</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPATLib/SemanticVersionAttributeType/ComposedTypeRevisionType</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">MTPATLib/SemanticVersionAttributeType</td>
	</tr>
	<tr>
		<th>Data Type</th>
		<td colspan="3">xs:string</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:Manifest.Composed V2.0.0</td>
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

#### Specification of the Role Class Library MTPRCLib
*RCL MTPRCLib* (Table~[Rcl MTPRC Lib](#tab:RclMTPRCLib)) contains the basic role classes for the *Manifest* of a Module Type Package. 

<a id="tab:RclMTPRCLib"></a>
**Table: Library Definition of *RCL MTPRCLib***

<table>
	<tr>
		<td colspan="3"><strong>▶ Module Type Package - Library Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="2"><strong>MTPRCLib</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="2">RoleClassLibrary (RCL)</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="2">Library containing the Manifest RC model definitions of an MTP</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="2">ModuleTypePackage:Manifest.Composed V2.0.0</td>
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

#### Specification of the Role Class HasExternalMtpContext
*RC HasExternalMtpContext* (Table~[Rc Has External Mtp Context](#tab:RcHasExternalMtpContext)) provides the capability to reference an object from an attached MTP file. For this purpose, the variable *ContextLink* is used to reference the MTP file that contains the object to be referenced by means of the ID link mechanism. To do so, the ID of the *IC AttachmentReference* of the corresponding MTP file is entered in the *ContextLink* variable. The referenced object itself can then be addressed according to the LinkedObject or ID link mechanism defined in [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1), or according to the CustomSymbols mechanism defined in Section~[Stat Hmi Objekte](#subsec:StatHmiObjekte), as if the object were located in the same MTP. *RC HasExternalMtpContext* can be annotated to derivations of *SUC LinkedObject*, *SUC PictureFrame*, and *SUC ReferencedPicture*. 

<a id="tab:RcHasExternalMtpContext"></a>
**Table: Model Definition of *RC HasExternalMtpContext***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>HasExternalMtpContext</strong></td>
	</tr>
	<tr>
		<th>Type</th>
		<td colspan="3">Role Class (RC)</td>
	</tr>
	<tr>
		<th>Modifier</th>
		<td colspan="3">sealed</td>
	</tr>
	<tr>
		<th>Description</th>
		<td colspan="3">Role Class for defining a referenced object originates from an external MTP context</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPRCLib/HasExternalMtpContext</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:Manifest.Composed V2.0.0</td>
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
		<td>ContextLink</td>
		<td>xs:string (GUID-formatted)</td>
		<td>object identifier of the referenced MTP in the attachment</td>
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
		<th>Allowed Annotations</th>
		<td colspan="3">IE of SUC LinkedObject as SRC<br>IE of SUC PictureFrame as SRC<br>IE of SUC ReferencedPicture as SRC</td>
	</tr>
</table>

### Workflows {#subsec:AnhangManifestWorkflows}
[MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) introduces mechanisms for type, version, and instance verification in the MTP context. These mechanisms can be used to verify the types, versions, and instance information of the individual LEAs of a logistics line. This chapter further shows how these mechanisms can be extended for verifying choreography-based functions and Composed MTPs.

#### Type Verification
[MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) describes type verification as a mechanism for checking compatibility between the PEA type described in an MTP and the type of a physically present PEA. For this purpose, manufacturer information and a product code in the MTP must be compared with the corresponding information at the runtime interface of the PEA.

To enable such type verification also for choreographed logistics lines, a *ManufacturerUri* and *ComposedTypeCode* are defined for the created choreography configuration during choreography configuration. During generation of the Composed MTP, this information is transferred to the identically named variables in the IE of *SUC ComposedModuleTypePackage*. When the choreography is downloaded to the LEAs of the logistics line, this information is also written to the identically named variables of the *ChoreographyParticipantManager* interface. 

For type verification of the choreography, the *ManufacturerUri* and *ComposedTypeCode* stored in the Composed MTP must then be compared with the *ManufacturerUri* and *ComposedTypeCode* of all LEAs participating in the choreography. This ensures that the correct choreography configuration type has been downloaded to the LEAs.

#### Version Verification
[MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) describes version verification as a mechanism for checking compatibility between the version of a PEA communication interface described in an MTP and the version of the communication interface of a physically present PEA. For this purpose, the corresponding semantic version information in the MTP and at the runtime interface of the PEA must be compared. [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) defines rules for this comparison that specify when compatibility exists and which limitations may apply.

To enable such version verification also for choreographed logistics lines, a *ComposedTypeRevision* is defined for the created choreography configuration during choreography configuration, in particular for the communication-relevant information of the line interface. It starts at "1.0.0" and is incremented according to the scope of the change based on the *Semantic Versioning* rules described in [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). During generation of the Composed MTP, the version information is transferred to the *ComposedTypeRevision* variable in the IE of *SUC ComposedModuleTypePackage*. When the choreography is downloaded to the LEAs of the logistics line, the version information is also written to the *ComposedTypeRevision* variable of the *ChoreographyParticipantManager* interface.

For version verification of the choreography, the version information stored in the Composed MTP must then be compared with the version information of all LEAs participating in the choreography. The compatibility rules and compatibility limitations described in [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) must be observed. Version verification ensures that a suitable version of the choreography configuration has been downloaded to the LEAs with respect to communication-relevant and thus integration-relevant content.

#### Instance Verification
[MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) describes instance verification as a mechanism for checking compatibility between the PEA instance planned in engineering and the PEA instance actually installed. For this purpose, information about the planned *ProductInstanceUri* must be compared with the *ProductInstanceUri* at the runtime interface of the installed PEA.

The instance of a choreographed logistics line results from the correct combination of the installed LEA instances. To verify these LEA instances, *Role-Idents* are assigned during choreography configuration for all participant roles to be filled in the choreography. These *RoleIdents* are stored in the Composed MTP as the *Name* of the *AttachmentReference* that points to the MTP file assigned to the role. In MLS engineering, it is defined which LEA instance, identifiable by its *ProductInstance-Uri*, is intended to fill which role of the choreographed logistics line. During download of the choreography configuration to the LEA instances, the corresponding *RoleIdent* is written to the identically named variable of the *ChoreographyParticipantManager* interface. 

For instance verification of the choreography, the assignments of *RoleIdent* and *ProductInstanceUri* defined in MLS engineering must then be compared with the corresponding information of all LEAs involved in the logistics line. The *RoleIdent* is obtained from the *ChoreographyParticipantManager* interface of the logistics line, and the *ProductInstanceUris* are obtained from the *PeaInformationLabel* interfaces of the LEAs according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). This ensures that the correct LEA instances are installed in the logistics line.



[^1]: Appendix~[MTP Extension of the HMISet](#sec:AnhangHMISet) also describes that *RC HasExternalMtpContext* can be assigned to *SUC PictureFrame* and *SUC ReferencedPicture*.
[^2]: *AT ComposedTypeRevisionType* is therefore similar to *AT DeviceRevisionType*. However, while *AT DeviceRevisionType* refers only to the content of the *ServerAssemblySet* of one MTP, *AT ComposedTypeRevisionType* refers to the distributed content of the *ServerAssemblySets* of multiple MTPs.
