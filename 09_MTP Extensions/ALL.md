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
  <tr style="background-color: #E0E0E0;">
    <th colspan="4">Module Type Package - Model Definition</th>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0; width: 28%;">Name</th>
    <td colspan="3">**ComposedModuleTypePackage**</td>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">Type</th>
    <td colspan="3">SystemUnitClass (SUC)</td>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">Modifier</th>
    <td colspan="3">sealed</td>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">Description</th>
    <td colspan="3">model definition for the entry point of a Composed Module Type Package</td>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">AutomationML Path</th>
    <td colspan="3">MTPSUCLib/ComposedModuleTypePackage</td>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">AutomationML BaseRef</th>
    <td colspan="3">-</td>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">RoleClasses</th>
    <td colspan="3">[1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC)</td>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">Version</th>
    <td colspan="3">ModuleTypePackage:Manifest.Composed V2.0.0</td>
  </tr>
  <tr style="background-color: #E0E0E0;">
    <th colspan="4">AutomationML Properties</th>
  </tr>
  <tr style="background-color: #E0E0E0;">
    <th>Name</th>
    <th style="width: 30%;">Type</th>
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
  <tr style="background-color: #E0E0E0;">
    <th colspan="4">AutomationML Attributes</th>
  </tr>
  <tr style="background-color: #E0E0E0;">
    <th>Name</th>
    <th>Type</th>
    <th style="width: 54%;">Description</th>
    <th style="width: 31%;">AttributeType Reference</th>
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
  <tr style="background-color: #E0E0E0;">
    <th colspan="4">Comment</th>
  </tr>
  <tr>
    <td colspan="4">-</td>
  </tr>
  <tr style="background-color: #E0E0E0;">
    <th colspan="4">AutomationML Object - Instance Constraints</th>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">Allowed Parents</th>
    <td colspan="3">IH ModuleTypePackage</td>
  </tr>
  <tr>
    <th style="background-color: #E0E0E0;">Allowed Children</th>
    <td colspan="3">[0..1] IE of each derivation of SUC MTPSet<br>[1] IE of SUC AttachmentSet</td>
  </tr>
</table>

#### Specification of the Attribute Type ComposedTypeRevisionType
*AT ComposedTypeRevisionType* (Table~[At Composed Type Revision Type](#tab:AtComposedTypeRevisionType)) defines the version information of the communication-relevant interface content of a Composed MTP according to the rules of *Semantic Versioning*. This AT is derived from *AT SemanticVersionAttributeType*.

% Modelldefinition AT ComposedTypeRevisionType
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *AT ComposedTypeRevisionType*}
		{#tab:AtComposedTypeRevisionType}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ComposedTypeRevisionType**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Attribute Type (AT)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition of a composed type revision information} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPATLib/SemanticVersionAttributeType/ComposedTypeRevisionType} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPATLib/SemanticVersionAttributeType} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Data Type**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} xs:string} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Manifest.Composed V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the Role Class Library MTPRCLib
*RCL MTPRCLib* (Table~[Rcl MTPRC Lib](#tab:RclMTPRCLib)) contains the basic role classes for the *Manifest* of a Module Type Package. 

% Bibliothek RCL MTPRCLib
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Library Definition of *RCL MTPRCLib*}
		{#tab:RclMTPRCLib}\\
		\hline

		\multicolumn{3}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Library Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **MTPRCLib**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} RoleClassLibrary (RCL)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Library containing the Manifest RC model definitions of an MTP} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Manifest.Composed V2.0.0} 
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}    \\ \hline
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the Role Class HasExternalMtpContext
*RC HasExternalMtpContext* (Table~[Rc Has External Mtp Context](#tab:RcHasExternalMtpContext)) provides the capability to reference an object from an attached MTP file. For this purpose, the variable *ContextLink* is used to reference the MTP file that contains the object to be referenced by means of the ID link mechanism. To do so, the ID of the *IC AttachmentReference* of the corresponding MTP file is entered in the *ContextLink* variable. The referenced object itself can then be addressed according to the LinkedObject or ID link mechanism defined in [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1), or according to the CustomSymbols mechanism defined in Section~[Stat Hmi Objekte](#subsec:StatHmiObjekte), as if the object were located in the same MTP. *RC HasExternalMtpContext* can be annotated to derivations of *SUC LinkedObject*, *SUC PictureFrame*, and *SUC ReferencedPicture*. 

% Modelldefinition RC HasExternalMtpContext
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *RC HasExternalMtpContext*}
		{#tab:RcHasExternalMtpContext}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **HasExternalMtpContext**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Role Class (RC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Role Class for defining a referenced object originates from an external MTP context } 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPRCLib/HasExternalMtpContext} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Manifest.Composed V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ContextLink}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string (GUID-formatted)}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} object identifier of the referenced MTP in the attachment}              & 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} IDLinkAttribute-Type}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Annotations}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 	IE of SUC LinkedObject as SRC \newline
																IE of SUC PictureFrame as SRC \newline
																IE of SUC ReferencedPicture as SRC} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

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

% Modelldefinition SUC PictureFrame
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC PictureFrame*}
		{#tab:SucPictureFrame}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **PictureFrame**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for including a process picture into another process picture} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPHMISUCLib/PictureFrame} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 	[1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC) \newline
																[0..1] MTPRCLib/HasExternalMtpContext (SRC)\textsuperscript{a)}} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:HMISet.Composed V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} PictureLink}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string (GUID-formatted)}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} object identifier of the referenced picture} &  
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} IDLinkAttribute-Type}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Width}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} width of the picture frame} &  
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Height}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} height of the picture frame} &  
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} X}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} X coordinate of the upper left corner of the picture frame} &  
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Y}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} Y coordinate of the upper left corner of the picture frame} &  
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ZIndex}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} index of the HMI layer the picture frame is located} &  
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} The RC HasExternalMtpContext has to be added, if the referenced picture is located in another MTP file.}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 	IE of SUC Picture \newline
																IE of SUC SemanticGroup} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no children allowed)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Extension of the System Unit Class Picture
*SUC Picture* (Table~[Suc Picture](#tab:SucPicture)) is the base class for modeling a process picture. This model definition is already defined in the MTP specification [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2) and is extended in this dissertation by the capability to include *PictureFrames*.

% Modelldefinition SUC Picture
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC Picture*}
		{#tab:SucPicture}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **Picture**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} object containing all picture elements to be displayed in a view} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPHMISUCLib/Picture} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{ModuleTypePackage:HMISet.Composed V2.0.0}} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Width}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} width of the original graphic}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Height}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} height of the original graphic}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} HierarchyLevel}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string (formatted)}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} indication of the detail depth of the HMI}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IH to which an IE of SUC HMISet relates via EI of IC AspectSetReference} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 	[0..*] IEs of SUC SemanticGroup \newline
																[0..*] IEs of SUC VisualObject \newline
																[0..*] IEs of SUC TopologyObject \newline
																[0..*] IEs of SUC Connection \newline
																\textcolor{red}{[0..*] IEs of SUC PictureFrame}} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Extension of the System Unit Class SemanticGroup
*SUC SemanticGroup* (Table~[Suc Semantic Group](#tab:SucSemanticGroup)) is used to mark semantically related elements in process pictures. This model definition is already defined in the MTP specification [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2) and is extended in this dissertation by the capability to include *PictureFrames*.

% Modelldefinition SUC SemanticGroup
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC SemanticGroup*}
		{#tab:SucSemanticGroup}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **SemanticGroup**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} object indicating that the subordinate symbols belong together} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPHMISUCLib/SemanticGroup} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{ModuleTypePackage:HMISet.Composed V2.0.0}} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 	IE of SUC Picture \newline
																IE of SUC SemanticGroup} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 	[0..*] IEs of SUC Semantic Group \newline
																[0..*] IEs of SUC VisualObject \newline
																[0..*] IEs of SUC TopologyObject \newline
																[0..*] IEs of SUC Connection \newline
																\textcolor{red}{[0..*] IEs of SUC PictureFrame}} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class ReferencedPicture
*SUC ReferencedPicture* (Table~[Suc Referenced Picture](#tab:SucReferencedPicture)) enables the embedding of a referenced process picture or an entire process-picture hierarchy from another LEA MTP into the local process-picture hierarchy, for example by embedding the process pictures of the individual LEAs of a logistics line into the corresponding Composed MTP. For this purpose, *RC HasExternalMtpContext* is annotated as an SRC. By entering a *ContextLink*, it enables a reference to the MTP file that contains the referenced process picture or referenced process-picture hierarchy. When a single process picture is embedded, the specific process picture to be embedded is referenced via *PictureLink* using the ID link mechanism according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). When an entire process-picture hierarchy is embedded, the variable *PictureLink* is left empty. In both cases, the variable *HierarchyLevel* is used to position the referenced process picture or referenced process-picture hierarchy within the local process-picture hierarchy.

% Modelldefinition SUC ReferencedPicture
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ReferencedPicture*}
		{#tab:SucReferencedPicture}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ReferencedPicture**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model to reference to a picture of another MTP file
		} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPHMISUCLib/ReferencedPicture} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 	[1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC) \newline
																[1] MTPRCLib/HasExternalMtpContext (SRC)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:HMISet.Composed V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} PictureLink}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string (GUID-formatted)}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} Object identifier of the referenced picture within the attached MTP} &  
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} IDLinkAttribute-Type}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} HierarchyLevel}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string (formatted)}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} Indication of the detail depth of the referenced process picture}              & 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IH to which an IE of SUC HMISet relates via EI of IC AspectSetReference} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no children allowed)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Extension of the System Unit Class HMISet
*SUC HMISet* (Table~[Suc HMI Set](#tab:SucHMISet)) is the base class for modeling all process-picture-related information of an MTP. This model definition is already defined in the MTP specification [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2) and is extended in this dissertation by the capability to include *ReferencedPictures*.

% Modelldefinition SUC HMISet
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC HMISet*}
		{#tab:SucHMISet}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **HMISet**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Module Type Package aspect set for operator pictures} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPHMISUCLib/HMISet} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/MTPSet} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{ModuleTypePackage:HMISet.Composed V2.0.0}} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1] EI of IC AspectSetReference which refers via ID to an IH containing [0..*] IEs of SUC Picture\newline \textcolor{red}{[0..*] IEs of SUC ReferencedPicture}} 
		\\ \hline

	\end{longtable}
\end{footnotesize}


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

% Schnittstellendefinition SUC StructView
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC StructView*}
		{#tab:DataAssemblySucStructView}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **StructView**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for displaying a value of structured data following the rules of modelling complex data types} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/IndicatorElement/StructView} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/IndicatorElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} V}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \textlangle empty\textrangle}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \{AT of StructuredDataType\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type}            
		\\ \hline

	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

The distinctive feature of this interface definition is the use of a user-defined structured data type. Figure~[Modeling of a User-Defined Data Type](#fig:CustomDatatypeModellierung) shows how such a data type can be modeled. For this purpose, the rules for modeling complex data types from [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51) are applied.

%TODO @Format: Bild schärfer machen!
![Modeling of a User-Defined Data Type](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Parameter/Modelling_Custom_Datatype.png)
*Modeling of a User-Defined Data Type* {#fig:CustomDatatypeModellierung}

The complex data type used must be derived from *AT StructuredDataType* defined in [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51). When this interface is used, a user-defined ATL must be created, here: CompanyAAttributeLib. Within this ATL, the structured data type that is later to be used in the IE of *SUC StructView* must be specified. By assigning this user-defined AT to the attribute *VType* of *SUC StructView*, the structured data type used is defined. This data type is then expected in the variable *V*. 

**Note:** If the *StructView* interface is used as a report value, it can be "frozen" by the variable *ReportValueFreeze* at the *ServiceControl* interface according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). Optionally, it can be extended by a *MissedValue* variable by assigning *RC MissedValueFlag*. 

#### Specification of the System Unit Class ArrayView
*SUC ArrayView* (Table~[Data Assembly Suc Array View](#tab:DataAssemblySucArrayView)) is used by the LOL to display the value at a specific position of an array located in an LEA.

% Schnittstellendefinition SUC ArrayView
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ArrayView*}
		{#tab:DataAssemblySucArrayView}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ArrayView**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for displaying a value at a specific position of an array located in a PEA by a POL} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/IndicatorElement/ArrayView} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/IndicatorElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} OSLevel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} OSLevel variable}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} OSLevel}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Index Select Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMin}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Low Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMax}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} High Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Current Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} V}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Output Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} a)}                &    
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Values}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \{AT derived from BaseData-Type\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type}            
		\\ \hline
	


		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} Type shall be \textlangle empty\textrangle~in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

The challenge of this interface definition is that it must access an array inside the LEA that may have an arbitrary length. In common automation solutions, this is often impossible or possible only under certain conditions because of predefined types. Therefore, a multiplexing mechanism is used that enables access to an array of arbitrary length via a structurally static interface. 

By means of the *OSLevel* variable, it can be defined according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3) whether the interface is currently operated by the LOL or locally at the LEA. The variable *IndexSel* selects the array position to be displayed, similar to a pointer. The variables *IndexMin* and *IndexMax* specify the lower and upper limits of the array. The variable *IndexCur* specifies the currently selected index. The value of the array at this position is displayed in *V*. 

*VType* defines the data type shared by all array elements. This may be a primitive data type or a user-defined structured data type according to the description of *SUC StructView*.

**Note 1:** If the *ArrayView* interface is used as a report value, it can be "frozen" by the variable *ReportValueFreeze* at the *ServiceControl* interface according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). In this case, the entire array must be frozen, not only the currently selected value. Individual frozen values of the array can then be displayed by selecting the indices. Optionally, the *ArrayView* interface can be extended by a *MissedValue* variable by assigning *RC MissedValueFlag*. 

**Note 2:** If the *ArrayView* interface is used as a report value and several or all values of an array are to be read for documentation purposes, several or all indices between *IndexMin* and *IndexMax* must be entered successively by the LOL at the *ArrayView* interface. The values of the individual array elements can then be stored one after another. This must also work in the frozen state.

#### Specification of the System Unit Class StructMan
*SUC StructMan* (Table~[Data Assembly Suc Struct Man](#tab:DataAssemblySucStructMan)) is used by the LOL to manipulate an LEA variable of a user-defined structured data type.

% Schnittstellendefinition SUC StructMan
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC StructMan*}
		{#tab:DataAssemblySucStructMan}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **StructMan**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for manipulating a value of structured data type following the rules of modelling complex data types} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OperationElement/StructMan} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OperationElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VOut}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Value Output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VMan}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Manual Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VRbk}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Readback Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Readback}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VFbk}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Feedback}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Feedback}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \textlangle empty\textrangle}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \{AT of StructuredDataType\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type}            
		\\ \hline
	

		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

*VMan* is used to enter the desired value of the variable. Analogous to the concept described in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3), *VRbk* is used to verify the communication between an LOL and the *StructMan* interface within an LEA and indicates the raw value communicated to the LEA. *VOut* indicates the value passed to a further LEA-internal block, possibly with applied constraints. The variable *VFbk* is used to display the current value of the structure influenced by the *StructMan* interface. 

The distinctive feature of this interface definition is the use of a user-defined structured data type. The modeling and use of such a type have already been described in connection with *SUC StructView* and are applied in the same way for *SUC StructMan*. This data type is then expected behind the variables *VOut*, *VMan*, *VRbk*, and *VFbk*. 

#### Specification of the System Unit Class StructManInt
*SUC StructManInt* (Table~[Data Assembly Suc Struct Man Int](#tab:DataAssemblySucStructManInt)) is used to manipulate an LEA variable of a user-defined structured data type within the LEA or by the LOL.

% Schnittstellendefinition SUC StructManInt
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC StructMan*}
		\caption{Interface Definition of *SUC StructManInt*}
		\caption{Interface Definition of *SUC ArrayMan*}
		\caption{Interface Definition of *SUC ArrayManInt*}
		\caption{Library Definition of *RCL MTPDataAssemblyRCLib*}
		\caption{Interface Definition of *RC HasTimeFormat*}
		\caption{Encoding of Time Formats}
		\caption{Interface Definition of *SUC DIntView*}
		\caption{Model Definition of *AT TimeFormatAttributeType*}
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **StructManInt**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for manipulating a value of structured data type following the rules of modelling complex data types by the LOL or from inside the LEA} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OperationElement/StructMan/ StructManInt} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OperationElement/StructMan} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Worst Quality Code variable}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} WQC}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} \textit{VMan \textsuperscript{a)}}}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \textit{LOL $\rightarrow$ LEA}}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \textit{\{VType\}}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} \textit{(relevant, if SrcManAct is true, see SourceMode) Manual Value}}              &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \textit{-}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \textit{-}}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} (relevant, if SrcIntAct is true, see SourceMode) Internal Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcChannel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode channel; 0: operator (*Op) shall be used; 1: automatic (*Aut) shall be used}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcManAut}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Request SourceMode to Manual by automatic (if SrcChannel is true); 1: request manual; 0: no operation}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcIntAut}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Request SourceMode to Internal by automatic (if SrcChannel is true); 1: request internal; 0: no operation}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcIntOp}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Request SourceMode to Internal by operator (if SrcChannel is false); 1: request internal; 0: no operation}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcManOp}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Request SourceMode to Manual by operator (if SrcChannel is false); 1: request manual; 0: no operation}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcIntAct}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} 1: internal mode active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
					
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcManAct}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} 1: manual mode active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline


		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} VMan is inherited from the StructMan interface. However, its meaning changes slightly in this case since it is only used when the SourceMode is set to manual.}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

The *StructManInt* interface extends the *StructMan* interface by internal value specification and a *SourceMode* according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). If the internal access channel is selected, an internal LEA value is used instead of the external value specification. Otherwise, the function of this interface is identical to that of the *StructMan* interface.

#### Specification of the System Unit Class ArrayMan
*SUC ArrayMan* (Table~[Data Assembly Suc Array Man](#tab:DataAssemblySucArrayMan)) is used by the LOL to manipulate a value at a specific position of an array located in an LEA.

% Schnittstellendefinition SUC ArrayMan
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ArrayMan*}
		{#tab:DataAssemblySucArrayMan}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ArrayMan**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for the POL to manipulate a value at a specific position of an array located in a LEA} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OperationElement/ArrayMan} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OperationElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Index Select Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMin}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Low Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMax}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} High Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Current Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VMan}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\} }               &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Manual Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VRbk}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Readback Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Readback}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VFbk}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}               &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Feedback}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Feedback}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VOut}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Value Output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Values}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \{AT derived from BaseData-Type\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} Type shall be \textlangle empty\textrangle~in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

As already described for the *ArrayView* interface, the challenge of this interface lies in accessing an array within an LEA that may have an arbitrary length. As described in the context of *SUC ArrayView*, access to this array is also index-based in the case of the *ArrayMan* interface.

The array position to be modified is selected via the variable *IndexSel*. The variables *IndexMin* and *IndexMax* specify the lower and upper limits of the array. The variable *IndexCur* specifies the currently selected index of the variable to be manipulated. The variable *VMan* is used to enter the desired value for the variable to be manipulated. Analogous to the concept specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3), *VRbk* is used to verify the communication between an LOL and the *ArrayMan* interface within an LEA and indicates the raw value of the variable communicated to the LEA. When a new index is selected, the variables *VMan* and *VRbk* are set to the value at the selected position in the array. *VOut* indicates the value passed to a further LEA-internal block, possibly with limitations. The variable *VFbk* is used to display the current value of the structure affected by the *ArrayMan* interface. *VType* defines the data type shared by all array elements. This may be a primitive data type or a user-defined structured data type.

#### Specification of the System Unit Class ArrayManInt
*SUC ArrayManInt* (Table~[Data Assembly Suc Array Man Int](#tab:DataAssemblySucArrayManInt)) is used by the LOL or by LEA-internal logic to manipulate a value at a specific position of an array located in an LEA.

% Schnittstellendefinition SUC ArrayManInt
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ArrayManInt*}
		{#tab:DataAssemblySucArrayManInt}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ArrayManInt**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for the POL or for a PEA internal logic to manipulate a value at a specific position of an array located in a PEA} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OperationElement/ArrayMan/ ArrayManInt} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OperationElement/ArrayMan} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Worst Quality Code variable}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} WQC}            
		\\ \hline
	

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} \textit{VMan \textsuperscript{a)}}}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \textit{LOL $\rightarrow$ LEA}}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \textit{\{VType\}}  }              &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} \textit{(relevant, if SrcManAct is true, see SourceMode) Manual Value} }              &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \textit{-} }               &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \textit{-} }           
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} (relevant, if SrcIntAct is true, see SourceMode) Internal Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcChannel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode channel; 0: operator (*Op) shall be used; 1: automatic (*Aut) shall be used.
		}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcManAut}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Request SourceMode to Manual by automatic (if SrcChannel is true); 1: request manual; 0: no operation}    &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcIntAut}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Request SourceMode to Internal by automatic (if SrcChannel is true); 1: request internal; 0: no operation}    &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcIntOp}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Request SourceMode to Internal by operator (if SrcChannel is false); 1: request internal; 0: no operation}    &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcManOp}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Request SourceMode to Manual by operator (if SrcChannel is false); 1: request manual; 0: no operation}  &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcIntAct}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} 1: internal mode active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} SrcManAct}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} 1: manual mode active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} SourceMode}            
		\\ \hline
	

		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} VMan is inherited from the ArrayMan interface. However, its meaning changes slightly in this case since it is only used when the SourceMode is set to manual.}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

The *ArrayManInt* interface extends the *ArrayMan* interface by internal value specification and a *SourceMode* according to [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). If the internal access channel is selected, an internal LEA value is used instead of the external value specification. Otherwise, the function of this interface is identical to that of the *ArrayMan* interface.

#### Specification of the Role Class Library MTPDataAssemblyRCLib
*RCL MTPDataAssemblyRCLib* (Table~[Rcl MTP Data Assembly RC Lib](#tab:RclMTPDataAssemblyRCLib)) contains the DataAssembly-related role classes of a Module Type Package.

% Bibliothek RCL MTPDataAssemblyRCLib
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Library Definition of *RCL MTPDataAssemblyRCLib*}
		{#tab:RclMTPDataAssemblyRCLib}\\
		\hline
		\caption{Library Definition of *RCL MTPDataAssemblyRCLib*}
		\multicolumn{3}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Library Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **MTPDataAssemblyRCLib**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} RoleClassLibrary (RCL)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Library containing all DataAssembly-realted role classes of an MTP} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.Time V2.0.0} 
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}                                                                                                                 \\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the Role Class HasTimeFormat
*RC HasTimeFormat* (Table~[Data Assembly Rc Has Time Format](#tab:DataAssemblyRcHasTimeFormat)) indicates that a DINT-based interface is to be interpreted in a time format. This RC can be assigned as an SRC to the interface definitions *SUC DIntView*, *SUC DIntMan*, *SUC DIntServParam*, and *SUC DIntProcessValueIn*. *RC HasTimeFormat* provides different formats for interpreting DINT values as time values, encoded in the variable *TimeFormat*. The meaning of the values of this variable is shown in Table~[Zeitformate](#tab:Zeitformate).

% Schnittstellendefinition RC HasTimeFormat
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *RC HasTimeFormat*}
		{#tab:DataAssemblyRcHasTimeFormat}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **HasTimeFormat**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Role Class (RC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Role Class to assign a time format interpretation to a DINT-based interface} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblyRCLib/HasTimeFormat} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.Time V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} TimeFormat}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Time format as defined in\newline Table~[Zeitformate](#tab:Zeitformate)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} TimeFormat-Attribute-Type}                &   
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Annotations}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IE of SUC DIntView as SRC\newline
																IE of SUC DIntMan as SRC\newline
																IE of SUC DIntServParam as SRC\newline
																IE of SUC DIntProcessValueIn as SRC} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize} 

% Zeitformate
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Encoding of Time Formats}
		{#tab:Zeitformate}\\
		\hline

		\multicolumn{1}{|L{1cm}|}{\cellcolor[HTML]{E0E0E0}**ID**}        & 
		\multicolumn{1}{L{2cm}|}{\cellcolor[HTML]{E0E0E0} **Name**} &
		\multicolumn{1}{L{7cm}|}{\cellcolor[HTML]{E0E0E0} **Beschreibung**}
		\\ \hline

		
		\multicolumn{1}{|L{1cm}|}{\cellcolor[HTML]{FFFFFF} 0}        & 
		\multicolumn{1}{L{2cm}|}{\cellcolor[HTML]{FFFFFF} None} &
		\multicolumn{1}{L{7cm}|}{\cellcolor[HTML]{FFFFFF} kein Format}
		\\ \hline

		\multicolumn{1}{|L{1cm}|}{\cellcolor[HTML]{FFFFFF} 1}        & 
		\multicolumn{1}{L{2cm}|}{\cellcolor[HTML]{FFFFFF} TIME} &
		\multicolumn{1}{L{7cm}|}{\cellcolor[HTML]{FFFFFF} DINT-Wert gibt eine Zeitspanne in Millisekunden (ms) an}
		\\ \hline
		
		\multicolumn{1}{|L{1cm}|}{\cellcolor[HTML]{FFFFFF} 2}        & 
		\multicolumn{1}{L{2cm}|}{\cellcolor[HTML]{FFFFFF} TIME\_OF\_ DAY (TOD)} &
		\multicolumn{1}{L{7cm}|}{\cellcolor[HTML]{FFFFFF} DINT-Wert gibt die Tageszeit in Millisekunden seit Mitternacht an}
		\\ \hline

		\multicolumn{1}{|L{1cm}|}{\cellcolor[HTML]{FFFFFF} 3}        & 
		\multicolumn{1}{L{2cm}|}{\cellcolor[HTML]{FFFFFF} DATE} &
		\multicolumn{1}{L{7cm}|}{\cellcolor[HTML]{FFFFFF} DINT-Wert gibt das Datum als Anzahl der Tage seit dem 01.01.1990 an}
		\\ \hline


	\end{longtable}
\end{footnotesize}

#### Extension of the System Unit Class DIntView
*SUC DIntView* (Table~[Data Assembly Suc D Int View](#tab:DataAssemblySucDIntView)) is used to display DINT values of an LEA. This interface definition is already specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3) and is extended in this dissertation by the capability to annotate *RC HasTimeFormat* as an SRC.[^6]

% Schnittstellendefinition SUC DIntView
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC DIntView*}
		{#tab:DataAssemblySucDIntView}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **DIntView**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} class used to display a double integer value of the LEA} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/IndicatorElement/DIntView} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/IndicatorElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [0..1] MTPTextRCLib/HasTextReference/HasEnumDefinition (SRC)\newline
															  \textcolor{red}{[0..1] MTPDataAssemblyRCLib/HasTimeFormat (SRC)}} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{ModuleTypePackage:DataAssemblySet.Time V2.0.0}} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} V}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VSclMin}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Value Scale Low Limit}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Scale Settings}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VSclMax}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Value Scale High Limit}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Scale Settings}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VUnit}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} INT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Value Unit}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Unit Settings}            
		\\ \hline


	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

### Model Definitions {#subsec:AnhangDataAssemblySetModelle}
#### Specification of the Attribute Type TimeFormatAttributeType
*AT TimeFormatAttributeType* (Table~[At Time Format Attribute Type](#tab:AtTimeFormatAttributeType)) defines the format for interpreting DINT values as time values. This AT is derived from *AT StaticValueAttributeType*.

% Modelldefinition AT TimeFormatAttributeType
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *AT TimeFormatAttributeType*}
		{#tab:AtTimeFormatAttributeType}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **TimeFormatAttributeType**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Attribute Type (AT)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} attribute type for time format information} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblyATLib/TimeFormatAttributeType} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPATLib/StaticValueAttributeType} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Data Type**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} BYTE} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.Time V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

	\end{longtable}
\end{footnotesize}


## MTP Extension of the ServiceSet {#sec:AnhangServiceSet}
This chapter specifies all identified extensions of the *ServiceSet* and integrates them into the existing MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

### Übersicht {#subsec:AnhangServiceSetUebersicht}
#### Semantic Description of LEA Services
To distinguish the CES and SES procedures introduced in Section~[Lea Dienste](#sec:LeaDienste) for an LOL, a semantic identifier in the form of *FunctionClassificationAttributes* is added to them. Tables~[Function Classification Ces](#tab:FunctionClassificationCes) and [Function Classification Ses](#tab:FunctionClassificationSes) specify the corresponding *FunctionClassificationAttributes*. "2.0" denotes the version in major-minor format and can be incremented accordingly when changes are made to the *FunctionClassificationAttributes*.  

% FunctionClassificationAttribute CES
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{FunctionClassificationAttribute of a Cyclic Execution Service Procedure}
		{#tab:FunctionClassificationCes}\\
		\hline

		\multicolumn{2}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**FunctionClassificationAttribute for CES**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Standard**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Level**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Machine}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} CES} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**IRDI**}     & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics:CES:2.0} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

% FunctionClassificationAttribute SES
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{FunctionClassificationAttribute of a Single Execution Service Procedure}
		{#tab:FunctionClassificationSes}\\
		\hline

		\multicolumn{2}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**FunctionClassificationAttribute for SES**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Standard**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Level**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Machine}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SES} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**IRDI**}     & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics:SES:2.0} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Semantic Description of Service Parameters
To enable a semantic description of service parameters, the model definition *ServiceParameter* is extended by the capability to append *FunctionClassificationAttributes*. The detailed specification is provided in Appendix~[Model Definitions](#subsec:AnhangServiceSetModelle). This extension, as a result of this dissertation, has already been adopted into the base profile *ModuleTypePackage:ServiceSet.Base V2.0.0* of the MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

Tables~[Function Classification Product Id](#tab:FunctionClassificationProductId) to [Function Classification Packaging Data Set](#tab:FunctionClassificationPackagingDataSet) specify *FunctionClassificationAttributes* for the parameters *ProductId*, *LogisticsObjectStatus*, *ProductDataSet*, *PackagingId*, and *PackagingDataSet* introduced in Section~[Parametrierngsmech](#subsec:Parametrierngsmech). "2.0" denotes the version in major-minor format and can be incremented accordingly when changes are made to the *FunctionClassificationAttributes*.

% FunctionClassificationAttribute ProductId
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{FunctionClassificationAttribute of a Procedure Parameter for Setting a ProductId}
		{#tab:FunctionClassificationProductId}\\
		\hline

		\multicolumn{2}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**FunctionClassificationAttribute for ProductId**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Standard**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Level**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Service Parameter}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ProductId Procedure Parameter} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**IRDI**}     & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics:ProductId:2.0} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

% FunctionClassificationAttribute LogisticsObjectStatus
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{FunctionClassificationAttribute of a Procedure Parameter for Setting a LogisticsObjectStatus}
		{#tab:FunctionClassificationLogisticsObjectStatus}\\
		\hline

		\multicolumn{2}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**FunctionClassificationAttribute for LogisticsObjectStatussObjectStatus**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Standard**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Level**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Service Parameter}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} LogisticsObjectStatussObjectStatus Procedure Parameter} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**IRDI**}     & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics:LogisticsObjectStatus:2.0} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

% FunctionClassificationAttribute ProductDataSet
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{FunctionClassificationAttribute of a Configuration Parameter for Accessing a ProductDataSet}
		{#tab:FunctionClassificationProductDataSet}\\
		\hline

		\multicolumn{2}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**FunctionClassificationAttribute for ProductDataSet**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Standard**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Level**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Service Parameter}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ProductDataSet Configuration Parameter} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**IRDI**}     & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics:ProductDataSet:2.0} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

% FunctionClassificationAttribute PackagingId
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{FunctionClassificationAttribute of a Procedure Parameter for Setting a PackagingId}
		{#tab:FunctionClassificationPackagingId}\\
		\hline

		\multicolumn{2}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**FunctionClassificationAttribute for PackagingId**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Standard**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Level**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Service Parameter}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} PackagingId Procedure Parameter} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**IRDI**}     & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics:PackagingId:2.0} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

% FunctionClassificationAttribute PackagingDataSet
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{FunctionClassificationAttribute of a Configuration Parameter for Accessing a PackagingDataSet}
		{#tab:FunctionClassificationPackagingDataSet}\\
		\hline

		\multicolumn{2}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**FunctionClassificationAttribute for PackagingDataSet**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Standard**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Level**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Service Parameter}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} PackagingDataSet Configuration Parameter} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**IRDI**}     & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics:PackagingDataSet:2.0} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Extension of the ParameterElements
According to Section~[Lea Parameter](#sec:LeaParameter), the two new interface definitions *SUC StructServParam* and *SUC ArrayServParam* are required for the parameterization of LEA services. As shown in Figure~[Extension of the ServiceSet for Implementing Structured and Array-Based Service Parameters](#fig:ErweiterungParam), *SUC StructServParam* and *SUC ArrayServParam*, together with all other interface definitions for service parameters, are derived from the interface definition *SUC ParameterElement* according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) and organized in *SUCL MTPDataAssemblySUCLib*. The detailed specification is provided in Appendix~[Anhang Service Set Schnittstellen](#subsec:AnhangServiceSetSchnittstellen). This extension, as a result of this dissertation, has already been adopted into the profile *ModuleTypePackage:ServiceSet.ComplexTypes V2.0.0* of the MTP specification [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

![Extension of the ServiceSet for Implementing Structured and Array-Based Service Parameters](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Parameter/Klassendiagramm.drawio.png)
*Extension of the ServiceSet for Implementing Structured and Array-Based Service Parameters* {#fig:ErweiterungParam}

#### Specification of the LogisticsInteraction {#subsec:LogisticsInteraction}
Section~[Lea Parameter](#sec:LeaParameter) and Section~[Ermittlung Next Node](#subsec:ErmittlungNextNode) introduce the LEA requests to an LOL shown in Table~[Arten Logistics Interaction](#tab:ArtenLogisticsInteraction).

% Arten der LogisticsInteraction
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l
		>{\columncolor[HTML]{FFFFFF}}l |}
		\caption{Possible Requests from an LEA to a Logistics Orchestration Layer}
		{#tab:ArtenLogisticsInteraction}\\
		\hline

		\multicolumn{1}{|L{3.1cm}|}{\cellcolor[HTML]{E0E0E0} **Name**}        	& 
		\multicolumn{1}{L{11.53cm}|}{\cellcolor[HTML]{E0E0E0}**Beschreibung**} 
		\\ \hline

		\multicolumn{1}{|L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} ProductParameter-Request}        	& 
		\multicolumn{1}{L{11.53cm}|}{\cellcolor[HTML]{FFFFFF} Mit dieser Anfrage bezieht eine LEA unter Angabe einer *ProductId* und eines *LogisticsObjectStatus* einen produktspezifischen Parametersatz vom LOL. } 
		\\ \hline

		\multicolumn{1}{|L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} Packaging-ParameterRequest}        	& 
		\multicolumn{1}{L{11.53cm}|}{\cellcolor[HTML]{FFFFFF} Mit dieser Anfrage bezieht eine LEA unter Angabe einer *PackagingId* einen verpackungsspezifischen Parametersatz vom LOL. } 
		\\ \hline

		\multicolumn{1}{|L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} ProductParameter-UpdatedInfo}        	& 
		\multicolumn{1}{L{11.53cm}|}{\cellcolor[HTML]{FFFFFF} Mit dieser Anfrage informiert eine LEA den LOL, dass sich der produktspezifische Parametersatz an einem definierten Arrayindex seines *ProductDataSet* geändert hat. } 
		\\ \hline

		\multicolumn{1}{|L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} Packaging-ParameterUpdated-Info}        	& 
		\multicolumn{1}{L{11.53cm}|}{\cellcolor[HTML]{FFFFFF} Mit dieser Anfrage informiert eine LEA den LOL, dass sich der verpackungsspezifische Parametersatz an einem definierten Arrayindex seines *PackagingDataSet* geändert hat. } 
		\\ \hline

		\multicolumn{1}{|L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} TransportNode-Request}        	& 
		\multicolumn{1}{L{11.53cm}|}{\cellcolor[HTML]{FFFFFF} Mit dieser Anfrage bezieht eine LEA unter Angabe einer *TransportId* den nächsten anzufahrenden Transportknoten für einen Transportauftrag vom LOL. } 
		\\ \hline
		
	\end{longtable}
\end{footnotesize}

These requests are implemented on the basis of service-operator interaction according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) and may occur once or not at all in an LEA. If they occur, they always follow the same sequence and always allow the same responses by an LOL. It is therefore appropriate to standardize these concrete service-operator interactions as logistics-specific interactions, hereafter called *LogisticsInteractions*. This allows an LEA MTP to model whether the corresponding *LogisticsInteractions* occur, while the structure of the *Questions* and *Answers* is standardized and does not need to be remodeled for every specific LEA type.
 
Figure~[Extension of the ServiceSet for Implementing Logistics Interactions](#fig:LogisticsInteractionKonzept) shows the interface and model definitions newly introduced for *LogisticsInteraction*.
 
![Extension of the ServiceSet for Implementing Logistics Interactions](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/Klassendiagramm.drawio.png)
*Extension of the ServiceSet for Implementing Logistics Interactions* {#fig:LogisticsInteractionKonzept}

\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Internal Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VOp}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Operator Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VReq}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Requested Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VOut}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Output Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VFbk}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Feedback Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \textlangle empty\textrangle}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Values}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF}  \{AT of Structured-DataType\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type}            
		\\ \hline


		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

The setting of a parameter of *SUC StructServParam* is performed via the access channels *Automatic Internal*, *Automatic External*, or *Operator* in the same way as for all other service parameters defined in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4).

The distinctive feature of this interface definition is the use of a user-defined structured data type. The modeling and use of such a type have already been described in connection with *SUC StructView* and are applied in the same way for *SUC StructServParam*. This data type is then expected behind the variables *VExt*, *VInt*, *VOp*, *VReq*, and *VOut*. 

#### Specification of the System Unit Class ArrayServParam
*SUC ArrayServParam* (Table~[Data Assembly Suc Array Serv Param](#tab:DataAssemblySucArrayServParam)) is used by the LOL to write data to an array or read data from an array managed in an LEA.

% Schnittstellendefinition SUC ArrayServParam
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ArrayServParam*}
		{#tab:DataAssemblySucArrayServParam}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ArrayServParam**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic parameter interface for an array data type following the rules of modelling complex data types} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ServiceElement/ \newline ParameterElement/ArrayServParam} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ServiceElement/\newline ParameterElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} External Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Internal Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexOp}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Operator Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMin}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Low Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMax}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} High Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Current Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Arrays}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} External Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Internal Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VOp}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Operator Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VReq}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Requested Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VOut}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Output Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VFbk}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Feedback Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} a)}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Values}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \{AT of BaseDataType\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type}            
		\\ \hline

	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} Type shall be \textlangle empty\textrangle~in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

As with the *ArrayView* interface definition, the challenge for *SUC ArrayServParam* is to access an array within an LEA that may have an arbitrary length. As introduced in connection with *SUC ArrayView*, access to this array is also index-based in the case of *SUC ArrayServParam*.

The variables *IndexExt*, *IndexInt*, and *IndexOp* are used to select an array element depending on the operating mode. According to the active access channel, one of these three values is transferred to the variable *IndexCur*. The variables of all three access channels are checked to determine whether they lie within the range between *IndexMin* and *IndexMax*. If an index outside this range is set, the last valid index remains active and the *Worst Quality Code (WQC)* is set to "Out of Specification" according to [NAMUR NE 184](../98_References/README.md#namur-ne-184).

According to the value of the variable *IndexCur*, the array element at the corresponding index is selected for processing. It can then be processed according to the parameter-transfer mechanisms specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). *VOut* always indicates the configured value of the array element located at the position in the array defined by *IndexCur*. This value does not necessarily have to match the parameter value currently used in the LEA.

*VType* defines the data type shared by all array elements. This may be a primitive data type or a user-defined structured data type according to the description of *SUC StructView*.

#### Specification of the Role Class LogisticsInteractionExtension
*RC LogisticsInteractionExtension* (Table~[Data Assembly Rc Logistics Interaction Extension](#tab:DataAssemblyRcLogisticsInteractionExtension)) extends the *ServiceControl* interface definition according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) by the variables required for logistics interactions. If a *LogisticsInteraction* is provided in the LEA, exactly one *LogisticsInteractionExtension* must be assigned as an SRC to the *ServiceControl* interface; otherwise none.

% Schnittstellendefinition RC LogisticsInteractionExtension
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *RC LogisticsInteractionExtension*}
		{#tab:DataAssemblyRcLogisticsInteractionExtension}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **LogisticsInteractionExtension**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Role Class (RC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} interface definition extending the ServiceControl interface for logistice interaction} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPServiceRCLib/LogisticsInteractionExtension} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} AutomationMLBaseRoleClassLib/AutomationMLBaseRole} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logistics-QuestionID}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Identifier of a currently pending logistics question}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} }            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logistics-QuestionParam1}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Question parameter 1 of a currently pending logistics question (e.g., ProductId)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} }            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logistics-QuestionParam2}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Question parameter 2 of a currently pending logistics question (e.g., LogisticsObjectStatus)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} }            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logistics-AnswerID}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Identifier of a currently given answer to a pending question}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} }            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logistics-AnswerTimeout}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME\_OF\_ DAY}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Timeout for a LEA to wait for an answer from a LOL; 0: timeout function deactivated; $> 0$: timeout in s}  &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} }            
		\\ \hline
	

		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Annotations}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IE of SUC ServiceControl as SRC} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

A *LogisticsInteraction* follows a principle similar to the service-operator interaction described in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). However, for the IDs of the questions, *LogisticsQuestionID*, and answers, *LogisticsAnswerID*, values from the DINT range, instead of DWORD, are used, where the value 0 and negative values may also be valid IDs. The value "-1" indicates that currently no question or answer is pending. By means of *LogisticsQuestionParam1* and *LogisticsQuestionParam2*, analogous to *InteractAddInfo* from [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), additional information can be attached to a request, for example *ProductId* and *LogisticsObjectStatus* for *ProductParameterRequest*. The variable *LogisticsAnswerTimeout* allows the entry of a time period that specifies how long an LEA should wait for the response of an LOL. After this time has elapsed, the LEA may execute an alternative program flow without the LOL response. Setting the timeout to 0 is interpreted as deactivation of the timeout function.

#### Extension of the System Unit Class ServiceControl
*SUC ServiceControl* (Table~[Data Assembly Suc Service Control](#tab:DataAssemblySucServiceControl)) defines the base class for controlling MTP services. This interface definition was already defined in the MTP specification and is extended in this dissertation by the capability to connect a RoleClass of type *RC LogisticsInteractionExtension* as an SRC.

% Schnittstellendefinition SUC ServiceControl
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ServiceControl*}
		{#tab:DataAssemblySucServiceControl}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ServiceControl**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} service control interface definition} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ServiceElement/ServiceControl} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ServiceElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{[0..1] MTPServiceRCLib/LogisticsInteractionExtension (SRC)}} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{ModuleTypePackage:ServiceSet.Logistics V2.0.0}} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} *The list of AutomationML Attributes is left out here. Please refer to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4) for the complete specification. * }  
		\\ \hline
		
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

### Model Definitions {#subsec:AnhangServiceSetModelle}
#### Extension of the System Unit Class ServiceParameter
*SUC ServiceParameter* (Table~[Suc Service Parameter](#tab:SucServiceParameter)) defines the base class for MTP service parameters of all data types. This model definition was already defined in the MTP specification and is extended in this dissertation by the attribute *Classification* for representing semantic information in the form of *FunctionClassificationAttributes*.

% Modelldefinition SUC ServiceParameter
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ServiceParameter*}
		{#tab:SucServiceParameter}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ServiceParameter**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} base model definition of service parameter} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPServiceSUCLib/ServiceParameter} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/LinkedObject} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{Classification}}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{\textlangle empty\textrangle}}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{list of child attributes of AttributeType FunctionClassificationAttribute}}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{OrderedListType}}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no children allowed)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class LogisticsInteraction
*SUC LogisticsInteraction* (Table~[Suc Logistics Interaction](#tab:SucLogisticsInteraction)) organizes all model definitions required for the logistics interaction between an LEA and an LOL. It is derived from *SUC TextDefinition* specified in [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). *SUC LogisticsInteraction* is linked to the model definition *SUC HasLogisticsInteraction* via a *TextRef*. *SUC LogisticsInteraction* follows a principle similar to *SUC ServiceInteraction* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), with the difference that it contains predefined *LogisticsQuestions*, which are specified below.

% Modelldefinition SUC LogisticsInteraction
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC LogisticsInteraction*}
		{#tab:SucLogisticsInteraction}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **LogisticsInteraction**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for logistics-specific service interaction} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1..*] IEs of SUC LogisticsQuestion} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class LogisticsQuestion
*SUC LogisticsQuestion* (Table~[Suc Logistics Question](#tab:SucLogisticsQuestion)) is an abstract class derived from *SUC Text* from [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) and represents a logistics-specific question that an LEA can ask an LOL. Five specific questions have so far been derived from *LogisticsQuestion*: *ProductParameterRequest*, *PackagingParameterRequest*, *ProductParameterUpdatedInfo*, *PackagingParameterUpdatedInfo*, and *TransportNodeRequest*. Each of these questions may occur either not at all or exactly once in an LEA.

% Modelldefinition SUC LogisticsQuestion
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC LogisticsQuestion*}
		{#tab:SucLogisticsQuestion}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **LogisticsQuestion**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for an abstract question for logistics-specific service interactions} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/Text} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Name}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} unique number of the question ($>0$)}       
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IE of SUC LogisticsInteraction} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no children allowed)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class ProductParameterRequest
*SUC ProductParameterRequest* (Table~[Suc Product Parameter Request](#tab:SucProductParameterRequest)) is derived from *SUC LogisticsQuestion* and is used to request product-specific parameter sets from an LOL. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC ProductParameterRequest*. Instead, a value in the DINT range is expected as the response. Values greater than or equal to 0 specify the index at which the LOL has written the requested parameter set into the *ProductDataSet* of the LEA. The array limits, minimum and maximum index, must not be exceeded or undershot. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC ProductParameterRequest
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ProductParameterRequest*}
		{#tab:SucProductParameterRequest}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ProductParameterRequest**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for requesting product parameter sets from a Logistics Orchestration Layer} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion/ ProductParameterRequest} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

The standard sequence of a *ProductParameterRequest* is shown in Figure~[Sequence of the Logistics Interaction of a ProductParameterRequest](#fig:ProductParameterRequest).

![Sequence of the Logistics Interaction of a ProductParameterRequest](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/ProductParameterRequest.png)
*Sequence of the Logistics Interaction of a ProductParameterRequest* {#fig:ProductParameterRequest}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 1$, the LEA sends a *ProductParameterRequest* to the LOL and transfers *ProductId* as *LogisticsQuestionParam1* and *LogisticsObjectStatus* as *LogisticsQuestionParam2*. The LOL then determines the required parameter set and writes it into the *ProductDataSet* of the LEA via the corresponding *ArrayServParm* interface. If the parameterization is successful, the LOL returns a *LogisticsAnswer-ID* $>= 0$, here: *LogisticsAnswerID* $= 3$, to the LEA, reflecting the index of the *ProductDateSet* to which the new parameter set was written. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question and no answer are currently pending. *LogisticsQuestionParam1* and *LogisticsQuestionParam2* are reset.

#### Specification of the System Unit Class PackagingParameterRequest
*SUC PackagingParameterRequest* (Table~[Suc Packaging Parameter Request](#tab:SucPackagingParameterRequest)) is derived from *SUC LogisticsQuestion* and is used to request packaging-specific parameter sets from an LOL. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC PackagingParameterRequest*. Instead, a value in the DINT range is expected as the response. Values greater than or equal to 0 specify the index at which the LOL has written the requested parameter set into the *PackagingDataSet* of the LEA. The array limits, minimum and maximum index, must not be exceeded or undershot. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC PackagingParameterRequest
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC PackagingParameterRequest*}
		{#tab:SucPackagingParameterRequest}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **PackagingParameterRequest**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for requesting packaging parameter sets from a Logistics Orchestration Layer} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion/ PackagingParameterRequest} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

The standard sequence of a *PackagingParameterRequest* is shown in Figure~[Sequence of the Logistics Interaction of a PackagingParameterRequest](#fig:PackagingParameterRequest).
 
![Sequence of the Logistics Interaction of a PackagingParameterRequest](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/PackagingParameterRequest.png)
*Sequence of the Logistics Interaction of a PackagingParameterRequest* {#fig:PackagingParameterRequest}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 2$, the LEA sends a *PackagingParameterRequest* to the LOL and transfers *PackagingId* as *LogisticsQuestionParam1*. The LOL then determines the required parameter set and writes it into the *PackagingDataSet* of the LEA via the corresponding *ArrayServParm* interface. If the parameterization is successful, the LOL returns a *LogisticsAnswerID* $>= 0$, here: *LogisticsAnswerID* $= 2$, to the LEA, reflecting the index of the *PackagingDateSet* to which the new parameter set was written. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question and no answer are currently pending. *LogisticsQuestionParam1* is reset.

#### Specification of the System Unit Class ProductParameterUpdatedInfo
*SUC ProductParameterUpdatedInfo* (Table~[Suc Product Parameter Updated Info](#tab:SucProductParameterUpdatedInfo)) is derived from *SUC LogisticsQuestion* and is used to inform an LOL that a parameter set in the *ProductDataSet* of an LEA has changed. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC ProductParameterUpdatedInfo*. Instead, the value "1" is expected as confirmation that the LOL has acknowledged the parameter change. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC ProductParameterUpdatedInfo
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ProductParameterUpdatedInfo*}
		{#tab:SucProductParameterUpdatedInfo}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ProductParameterUpdatedInfo**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for informing a LOL of a change in a product parameter set} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion/ ProductParameterUpdatedInfo} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}
 
The standard sequence of a *ProductParameterUpdatedInfo* is shown in Figure~[Sequence of the Logistics Interaction of a ProductParameterUpdatedInfo](#fig:ProductParameterUpdatedInfo).

![Sequence of the Logistics Interaction of a ProductParameterUpdatedInfo](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/ProductParameterUpdatedInfo.png)
*Sequence of the Logistics Interaction of a ProductParameterUpdatedInfo* {#fig:ProductParameterUpdatedInfo}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 3$, the LEA sends a *ProductParameterUpdatedInfo* to the LOL and transfers the array index, here: array index $= 5$, of the changed parameter set in the *ProductDataSet* as *LogisticsQuestionParam1*. The LOL parameter management then determines whether the corresponding product parameter data set is also to be adapted in the LOL, if necessary by user request, and updates the parameter set if required. The LOL acknowledges the parameter change by sending *LogisticsAnswerID*~$= 1$ to the LEA. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question and no answer are currently pending. *LogisticsQuestionParam1* is reset.

#### Specification of the System Unit Class PackagingParameterUpdatedInfo
*SUC PackagingParameterUpdatedInfo* (Table~[Suc Packaging Parameter Updated Info](#tab:SucPackagingParameterUpdatedInfo)) is derived from *SUC LogisticsQuestion* and is used to inform an LOL that a parameter set in the *PackagingDataSet* of an LEA has changed. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC PackagingParameterUpdatedInfo*. Instead, the value "1" is expected as confirmation that the LOL has acknowledged the parameter change. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC PackagingParameterUpdatedInfo
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC PackagingParameterUpdatedInfo*}
		{#tab:SucPackagingParameterUpdatedInfo}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **PackagingParameterUpdatedInfo**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for informing a LOL of a change in a packaging parameter set} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion/ PackagingParameterUpdatedInfo} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextSUCLib/TextDefinition/LogisticsInteraction/LogisticsQuestion} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}
 
The standard sequence of a *PackagingParameterUpdatedInfo* is shown in Figure~[Sequence of the Logistics Interaction of a PackagingParameterUpdatedInfo](#fig:PackagingParameterUpdatedInfo).

![Sequence of the Logistics Interaction of a PackagingParameterUpdatedInfo](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Logistics_Interaction/PackagingParameterUpdatedInfo.png)
*Sequence of the Logistics Interaction of a PackagingParameterUpdatedInfo* {#fig:PackagingParameterUpdatedInfo}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 4$, the LEA sends a *PackagingParameterUpdatedInfo* to the LOL and transfers the array index, here: array index $= 4$, of the changed parameter set in the *PackagingDataSet* as *LogisticsQuestionParam1*. The LOL parameter management then determines whether the corresponding product parameter data set is also to be adapted in the LOL, if necessary by user request, and updates the parameter set if required. The LOL acknowledges the parameter change by sending *LogisticsAnswerID*~$= 1$ to the LEA. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question and no answer are currently pending. *LogisticsQuestionParam1* is reset.

#### Specification of the System Unit Class TransportNodeRequest
*SUC TransportNodeRequest* (Table~[Suc Transport Node Request](#tab:SucTransportNodeRequest)) is derived from *SUC LogisticsQuestion* and is used to request the next transport node to be approached from an LOL. In contrast to *SUC Question* specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4), no *Answers* are modeled in the MTP for *SUC TransportNodeRequest*. Instead, a value in the DINT range is expected as the response. Values greater than 0 directly specify the ID of the next transport node to be approached. This eliminates the need for a separate parameter interface to configure the next transport node to be approached. Only values corresponding to the ID of a transport node in the respective MLS may be returned as a response. The value "0" indicates that the *FinalTargetNode* specified in the transport service interface is to be used as the next transport node. The value "-1" indicates that no answer is yet available. The value "-2" indicates that an error occurred during the request. Other responses are currently neither required nor valid.

% Modelldefinition SUC TransportNodeRequest
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC TransportNodeRequest*}
		{#tab:SucTransportNodeRequest}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **TransportNodeRequest**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for requesting the next transport node to be approached from a Logistics Orchestration Layer} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPLogisticsSUCLib/LogisticsInteraction/LogisticsQuestion/\newline TransportNodeRequest} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPLogisticsSUCLib/LogisticsInteraction/LogisticsQuestion} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

The standard sequence of a *TransportNodeRequest* is shown in Figure~[Sequence of the Logistics Interaction of a TransportNodeRequest](#fig:TransportNodeRequest).

![Sequence of the Logistics Interaction of a TransportNodeRequest](Inhalt/Abbildungen/08_Bereichs-Automatisierung/TransportNodeRequest.png)
*Sequence of the Logistics Interaction of a TransportNodeRequest* {#fig:TransportNodeRequest}

Via the corresponding *LogisticsQuestionID*, here: *LogisticsQuestionID* $= 5$, the LEA sends a *TransportNodeRequest* to the LOL and transfers the *TransportId* of the associated transport service as *LogisticsQuestionParam1*. The LOL then determines the required next transport node. If the next transport node is successfully determined, the LOL returns a *LogisticsAnswerID* $>= 0$ to the LEA. This response directly reflects the ID of the next transport node to be approached. A *LogisticsAnswerID* $= 0$ indicates that the *FinalTargetNode* of the transport service is to be used. Afterwards, *LogisticsQuestionID* and *LogisticsAnswerID* are set to "$-1$", indicating that no question or answer is currently pending. *LogisticsQuestionParam1* and *LogisticsQuestionParam2* are reset. The information received about the next transport node is transferred by the LEA to the procedure parameter *NextNode* in the corresponding transport service.

#### Specification of the Role Class HasLogisticsInteraction
*RC HasLogisticsInteraction* (Table~[Rc Has Logistics Interaction](#tab:RcHasLogisticsInteraction)) is derived from *RC HasTextReference* specified in [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). *SUC HasLogisticsInteraction* is used to assign a *LogisticsInteraction* to the model definition *SUC Service*, specified in [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). For this purpose, a *SUC LogisticsInteraction* model definition is referenced by means of *TextRef*. If a *LogisticsInteraction* is provided in an LEA, exactly one *SUC HasLogisticsInteraction* must be assigned to the LEA service as a RoleRequirement; otherwise none.

% Modelldefinition RC HasLogisticsInteraction
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *RC HasLogisticsInteraction*}
		{#tab:RcHasLogisticsInteraction}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **HasLogisticsInteraction**\textsuperscript{a)}} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Role Class (RC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for assigning a logistics interaction to a service} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextRCLib/HasTextReference/HasLogisticsInteraction} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTextRCLib/HasTextReference} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} The usage of the HasLogisticsInteraction is allowed exactly once at a ServiceElement. }   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Annotations}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IE of SUC Services as RR} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Extension of the System Unit Class Service
*SUC ServiceParameter* (Table~[Suc Service](#tab:SucService)) defines the base class for modeling MTP services. This model definition was already defined in the MTP specification and is extended in this dissertation by the capability to connect a RoleClass of *RC HasLogisticsInteraction* as an RR.

% Modelldefinition SUC Service 
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC Service*}
		{#tab:SucService}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **Service**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a Service} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPServiceSUCLib/Service} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/LinkedObject} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF}
		[0..1] MTPTextRCLib/HasTextReference/HasServicePosition (RR) \newline
		[0..1] MTPTextRCLib/HasTextReference/HasServiceInteraction (RR) \newline
		\textcolor{red}{[0..1] MTPTextRCLib/HasTextReference/HasLogisticsInteraction (RR)}
		} 
		\\ \hline
 
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} \textcolor{red}{ModuleTypePackage:ServiceSet.Logistics V2.0.0}} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Classification}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} \textlangle empty\textrangle}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} List of child attributes of AttributeTypes FunctionClassificationAttribute}  &                   
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} OrderedListType }              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IH to which an IE of SUC ServiceSet relates via EI of IC AspectSetReference } 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 
		[1..*] IEs of SUC Procedure \newline
		[0..*] IEs of SUC ConfigurationParameter
		} 
		\\ \hline

	\end{longtable}
\end{footnotesize}
 

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
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC StructProcessValueIn*}
		{#tab:DataAssemblySucStructProcessValueIn}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **StructProcessValueIn**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for accessing a value of structured data type from another LEA} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/InputElement/StructProcess-ValueIn} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/InputElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} V}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \textlangle empty\textrangle}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \{AT of Structured-DataType\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

The required value is transferred in the variable *V* according to [MTP Specification Part 4](../98_References/README.md#mtp-specification-part-4). The distinctive feature of this interface definition is the use of a user-defined structured data type. The modeling and use of such a type have already been described in connection with *SUC StructView* and are applied in the same way for *SUC StructProcessValueIn*. This data type is then expected behind the variable *V*. 

#### Specification of the System Unit Class ArrayProcessValueIn
*SUC ArrayProcessValueIn* (Table~[Data Assembly Suc Array Process Value In](#tab:DataAssemblySucArrayProcessValueIn)) is used by an LEA to access a value at a specific position of an array in another LEA.

% Schnittstellendefinition SUC ArrayProcessValueIn
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ArrayProcessValueIn*}
		{#tab:DataAssemblySucArrayProcessValueIn}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ArrayProcessValueIn**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for accessing a value of array data type from another PEA} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/InputElement/ArrayProcess-ValueIn} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/InputElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Process Values}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMin}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Low Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Process Values}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMax}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} High Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Process Values}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Current Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Process Values}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} V}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Output Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} a)}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Values}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \{AT of BaseDataType\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type}            
		\\ \hline
	

		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} Type shall be \textlangle empty\textrangle~in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

Ähnlich wie bei der *SUC ArrayView* besteht die Herausforderung bei dieser Schnittstelle darin, auf ein Array innerhalb einer LEA zuzugreifen, das eine beliebige Länge haben kann. Wie bei der *SUC ArrayView* soll der Zugriff auf dieses Array auch im Falle der *SUC ArrayProcessValueIn* indexbasiert erfolgen.

The array position to be displayed is selected via the variable *IndexSel*. The variables *IndexMin* and *IndexMax* specify the lower and upper limits of the array. The variable *IndexCur* specifies the currently selected index, and the value of the array at this position is displayed in *V*. *VType* defines the data type shared by all array elements. This may be a primitive data type or a structured data type.

**Note:** This interface definition differs from all other interfaces derived from the *InputElement* interface definition because it also includes information flows from the LEA to the LOL. This had not previously been envisaged.

#### Specification of the System Unit Class OutputElement
*SUC OutputElement* (Table~[Data Assembly Suc Output Element](#tab:DataAssemblySucOutputElement)) is an abstract interface from which specific process-value outputs of different data types can be derived. The interface definition itself serves only an organizational purpose and provides a variable for transmitting a *Worst Quality Code (WQC)*.

% Schnittstellendefinition SUC OutputElement
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC OutputElement*}
		{#tab:DataAssemblySucOutputElement}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **OutputElement**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract interface from which specific process value outputs can be derived} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OutputElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                & 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Worst Quality Code variable}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &   
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} WQC}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

**Note:** For greater clarity in modeling and with regard to possible future developments, MTP standardization should consider explicitly modeling *ProcessValueOutputs* of all MTP data types, including structured data types, and also deriving them from the newly specified *OutputElement*.

#### Specification of the System Unit Class ArrayProcessValueOut
*SUC ArrayProcessValueOut* (Table~[Data Assembly Suc Array Process Value Out](#tab:DataAssemblySucArrayProcessValueOut)) is used by an LEA to provide the values of an LEA-internal array to another LEA.

% Schnittstellendefinition SUC ArrayProcessValueOut
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ArrayProcessValueOut*}
		{#tab:DataAssemblySucArrayProcessValueOut}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ArrayProcessValueOut**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} generic interface for making available a value of array data type to another LEA} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OutputElement/ArrayProcess-ValueOut} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/OutputElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ProcessValueSet.ComplexTypes V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Process Values}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMin}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Low Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Process Values}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexMax}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} High Limit of the Index}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Process Values}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} IndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Current Index Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Multiplexing for Process Values}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} V}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} \{VType\}}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Output Value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} MTP}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} a)}                &  
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Type Definition of the Values}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} \{AT of BaseDataType\}}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} Complex-Type }            
		\\ \hline
	


		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} \textsuperscript{a)} Type shall be \textlangle empty\textrangle~in case of a StructuredDataType and shall be set to the defined type in case of a PrimitiveDataType.}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

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
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC UnionElement*}
		{#tab:DataAssemblySucUnionElement}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **UnionElement**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -[^9]}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} interface for displaying a value with datatype defined at runtime} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/UnionElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} quality Code of the value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} DataType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier of selected data type\newline (0 : None, 1: VReal, 2: VDInt, 3: VDWord, 4: VBool, 5: VString)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VReal}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Real Value\newline (Type: 1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VDInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Double Integer Value (Type: 2)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VDWord}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Double Word Value (Type: 3)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VBool}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Boolean Value (Type: 4)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VString}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} String Value\newline (Type: 5)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
	

		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

The variables *VReal*, *VDInt*, *VDWord*, *VBool*, and *VString * are used to display the desired value. The variable *DataType* indicates which data type is currently active and which of the previously mentioned variables is therefore to be interpreted. *UnionElement* can thus display only one value of one defined data type at a time. *VQC* provides information about the quality and trustworthiness of the displayed value.

#### Specification of the System Unit Class WritableUnionElement
*SUC WritableUnionElement* (Table~[Data Assembly Suc Writable Union Element](#tab:DataAssemblySucWritableUnionElement)) is derived from *UnionElement* and is used to write a value into a *WritableInputElement*. Accordingly, a *WritableUnionElement* interface is always assigned to a *WritableInputElement* via a LinkedObject relation. 

% Schnittstellendefinition SUC WritableUnionElement
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC WritableUnionElement*}
		{#tab:DataAssemblySucWritableUnionElement}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **WritableUnionElement**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} interface for writing a value with datatype defined at runtime} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/UnionElement/WritableUnion-Element} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/UnionElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} quality Code of the value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} DataType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier of selected data type (0 : None, 1: VReal, 2: VDInt, 3: VDWord, 4: VBool, 5: VString)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VReal}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Real Value (Type: 1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VDInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Double Integer Value (Type: 2)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VDWord}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Double Word Value (Type: 3)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VBool}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Boolean Value (Type: 4)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} VString}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} String Value (Type: 5)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline


		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

The variables *VReal*, *VDInt*, *VDWord*, *VBool*, and *VString* are used to enter the desired value. The variable *DataType* indicates which data type is currently active and which of the previously mentioned variables is to be used in the LEA program. *WritableUnionElement* thus accepts only one value of one defined data type at a time. *VQC* can be used to transmit information about the quality and trustworthiness of the entered value.

#### Specification of the System Unit Class ChoreographyElement
*SUC ChoreographyElement* (Table~[Data Assembly Suc Choreography Element](#tab:DataAssemblySucChoreographyElement)) is an abstract class derived from *SUC DataAssembly* specified in [MTP Specification Part 3](../98_References/README.md#mtp-specification-part-3). The choreography-relevant interface definitions *ChoreographyParticipantManager* and *CommunicationManager* are derived from *ChoreographyElement*.

% Schnittstellendefinition SUC ChoreographyElement
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ChoreographyElement*}
		{#tab:DataAssemblySucChoreographyElement}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ChoreographyElement**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} root interface class for choreography-related interface definitions} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Worst Quality Code}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} WQC}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class ChoreographyParticipantManager
*SUC ChoreographyParticipantManager* (Table~[Data Assembly Suc Choreography Participant Manager](#tab:DataAssemblySucChoreographyParticipantManager)) is derived from *SUC ChoreographyElement* and is used to configure the configurable logic of a choreography participant. In addition, it provides information for type, version, and instance verification of choreographed logistics lines, see also Appendix~[Workflows](#subsec:AnhangManifestWorkflows). This interface definition is assigned to an *SUC ChoreographyParticipant* in the *ChoreographySet* via a LinkedObject relation.

% Schnittstellendefinition SUC ChoreographyParticipantManager
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC ChoreographyParticipantManager*}
		{#tab:DataAssemblySucChoreographyParticipantManager}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ChoreographyParticipantManager**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} configuration interface for a choreography participant} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement/Choreo-graphyParticipantManager} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ComposedType-Code}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier of the choreography type}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ComposedType-Revision}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} version of the choreography type}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} RoleIdent}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier of the participant role within the choreography}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ViewSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} selection to view prepared configuration (false) or active configuration (true)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ViewCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} currently selected view: false = prepared, true = active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} RestoreDefaultEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enable flag to restore default configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} RestoreDefault}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} restores the default config of all inputs, logics, and outputs}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ExecuteEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enable flag to execute the configurable logic}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ExecuteOn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} trigger to apply the current configuration and start the execution}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ExecuteOff}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} trigger to quit the execution, outputs are set to default value}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ExecuteAct}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} flag which indicates the active execution}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ExecuteErr}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} flag which indicates min. one processing error}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} InputCnt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of input configurations (maximum index of input configurations = InputCnt-1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} InputIndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the desired input configuration to be shown}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} InputIndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the currently selected input configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Input\_VQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} value quality code of the currently selected input}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Input\_DataType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} data type of the currently selected input}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Input\_VReal}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} real value of the currently selected input}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Input\_VDInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} double Integer value of the currently selected input}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Input\_VDWord}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} double Word value of the currently selected input}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Input\_VBool}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} boolean value of the currently selected input}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Input\_VString}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} string value of the currently selected input}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} LogicCnt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of logic configurations (maximum index of logic configurations = LogicCnt-1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} LogicIndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the desired logic configuration to be shown}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} LogicIndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the currently selected logic configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_\newline FuncTypeSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} function type selector of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Source}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} SINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} source of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Index}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Const\_
		VQC
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant value quality code of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Const\_
		DataTypeSel
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant data type of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Const\_
		VReal
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Real value of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Const\_
		VDInt
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Double Integer value of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Const\_
		VDWord
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant double word value of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Const\_
		VBool
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant boolean value of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In0\_Const\_
		VString
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant String value of input 0 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline


		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Source}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} SINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} source of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Index}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Const\_
		VQC
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant value quality code of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Const\_
		DataTypeSel
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant data type of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Const\_
		VReal
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Real value of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Const\_
		VDInt
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Double Integer value of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Const\_
		VDWord
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant double word value of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Const\_
		VBool
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant boolean value of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In1\_Const\_
		VString
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant String value of input 1 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Source}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} SINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} source of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Index}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Const\_
		VQC
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant value quality code of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Const\_
		DataTypeSel
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant data type of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Const\_
		VReal
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Real value of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Const\_
		VDInt
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Double Integer value of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Const\_
		VDWord
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant double word value of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Const\_
		VBool
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant boolean value of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In2\_Const\_
		VString
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant String value of input 2 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Source}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} SINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} source of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Index}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Const\_
		VQC
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant value quality code of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Const\_
		DataTypeSel
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant data type of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Const\_
		VReal
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Real value of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Const\_
		VDInt
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Double Integer value of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Const\_
		VDWord
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant double word value of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Const\_
		VBool
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant boolean value of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_In3\_Const\_
		VString
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant String value of input 3 of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_Out\_VQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant value quality code of output of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_Out\_
		DataType
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant data type of output of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_Out\_VReal}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Real value of output of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_Out\_VDInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Double Integer value of output of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_Out\_
		VDWord}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Double Word value of output of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_Out\_VBool}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Boolean value of output of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_Out\_\newline VString}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant String value of output of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Logic\_Ret}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} return value of the currently selected logic element}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} OutputCnt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of output configurations (maximum index of output configurations = OutputCnt-1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} OutputIndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the desired output configuration to be shown}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} OutputIndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the currently selected output configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Source}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} SINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} source of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Index}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_DataType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} data type of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Const\_
		VQC
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant value quality code of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Const\_
		DataTypeSel
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant data type of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Const\_
		VReal
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Real value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Const\_
		VDInt
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Double Integer value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Const\_
		VDWord
		}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Double Word value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Const\_
		VBool}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant Boolean value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Const\_
		VString}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} constant String value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Value\_
		VQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} value quality code of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Value\_
		DataTypeSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} data type of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Value\_
		VReal}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} real value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Value\_
		VDInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} double integer value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Value\_
		VDWord}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} double word value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Value\_
		VBool}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} boolean value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Value\_
		VString}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} string value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Output\_Ret}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} return value of the currently selected output}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	


		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class CommunicationManager
*SUC CommunicationManager* (Table~[Data Assembly Suc Communication Manager](#tab:DataAssemblySucCommunicationManager)) is an abstract class derived from *SUC ChoreographyElement*. It is to be understood as a generic interface definition for configuring the configurable communication of a choreography participant. To use this interface definition, a concrete manager for a specific communication technology must be derived from it. So far, only *OpcUaClientServerManager* has been implemented for configuring OPC~UA client/server connections; additional derivations can be developed in the future. The derivations of *SUC CommunicationManager* are assigned to the model definitions of *SUC ConfigurableInputElements* and *SUC ConfigurableOutputElements* in the *ChoreographySet* via an ID link relation, variable *ManagerLink*. In addition, each model definition specifies a *ManagerIndex* that refers to a concrete communication element within the *CommunicationManager*.

% Schnittstellendefinition SUC CommunicationManager
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC CommunicationManager*}
		{#tab:DataAssemblySucCommunicationManager}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **CommunicationManager**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract interface definition for the communication between different choreography participants } 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement/Commu-nicationManager} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} -}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class OpcUaClientServerManager
*SUC OpcUaClientServerManager* (Table~[Data Assembly Suc Opc Ua Client Server Manager](#tab:DataAssemblySucOpcUaClientServerManager)) is derived from the abstract *SUC CommunicationManager*. It is used to configure OPC~UA client/server communication of an LEA with other LEAs participating in a choreography. *SUC OpcUaClientServerManager* is assigned to the model definitions of *SUC ConfigurableInputElements* and *SUC ConfigurableOutputElements* in the *ChoreographySet* via an ID link relation, variable *ManagerLink*. Each model definition specifies a *ManagerIndex* that refers to a concrete communication element within the *CommunicationManager*. In the case of *OpcUaClientServerManager*, these communication elements are the *UaReader* and *UaWriter* managed by the manager, which are referenced via their index. The *UaReader* are each assigned to a *ConfigurableInputElement*, and the *UaWriter* are each assigned to a *ConfigurableOutputElement*. For the communication variant of active writing, *SUC OpcUaClientServerManager* manages the existing *ValueFields* of an LEA that can be written by other LEAs. 

% Schnittstellendefinition SUC OpcUaClientServerManager
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC OpcUaClientServerManager*}
		{#tab:DataAssemblySucOpcUaClientServerManager}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **OpcUaClientServerManager**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} interface for managing the OPC~UA connections, readers, writers and value fields of a choreography participant} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement/\newline CommunicationManager/OpcUaClientServerManager} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/ChoreographyElement/\newline CommunicationManager} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionView-Sel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} selection to view prepared configuration (false) or active configuration (true)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionView-Cur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} currently selected view: false = prepared, true = active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionCnt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of connection configurations (maximum index of connection configurations = ConnectionCnt-1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionCnt-Active}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of active connections}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionCnt-Inactive}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of inactive but configured connections}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionCnt-Error}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of failed connections}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionIndex-Sel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the desired connection configuration to be shown}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionIndex-Cur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the currently selected connection configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline RestoreDefaultEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enable flag to restore default configuration of the currently selected connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline RestoreDefault}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} restore default configuration of the currently selected connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline ConnectEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enable flag to connect the currently selected connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline Connect}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} apply the configuration and establish the currently selected connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline ConnectAct}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} indication whether the currently selected connection is established}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline ConnectErr}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} indication whether the currently selected connection has an error}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline DisconnectEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enable flag to disconnect the currently selected connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline Disconnect}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} disconnect the currently selected connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_Reset}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} reset the currently selected connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline Active}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} indicates that the selected connection is activated to be used}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline ServerUrl}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} server URL for the connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline NamespaceUri-Cnt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of namespace URIs}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline NamespaceUri\_1}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace URI 1}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

				
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline NamespaceUri\_2}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace URI 2}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
				
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline NamespaceUri\_3}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace URI 3}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
				
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline NamespaceUri\_4}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace URI 4}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
				
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline NamespaceUri\_5}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace URI 5}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
				
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline SessionName}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} name of the session assigned by the client (when empty, then generated by the server)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline ApplicationName}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} readable name of the OPC~UA client application}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline SecurityMsgMode}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enum UASecurityMsgMode}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline SecurityPolicy}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enum UASecurityPolicy}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline ServerUri}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} defines the URI of the server, coded in ASCII}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline CheckServer-Certificate}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} flag indicating if the server certificate should be checked}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	 
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline TransportProfile}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enum UATransportProfile}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline 
		UserIdentity-TokenType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enum UAUserIdentityTokenType}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline UserTokenParam1}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} meaning according to UserIdentityTokenType, e.g., username}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline UserTokenParam2}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} meaning according to UserIdentityTokenType, e.g., password}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline CertificateID}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} certificate identifier}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline SessionTimeout}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} timeout for the session in case of connection loss}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline Monitor-Connection}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} interval time to check the connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline LocaleID\_1}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline LocaleID\_2}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline LocaleID\_3}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline LocaleID\_4}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline SessionInfo\_\newline LocaleID\_5}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} optional language and regional identifier acc. to RFC 3066. 0 = no or unknown LocaleID.}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Connection\_\newline Status}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} status of current connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ReaderViewSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} selection to view prepared configuration (false) or active configuration (true)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ReaderViewCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} currently selected view: false = prepared, true = active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ReaderCnt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of reader configurations (maximum index of reader configurations = ReaderCnt-1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ReaderCntIn-Use}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of readers in use}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ReaderCnt-Error}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of readers with failures}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ReaderIndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the desired reader configuration to be shown}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ReaderIndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the currently selected reader configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_\newline RestoreDefaultEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enable Flag to restore the default configuration of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_\newline RestoreDefault}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} restore the default configuration of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_Reset}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} reset the reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_\newline ConnectionIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} INT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} connection index the currently selected reader should use}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_\newline InputIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} indicates the index of the Input List the reader refers to}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_\newline DataTypeSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} data type of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_Timeout}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} timeout for the used OPC~UA operations}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_\newline MaxTryCount}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of tries for an OPC~UA operation until the Reader transitions into the error state}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_CycleSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} target cycle for the read operation}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_CycleCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} actual read cycle}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_Error}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} true, if the reader is in the error state}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_Status}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} status of the Reader (e.g., status codes of OPC~UA operations in case of an error)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_Value\_\newline NamespaceIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace index of the value of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_Value\_\newline Identifier}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier of the value of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_Value\_\newline IdentifierType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier type of the value of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_QC\_\newline NamespaceIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace index of the quality code of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_QC\_\newline Identifier}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier of the quality code of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Reader\_QC\_\newline IdentifierType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier type of the quality code of the currently selected reader}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
				
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WriterViewSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} selection to view prepared configuration (false) or active configuration (true)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WriterViewCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} currently selected view: false = pre-pared, true = active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WriterCnt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of writer configurations (maximum index of writer configurations = WriterCnt-1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline		

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WriterCntIn-Use}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of writers in use}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WriterCntError}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of writers with failures}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WriterIndexSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the desired writer configuration to be shown}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WriterIndexCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the currently selected writer configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_\newline RestoreDefaultEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} enable Flag to restore the default configuration of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_\newline RestoreDefault}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} restore the default configuration of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_Reset}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} reset the writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_\newline ConnectionIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} INT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} connection index the currently selected writer should use}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_\newline OutputIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} indicates the index of the Output List the writer refers to}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline		

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_\newline DataTypeSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} data type of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_Timeout}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} timeout for the used OPC~UA operations}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_\newline MaxTryCount}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of tries for an OPC~UA operation until the writer transitions into the error state}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_CycleSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} target cycle for the write operation}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_CycleCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} TIME}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} actual write cycle}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_Error}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} true, if the writer is in the error state}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline	

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_Status}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} status of the Writer (e.g., status codes of OPC~UA operations in case of an error)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_Value\_\newline NamespaceIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace index of the value of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_Value\_\newline Identifier}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier of the value of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_Value\_\newline IdentifierType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier type of the value of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_QC\_\newline NamespaceIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} namespace index of the quality code of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_QC\_\newline Identifier}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier of the quality code of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Writer\_QC\_\newline IdentifierType}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UDINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} identifier type of the quality code of the currently selected writer}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueFieldView-Sel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} selection to view prepared configuration (false) or active configuration (true)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueFieldView-Cur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} currently selected view: false = prepared, true = active}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueFieldApply}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} variable for applying the data type configuration of all value fields}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueFieldCnt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} number of value fields (maximum index of value fields = ValueFieldCnt-1)}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline	

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueFieldIndex-Sel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the desired value field to be shown}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueFieldIndex-Cur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} index of the currently selected value field}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueField\_\newline InputIndex}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} UINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} indicates the index of the Input List the selected value field refers to}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline		
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueField\_\newline DataTypeSel}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} data type of the currently selected value field}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueField\_VQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} value quality code of the currently selected value field}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueField\_VReal}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} REAL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Real value of the currently selected value field}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueField\_VDInt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Double Integer value of the currently selected value field}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueField\_\newline VDWord}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Double Word value of the currently selected value field}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueField\_VBool}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Boolean value of the currently selected value field}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ValueField\_\newline VString}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} String value of the currently selected value field}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		

		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

### Model Definitions {#subsec:AnhangChoreographySetModelle}
#### Specification of the Instance Hierarchy Choreography
*IH Choreography* (Table~[Ih Choreography](#tab:IhChoreography)) is the entry point for the choreography-related information model in the instance hierarchy of an MTP.

% Modelldefinition IH Choreography
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *IH Choreography*}
		{#tab:IhChoreography}\\
		\hline

		\multicolumn{3}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **Choreography**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Instance Hierarchy (IH)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} root element for the choreography-related information model of n MTP} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ID}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &                                              
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} Identifier of the Instance Hierarchy}              
		\\ \hline


		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}      
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{3}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1] IE of SUC ChoreographyParticipant} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class Library MTPChoreographySUCLib
*SUCL MTPChoreographySUCLib* (Table~[Sucl MTP Choreography SUC Lib](#tab:SuclMTPChoreographySUCLib)) contains the System Unit Classes of the *ChoreographySet* of a Module Type Package.

% Bibliothek SUCL MTPChoreographySUCLib
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Library Definition of *SUCL MTPChoreographySUCLib*}
		{#tab:SuclMTPChoreographySUCLib}\\
		\hline

		\multicolumn{3}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Library Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **MTPChoreographySUCLib**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClassLibrary (SUCL)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Library containing the Choreography-related SUC model definitions of an MTP} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class ChoreographySet
The *SUC ChoreographySet* (Table~[Suc Choreography Set](#tab:SucChoreographySet)), as a new aspect set of the MTP specification, is derived from *SUC MTPSet* according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1) and organizes all model definitions required to describe an LEA as a participant in a choreography.

% Modelldefinition SUC ChoreographySet
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ChoreographySet*}
		{#tab:SucChoreographySet}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ChoreographySet**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for choreography aspect set} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/ChoreographySet} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/MTPSet} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1] EI of IC AspectSetReference which refers via ID to an IH containing [1]~IE of SUC ChoreographyParticipant} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class ChoreographyParticipant
*SUC ChoreographyParticipant* (Table~[Suc Choreography Participant](#tab:SucChoreographyParticipant)) describes an LEA as a choreography participant. The interface definition *SUC ChoreographyParticipantManager* is assigned to this model definition via a LinkedObject relation.

% Modelldefinition SUC ChoreographyParticipant
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ChoreographyParticipant*}
		{#tab:SucChoreographyParticipant}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ChoreographyParticipant**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for choreography participant} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/ChoreographyParticipant} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/LinkedObject} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IH to which an IE of SUC ChoreographySet relates via EI of IC AspectSet-Reference} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} 	[1] IE of SUC InputList \newline
																[1] IE of SUC OutputList } 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class InputList
*SUC InputList* (Table~[Suc Input List](#tab:SucInputList)) organizes all incoming system variables relevant to the configurable logic of a choreography participant. The MTP of a choreography participant always contains exactly one *InputList*.

% Modelldefinition SUC InputList
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC InputList*}
		{#tab:SucInputList}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **InputList**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for the list of input elements of a choreography participant} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/ChoreographyParticipant/InputList} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IE of SUC ChoreographyParticipant} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [0..*] IE of SUC InputElement} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class InputElement
*SUC InputElement* (Table~[Suc Input Element](#tab:SucInputElement)) describes an incoming system variable relevant to the configurable logic of a choreography participant. This may be a statically defined internal process variable of the participant or a process variable received by the participant from another participant.

% Modelldefinition SUC InputElement
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC InputElement*}
		{#tab:SucInputElement}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **InputElement**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for an input element of a choreography participant} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/InputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/LinkedObject} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Name}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} unique Number as index in the InputList (beginning at 0)}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IE of SUC InputList} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no children allowed)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class FixedInputElement
*SUC FixedInputElement* (Table~[Suc Fixed Input Element](#tab:SucFixedInputElement)) is derived from *SUC InputElement* and describes a statically defined incoming system variable provided by the choreography participant itself. A *FixedInputElement* is assigned to a *UnionElement* interface via a LinkedObject relation.

% Modelldefinition SUC FixedInputElement
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC FixedInputElement*}
		{#tab:SucFixedInputElement}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **FixedInputElement**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a statically defined input element} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/InputElement/FixedInputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/InputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class ConfigurableInputElement
*SUC ConfigurableInputElement* (Table~[Suc Configurable Input Element](#tab:SucConfigurableInputElement)) is derived from *SUC InputElement* and describes a configurable incoming system variable received by the choreography participant from another choreography participant. A *ConfigurableInputElement* is assigned to a derivation of the *CommunicationManager* interface via an ID link relation using the variable *ManagerLink*. A *ManagerIndex* is used to refer to a specific communication element within the *CommunicationManager*. In this way, the communication is configured such that the required system variable is exchanged. The interpretation of *ManagerIndex* depends on the derivation of *CommunicationManager* used. In the case of *OpcUaClientServerManager*, this is the index of the reader used.

% Modelldefinition SUC ConfigurableInputElement
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ConfigurableInputElement*}
		{#tab:SucConfigurableInputElement}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ConfigurableInputElement**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a configurable input element} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/InputElement/ConfigurableInputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/InputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                      & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ManagerLink}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} object identifier of the associated CommunicationManager interface}   &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} IDLinkAttribute-Type}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ManagerIndex}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} index of the incoming configurable communication entity within the communication manager}  &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class WritableInputElement
*SUC WritableInputElement* (Table~[Suc Writable Input Element](#tab:SucWritableInputElement)) is derived from *SUC InputElement* and describes an incoming system variable into which values can be written by another choreography participant. A *WritableInputElement* is assigned to a *WritableUnionElement* interface definition via a LinkedObject relation.

% Modelldefinition SUC WritableInputElement
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC WritableInputElement*}
		{#tab:SucWritableInputElement}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **WritableInputElement**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a writable input element} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/InputElement/WritableInputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/InputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ManagerLink}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} object identifier of the associated CommunicationManager interface}   &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} IDLinkAttribute-Type}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ManagerIndex}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} index of the field the value is written to within the communication manager}  &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class OutputList
*SUC OutputList* (Table~[Suc Output List](#tab:SucOutputList)) organizes all outgoing system variables relevant to the configurable logic of a choreography participant. The MTP of a choreography participant always contains exactly one *OutputList*.

% Modelldefinition SUC OutputList
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC OutputList*}
		{#tab:SucOutputList}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **OutputList**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for the list of output elements of a choreography participant} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/ChoreographyParticipant/OutputList} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1] AutomationMLBaseRoleClassLib/AutomationMLBaseRole (SRC)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IE of SUC ChoreographyParticipant} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [0..*] IE of SUC OutputElement} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class OutputElement
*SUC OutputElement* (Table~[Suc Output Element](#tab:SucOutputElement)) describes an outgoing system variable relevant to the configurable logic of a choreography participant. This may be a statically defined internal process variable of the participant or a configurable process variable received by the participant from another participant. An *OutputElement* is always assigned to a *UnionElement* interface via a LinkedObject relation.

% Modelldefinition SUC OutputElement
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC OutputElement*}
		{#tab:SucOutputElement}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **OutputElement**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for an output element of a choreography participant} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/OutputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/LinkedObject} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Name}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} unique Number as Index in the Output List (beginning at 0)}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IE of SUC OutputList} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no children allowed)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class FixedOutputElement
*SUC FixedOutputElement* (Table~[Suc Fixed Output Element](#tab:SucFixedOutputElement)) is derived from *SUC OutputElement* and describes a statically defined outgoing system variable used by the internal program of the choreography participant.

% Modelldefinition SUC FixedOutputElement
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC FixedOutputElement*}
		{#tab:SucFixedOutputElement}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **FixedOutputElement**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a statically defined output element} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/OutputElement/FixedOutputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/OutputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class ConfigurableOutputElement
*SUC ConfigurableOutputElement* (Table~[Suc Configurable Output Element](#tab:SucConfigurableOutputElement)) is derived from *SUC OutputElement* and describes a configurable outgoing system variable sent by the choreography participant to another choreography participant. A *ConfigurableOutputElement* is assigned to a derivation of the *CommunicationManager* interface via an ID link relation using the variable *ManagerLink*. A *ManagerIndex* is used to refer to a specific communication element within the *CommunicationManager*. In this way, the communication is configured such that the required system variable is exchanged. The interpretation of *ManagerIndex* depends on the derivation of *CommunicationManager* used. In the case of *OpcUaClientServerManager*, this is the index of the writer used.

% Modelldefinition SUC ConfigurableOutputElement
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ConfigurableOutputElement*}
		{#tab:SucConfigurableOutputElement}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ConfigurableOutputElement**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a configurable output element} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/OutputElement/ConfigurableOutputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPChoreographySUCLib/OutputElement} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ChoreographySet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ManagerLink}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} object identifier of the associated CommunicationManager interface}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} IDLinkAttribute-Type}              
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ManagerIndex}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:unsignedInt}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} index of the outcoming configurable communication entity within the CommunicationManager}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}


## MTP Specification of the TransportSet {#sec:AnhangTransportAspekt}
This chapter specifies the *TransportSet* as a new aspect of the MTP specification that contains all elements identified in the conceptual chapter~[Art3 LA](#chap:Art3LA).

### Übersicht {#subsec:AnhangTransportSetUebersicht}
#### Semantic Description of Transport Services
For semantic identification of the transport services introduced in Section~[Transportdienste](#sec:Transportdienste), a semantic identifier in the form of a *FunctionClassificationAttribute* is added to them. Table~[Function Classification Transportdienst](#tab:FunctionClassificationTransportdienst) specifies the corresponding *FunctionClassificationAttribute*. "2.0" denotes the version in major-minor format and can be incremented accordingly when changes are made to the *FunctionClassificationAttributes*.

% FunctionClassificationAttribute Transportdienst
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{FunctionClassificationAttribute of a Transport Service}
		{#tab:FunctionClassificationTransportdienst}\\
		\hline

		\multicolumn{2}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**FunctionClassificationAttribute for Transport Service**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Standard**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Level**}        & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Transport-Management}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Transport} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**IRDI**}     & 
		\multicolumn{1}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Logistics:Transport:2.0} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

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

% Schnittstellendefinition SUC TransportElement
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC TransportElement*}
		{#tab:DataAssemblySucTransportElement}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **TransportElement**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} root interface class for transport-related interface definitions} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/TransportElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &         
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} WQC}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BYTE}                &  
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Worst Quality Code}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &   
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} WQC}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class TransportClientManager
*SUC TransportClientManager* (Table~[Data Assembly Suc Transport Client Manager](#tab:DataAssemblySucTransportClientManager)) is derived from *SUC TransportElement* and is an abstract interface definition for configuring the communication link between an LEA and a flexible transport system. To implement this interface definition, a concrete manager must be derived from it. So far, only *SUC OpcUaTransportClientManager* has been specified as a derivation. *SUC TransportClientManager*, and thus also its derivations, are assigned to a *TransportNode* model definition in the *TransportSet* via an ID link relation.

% Schnittstellendefinition SUC TransportClientManager
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC TransportClientManager*}
		{#tab:DataAssemblySucTransportClientManager}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **TransportClientManager**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract interface definition for configuring the communication of the Logistics Equipment Assembly to a transport management system} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/TransportElement/Transport-ClientManager} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/TransportElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} }                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} -}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class OpcUaTransportClientManager
*SUC OpcUaTransportClientManager* (Table~[Data Assembly Suc Opc Ua Transport Client Manager](#tab:DataAssemblySucOpcUaTransportClientManager)) is derived from *SUC TransportClientManager* and is used to configure and establish an OPC~UA client/server communication link between the LEA and a flexible transport system. In addition, this interface contains the variable *LeaStateCur*, which enables transport management to determine the state of the LEA service. This is used to detect possible faults in the LEA and, if necessary, reroute transport services to this LEA.

% Schnittstellendefinition SUC OpcUaTransportClientManager
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC OpcUaTransportClientManager*}
		{#tab:DataAssemblySucOpcUaTransportClientManager}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **OpcUaTransportClientManager**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} configuration interface for an OPC~UA client communicating transport-relevant data} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/TransportElement/Transport-ClientManager/OpcUaTransportClientManager} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/TransportElement/Transport-ClientManager} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConfigApplyEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Enable flag to apply the prepared configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConfigApplyExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Apply the prepared configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Enable flag to establish connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Establish connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} DisconnectEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Enable flag to remove connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} DisconnectExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Remove connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ResetExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Reset communication block}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionAct}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Flag indicating an established connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionErr}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Flag indicating a connection error}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ErrorId}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Identifier of the connection error}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} EndpointExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Defines the server URL to connect with}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} NamespaceExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Defines Namespace to be used}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} EndpointReq}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Requested server URL}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} NamespaceReq}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Requested namespace}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}               &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} EndpointCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Currently configured server URL}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} NamespaceCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} STRING}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Currently configured namespace}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} LeaStateCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} MTP service state of the LEA service}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class TransportNodeManager
*SUC TransportNodeManager* (Table~[Data Assembly Suc Transport Node Manager](#tab:DataAssemblySucTransportNodeManager)) is derived from *SUC TransportElement* and is used to assign a TN proxy to a specific transport node in the LEA. This interface definition is assigned to a *TransportNode* model definition in the *TransportSet* via a LinkedObject relation.

% Schnittstellendefinition SUC TransportNodeManager
\begin{footnotesize}
	\begin{longtable}
		{
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l }
	
		\caption{Interface Definition of *SUC TransportNodeManager*}
		{#tab:DataAssemblySucTransportNodeManager}\\
	
		\hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - DataAssembly Definition**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **TransportNodeManager**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} System Unit Class (SUC)}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -}
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} configuration interface to assign transport nodes to transport proxies} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/TransportElement/Transport-NodeManager} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPDataAssemblySUCLib/DataAssembly/TransportElement} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Role Classes**} & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} -}                     & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}              &                                              
		\multicolumn{4}{L{9.6cm}|}{\cellcolor[HTML]{FFFFFF} -}              
		\\ \hline
	
	
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Access**}        	& 
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Attribute-Type Reference**} 			& 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{E0E0E0}**Base Function**} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConfigApplyEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Enable flag to apply the prepared configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
	
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConfigApplyExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Apply the prepared configuration}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Enable flag to establish connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Establish connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} DisconnectEn}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Enable flag to remove connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} DisconnectExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Remove connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ResetExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Reset communication block}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionAct}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Flag indicating an established connection}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ConnectionErr}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} BOOL}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Flag indicating a connection error}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ErrorId}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DWORD}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Identifier of the connection error}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ProxyIdExt}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\rightarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Defines related proxy in the transportsystem}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ProxyIdReq}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Requested transport proxy}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ProxyIdCur}               & 
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} LOL $\leftarrow$ LEA}                &      
		\multicolumn{1}{L{1.9cm}|}{\cellcolor[HTML]{FFFFFF} DINT}                &                                             
		\multicolumn{1}{L{3.01cm}|}{\cellcolor[HTML]{FFFFFF} Currently configured transport proxy}               &
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}                &                                             
		\multicolumn{1}{L{2.1cm}|}{\cellcolor[HTML]{FFFFFF} -}            
		\\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}  \\ \hline
		
		\multicolumn{6}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline
	
		\multicolumn{6}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{5}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline
	
	\end{longtable}
\end{footnotesize}

### Model Definitions {#subsec:AnhangTransportSetModelle}
#### Specification of the Instance Hierarchy Transports
*IH Transports* (Table~[Ih Transports](#tab:IhTransports)) is the entry point for the transport-related information model in the instance hierarchy of an MTP.

% Modelldefinition IH Transports
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *IH Transports*}
		{#tab:IhTransports}\\
		\hline

		\multicolumn{3}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **Transports**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Instance Hierarchy (IH)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} root element for the transport-related information model of an MTP} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ID}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &                                              
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF} Identifier of the Instance Hierarchy}              
		\\ \hline


		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**}      
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF} -}   
		\\ \hline

		\multicolumn{3}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1..*] IE of SUC TransportNode} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class Library MTPTransportSUCLib
*SUCL MTPTransportSUCLib* (Table~[Sucl MTP Transport SUC Lib](#tab:SuclMTPTransportSUCLib)) contains the System Unit Classes of the *TransportSet* of an MTP.

% Bibliothek SUCL MTPTransportSUCLib
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Library Definition of *SUCL MTPTransportSUCLib*}
		{#tab:SuclMTPTransportSUCLib}\\
		\hline

		\multicolumn{3}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Library Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **MTPTransportSUCLib**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClassLibrary (SUCL)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Library containing the transport-related SUC model definitions of an MTP} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{2}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{1}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{3}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class TransportSet
*SUC TransportSet* (Table~[Suc Transport Set](#tab:SucTransportSet)), as a new aspect set of the MTP specification, contains all model definitions required to describe the transport-relevant information of an LEA.

% Modelldefinition SUC TransportSet
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC TransportSet*}
		{#tab:SucTransportSet}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **TransportSet**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Model definition for transport aspect set} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportSet} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/MTPSet} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} [1] EI of IC AspectSetReference which refers via ID to an IH containing \newline
		[1..*] IE of SUC TransportNode} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class TransportNode
*SUC TransportNode* (Table~[Suc Transport Node](#tab:SucTransportNode)) is an abstract model definition for describing a transport node available in an LEA. Currently, five concrete types of transport nodes are derived from this model definition: *SUC InboundNode*, *SUC OutboundNode*, *SUC InOutboundNode*, *SUC ProcessingNode*, and *SUC OrderNode*. A *SUC TransportNode* is assigned to the *TransportNodeManager* interface definition via a LinkedObject relation, which enables the assignment of the transport node to a TN proxy in transport management. In addition, *SUC TransportNode* is assigned to the *TransportClientManager* interface, which connects the LEA to transport management. For this assignment, the ID link mechanism and the variable *ClientLink* are used.

% Modelldefinition SUC TransportNode
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC TransportNode*}
		{#tab:SucTransportNode}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **TransportNode**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} abstract}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Model definition for a transport node of a transport-enabled Logistics Equipment Assembly} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPSUCLib/LinkedObject} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &                                              
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} ClientLink}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF} xs:string}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF} object identifier of the associated TransportClientManager interface}              &                                             
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF} IDLinkAttribute-Type}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} IH to which an IE of SUC TransportSet relates via EI of IC AspectSetReference} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no children allowed)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class InboundNode
*SUC InboundNode* (Table~[Suc Inbound Node](#tab:SucInboundNode)) is derived from *SUC TransportNode* and describes a transport node for transferring an LO from a flexible transport system to an LEA.

% Modelldefinition SUC InboundNode
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC InboundNode*}
		{#tab:SucInboundNode}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **InboundNode**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} Model definition for a transport node transferring objects from a flexible transport system to the Logistics Equipment Assembly} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode/InboundNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}    &   
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &     
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class OutboundNode
*SUC OutboundNode* (Table~[Suc Outbound Node](#tab:SucOutboundNode)) is derived from *SUC TransportNode* and describes a transport node for transferring an LO from an LEA to a flexible transport system.

% Modelldefinition SUC OutboundNode
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC OutboundNode*}
		{#tab:SucOutboundNode}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **OutboundNode**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a transport node transferring objects from the Logistics Equipment Assembly to a flexible transport system} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode/OutboundNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}    &   
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &     
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class InOutboundNode
*SUC InOutboundNode* (Table~[Suc In Outbound Node](#tab:SucInOutboundNode)) is derived from *SUC TransportNode* and describes a transport node for transferring LOs between an LEA and a flexible transport system in both directions.

% Modelldefinition SUC InOutboundNode
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC InOutboundNode*}
		{#tab:SucInOutboundNode}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **InOutboundNode**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a transport node transferring objects between the Logistics Equipment Assembly and a flexible transport system in both directions} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode/InOutboundNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}    &   
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &     
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class ProcessingNode
*SUC ProcessingNode* (Table~[Suc Processing Node](#tab:SucProcessingNode)) is derived from *SUC TransportNode* and describes a transport node for processing an LO without handing it over from the flexible transport system to an LEA.

% Modelldefinition SUC ProcessingNode
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC ProcessingNode*}
		{#tab:SucProcessingNode}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **ProcessingNode**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a transport node processing an object without transferring the object from the flexible transport system to the Logistics Equipment Assembly} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode/ProcessingNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}    &   
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &     
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}

#### Specification of the System Unit Class OrderNode
*SUC OrderNode* (Table~[Suc Order Node](#tab:SucOrderNode)) is derived from *SUC TransportNode* and describes a transport node for reporting transport demands and initiating corresponding transport processes.

% Modelldefinition SUC OrderNode
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}l 
		>{\columncolor[HTML]{FFFFFF}}l
		>{\columncolor[HTML]{FFFFFF}}l |}

		\caption{Model Definition of *SUC OrderNode*}
		{#tab:SucOrderNode}\\
		\hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Module Type Package - Model Definition**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} **OrderNode**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Type**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} SystemUnitClass (SUC)}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Modifier**}        & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} sealed}
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} model definition for a node to indicate transport demands and initialize corresponding transport processes} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Path**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode/OrderNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML BaseRef**} & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} MTPTransportSUCLib/TransportNode} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**RoleClasses**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} -} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Version**}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TransportSet.Base V2.0.0} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Properties**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}    &   
		\multicolumn{2}{L{8.69cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Attributes**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{E0E0E0}**Name**}        	& 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{E0E0E0}**Type**} 			& 
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{E0E0E0}**Description**} 			& 
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{E0E0E0}**AttributeType Reference**} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF}-}                     & 
		\multicolumn{1}{L{3cm}|}{\cellcolor[HTML]{FFFFFF}-}              &      
		\multicolumn{1}{L{5.43cm}|}{\cellcolor[HTML]{FFFFFF}-}              &     
		\multicolumn{1}{L{3.1cm}|}{\cellcolor[HTML]{FFFFFF}-}              
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Comment**} 
		\\ \hline
		
		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{FFFFFF}-}   
		\\ \hline

		\multicolumn{4}{|C{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AutomationML Object - Instance Constraints**}  
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Parents}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

		\multicolumn{1}{|L{2.8cm}|}{\cellcolor[HTML]{FFFFFF} Allowed Children}     & 
		\multicolumn{3}{L{11.83cm}|}{\cellcolor[HTML]{FFFFFF} (no further constraints given)} 
		\\ \hline

	\end{longtable}
\end{footnotesize}


## Conformity Declaration for Logistics Equipment Assemblies {#sec:Konformitätsbeschreibung}
Based on the findings of this dissertation, Table~[Konformitätsbeschreibung](#tab:Konformitätsbeschreibung) provides an overview of the existing and newly introduced profiles required for applying the MTP concept in production-related logistics. A distinction is made between profiles that are generally relevant for LEA automation, profiles that LEAs must fulfill in order to participate in a logistics line, and profiles required for connecting LEAs to flexible transport systems.

% Konformitätsbeschreibung
\begin{footnotesize}
	\begin{longtable}{|
		>{\columncolor[HTML]{E0E0E0}}l 
		>{\columncolor[HTML]{FFFFFF}}c 
		>{\columncolor[HTML]{FFFFFF}}c 
		>{\columncolor[HTML]{FFFFFF}}c |}
		\caption{Profiles to Be Implemented for Applying the MTP Concept in Production-Related Logistics; $\times$ - profile is required; ($\times$) - profile is optional; empty - profile is not required}
		{#tab:Konformitätsbeschreibung}\\
		\hline

		\multicolumn{1}{|C{6.78cm}|}{\cellcolor[HTML]{E0E0E0}**Profil**}        	& 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{E0E0E0}**LEA-Automati-sierung**} 			& 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{E0E0E0}**Teilnahme Logistics Line**} 			& 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{E0E0E0}**Anbindung Transportsystem**} 
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**Manifest**} 
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Manifest.Base }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		
		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:Manifest.Composed (neu) }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} } &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} }
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**AttachmentSet**} 
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:AttachmentSet.Base }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)}
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**TextSet**} 
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:TextSet.Base }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline


		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**HMISet**} 
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:HMISet.Base }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:HMISet.Composed (neu) }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} } &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} }
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**DataAssemblySet**} 
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet.Base }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet. ComplexTypes (neu) }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:DataAssemblySet. Time (neu) }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**ServiceSet**} 
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Base }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet. ComplexTypes (neu) }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServiceSet.Logistics (neu) }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**ProcessValueSet**} 
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ProcessValueSet.Base }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)}
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ProcessValueSet. ComplexTypes (neu) }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} ($\times$)}
		\\ \hline

		\multicolumn{4}{|L{14.8cm}|}{\cellcolor[HTML]{E0E0E0}**ServerAssemblySet**} 
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServerAssemblySet. Base }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

		\multicolumn{1}{|L{6.78cm}|}{\cellcolor[HTML]{FFFFFF} ModuleTypePackage:ServerAssemblySet. OPCUA }  & 
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$} &      
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}  &     
		\multicolumn{1}{C{2.5cm}|}{\cellcolor[HTML]{FFFFFF} $\times$}
		\\ \hline

	\end{longtable}
\end{footnotesize}

It should be noted with regard to this list that this dissertation initially considers the core aspects of Parts 1 to 5 of the MTP specification. Logistics-specific extensions may also arise in further aspects of the MTP specification in the future. For example, it may become necessary to provide alarms at LEA level rather than at service or individual-control level. In addition, logistics-specific diagnostic functions may be required. These aspects should be investigated in future work, see also Chapter~[ausblick](#chap:ausblick).

[^1]: Appendix~[MTP Extension of the HMISet](#sec:AnhangHMISet) also describes that *RC HasExternalMtpContext* can be assigned to *SUC PictureFrame* and *SUC ReferencedPicture*.
[^2]: *AT ComposedTypeRevisionType* is therefore similar to *AT DeviceRevisionType*. However, while *AT DeviceRevisionType* refers only to the content of the *ServerAssemblySet* of one MTP, *AT ComposedTypeRevisionType* refers to the distributed content of the *ServerAssemblySets* of multiple MTPs.
[^3]: In this dissertation, *SUC PictureFrame* is initially assigned to the profile *ModuleTypePackage:HMISet.Composed V2.0.0* because it is used exclusively to embed external LEA process pictures into a Composed MTP. However, this SUC is also suitable for embedding MTP-internal process pictures in non-composed MTPs. Therefore, if it is adopted into the MTP specification in the future, it appears appropriate to define a separate profile for this SUC.
[^4]: This *PictureFrame* mechanism may also be useful in non-composed MTPs, for example to embed detail pictures into an overall picture of one PEA or LEA. In that case, *ContextLink* is not required. Within this dissertation, however, *SUC PictureFrame* is considered exclusively in the context of line process pictures in Composed MTPs.
[^5]: It is recommended to incorporate *RC HasTimeFormat* and the associated *AT TimeFormatAttributeType* into the base profile *ModuleTypePackage:DataAssemblySet.Base* in the future.
[^6]: Since only the extension of *SUC DIntView* is used in this dissertation, only this case is described here. *SUC DIntMan*, *SUC DIntServParam*, and *SUC DIntProcessValueIn* must be extended in the same way by assigning *RC HasTimeFormat*.
[^7]: This derivation is possible because a write access always includes reading back the written value. A write access is therefore an extension of a read access.
[^8]: *SUC CommunicationManager* and the derived *SUC OpcUaClientServerManager* can in principle also be used for configurable communication independently of choreographies, for example in decentralized orchestrations. Since such approaches are not yet provided in the MTP specification, these interface definitions are initially assigned to the *ChoreographySet*. For future cross-cutting use cases, a shift into the *ServerAssemblySet* [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51) may be appropriate.
[^9]: Bei der *SUC UnionElement* könnten zukünftig noch andere Datentypen ergänzt werden. Alle weiteren Schnittstellen, die die *SUC UnionElement* nutzen, sollte folglich auch Erweiterungen erlauben und nicht *sealed* sein.

