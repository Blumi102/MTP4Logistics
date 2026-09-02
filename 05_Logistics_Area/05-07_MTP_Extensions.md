## 5.7 MTP Extensions

In the preceding sections, a number of extensions to the MTP specification were identified that are necessary in the context of automating flexible transports in the Logistics Area. [Table 5.7](#table-57-mtp-specification-extensions-for-logistics-area-transport-automation) provides an overview of the model and DataAssembly definitions to be introduced, with links to their detailed specifications.

##### Table 5.7: MTP Specification Extensions for Logistics Area Transport Automation

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
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportElement</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-767-dataassembly-definition-of-suc-transportelement">Table 7.67</a>)</td>
    <td align="left">Base interface for all transport-relevant interfaces</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportClientManager</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-768-dataassembly-definition-of-suc-transportclientmanager">Table 7.68</a>)</td>
    <td align="left">Abstract interface for configuring and establishing a communication connection between a LEA and a Transport Management</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OpcUaTransportClientManager</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-769-dataassembly-definition-of-suc-opcuatransportclientmanager">Table 7.69</a>)</td>
    <td align="left">Interface for configuring and establishing an OPC UA connection between a LEA (client) and a Transport Management (server)</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportNodeManager</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-770-dataassembly-definition-of-suc-transportnodemanager">Table 7.70</a>)</td>
    <td align="left">Interface for assigning a TK Block in the LEA to a TK Proxy in the Transport Management</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.Time V2.0.0</td>
    <td align="left"><em>RC HasTimeFormat</em> (<a href="../07_MTP%20Extensions/07-03_DataAssemblySet.md#table-717-dataassembly-definition-of-rc-hastimeformat">Table 7.17</a>)</td>
    <td align="left">Role class for DINT-based interfaces to indicate timestamp interpretation</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.Time V2.0.0</td>
    <td align="left"><em>SUC DIntView</em> (extension) (<a href="../07_MTP%20Extensions/07-03_DataAssemblySet.md#table-719-dataassembly-definition-of-suc-dintview">Table 7.19</a>)</td>
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
    <td align="left"><em>IH Transports</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-771-model-definition-of-ih-transports">Table 7.71</a>)</td>
    <td align="left">Instance hierarchy for managing all transport-related models of an MTP</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportSet</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-773-model-definition-of-suc-transportset">Table 7.73</a>)</td>
    <td align="left">Aspect set organizing all transport-relevant model definitions</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportNode</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-774-model-definition-of-suc-transportnode">Table 7.74</a>)</td>
    <td align="left">Abstract model for a transport node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC InboundNode</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-775-model-definition-of-suc-inboundnode">Table 7.75</a>)</td>
    <td align="left">Model for an Inbound node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OutboundNode</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-776-model-definition-of-suc-outboundnode">Table 7.76</a>)</td>
    <td align="left">Model for an Outbound node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC InOutboundNode</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-777-model-definition-of-suc-inoutboundnode">Table 7.77</a>)</td>
    <td align="left">Model for an InOutbound node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC ProcessingNode</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-778-model-definition-of-suc-processingnode">Table 7.78</a>)</td>
    <td align="left">Model for a Processing node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OrderNode</em> (<a href="../07_MTP%20Extensions/07-08_TransportSet.md#table-779-model-definition-of-suc-ordernode">Table 7.79</a>)</td>
    <td align="left">Model for an Order node of a LEA</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC TransportNodeRequest</em> (<a href="../07_MTP%20Extensions/07-04_ServiceSet.md#table-740-model-definition-of-suc-transportnoderequest">Table 7.40</a>)</td>
    <td align="left">Model of a LEA request for the next transport node to approach</td>
  </tr>
</table>

Two new libraries accompany these definitions: *SUCL MTPTransportSUCLib* for all transport-relevant model definitions, and *RCL MTPDataAssemblyRCLib* for the RC HasTimeFormat role class.
