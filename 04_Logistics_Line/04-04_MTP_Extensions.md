## 4.4 MTP Extensions

In the preceding sections, a number of extensions to the MTP specification were identified that are necessary in the context of automating choreographed Logistics Lines. [Table 4.4](#table-44-mtp-specification-extensions-for-logistics-line-automation) provides an overview of the model and DataAssembly definitions as well as workflows to be introduced. A more detailed description is provided in the specification sections referenced in [Table 4.4](#table-44-mtp-specification-extensions-for-logistics-line-automation).

##### Table 4.4: MTP Specification Extensions for Logistics Line Automation

<table>
  <tr>
    <th align="left" colspan="3">DataAssembly definitions</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Definition</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC UnionElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-747-dataassembly-definition-of-suc-unionelement">Table 7.47</a>)</td>
    <td align="left">Interface for reading a value with a runtime-selectable data type</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC WritableUnionElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-748-dataassembly-definition-of-suc-writableunionelement">Table 7.48</a>)</td>
    <td align="left">Interface for writing a value with a runtime-selectable data type</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ChoreographyElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-749-dataassembly-definition-of-suc-choreographyelement">Table 7.49</a>)</td>
    <td align="left">Base interface for all interfaces required for choreography configuration</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ChoreographyParticipantManager</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-750-dataassembly-definition-of-suc-choreographyparticipantmanager">Table 7.50</a>)</td>
    <td align="left">Interface for configuring and controlling the execution of Configurable Logic</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC CommunicationManager</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-751-dataassembly-definition-of-suc-communicationmanager">Table 7.51</a>)</td>
    <td align="left">Base interface for all Configurable Communication configuration interfaces</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC OpcUaClientServerManager</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-752-dataassembly-definition-of-suc-opcuaclientservermanager">Table 7.52</a>)</td>
    <td align="left">Interface for configuring and controlling OPC UA Client/Server-based Configurable Communication</td>
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
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>IH Choreography</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-753-model-definition-of-ih-choreography">Table 7.53</a>)</td>
    <td align="left">Instance hierarchy for organizing all choreography-related models of an MTP</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ChoreographySet</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-755-model-definition-of-suc-choreographyset">Table 7.55</a>)</td>
    <td align="left">Aspect set organizing all choreography-related model definitions</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ChoreographyParticipant</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-756-model-definition-of-suc-choreographyparticipant">Table 7.56</a>)</td>
    <td align="left">Model describing a LEA as a choreography participant</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC InputList</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-757-model-definition-of-suc-inputlist">Table 7.57</a>)</td>
    <td align="left">Model for the Input List of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC OutputList</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-762-model-definition-of-suc-outputlist">Table 7.62</a>)</td>
    <td align="left">Model for the Output List of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC InputElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-758-model-definition-of-suc-inputelement">Table 7.58</a>)</td>
    <td align="left">Model for an element of the Input List</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC OutputElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-763-model-definition-of-suc-outputelement">Table 7.63</a>)</td>
    <td align="left">Model for an element of the Output List</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC FixedInputElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-759-model-definition-of-suc-fixedinputelement">Table 7.59</a>)</td>
    <td align="left">Fixed input element hard-coded by the LEA program</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC FixedOutputElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-764-model-definition-of-suc-fixedoutputelement">Table 7.64</a>)</td>
    <td align="left">Fixed output element hard-coded by the LEA program</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ConfigurableInputElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-760-model-definition-of-suc-configurableinputelement">Table 7.60</a>)</td>
    <td align="left">Input element for reading a value from another LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ConfigurableOutputElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-765-model-definition-of-suc-configurableoutputelement">Table 7.65</a>)</td>
    <td align="left">Output element for writing a value to another LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC WritableInputElement</em> (<a href="../07_MTP%20Extensions/07-07_ChoreographySet.md#table-761-model-definition-of-suc-writableinputelement">Table 7.61</a>)</td>
    <td align="left">Passive input element that can be written by another LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: Manifest.Composed V2.0.0</td>
    <td align="left"><em>SUC ComposedModuleTypePackage</em> (<a href="../07_MTP%20Extensions/07-01_Manifest.md#table-71-model-definition-of-suc-composedmoduletypepackage">Table 7.1</a>)</td>
    <td align="left">Base model for a Composed MTP; signals a composed type and carries verification metadata</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: Manifest.Composed V2.0.0</td>
    <td align="left"><em>AT ComposedTypeRevisionType</em> (<a href="../07_MTP%20Extensions/07-01_Manifest.md#table-72-model-definition-of-at-composedtyperevisiontype">Table 7.2</a>)</td>
    <td align="left">Attribute type for version information of a choreographed function</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: Manifest.Composed V2.0.0</td>
    <td align="left"><em>RC HasExternalMtpContext</em> (<a href="../07_MTP%20Extensions/07-01_Manifest.md#table-74-model-definition-of-rc-hasexternalmtpcontext">Table 7.4</a>)</td>
    <td align="left">RoleClass indicating that a referenced object originates from an attached LEA MTP</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC PictureFrame</em> (<a href="../07_MTP%20Extensions/07-02_HMISet.md#table-75-model-definition-of-suc-pictureframe">Table 7.5</a>)</td>
    <td align="left">Model for embedding a display from an attached LEA MTP into another display (display-in-display, Variant 2)</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC Picture</em> (extension) (<a href="../07_MTP%20Extensions/07-02_HMISet.md#table-76-model-definition-of-suc-picture">Table 7.6</a>)</td>
    <td align="left">Extension of the existing Picture model to support PictureFrames</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC SemanticGroup</em> (extension) (<a href="../07_MTP%20Extensions/07-02_HMISet.md#table-77-model-definition-of-suc-semanticgroup">Table 7.7</a>)</td>
    <td align="left">Extension of the existing SemanticGroup model to support PictureFrames</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC ReferencedPicture</em> (<a href="../07_MTP%20Extensions/07-02_HMISet.md#table-78-model-definition-of-suc-referencedpicture">Table 7.8</a>)</td>
    <td align="left">Model for referencing displays or display hierarchies from attached LEA MTPs into the Composed MTP display hierarchy (Variants 3 and 4)</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC HMISet</em> (extension) (<a href="../07_MTP%20Extensions/07-02_HMISet.md#table-79-model-definition-of-suc-hmiset">Table 7.9</a>)</td>
    <td align="left">Extension of the existing HMISet model to support ReferencedPictures</td>
  </tr>
  <tr>
    <th align="left" colspan="3">Workflows</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Workflow</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: Manifest.Composed V2.0.0</td>
    <td align="left"><a href="../07_MTP%20Extensions/07-01_Manifest.md#type-verification">Type verification</a></td>
    <td align="left">Verifies the type of the choreography configuration loaded on the LEAs against the type described in the Composed MTP</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: Manifest.Composed V2.0.0</td>
    <td align="left"><a href="../07_MTP%20Extensions/07-01_Manifest.md#version-verification">Version verification</a></td>
    <td align="left">Verifies the version of the choreography configuration loaded on the LEAs against the version described in the Composed MTP</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: Manifest.Composed V2.0.0</td>
    <td align="left"><a href="../07_MTP%20Extensions/07-01_Manifest.md#instance-verification">Instance verification</a></td>
    <td align="left">Verifies that the LEA instances installed in the Logistics Line match the planned instances specified in the Composed MTP</td>
  </tr>
</table>

For the choreography-related model definitions, a new library *SUCL MTPChoreographySUCLib* is introduced. For the *RC HasExternalMtpContext*, a new library *RCL MTPRCLib* is introduced.
