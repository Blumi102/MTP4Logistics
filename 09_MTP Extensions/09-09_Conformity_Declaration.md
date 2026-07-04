## Conformity Declaration for Logistics Equipment Assemblies
Based on the findings of this work, Table~[Konformitätsbeschreibung](#tab:Konformitätsbeschreibung) provides an overview of the existing and newly introduced profiles required for applying the MTP concept in production-related logistics. A distinction is made between profiles that are generally relevant for LEA automation, profiles that LEAs must fulfill in order to participate in a logistics line, and profiles required for connecting LEAs to flexible transport systems.

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

It should be noted with regard to this list that this work initially considers the core aspects of Parts 1 to 5 of the MTP specification. Logistics-specific extensions may also arise in further aspects of the MTP specification in the future. For example, it may become necessary to provide alarms at LEA level rather than at service or individual-control level. In addition, logistics-specific diagnostic functions may be required. These aspects should be investigated in future work, see also Chapter~[ausblick](#chap:ausblick).
