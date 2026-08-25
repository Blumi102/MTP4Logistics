### 5.7 MTP Extensions

In the preceding sections, a number of extensions to the MTP specification were identified that are necessary in the context of automating flexible transports in the Logistics Area. [Table 5.6](#table-56-mtp-specification-extensions-for-logistics-area-transport-automation) provides an overview of the model and interface definitions to be introduced, with links to their detailed specifications.

##### Table 5.6: MTP Specification Extensions for Logistics Area Transport Automation

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
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportElement</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-863-dataassembly-definition-of-suc-transportelement">Table 8.63</a>)</td>
    <td align="left">Base interface for all transport-relevant interfaces</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportClientManager</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-864-dataassembly-definition-of-suc-transportclientmanager">Table 8.64</a>)</td>
    <td align="left">Abstract interface for configuring and establishing a communication connection between a LEA and a Transport Management</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OpcUaTransportClientManager</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-865-dataassembly-definition-of-suc-opcuatransportclientmanager">Table 8.65</a>)</td>
    <td align="left">Interface for configuring and establishing an OPC UA connection between a LEA (client) and a Transport Management (server)</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportNodeManager</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-866-dataassembly-definition-of-suc-transportnodemanager">Table 8.66</a>)</td>
    <td align="left">Interface for assigning a TK Block in the LEA to a TK Proxy in the Transport Management</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.Time V2.0.0</td>
    <td align="left"><em>RC HasTimeFormat</em> (<a href="../08_MTP%20Extensions/08-03_DataAssemblySet.md#table-815-dataassembly-definition-of-rc-hastimeformat">Table 8.15</a>)</td>
    <td align="left">Role class for DINT-based interfaces to indicate timestamp interpretation</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.Time V2.0.0</td>
    <td align="left"><em>SUC DIntView</em> (extension) (<a href="../08_MTP%20Extensions/08-03_DataAssemblySet.md#table-817-dataassembly-definition-of-suc-dintview">Table 8.17</a>)</td>
    <td align="left">Extension of the existing DIntView interface to support the RC HasTimeFormat role class</td>
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
    <td align="left"><em>IH Transports</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-867-model-definition-of-ih-transports">Table 8.67</a>)</td>
    <td align="left">Instance hierarchy for managing all transport-related models of an MTP</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportSet</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-869-model-definition-of-suc-transportset">Table 8.69</a>)</td>
    <td align="left">Aspect set organizing all transport-relevant model definitions</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportNode</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-870-model-definition-of-suc-transportnode">Table 8.70</a>)</td>
    <td align="left">Abstract model for a transport node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC InboundNode</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-871-model-definition-of-suc-inboundnode">Table 8.71</a>)</td>
    <td align="left">Model for an Inbound node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OutboundNode</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-872-model-definition-of-suc-outboundnode">Table 8.72</a>)</td>
    <td align="left">Model for an Outbound node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC InOutboundNode</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-873-model-definition-of-suc-inoutboundnode">Table 8.73</a>)</td>
    <td align="left">Model for an InOutbound node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC ProcessingNode</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-874-model-definition-of-suc-processingnode">Table 8.74</a>)</td>
    <td align="left">Model for a Processing node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OrderNode</em> (<a href="../08_MTP%20Extensions/08-08_TransportSet.md#table-875-model-definition-of-suc-ordernode">Table 8.75</a>)</td>
    <td align="left">Model for an Order node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC TransportNodeRequest</em> (<a href="../08_MTP%20Extensions/08-04_ServiceSet.md#table-836-model-definition-of-suc-transportnoderequest">Table 8.36</a>)</td>
    <td align="left">Model of a LEA request for the next transport node to approach</td>
  </tr>
</table>

Two new libraries accompany these definitions: *SUCL MTPTransportSUCLib* for all transport-relevant model definitions, and *RCL MTPDataAssemblyRCLib* for the RC HasTimeFormat role class.
