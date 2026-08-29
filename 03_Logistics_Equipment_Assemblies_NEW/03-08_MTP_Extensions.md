### 3.8 MTP Extensions

In the preceding sections, a number of extensions to the MTP specification were identified that are necessary in the context of automating Logistics Equipment Assemblies. [Table 3.5](#table-35-mtp-extensions-for-lea-automation) provides an overview of the model and interface definitions to be introduced. A more detailed description is provided in the specification sections referenced in [Table 3.5](#table-35-mtp-extensions-for-lea-automation).

##### Table 3.5: MTP Extensions for LEA Automation

<table>
  <tr>
    <th align="left" colspan="3">Interface Definitions</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Definition</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC StructServParam</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-725-dataassembly-definition-of-suc-structservparam">Table 7.25</a>)</td>
    <td align="left">Transfer of service parameters with structured data types</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC ArrayServParam</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-726-dataassembly-definition-of-suc-arrayservparam">Table 7.26</a>)</td>
    <td align="left">Transfer of service parameters with array data types</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>RC LogisticsInteractionExtension</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-727-dataassembly-definition-of-rc-logisticsinteractionextension">Table 7.27</a>)</td>
    <td align="left">Extension of the ServiceControl interface for logistics interaction variables</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC ServiceControl</em> (extension) (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-728-dataassembly-definition-of-suc-servicecontrol">Table 7.28</a>)</td>
    <td align="left">Extension of the existing ServiceControl interface to allow attachment of <em>RC LogisticsInteractionExtension</em></td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC StructView</em> (<a href="../07_MTP%20Extensions/07-03_DataAssemblySet.md#table-78-dataassembly-definition-of-suc-structview">Table 7.8</a>)</td>
    <td align="left">Display of structured values</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC ArrayView</em> (<a href="../07_MTP%20Extensions/07-03_DataAssemblySet.md#table-79-dataassembly-definition-of-suc-arrayview">Table 7.9</a>)</td>
    <td align="left">Display of array-managed values</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC StructMan</em> (<a href="../07_MTP%20Extensions/07-03_DataAssemblySet.md#table-710-dataassembly-definition-of-suc-structman">Table 7.10</a>)</td>
    <td align="left">Operator manipulation of structured-type values</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC StructManInt</em> (<a href="../07_MTP%20Extensions/07-03_DataAssemblySet.md#table-711-dataassembly-definition-of-suc-structmanint">Table 7.11</a>)</td>
    <td align="left">Operator or LEA-internal manipulation of structured-type values</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC ArrayMan</em> (<a href="../07_MTP%20Extensions/07-03_DataAssemblySet.md#table-712-dataassembly-definition-of-suc-arrayman">Table 7.12</a>)</td>
    <td align="left">Operator manipulation of array-type values</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC ArrayManInt</em> (<a href="../07_MTP%20Extensions/07-03_DataAssemblySet.md#table-713-dataassembly-definition-of-suc-arraymanint">Table 7.13</a>)</td>
    <td align="left">Operator or LEA-internal manipulation of array-type values</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ProcessValueSet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC StructProcessValueIn</em> (<a href="../07_MTP%20Extensions/07-05_ProcessValueSet.md#table-739-dataassembly-definition-of-suc-structprocessvaluein">Table 7.39</a>)</td>
    <td align="left">Reading a structured-type value from another LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ProcessValueSet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC ArrayProcessValueIn</em> (<a href="../07_MTP%20Extensions/07-05_ProcessValueSet.md#table-740-dataassembly-definition-of-suc-arrayprocessvaluein">Table 7.40</a>)</td>
    <td align="left">Reading an array managed by another LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ProcessValueSet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC OutputElement</em> (<a href="../07_MTP%20Extensions/07-05_ProcessValueSet.md#table-741-dataassembly-definition-of-suc-outputelement">Table 7.41</a>)</td>
    <td align="left">Abstract base for typed process value outputs</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ProcessValueSet.ComplexTypes V2.0.0</td>
    <td align="left"><em>SUC ArrayProcessValueOut</em> (<a href="../07_MTP%20Extensions/07-05_ProcessValueSet.md#table-742-dataassembly-definition-of-suc-arrayprocessvalueout">Table 7.42</a>)</td>
    <td align="left">Providing a LEA-internal array to another LEA</td>
  </tr>
  <tr>
    <th align="left" colspan="3">Model Definitions</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Definition</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Base V2.0.0</td>
    <td align="left"><em>SUC ServiceParameter</em> (extension) (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-729-model-definition-of-suc-serviceparameter">Table 7.29</a>)</td>
    <td align="left">Extension with <em>FunctionClassificationAttributes</em> for parameters</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC LogisticsInteraction</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-730-model-definition-of-suc-logisticsinteraction">Table 7.30</a>)</td>
    <td align="left">Aggregation of all logistics-specific LEA requests to the LOL</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC LogisticsQuestion</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-731-model-definition-of-suc-logisticsquestion">Table 7.31</a>)</td>
    <td align="left">Base model for a LEA request to the LOL</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC ProductParameterRequest</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-732-model-definition-of-suc-productparameterrequest">Table 7.32</a>)</td>
    <td align="left">LEA request for product-specific parameters</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC PackagingParameterRequest</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-733-model-definition-of-suc-packagingparameterrequest">Table 7.33</a>)</td>
    <td align="left">LEA request for packaging-specific parameters</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC ProductParameterUpdatedInfo</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-734-model-definition-of-suc-productparameterupdatedinfo">Table 7.34</a>)</td>
    <td align="left">LEA notification to the LOL of a changed product parameter set</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC PackagingParameterUpdatedInfo</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-735-model-definition-of-suc-packagingparameterupdatedinfo">Table 7.35</a>)</td>
    <td align="left">LEA notification to the LOL of a changed packaging parameter set</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>RC HasLogisticsInteraction</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-737-model-definition-of-rc-haslogisticsinteraction">Table 7.37</a>)</td>
    <td align="left">Association of a <em>LogisticsInteraction</em> to a LEA service</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC Service</em> (extension) (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-738-model-definition-of-suc-service">Table 7.38</a>)</td>
    <td align="left">Extension of the existing Service model to allow attachment of <em>RC HasLogisticsInteraction</em></td>
  </tr>
</table>

In addition to these definitions, *FunctionClassificationAttributes* are introduced for CES and SES procedures as well as for the parameters *ProductId*, *LogisticsObjectStatus*, *ProductDataSet*, *PackagingId*, and *PackagingDataSet* ([Section 7.4.1](../07_MTP%20Extensions/07-04_ServiceSet.md#741-overview)). A mechanism for modeling complex data types in an OPC UA server is also specified as a supplementary artifact ([Section 7.6](../07_MTP%20Extensions/07-06_ServerAssemblySet.md#76-mtp-extension-of-the-serverassemblyset)). 
