### 5.4 Transport Management

#### 5.4.1 LEA-Management

The LEA-Management integrates LEAs into the Transport Management by importing their MTP files. For each transport node described in the LEA's *TransportSet* (see [Section 5.5.2](#transportset)), the LEA-Management generates a **TK Proxy** — a proxy object in the Transport Management that represents the transport node. Each TK Proxy receives a unique integer **ProxyId**. The TK Proxies expose the interface data of their bound transport services via an OPC UA server in the Transport Management.

After proxy generation, the Transport Management configures the TK Blocks in the LEA: it transmits OPC UA connection parameters (*TransportClientManager* interface) and assigns each TK Block the ProxyId of its corresponding TK Proxy (*TransportNodeManager* interface).

#### 5.4.2 Order-Management

The Order-Management creates and manages transport services. Each transport order is mapped to one MTP service instance. Services are created dynamically when a transport need is detected and deleted when the order is complete.

##### Transport Service Interface

The interface of a transport service comprises the following parameters and report values:

##### Table 5.1: Interface of a Transport Service

<table>
  <tr>
    <th align="left">Name</th>
    <th align="left">Interface Type</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">TransportControl</td>
    <td align="left">ServiceControl</td>
    <td align="left">Service control interface</td>
  </tr>
  <tr>
    <td align="left">ProductionId</td>
    <td align="left">StringServParam</td>
    <td align="left">Production order ID</td>
  </tr>
  <tr>
    <td align="left">ProductId</td>
    <td align="left">DIntServParam</td>
    <td align="left">Product type ID</td>
  </tr>
  <tr>
    <td align="left">LogisticsObjectId</td>
    <td align="left">StringServParam</td>
    <td align="left">LO instance ID</td>
  </tr>
  <tr>
    <td align="left">LogisticsObjectStatus</td>
    <td align="left">DIntServParam</td>
    <td align="left">LO packaging status</td>
  </tr>
  <tr>
    <td align="left">IsPriorityOrder</td>
    <td align="left">BinServParam</td>
    <td align="left">Priority flag</td>
  </tr>
  <tr>
    <td align="left">NextNode</td>
    <td align="left">DIntServParam</td>
    <td align="left">ProxyId of the next transport node to approach</td>
  </tr>
  <tr>
    <td align="left">FinalTargetNode</td>
    <td align="left">DIntServParam</td>
    <td align="left">ProxyId of the final destination node</td>
  </tr>
  <tr>
    <td align="left">TransportId</td>
    <td align="left">StringView</td>
    <td align="left">Unique transport order ID (read-only)</td>
  </tr>
  <tr>
    <td align="left">ResourceId</td>
    <td align="left">DIntView</td>
    <td align="left">ID of the assigned AGV (read-only)</td>
  </tr>
  <tr>
    <td align="left">RequestedTimestamp</td>
    <td align="left">DIntView + RC HasTimeFormat</td>
    <td align="left">Order initiation time (read-only)</td>
  </tr>
  <tr>
    <td align="left">LastUpdatedTimestamp</td>
    <td align="left">DIntView + RC HasTimeFormat</td>
    <td align="left">Last update time (read-only)</td>
  </tr>
  <tr>
    <td align="left">CompletedTimestamp</td>
    <td align="left">DIntView + RC HasTimeFormat</td>
    <td align="left">Completion time (read-only)</td>
  </tr>
</table>

The order metadata (*ProductionId*, *ProductId*, *LogisticsObjectId*, *LogisticsObjectStatus*, *IsPriorityOrder*) and routing parameters (*NextNode*, *FinalTargetNode*) are implemented as procedure parameters [[MTP Specification Part 4]](../98_References/README.md#mtp-specification-part-4), so that both the Transport Management and the currently bound LEA can read and modify them. The management data (*TransportId*, *ResourceId*, timestamps) are report values [[MTP Specification Part 4]](../98_References/README.md#mtp-specification-part-4) that are set by the Transport Management and read-only for LEAs.

##### Timestamp Representation

The existing MTP specification does not support time values. This dissertation introduces a new role class **RC HasTimeFormat**, which can be added to DINT-based interface definitions (in particular *DIntView*, *DIntMon*, *DIntMan*, *DIntManInt*, *DIntServParam*, *DIntProcessValueIn*) to indicate that the DINT value is to be interpreted as a timestamp.

##### Transport Status via Procedures

Transport status is represented using MTP procedures rather than parameters or process values. This enables bidirectional status control with command-enable logic. [Figure 5.10](#figure-510-transport-status-via-procedures) shows the procedure state machine extended with logistics-specific transport statuses.

##### Figure 5.10: Transport Status via Procedures
![Transport Status via Procedures](./images/TransportstatusZA.svg)

##### Figure 5.11: Overview of Procedure Switching
![Overview of Procedure Switching](./images/Uebersicht_Prozedurumschaltung.svg)

The transport statuses correspond to procedure identifiers. [Table 5.2](#table-52-transport-status-procedures) lists all 15 transport procedure states.

##### Table 5.2: Transport Status Procedures

<table>
  <tr>
    <th align="left">ID</th>
    <th align="left">Name</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">16#0</td>
    <td align="left">TransportIdle</td>
    <td align="left">No active transport order</td>
  </tr>
  <tr>
    <td align="left">16#1</td>
    <td align="left">TransportRequested</td>
    <td align="left">A transport need has been signaled by a LEA; transport order is being processed by the Transport Management</td>
  </tr>
  <tr>
    <td align="left">16#2</td>
    <td align="left">TransportPrepared</td>
    <td align="left">An AGV has been assigned and the transport order has been transmitted to the AGV system</td>
  </tr>
  <tr>
    <td align="left">16#3</td>
    <td align="left">Transport</td>
    <td align="left">The AGV is traveling toward the next transport node</td>
  </tr>
  <tr>
    <td align="left">16#4</td>
    <td align="left">TransportAwaitRequested</td>
    <td align="left">The AGV is in the approach zone of the next node and requests permission to proceed to the node</td>
  </tr>
  <tr>
    <td align="left">16#5</td>
    <td align="left">TransportAwaited</td>
    <td align="left">The transport service has been bound to a LEA's proxy interface; the LEA confirms the assigned transport order</td>
  </tr>
  <tr>
    <td align="left">16#6</td>
    <td align="left">TransportDeclined</td>
    <td align="left">The transport service has been bound to a LEA's proxy interface; the LEA rejects the assigned transport order</td>
  </tr>
  <tr>
    <td align="left">16#7</td>
    <td align="left">TransportArrived</td>
    <td align="left">The AGV has reached its target node and is ready to interact with the LEA</td>
  </tr>
  <tr>
    <td align="left">16#8</td>
    <td align="left">TransferFromLea</td>
    <td align="left">An LO is being transferred from a LEA to an AGV</td>
  </tr>
  <tr>
    <td align="left">16#9</td>
    <td align="left">TransferFromLeaSucceeded</td>
    <td align="left">An LO has been successfully transferred from a LEA to an AGV</td>
  </tr>
  <tr>
    <td align="left">16#A</td>
    <td align="left">Processing</td>
    <td align="left">A LEA is performing a processing operation on an LO located on an AGV</td>
  </tr>
  <tr>
    <td align="left">16#B</td>
    <td align="left">ProcessingSucceeded</td>
    <td align="left">A processing operation has been successfully completed on an LO located on an AGV</td>
  </tr>
  <tr>
    <td align="left">16#C</td>
    <td align="left">TransferToLea</td>
    <td align="left">An LO is being transferred from an AGV to a LEA</td>
  </tr>
  <tr>
    <td align="left">16#D</td>
    <td align="left">TransferToLeaSucceeded</td>
    <td align="left">An LO has been successfully transferred from an AGV to a LEA</td>
  </tr>
  <tr>
    <td align="left">16#E</td>
    <td align="left">Rerouting</td>
    <td align="left">The transport service must be rerouted due to a LEA fault</td>
  </tr>
</table>
