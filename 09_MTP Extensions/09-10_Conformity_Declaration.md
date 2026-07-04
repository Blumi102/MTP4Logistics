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






