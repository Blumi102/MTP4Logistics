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


## MTP Extension of the HMISet {#sec:AnhangHMISet}
This chapter specifies all identified extensions of the *HMISet* and integrates them into the existing MTP specification [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2).

### Overview {#subsec:AnhangHMISetUebersicht}
According to Section~[Linien Bedienbild](#subsec:LinienBedienbild), the two model definitions *SUC PictureFrame* and *SUC ReferencedPicture* are required for process-picture modeling in choreographed logistics lines. As shown in Figure~[Extension of the HMISet for Representing Line Process Pictures](#fig:ErweiterungHMISet), these definitions, together with all other model definitions for process-picture modeling, are organized in *SUCL MTPHMISUCLib*. In MTP modeling, any number of *ReferencedPictures* can be inserted into the instance hierarchy of the *HMISet*, similar to *Pictures* according to [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2). Any number of instances of *SUC PictureFrame* can be added to the *Pictures* or *SemanticGroups* modeled in the MTP, similar to *VisualObjects* according to [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2). The model definitions of *SUC HMISet*, *SUC Picture*, and *SUC SemanticGroup* must therefore be extended to allow subordinate *ReferencedPictures* and *PictureFrames*, respectively. *SUC PictureFrame* and *SUC ReferencedPicture* use *RC HasExternalMtpContext*, specified in Appendix~[Model Definitions](#subsec:AnhangManifestModelle), to reference external objects from other MTP files. The new and extended model definitions are specified in detail in Appendix~[Model Definitions](#subsec:AnhangHMISetModelle) and are assigned to the new profile *ModuleTypePackage:HMISet.Composed V2.0.0*.[^3]

![Extension of the HMISet for Representing Line Process Pictures](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/HMISet Erweiterungen/Klassendiagramm.drawio.png)
*Extension of the HMISet for Representing Line Process Pictures* {#fig:ErweiterungHMISet}

### Model Definitions {#subsec:AnhangHMISetModelle}
#### Specification of the System Unit Class PictureFrame
*SUC PictureFrame* (Table~[Suc Picture Frame](#tab:SucPictureFrame)) enables the embedding of a referenced process picture into another process picture. For this purpose, the process picture to be displayed in the *PictureFrame* is referenced by means of *PictureLink* using the ID link mechanism according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). The *Picture-Frame* itself can be placed in a process picture of *SUC Picture* or, if applicable, in a contained *SUC SemanticGroup*, analogous to a *VisualObject* according to [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2). The size and position of the *PictureFrame* are defined by the variables *Width*, *Height*, *X*, *Y*, and *ZIndex*.[^4] If a process picture modeled in another MTP is to be displayed in the *PictureFrame* for example, a line process picture according to Section~[Linien Bedienbild](#subsec:LinienBedienbild), *RC HasExternalMtpContext* must additionally be annotated as an SRC. This enables the referenced MTP file to be addressed by entering a *ContextLink*.

<a id="tab:SucPictureFrame"></a>
**Table: Model Definition of *SUC PictureFrame***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>PictureFrame</strong></td>
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
		<td colspan="3">model definition for including a process picture into another process picture</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPHMISUCLib/PictureFrame</td>
	</tr>
	<tr>
		<th>AutomationML BaseRef</th>
		<td colspan="3">-</td>
	</tr>
	<tr>
		<th>RoleClasses</th>
		<td colspan="3">[1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC)<br>[0..1] MTPRCLib/HasExternalMtpContext (SRC)<sup>a)</sup></td>
	</tr>
	<tr>
		<th>Version</th>
		<td colspan="3">ModuleTypePackage:HMISet.Composed V2.0.0</td>
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
		<td>PictureLink</td>
		<td>xs:string (GUID-formatted)</td>
		<td>object identifier of the referenced picture</td>
		<td>IDLinkAttribute-Type</td>
	</tr>
	<tr>
		<td>Width</td>
		<td>xs:unsignedInt</td>
		<td>width of the picture frame</td>
		<td>-</td>
	</tr>
	<tr>
		<td>Height</td>
		<td>xs:unsignedInt</td>
		<td>height of the picture frame</td>
		<td>-</td>
	</tr>
	<tr>
		<td>X</td>
		<td>xs:unsignedInt</td>
		<td>X coordinate of the upper left corner of the picture frame</td>
		<td>-</td>
	</tr>
	<tr>
		<td>Y</td>
		<td>xs:unsignedInt</td>
		<td>Y coordinate of the upper left corner of the picture frame</td>
		<td>-</td>
	</tr>
	<tr>
		<td>ZIndex</td>
		<td>xs:unsignedInt</td>
		<td>index of the HMI layer the picture frame is located</td>
		<td>-</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 Comment</strong></td>
	</tr>
	<tr>
		<td colspan="4"><sup>a)</sup> The RC HasExternalMtpContext has to be added, if the referenced picture is located in another MTP file.</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Object - Instance Constraints</strong></td>
	</tr>
	<tr>
		<th>Allowed Parents</th>
		<td colspan="3">IE of SUC Picture<br>IE of SUC SemanticGroup</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">(no children allowed)</td>
	</tr>
</table>

#### Extension of the System Unit Class Picture
*SUC Picture* (Table~[Suc Picture](#tab:SucPicture)) is the base class for modeling a process picture. This model definition is already defined in the MTP specification [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2) and is extended in this dissertation by the capability to include *PictureFrames*.

<a id="tab:SucPicture"></a>
**Table: Model Definition of *SUC Picture***

<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>Picture</strong></td>
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
		<td colspan="3">object containing all picture elements to be displayed in a view</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPHMISUCLib/Picture</td>
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
		<td colspan="3">ModuleTypePackage:HMISet.Composed V2.0.0</td>
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
		<td>Width</td>
		<td>xs:unsignedInt</td>
		<td>width of the original graphic</td>
		<td>-</td>
	</tr>
	<tr>
		<td>Height</td>
		<td>xs:unsignedInt</td>
		<td>height of the original graphic</td>
		<td>-</td>
	</tr>
	<tr>
		<td>HierarchyLevel</td>
		<td>xs:string (formatted)</td>
		<td>indication of the detail depth of the HMI</td>
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
		<td colspan="3">IH to which an IE of SUC HMISet relates via EI of IC AspectSetReference</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">[0..*] IEs of SUC SemanticGroup<br>[0..*] IEs of SUC VisualObject<br>[0..*] IEs of SUC TopologyObject<br>[0..*] IEs of SUC Connection<br>[0..*] IEs of SUC PictureFrame</td>
	</tr>
</table>

#### Extension of the System Unit Class SemanticGroup
*SUC SemanticGroup* (Table~[Suc Semantic Group](#tab:SucSemanticGroup)) is used to mark semantically related elements in process pictures. This model definition is already defined in the MTP specification [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2) and is extended in this dissertation by the capability to include *PictureFrames*.

<a id="tab:SucSemanticGroup"></a>
**Table: Model Definition of *SUC SemanticGroup***
<table>
	<tr>
		<td colspan="4"><strong>▶ Module Type Package - Model Definition</strong></td>
	</tr>
	<tr>
		<th>Name</th>
		<td colspan="3"><strong>SemanticGroup</strong></td>
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
		<td colspan="3">object indicating that the subordinate symbols belong together</td>
	</tr>
	<tr>
		<th>AutomationML Path</th>
		<td colspan="3">MTPHMISUCLib/SemanticGroup</td>
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
		<td colspan="3">ModuleTypePackage:HMISet.Composed V2.0.0</td>
	</tr>
	<tr>
		<td colspan="4"><strong>📌 AutomationML Properties</strong></td>
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
		<td colspan="3">IE of SUC Picture<br>IE of SUC SemanticGroup</td>
	</tr>
	<tr>
		<th>Allowed Children</th>
		<td colspan="3">[0..*] IEs of SUC Semantic Group<br>[0..*] IEs of SUC VisualObject<br>[0..*] IEs of SUC TopologyObject<br>[0..*] IEs of SUC Connection<br>[0..*] IEs of SUC PictureFrame</td>
	</tr>
</table>


## MTP Extension of the DataAssemblySet {#sec:AnhangDataAssemblySet}
This chapter specifies all identified extensions of the *DataAssemblySet* and integrates them into the existing MTP specification [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3).

### Übersicht {#subsec:AnhangDataAssemblySetUebersicht}
#### Extension of the IndicatorElements
According to Chapters~[Reportwerte](#sec:Reportwerte) and [Lea Hmi](#sec:LeaHmi), the two interface definitions *SUC StructView* and *SUC ArrayView* are required for value displays in LEA HMIs and for mapping report values on LEA services. According to Section~[Prozesswerte](#sec:Prozesswerte), *StructView* is also required for process-value outputs of structured data types. As shown in Figure~[Extension of the DataAssemblySet for Implementing Structured and Array-Based IndicatorElements](#fig:ErweiterungIndicatorElement), *SUC StructView* and *SUC ArrayView*, together with all other interface definitions for report values, are derived from the interface definition *SUC IndicatorElement* according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3) and organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangDataAssemblySetSchnittstellen). This extension, as a result of this dissertation, has already been adopted into the profile *ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0* of the MTP specification [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3).

![Extension of the DataAssemblySet for Implementing Structured and Array-Based IndicatorElements](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/IndicatorElement/Klassendiagramm.drawio.png)
*Extension of the DataAssemblySet for Implementing Structured and Array-Based IndicatorElements* {#fig:ErweiterungIndicatorElement}

#### Extension of the OperationElements
According to Section~[Lea Hmi](#sec:LeaHmi), the new interface definitions *SUC StructMan*, *SUC StructManInt*, *SUC ArrayMan*, and *SUC ArrayManInt* are required for operator-driven value manipulation in LEA HMIs. As shown in Figure~[Extension of the DataAssemblySet for Implementing Structured and Array-Based OperationElements](#fig:ErweiterungOperationElement), *SUC StructMan* and *SUC ArrayMan*, together with all other interface definitions for value manipulation, are derived from the interface definition *SUC OperationElement* according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). *SUC StructManInt* is derived from *SUC StructMan*, and *SUC ArrayManInt* from *SUC ArrayMan*. All four interface definitions are organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangDataAssemblySetSchnittstellen). This extension, as a result of this dissertation, has already been adopted into the profile *ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0* of the MTP specification [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3).

![Extension of the DataAssemblySet for Implementing Structured and Array-Based OperationElements](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/OperationElement/Klassendiagramm.drawio.png)
*Extension of the DataAssemblySet for Implementing Structured and Array-Based OperationElements* {#fig:ErweiterungOperationElement}

#### Extension of DINT-Based Interfaces with Time Formats
According to Section~[Schnittstelle Transportdienst](#subsec:SchnittstelleTransportdienst), report values in a time format are required for the timestamps of a transport service. For this purpose, *RC HasTimeFormat* is introduced. As shown in Figure~[Extension of the DataAssemblySet for Interpreting DINT Values in a Time Format](#fig:ErweiterungTimeFormat), this RC can be added as an SRC to all DINT-based interface definitions, in particular to *SUC DIntView*, *SUC DIntMan*, *SUC DIntServParam*, and *SUC DIntProcessValueIn*. *RC HasTimeFormat* is organized in the newly introduced *RCL MTPDataAssemblyRCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangDataAssemblySetSchnittstellen). 

*RC HasTimeFormat* uses a new *AT TimeFormatAttributeType* to specify the time format in which a DINT value is to be interpreted. As shown in Figure~[Extension of the DataAssemblySet for Interpreting DINT Values in a Time Format](#fig:ErweiterungTimeFormat), this AT is organized in *ATL MTPDataAssemblyATLib*. The detailed specification is provided in Appendix~[Model Definitions](#subsec:AnhangDataAssemblySetModelle).

These extensions are assigned to the newly introduced profile *ModuleTypePackage:DataAssemblySet.Time V2.0.0*.[^5]

![Extension of the DataAssemblySet for Interpreting DINT Values in a Time Format](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Zeitformate/Klassendiagramm.drawio.png)
*Extension of the DataAssemblySet for Interpreting DINT Values in a Time Format* {#fig:ErweiterungTimeFormat}

### Interface Definitions {#subsec:AnhangDataAssemblySetSchnittstellen}
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
*Modeling of a User-Defined Data Type* {#fig:CustomDatatypeModellierung}

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
*SUC DIntView* (Table~[Data Assembly Suc D Int View](#tab:DataAssemblySucDIntView)) is used to display DINT values of an LEA. This interface definition is already specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3) and is extended in this dissertation by the capability to annotate *RC HasTimeFormat* as an SRC.[^6]

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

### Model Definitions {#subsec:AnhangDataAssemblySetModelle}
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


## MTP Extension of the ServerAssemblySet
This chapter specifies all identified extensions of the *ServerAssemblySet* and integrates them into the existing MTP specification [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51) and [MTP Specification Part 5](../98_References/README.md#mtp-specification-part-5), respectively.

#### Mapping Complex Data Types in OPC~UA
The specification chapters~[MTP Extension of the DataAssemblySet](#sec:AnhangDataAssemblySet), [MTP Extension of the ServiceSet](#sec:AnhangServiceSet), and [MTP Extension of the ProcessValueSet](#sec:AnhangProcessValueSet) described interface definitions with complex data types, Struct and Array. To transmit these data types via OPC~UA, not only the existing primitive data types but also the mapping of complex data types into the address space of the OPC~UA server of an LEA must be specified.

Figure~[Mapping of Structured Data Types in OPC UA Based on PNO.2025.Part5](#fig:StructOPCUA) shows the mapping of variables of **structured data types** in OPC~UA. 

![Mapping of Structured Data Types in OPC UA Based on PNO.2025.Part5](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Komplexe Datentypen/Komplexe_Typen_OPC_UA.drawio.png)
*Mapping of Structured Data Types in OPC UA Based on PNO.2025.Part5* {#fig:StructOPCUA}

Variables of a structured data type have a *HasTypeDefinition* to an OPC~UA *VariableType* that describes the underlying structure. This *VariableType* has a data type that is an OPC~UA *DataType*. This *DataType*, in turn, has a *StructureDefinition* that contains a list of *StructureFields*, not shown in the figure. These *StructureFields* correspond to the subordinate variables of the *VariableType* and thus to the complex data type to be mapped. This modeling of structured data types is possible with the native OPC~UA means according to [OPC 10000-3](../98_References/README.md#opc-10000-3). As a result of this dissertation, it has already been adopted into the profile *ModuleTypePackage:ServerAssemblySet.OPCUA V2.0.0* of the MTP specification [MTP Specification Part 5](../98_References/README.md#mtp-specification-part-5).

Variables with **array data types** do not require additional rules for mapping to OPC~UA. By using the multiplexing mechanism, the arrays are represented in OPC~UA in the form of primitive or structured data types. 


## MTP Specification of the ChoreographySet {#sec:AnhangChoreoAspekt}
This chapter specifies the *ChoreographySet* as a new aspect of the MTP specification that contains all elements identified in the conceptual chapter~[Art2 LL](#chap:Art2LL).
 
### Übersicht {#subsec:AnhangChoreographySetUebersicht}
According to Chapter~[Art2 LL](#chap:Art2LL), a series of new model and interface definitions is required to represent choreography-relevant information in the MTP of an LEA. Figure~[Specification of the ChoreographySet for Implementing Choreography-Based Logistics Lines](#fig:AnhangUebersichtChoreoAspekt) provides an overview of these newly specified definitions.

![Specification of the ChoreographySet for Implementing Choreography-Based Logistics Lines](Inhalt/Abbildungen/99_Anhang/Spezifikation_Choreografie/Klassendiagramm.drawio.png)
*Specification of the ChoreographySet for Implementing Choreography-Based Logistics Lines* {#fig:AnhangUebersichtChoreoAspekt}

#### Interface Definitions
On the interface-definition side, *SUC ChoreographyParticipantManager* is introduced as an interface for configuring configurable logic, and *SUC CommunicationManager* is introduced as an interface for configurable communication. *SUC CommunicationManager* is an abstract interface definition that fundamentally allows the use of different communication technologies through different derivations. For implementation based on OPC~UA client/server, the derived *SUC OpcUaClientServerManager* is introduced. A convention in the MTP specifications provides that interface definitions belonging together in terms of content are derived from a common interface definition with the suffix **Element*. Accordingly, in this case *SUC ChoreographyElement*, derived from *SUC DataAssembly* [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3), is introduced, from which *SUC ChoreographyParticipantManager* and *SUC CommunicationManager* are derived.

For individual values exchanged and processed within a choreography, *SUC UnionElement*, derived from *SUC DataAssembly* [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1), is introduced according to Section~[Union Type](#subsec:UnionType) to display a value with configurable data type. For the communication variant of active writing, *SUC WritableUnionElements*, derived from *SUC UnionElement*, is additionally provided[^7] and enables write access to a value with configurable data type. 

These interface definitions are organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangChoreographySetSchnittstellen). 

#### Model Definitions
On the model-definition side, *SUC ChoreographySet* is introduced as a new aspect set for organizing all choreography-related models and is derived from the abstract *SUC MTPSet* according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). The *ChoreographySet* always contains exactly one IE of *SUC ChoreographyParticipant*, derived from *SUC LinkedObject* [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). It indicates that an LEA has the capability to participate in a choreography and is linked to a *ChoreographyParticipantManager* interface. The input list and output list of the choreography participant are represented by the subordinate *SUC InputList* and *SUC OutputList*. These lists can contain any number of IEs of *SUC InputElemente* and *SUC OutputElement*. They are derived from *SUC LinkedObject* and represent incoming or outgoing system variables. According to Section~[Choreo Konfiguration](#subsec:ChoreoKonfiguration), the classes *SUC FixedInputElement*, *SUC ConfigurableInputElement*, *SUC WritableInputElement*, *SUC FixedOutputElement*, and *SUC ConfigurableOutputElement* are provided as concrete derivations of *SUC InputElemente* and *SUC OutputElement*. Almost all *InputElements* and *OutputElements* are linked to a *UnionElement* interface via LinkedObject relations. An exception is formed by *WritableInputElements*, each of which is assigned to a *WritableUnionElement* interface. In the case of *ConfigurableInputElements* and *ConfigurableOutpuElements*, an ID link relation to a *CommunicationManager* interface also exists, which handles value transfer in the sense of configurable communication. The model definitions are organized in the newly introduced library *SUCL MTPChoreographySUCLib*. The detailed specification is provided in Appendix~[Model Definitions](#subsec:AnhangChoreographySetModelle).

All model and interface definitions required for the *ChoreographySet* are assigned to the new profile *ModuleTypePackage:ChoreographySet.Base V2.0.0*.[^8]

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


## MTP Specification of the TransportSet {#sec:AnhangTransportAspekt}
This chapter specifies the *TransportSet* as a new aspect of the MTP specification that contains all elements identified in the conceptual chapter~[Art3 LA](#chap:Art3LA).

### Übersicht {#subsec:AnhangTransportSetUebersicht}
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
*Specification of the TransportSet for Connecting Flexible Transport Systems to LEAs* {#fig:AnhangUebersichtTransportAspekt}

On the **interface-definition** side, *SUC TransportClientManager* is introduced as an interface definition for configuring and establishing a communication link between an LEA and transport management. It is an abstract interface definition that fundamentally allows the use of different communication technologies through different derivations. For implementation based on OPC~UA client/server, the derived *SUC OpcUaTransportClientManager* is introduced. In addition, *SUC TransportNodeManager* is introduced as an interface that enables the assignment of a transport node of an LEA to the associated TN proxy in transport management. A convention in the MTP specifications provides that interface definitions belonging together in terms of content are derived from a common interface definition with the suffix **Element*. Accordingly, in this case *SUC TransportElement*, derived from *SUC DataAssembly* [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3), is introduced, from which *SUC TransportClientManager* and *SUC TransportNodeManager* are derived. These interface definitions are organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Interface Definitions](#subsec:AnhangTransportSetSchnittstellen). 

On the **model-definition** side, *SUC TransportSet* is introduced as a new aspect set for organizing all transport-relevant models and is derived from the abstract *SUC MTPSet* according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). The *TransportSet* indicates that an LEA has the capability to be connected to a flexible transport system according to the concepts of this dissertation and contains all model definitions required for this purpose. In particular, this consists of any number of IEs of *SUC TransportNode*. The latter is an abstract class for representing transport nodes and is derived from *SUC LinkedObject*. The concrete derivations provided are *SUC InboundNode*, *SUC OutboundNode*, *SUC InOutboundNode*, *SUC ProcessingNode*, and *SUC OrderNode*. All *TransportNodes* are linked to one *TransportClientManager* interface each by means of an ID link relation and to one *TransportNodeManager* interface by means of LinkedObject relations. The model definitions are organized in the newly introduced library *SUCL MTPTransportSUCLib*. The detailed specification is provided in Appendix~[Model Definitions](#subsec:AnhangTransportSetModelle). 

All model and interface definitions required for the *TransportSet* are assigned to the new profile *ModuleTypePackage:TransportSet.Base V2.0.0*.
 
### Interface Definitions {#subsec:AnhangTransportSetSchnittstellen}
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

### Model Definitions {#subsec:AnhangTransportSetModelle}
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


## Conformity Declaration for Logistics Equipment Assemblies {#sec:Konformitätsbeschreibung}
Based on the findings of this dissertation, Table~[Konformitätsbeschreibung](#tab:Konformitätsbeschreibung) provides an overview of the existing and newly introduced profiles required for applying the MTP concept in production-related logistics. A distinction is made between profiles that are generally relevant for LEA automation, profiles that LEAs must fulfill in order to participate in a logistics line, and profiles required for connecting LEAs to flexible transport systems.

% Konformitätsbeschreibung
<a id="tab:Konformitätsbeschreibung"></a>
**Table: Profiles to Be Implemented for Applying the MTP Concept in Production-Related Logistics; &times; - profile is required; (&times;) - profile is optional; empty - profile is not required**

<table>
	<tr>
		<th>Profil</th>
		<th>LEA-Automati-sierung</th>
		<th>Teilnahme Logistics Line</th>
		<th>Anbindung Transportsystem</th>
	</tr>
	<tr>
		<td colspan="4"><strong>Manifest</strong></td>
	</tr>
	<tr>
		<td>ModuleTypePackage:Manifest.Base</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td>ModuleTypePackage:Manifest.Composed (neu)</td>
		<td></td>
		<td>&times;</td>
		<td></td>
	</tr>
	<tr>
		<td colspan="4"><strong>AttachmentSet</strong></td>
	</tr>
	<tr>
		<td>ModuleTypePackage:AttachmentSet.Base</td>
		<td>(&times;)</td>
		<td>&times;</td>
		<td>(&times;)</td>
	</tr>
	<tr>
		<td colspan="4"><strong>TextSet</strong></td>
	</tr>
	<tr>
		<td>ModuleTypePackage:TextSet.Base</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td colspan="4"><strong>HMISet</strong></td>
	</tr>
	<tr>
		<td>ModuleTypePackage:HMISet.Base</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td>ModuleTypePackage:HMISet.Composed (neu)</td>
		<td></td>
		<td>&times;</td>
		<td></td>
	</tr>
	<tr>
		<td colspan="4"><strong>DataAssemblySet</strong></td>
	</tr>
	<tr>
		<td>ModuleTypePackage:DataAssemblySet.Base</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td>ModuleTypePackage:DataAssemblySet. ComplexTypes (neu)</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td>ModuleTypePackage:DataAssemblySet. Time (neu)</td>
		<td>(&times;)</td>
		<td>(&times;)</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td colspan="4"><strong>ServiceSet</strong></td>
	</tr>
	<tr>
		<td>ModuleTypePackage:ServiceSet.Base</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td>ModuleTypePackage:ServiceSet. ComplexTypes (neu)</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td>ModuleTypePackage:ServiceSet.Logistics (neu)</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td colspan="4"><strong>ProcessValueSet</strong></td>
	</tr>
	<tr>
		<td>ModuleTypePackage:ProcessValueSet.Base</td>
		<td>(&times;)</td>
		<td>(&times;)</td>
		<td>(&times;)</td>
	</tr>
	<tr>
		<td>ModuleTypePackage:ProcessValueSet. ComplexTypes (neu)</td>
		<td>(&times;)</td>
		<td>(&times;)</td>
		<td>(&times;)</td>
	</tr>
	<tr>
		<td colspan="4"><strong>ServerAssemblySet</strong></td>
	</tr>
	<tr>
		<td>ModuleTypePackage:ServerAssemblySet. Base</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
	<tr>
		<td>ModuleTypePackage:ServerAssemblySet. OPCUA</td>
		<td>&times;</td>
		<td>&times;</td>
		<td>&times;</td>
	</tr>
</table>

It should be noted with regard to this list that this dissertation initially considers the core aspects of Parts 1 to 5 of the MTP specification. Logistics-specific extensions may also arise in further aspects of the MTP specification in the future. For example, it may become necessary to provide alarms at LEA level rather than at service or individual-control level. In addition, logistics-specific diagnostic functions may be required. These aspects should be investigated in future work, see also Chapter~[ausblick](#chap:ausblick).

[^1]: Appendix~[MTP Extension of the HMISet](#sec:AnhangHMISet) also describes that *RC HasExternalMtpContext* can be assigned to *SUC PictureFrame* and *SUC ReferencedPicture*.
[^2]: *AT ComposedTypeRevisionType* is therefore similar to *AT DeviceRevisionType*. However, while *AT DeviceRevisionType* refers only to the content of the *ServerAssemblySet* of one MTP, *AT ComposedTypeRevisionType* refers to the distributed content of the *ServerAssemblySets* of multiple MTPs.
[^3]: In this dissertation, *SUC PictureFrame* is initially assigned to the profile *ModuleTypePackage:HMISet.Composed V2.0.0* because it is used exclusively to embed external LEA process pictures into a Composed MTP. However, this SUC is also suitable for embedding MTP-internal process pictures in non-composed MTPs. Therefore, if it is adopted into the MTP specification in the future, it appears appropriate to define a separate profile for this SUC.
[^4]: This *PictureFrame* mechanism may also be useful in non-composed MTPs, for example to embed detail pictures into an overall picture of one PEA or LEA. In that case, *ContextLink* is not required. Within this dissertation, however, *SUC PictureFrame* is considered exclusively in the context of line process pictures in Composed MTPs.
[^5]: It is recommended to incorporate *RC HasTimeFormat* and the associated *AT TimeFormatAttributeType* into the base profile *ModuleTypePackage:DataAssemblySet.Base* in the future.
[^6]: Since only the extension of *SUC DIntView* is used in this dissertation, only this case is described here. *SUC DIntMan*, *SUC DIntServParam*, and *SUC DIntProcessValueIn* must be extended in the same way by assigning *RC HasTimeFormat*.
[^7]: This derivation is possible because a write access always includes reading back the written value. A write access is therefore an extension of a read access.
[^8]: *SUC CommunicationManager* and the derived *SUC OpcUaClientServerManager* can in principle also be used for configurable communication independently of choreographies, for example in decentralized orchestrations. Since such approaches are not yet provided in the MTP specification, these interface definitions are initially assigned to the *ChoreographySet*. For future cross-cutting use cases, a shift into the *ServerAssemblySet* [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51) may be appropriate.






