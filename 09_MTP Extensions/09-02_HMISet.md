## MTP Extension of the HMISet {#sec:AnhangHMISet}
This chapter specifies all identified extensions of the *HMISet* and integrates them into the existing MTP specification [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2).

### Overview {#subsec:AnhangHMISetUebersicht}
According to Section~[Linien Bedienbild](#subsec:LinienBedienbild), the two model definitions *SUC PictureFrame* and *SUC ReferencedPicture* are required for process-picture modeling in choreographed logistics lines. As shown in Figure~[Extension of the HMISet for Representing Line Process Pictures](#fig:ErweiterungHMISet), these definitions, together with all other model definitions for process-picture modeling, are organized in *SUCL MTPHMISUCLib*. In MTP modeling, any number of *ReferencedPictures* can be inserted into the instance hierarchy of the *HMISet*, similar to *Pictures* according to [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2). Any number of instances of *SUC PictureFrame* can be added to the *Pictures* or *SemanticGroups* modeled in the MTP, similar to *VisualObjects* according to [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2). The model definitions of *SUC HMISet*, *SUC Picture*, and *SUC SemanticGroup* must therefore be extended to allow subordinate *ReferencedPictures* and *PictureFrames*, respectively. *SUC PictureFrame* and *SUC ReferencedPicture* use *RC HasExternalMtpContext*, specified in Appendix~[Model Definitions](#subsec:AnhangManifestModelle), to reference external objects from other MTP files. The new and extended model definitions are specified in detail in Appendix~[Model Definitions](#subsec:AnhangHMISetModelle) and are assigned to the new profile *ModuleTypePackage:HMISet.Composed V2.0.0*.[^1]

![Extension of the HMISet for Representing Line Process Pictures](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/HMISet Erweiterungen/Klassendiagramm.drawio.png)
*Extension of the HMISet for Representing Line Process Pictures* {#fig:ErweiterungHMISet}

### Model Definitions {#subsec:AnhangHMISetModelle}
#### Specification of the System Unit Class PictureFrame
*SUC PictureFrame* (Table~[Suc Picture Frame](#tab:SucPictureFrame)) enables the embedding of a referenced process picture into another process picture. For this purpose, the process picture to be displayed in the *PictureFrame* is referenced by means of *PictureLink* using the ID link mechanism according to [MTP Specification Part 1](../98_References/README.md#mtp-specification-part-1). The *Picture-Frame* itself can be placed in a process picture of *SUC Picture* or, if applicable, in a contained *SUC SemanticGroup*, analogous to a *VisualObject* according to [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2). The size and position of the *PictureFrame* are defined by the variables *Width*, *Height*, *X*, *Y*, and *ZIndex*.[^2] If a process picture modeled in another MTP is to be displayed in the *PictureFrame* for example, a line process picture according to Section~[Linien Bedienbild](#subsec:LinienBedienbild), *RC HasExternalMtpContext* must additionally be annotated as an SRC. This enables the referenced MTP file to be addressed by entering a *ContextLink*.

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



[^1]: In this dissertation, *SUC PictureFrame* is initially assigned to the profile *ModuleTypePackage:HMISet.Composed V2.0.0* because it is used exclusively to embed external LEA process pictures into a Composed MTP. However, this SUC is also suitable for embedding MTP-internal process pictures in non-composed MTPs. Therefore, if it is adopted into the MTP specification in the future, it appears appropriate to define a separate profile for this SUC.
[^2]: This *PictureFrame* mechanism may also be useful in non-composed MTPs, for example to embed detail pictures into an overall picture of one PEA or LEA. In that case, *ContextLink* is not required. Within this dissertation, however, *SUC PictureFrame* is considered exclusively in the context of line process pictures in Composed MTPs.
