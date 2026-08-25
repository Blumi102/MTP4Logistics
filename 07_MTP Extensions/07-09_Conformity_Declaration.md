## Conformity Declaration for Logistics Equipment Assemblies
Based on the findings of this work, [Table 7.76](#table-776-profiles-to-be-implemented-for-applying-the-mtp-concept-in-production-related-logistics) provides an overview of the existing and newly introduced profiles required for applying the MTP concept in production-related logistics. A distinction is made between profiles that are generally relevant for LEA automation, profiles that LEAs must fulfill in order to participate in a logistics line, and profiles required for connecting LEAs to flexible transport systems.

##### Table 7.76: Profiles to Be Implemented for Applying the MTP Concept in Production-Related Logistics
*&times; - profile is required; (&times;) - profile is optional; empty - profile is not required*

<table>
	<tr>
		<th align="left">Profile</th>
		<th align="left">LEA Automation</th>
		<th align="left">Participation in Logistics Line</th>
		<th align="left">Connection to Transport System</th>
	</tr>
	<tr>
		<td colspan="4" align="left"><strong>Manifest</strong></td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:Manifest.Base</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:Manifest.Composed (neu)</td>
		<td align="left"></td>
		<td align="left">&times;</td>
		<td align="left"></td>
	</tr>
	<tr>
		<td colspan="4" align="left"><strong>AttachmentSet</strong></td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:AttachmentSet.Base</td>
		<td align="left">(&times;)</td>
		<td align="left">&times;</td>
		<td align="left">(&times;)</td>
	</tr>
	<tr>
		<td colspan="4" align="left"><strong>TextSet</strong></td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:TextSet.Base</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td colspan="4" align="left"><strong>HMISet</strong></td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:HMISet.Base</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:HMISet.Composed (neu)</td>
		<td align="left"></td>
		<td align="left">&times;</td>
		<td align="left"></td>
	</tr>
	<tr>
		<td colspan="4" align="left"><strong>DataAssemblySet</strong></td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:DataAssemblySet.Base</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:DataAssemblySet. ComplexTypes (neu)</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:DataAssemblySet. Time (neu)</td>
		<td align="left">(&times;)</td>
		<td align="left">(&times;)</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td colspan="4" align="left"><strong>ServiceSet</strong></td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:ServiceSet.Base</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:ServiceSet. ComplexTypes (neu)</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:ServiceSet.Logistics (neu)</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td colspan="4" align="left"><strong>ProcessValueSet</strong></td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:ProcessValueSet.Base</td>
		<td align="left">(&times;)</td>
		<td align="left">(&times;)</td>
		<td align="left">(&times;)</td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:ProcessValueSet. ComplexTypes (neu)</td>
		<td align="left">(&times;)</td>
		<td align="left">(&times;)</td>
		<td align="left">(&times;)</td>
	</tr>
	<tr>
		<td colspan="4" align="left"><strong>ServerAssemblySet</strong></td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:ServerAssemblySet. Base</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
	<tr>
		<td align="left">ModuleTypePackage:ServerAssemblySet. OPCUA</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
		<td align="left">&times;</td>
	</tr>
</table>

It should be noted with regard to this list that this work initially considers the core aspects of Parts 1 to 5 of the MTP specification. Logistics-specific extensions may also arise in further aspects of the MTP specification in the future. For example, it may become necessary to provide alarms at LEA level rather than at service or individual-control level. In addition, logistics-specific diagnostic functions may be required. These aspects should be investigated in future work.
