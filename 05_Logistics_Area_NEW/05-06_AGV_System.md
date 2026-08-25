### 5.6 AGV System

In this work AGV systems consisting of a fleet manager and multiple AGVs are considered for implementing flexible transports in Logistics Areas. They serve to execute the transport orders managed in the Transport Management.

#### Integration into the Transport Management

In an MLS, different AGV systems with different technical characteristics and proprietary interfaces can be used. To manage this technical diversity, the Transport Management was designed as an abstraction layer between the LEAs and the AGV systems. The AGV systems are connected to the Transport Management via proprietary interfaces, e.g., REST or MQTT interfaces. To integrate different AGV systems, AGV system adapters are provided within the Transport Management. These adapters are capable of communicating downward with the proprietary interfaces of the AGV systems and upward with a uniform interface of the Transport Management that is consistent across all adapters. Additional adapters can be integrated into the Transport Management via a plugin mechanism to enable simple connection of further AGV systems. The exact implementation of the adapters and the definition of their interface to the Transport Management is implementation-specific and is not considered in this work.

#### Interaction with the Transport Management

For the execution of transport orders, the AGV system adapters must be able to access information from transport services in the Transport Management and synchronize it in a suitable manner with the proprietary interface of the AGV systems.

To enable the interaction with the AGV system according to the presented working principle ([Sections 5.1.2](05_Logistics_Area.md#512-working-principle) and [5.3](05-03_Transport_Process.md#53-transport-process)), the proprietary interface of an AGV system must be able to provide or process certain information for each transport order. [Table 5.7](#table-57-minimum-interface-requirements-for-an-agv-system) provides an overview of this information. Additionally, the fleet manager of the AGV system must be able to select a suitable AGV for the transport order based on the transport order information received from the adapter, reserve it for the transport order, and execute the transport order according to the described working principle.

##### Table 5.7: Minimum Interface Requirements for an AGV System

<table>
  <tr>
    <th align="left" colspan="2"><strong>Information provided by the AGV system</strong></th>
  </tr>
  <tr>
    <th align="left">Information</th>
    <th align="left">Processing</th>
  </tr>
  <tr>
    <td align="left">ID of the selected AGV</td>
    <td align="left">This information is provided as report value <em>ResourceId</em> on the transport service.</td>
  </tr>
  <tr>
    <td align="left">Indicator whether the AGV is currently moving or stopped</td>
    <td align="left">Based on this information, the transport status <em>Transport</em> is set by the Transport Management.</td>
  </tr>
  <tr>
    <td align="left">Indicator whether there are errors in the execution of the transport order</td>
    <td align="left">Based on this information, the transport service can be set to an error state (HELD, STOPPED, ABORTED).</td>
  </tr>
  <tr>
    <td align="left">Indicator of AGV arrival in the approach area of the target LEA</td>
    <td align="left">Based on this information, the transport status <em>TransportAwaitRequested</em> is set by the Transport Management.</td>
  </tr>
  <tr>
    <td align="left">Indicator of AGV arrival at the target LEA</td>
    <td align="left">Based on this information, the transport status <em>TransportArrived</em> is set by the Transport Management.</td>
  </tr>
  <tr>
    <th align="left" colspan="2"><strong>Information to be processed by the AGV system</strong></th>
  </tr>
  <tr>
    <th align="left">Information</th>
    <th align="left">Processing</th>
  </tr>
  <tr>
    <td align="left">ProxyId of the next transport node to approach</td>
    <td align="left">This information must be provided to the AGV as the next target to approach.</td>
  </tr>
  <tr>
    <td align="left">Indicator that a transport shall start</td>
    <td align="left">This indicator commands the AGV to depart toward the next transport node to approach.</td>
  </tr>
  <tr>
    <td align="left">Clearance for the AGV to approach a LEA</td>
    <td align="left">This indicator commands the AGV to approach a LEA.</td>
  </tr>
  <tr>
    <td align="left">Indicator that a handover/pickup of an LO to/from a LEA is occurring</td>
    <td align="left">This indicator commands the AGV to activate its available transfer mechanisms (e.g., conveyor belts for receiving an LO).</td>
  </tr>
  <tr>
    <td align="left">Indicator of transport order completion</td>
    <td align="left">This indicator informs the fleet manager that the transport order is complete and commands it to release the AGV for future transport orders.</td>
  </tr>
</table>
