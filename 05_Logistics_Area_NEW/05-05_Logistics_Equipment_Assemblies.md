### 5.5 Logistics Equipment Assemblies

#### 5.5.1 Structure and Interaction with Transport Services

In the transport coordination context, LEAs act as initiators of transport orders. Each transport node in a LEA is implemented as a **TK Block** (transport node building block) in the LEA service. A TK Block is an OPC UA client block [[OPC 30001]](../98_References/README.md#opc-30001) that connects to the OPC UA server of the Transport Management and accesses the interface data of its assigned TK Proxy.

After binding, the TK Block can read the current transport status (*ProcedureCur*) from the TK Proxy via OPC UA Read, and write parameters such as *NextNode.VExt* via OPC UA Write. All reads and writes are batched into single read and write operations using *OpcUaReadList* and *OpcUaWriteList* blocks [[OPC 30001]](../98_References/README.md#opc-30001). Before each write, the TK Block reads all writable variables first, applies the required changes, and then writes the complete variable set in a single operation — preventing inadvertent overwriting of consistent state data.

Although each TK Block is persistently bound to the same TK Proxy, the proxy may present different transport services over time as orders are created and completed. This dynamic binding differs from conventional static decentralized orchestration approaches [[Spa19]](../98_References/README.md#spaethe-2019) [[SMS+20]](../98_References/README.md#stutz-et-al-2020) and is required to support the interaction of one transport service with multiple transport nodes across different LEAs.

##### Figure 5.12: Interaction of a Transport Service with a LEA Transport Node via a TK Proxy
![Interaction of a Transport Service with a LEA Transport Node via a TK Proxy](./images/Interaktion_LEA_TCS.svg)

##### Figure 5.13: Logical View of Decentralized Orchestration
![Logical View of Decentralized Orchestration](./images/DO_LogischeSicht.svg)

#### 5.5.2 Integration of LEAs into the Transport Management

LEA integration into the Transport Management follows three steps, as shown in [Figure 5.14](#figure-514-integration-of-a-lea-into-the-transport-management):

##### Figure 5.14: Integration of a LEA into the Transport Management
![Integration of a LEA into the Transport Management](./images/ProxyGenerierung.svg)

1. **MTP import**: The LEA MTP file is imported into the LEA-Management. The *TransportSet* aspect (see below) contains all transport-relevant information.
2. **TK Proxy generation**: For each transport node described in the *TransportSet*, the Transport Management generates a TK Proxy with a unique ProxyId and exposes its interface in the OPC UA server.
3. **LEA configuration**: The Transport Management configures each TK Block in the LEA:
   - It transmits OPC UA connection parameters (endpoint URL, namespace) via the *TransportClientManager* interface, causing the LEA to establish an OPC UA client connection to the Transport Management.
   - It transmits the ProxyId of the corresponding TK Proxy via the *TransportNodeManager* interface, enabling the TK Block to derive all OPC UA NodeIds needed to access the proxy.

**Note on Logistics Lines**: For Logistics Lines (composed MTPs), the relevant transport nodes of the participating LEAs are exposed at the line interface. The interaction between transport services and these nodes is identical to that with single-LEA transport nodes.

##### TransportSet

The *TransportSet* is a new MTP aspect (profile) introduced in this dissertation to enable automated LEA integration. It contains all model and interface definitions needed to describe the transport-relevant information of a LEA. Key elements:

- **TransportNode** (abstract): base model for LEA transport nodes; concrete subtypes are *InboundNode*, *OutboundNode*, *InOutboundNode*, *ProcessingNode*, and *OrderNode*, listed in a flat list directly under the *TransportSet*.
- **OpcUaTransportClientManager**: interface for transmitting OPC UA connection parameters from the Transport Management to the LEA (derived from abstract *TransportClientManager*).
- **TransportNodeManager**: interface for assigning a TK Block to its TK Proxy via ProxyId transmission.

Each *TransportNode* model definition is associated with exactly one *TransportClientManager* and one *TransportNodeManager* interface, making it unambiguous which interfaces the Transport Management must use for a given transport node.

#### 5.5.3 Determination of the Next Transport Node

According to DE6, the LEA currently bound to a transport service determines the next transport node and writes its ProxyId to the *NextNode* parameter. Four scenarios require this determination:

##### Table 5.3: Scenarios for Next Node Determination

<table>
  <tr>
    <th align="left">Case</th>
    <th align="left">Name</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">S1</td>
    <td align="left">Push order</td>
    <td align="left">LEA has completed processing an LO and initiates a push transport for pickup. The next node is a node on the LEA itself (e.g. PAL signals a completed pallet for AGV pickup).</td>
  </tr>
  <tr>
    <td align="left">S2</td>
    <td align="left">Pull order</td>
    <td align="left">LEA requires material and initiates a pull transport. The next node is the node from which material is to be sourced (e.g. PAL requests an empty pallet from a pallet supply station).</td>
  </tr>
  <tr>
    <td align="left">S3</td>
    <td align="left">LO handover (Outbound)</td>
    <td align="left">LEA hands over an LO at an Outbound or InOutbound node. The next node is at the receiving LEA (e.g. after handover, AGV is directed to the LABEL-LEA).</td>
  </tr>
  <tr>
    <td align="left">S4</td>
    <td align="left">LO processing (Processing)</td>
    <td align="left">LEA has processed an LO on the AGV at its Processing node. The next node is at the downstream LEA (e.g. LABEL-LEA sends pallet onward to the stretch-hood machine).</td>
  </tr>
</table>

##### Figure 5.15: Cases for Next Node Determination
![Cases for Next Node Determination](./images/NextNode.drawio.png)

The *RoutingMode* variable (DINT, stored in the LEA's *ProductDataSet*) controls which method is used:

##### Table 5.4: Meaning of the *RoutingMode* Variable

<table>
  <tr>
    <th align="left">Value</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">1</td>
    <td align="left">Use static default values from the <em>ProductDataSet</em></td>
  </tr>
  <tr>
    <td align="left">2</td>
    <td align="left">Query the next node dynamically from the Materialfluss-Management in the LOL</td>
  </tr>
</table>

##### Static Default Routes

For S1, the ProxyId of the LEA's own Outbound/InOutbound node is available internally via the *TransportNodeManager* interface — no further lookup is required.

For S2–S4, static default values can be read from the LEA's *ProductDataSet* using the *ProductId* and *LogisticsObjectStatus* as lookup keys. Two variables hold the default ProxyIds:

- **DefaultSupplyNode**: ProxyId of the node from which the LEA sources material by default (used in S2).
- **DefaultNextNode**: ProxyId of the node to which the LEA forwards completed LOs by default (used in S3 and S4). A value of `0` means the *FinalTargetNode* is used as the next (and final) node.

##### Dynamic Next Node Query

The *TransportNodeRequest* is a new logistics-specific service-operator interaction introduced in this dissertation. A LEA queries the next transport node from the Materialfluss-Management by providing the *TransportId* of the active transport service. The Materialfluss-Management returns the ProxyId of the next node, or `0` if the *FinalTargetNode* should be approached next.
