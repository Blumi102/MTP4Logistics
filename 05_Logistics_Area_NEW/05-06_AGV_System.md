### 5.6 AGV System

##### Figure 5.16: Classification within the SAIL Architecture
![Classification within the SAIL Architecture](./images/Einorndung_SAIL.svg)

The Transport Management covers the Transport Coordination level of the SAIL architecture [[VDI/VDMA 5100-1]](../98_References/README.md#vdivdma-5100-1-2016), as shown in [Figure 5.16](#figure-516-classification-within-the-sail-architecture). AGV systems — each consisting of a fleet manager and multiple AGVs — execute the transport orders managed by the Transport Management.

Different AGV systems may use different proprietary interfaces (REST, MQTT, etc.). The Transport Management uses **AGV system adapters** to bridge these proprietary interfaces to a uniform internal interface. Additional adapters can be integrated via a plugin mechanism. The internal interface and adapter implementations are system-specific and not further specified in this dissertation.

For each transport order, the AGV system must be capable of providing and processing the following information:

##### Table 5.5: Minimum Interface Requirements for an AGV System

<table>
  <tr>
    <th align="left" colspan="2">Information provided by the AGV system</th>
  </tr>
  <tr>
    <th align="left">Information</th>
    <th align="left">Usage in Transport Management</th>
  </tr>
  <tr>
    <td align="left">ID of the selected AGV</td>
    <td align="left">Provided as report value <em>ResourceId</em> on the transport service</td>
  </tr>
  <tr>
    <td align="left">Indicator: AGV currently moving or stopped</td>
    <td align="left">Used to set transport status <em>Transport</em></td>
  </tr>
  <tr>
    <td align="left">Indicator: execution error</td>
    <td align="left">Used to transition transport service to error state (HELD, STOPPED, ABORTED)</td>
  </tr>
  <tr>
    <td align="left">Indicator: AGV in approach zone of target LEA</td>
    <td align="left">Used to set transport status <em>TransportAwaitRequested</em></td>
  </tr>
  <tr>
    <td align="left">Indicator: AGV arrived at target LEA</td>
    <td align="left">Used to set transport status <em>TransportArrived</em></td>
  </tr>
  <tr>
    <th align="left" colspan="2">Information consumed by the AGV system</th>
  </tr>
  <tr>
    <th align="left">Information</th>
    <th align="left">Usage in AGV system</th>
  </tr>
  <tr>
    <td align="left">ProxyId of the next transport node</td>
    <td align="left">Used as the next navigation target for the AGV</td>
  </tr>
  <tr>
    <td align="left">Indicator: transport shall start</td>
    <td align="left">Commands AGV to depart toward the next transport node</td>
  </tr>
  <tr>
    <td align="left">Clearance for AGV to approach the LEA</td>
    <td align="left">Commands AGV to move from approach zone to the LEA docking position</td>
  </tr>
  <tr>
    <td align="left">Indicator: LO handover/pickup occurring</td>
    <td align="left">Commands AGV to activate transfer mechanisms (e.g. conveyor belts)</td>
  </tr>
  <tr>
    <td align="left">Indicator: transport order complete</td>
    <td align="left">Informs fleet manager that the AGV is free for the next order</td>
  </tr>
</table>
