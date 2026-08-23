### 5.7 MTP Extensions

The concepts described in this chapter require the following new model and interface definitions, which extend the MTP specification [[MTP Specification Part 1]](../98_References/README.md#mtp-specification-part-1) [[MTP Specification Part 4]](../98_References/README.md#mtp-specification-part-4):

##### Table 5.6: MTP Specification Extensions for Logistics Area Transport Automation

<table>
  <tr>
    <th align="left" colspan="4">Interface Definitions</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Definition</th>
    <th align="left">Description</th>
    <th align="left">Detailed Spec.</th>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportElement</em></td>
    <td align="left">Base interface for all transport-relevant interfaces</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportClientManager</em></td>
    <td align="left">Abstract interface for configuring and establishing a communication connection between a LEA and a Transport Management</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OpcUaTransportClientManager</em></td>
    <td align="left">Interface for configuring and establishing an OPC UA connection between a LEA (client) and a Transport Management (server)</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportNodeManager</em></td>
    <td align="left">Interface for assigning a TK Block in the LEA to a TK Proxy in the Transport Management</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.Time V2.0.0</td>
    <td align="left"><em>RC HasTimeFormat</em></td>
    <td align="left">Role class for DINT-based interfaces to indicate timestamp interpretation</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: DataAssemblySet.Time V2.0.0</td>
    <td align="left"><em>SUC DIntView</em> (extension)</td>
    <td align="left">Extension of the existing DIntView interface to support the RC HasTimeFormat role class</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <th align="left" colspan="4">Model Definitions</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Definition</th>
    <th align="left">Description</th>
    <th align="left">Detailed Spec.</th>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>IH Transports</em></td>
    <td align="left">Instance hierarchy for managing all transport-related models of an MTP</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportSet</em></td>
    <td align="left">Aspect set organizing all transport-relevant model definitions</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC TransportNode</em></td>
    <td align="left">Abstract model for a transport node of a LEA</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC InboundNode</em></td>
    <td align="left">Model for an Inbound node of a LEA</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OutboundNode</em></td>
    <td align="left">Model for an Outbound node of a LEA</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC InOutboundNode</em></td>
    <td align="left">Model for an InOutbound node of a LEA</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC ProcessingNode</em></td>
    <td align="left">Model for a Processing node of a LEA</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: TransportSet.Base V2.0.0</td>
    <td align="left"><em>SUC OrderNode</em></td>
    <td align="left">Model for an Order node of a LEA</td>
    <td align="left">Appendix</td>
  </tr>
  <tr>
    <td align="left">ModuleTypePackage: ServiceSet.Logistics V2.0.0</td>
    <td align="left"><em>SUC TransportNodeRequest</em></td>
    <td align="left">Model of a LEA request for the next transport node to approach</td>
    <td align="left">Appendix</td>
  </tr>
</table>

Two new libraries accompany these definitions: *SUCL MTPTransportSUCLib* for all transport-relevant model definitions, and *RCL MTPDataAssemblyRCLib* for the RC HasTimeFormat role class.
