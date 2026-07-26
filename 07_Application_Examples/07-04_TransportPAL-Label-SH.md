## 7.4 Application Example: Transport PAL–Label–SH
To illustrate the transport concepts described in the dissertation for logistics area automation, this section presents an exemplary application of the transport concept. A push transport from the PAL to SH1 is used as the example; however, a labeling LEA (LABEL) with a Processing node is additionally to be visited along the way. [Figure 7.12](#figure-712-example-of-a-push-transport-from-a-palletizer-via-a-labeling-unit-to-a-stretch-hood-machine) shows the LEAs and their transport nodes.

##### Figure 7.12: Example of a Push Transport from a Palletizer via a Labeling Unit to a Stretch Hood Machine
![Example of a Push Transport from a Palletizer via a Labeling Unit to a Stretch Hood Machine](./images/Transport_Beispiel.png)

### 7.4.1 0) LEA Integration
As the basis for carrying out the transport process, the MTPs of the three LEAs are imported into the transport management, *Transport Proxies* are generated, and these are connected to the LEA transport nodes. [Figure 7.13](#figure-713-integration-of-leas-into-a-transport-management-system) shows the process of integrating the three LEAs; [Figure 7.14](#figure-714-integration-of-all-transport-nodes-of-leas-into-a-transport-management-system) shows the process of integrating all transport nodes available in the LEAs.[^1]

##### Figure 7.13: Integration of LEAs into a Transport Management System
![Integration of LEAs into a Transport Management System](./images/Integration_LEA.png)

##### Figure 7.14: Integration of All Transport Nodes of LEAs into a Transport Management System
![Integration of All Transport Nodes of LEAs into a Transport Management System](./images/Integration_Node.png)

### 7.4.2 1) Transport Initiation
[Figure 7.15](#figure-715-initiation-of-a-push-transport-order) shows the transport initiation process.

##### Figure 7.15: Initiation of a Push Transport Order
![Initiation of a Push Transport Order](./images/Transport_Initiierung.png)

In the context of the selected example, only the PAL has an Order node for initiating transport orders. Since no transport service is initially assigned to it, a new transport service (ID: transA) is created in the transport management and connected to the Order node (ID: 1).

In the example, the PAL has a push transport requirement and starts the transport service in the *PushRequested* procedure. The *NextNode* is set to the InOutbound node of the PAL (ID: 2). The PAL obtains this ID by reading the *ProxyId* from the *TransportNodeManager* interface of its InOutbound node and sets it at the procedure parameter *NextNode* of the transport service.

After the transport service is started, its OPC UA connection to the Order node is disconnected; however, it continues to run in the transport management. A new transport service (ID: transB) is created for the now-free Order node and assigned to it.

### 7.4.3 2) Travel to the Start Node
[Figure 7.16](#figure-716-travel-to-the-start-node) shows the process of traveling to the start node.

##### Figure 7.16: Travel to the Start Node
![Travel to the Start Node](./images/Transport_Fahrt_Start.png)

The running transport service (ID: transA) is made available to a suitable FMS via its adapter. Depending on the FMS interface, this can occur at the initiative of the transport management or the FMS. Once the FMS has available capacity, it internally selects a suitable AGV to execute the transport process and reports the ID (here: agv3) back to an adapter. The adapter stores this ID in the *ResourceId* variable of the transport service. Once the FMS begins executing the transport process, it restarts the transport service in the *TransportRequested* procedure via its adapter. The selected AGV then travels to the InOutbound node of the PAL as the start node of the transport process.

### 7.4.4 3) Coupling the Transport Service to the Start Node
[Figure 7.17](#figure-717-coupling-the-transport-service-to-the-start-node) shows the process of coupling the transport service to the start node.

##### Figure 7.17: Coupling the Transport Service to the Start Node
![Coupling the Transport Service to the Start Node](./images/Anbindung_Transportdienst.png)

Shortly before the AGV arrives at the InOutbound node of the PAL, the FMS notifies its adapter of the imminent arrival. The adapter subsequently initiates a procedure change to *TransportAwaitRequested* at the transport service. If the InOutbound node is not occupied by another transport service, the transport management assigns the transport service (ID: transA) to the *Transport Proxy* of this node. The PAL then checks, based on the data from the transport service interface (e.g., *ProductId*), whether it can process the transported product. For example, it may compare the *ProductId* of the transport service with the *ProductId* of the packaging order it is currently processing.

Depending on the result of this check, the PAL sets the procedure of the transport service to either *TransportAwaited* or *TransportDeclined*. In the event of a negative result (*TransportDeclined*), the next transport node to be approached (procedure parameter *NextNode*) must be redefined. To do so, the LEA may request an alternative node from the LOL or the operator via *TransportNodeRequest* and reroute the transport accordingly. Alternatively, the FMS can direct the AGV to a safe position and the transport management places the transport service in the HELD state, signaling the need for manual intervention.

In the present example, a positive result is assumed. In this case, the PAL sets the procedure of the transport service to *TransportAwaited*, which corresponds to the authorization for the AGV to approach the InOutbound node. When the FMS signals that the AGV has arrived at the node, the FMS adapter initiates a procedure change to *TransportArrived*.

### 7.4.5 4) Loading the AGV
[Figure 7.18](#figure-718-loading-the-agv) shows the AGV loading process.

##### Figure 7.18: Loading the AGV
![Loading the AGV](./images/Beladung_AGV.png)

As soon as the InOutbound node of the PAL detects the *TransportArrived* status, it initiates a procedure change to *TransferFromLea* and the handover of the LO (here: pallet) to the AGV begins. Once the transfer is complete, the next transport node to be approached (here: the Processing node of the LABEL LEA) is determined and set at the procedure parameter *NextNode* of the transport service. The LEA then restarts the transport service in the *TransferFromLeaSucceeded* procedure. The transport management recognizes this and decouples the transport service from the InOutbound node of the PAL, which is then again available for other transport orders.

### 7.4.6 5) Travel to the Next Node Including Rerouting
[Figure 7.19](#figure-719-travel-to-the-next-node-including-rerouting) shows the process of traveling to the next node, including the option of rerouting.

##### Figure 7.19: Travel to the Next Node Including Rerouting
![Travel to the Next Node Including Rerouting](./images/Transport_Fahrt_NextNode_Rerouting.png)

As soon as the FMS adapter detects the *TransferFromLeaSucceeded* procedure, it forwards the instruction to travel to the next transport node (here: the Processing node of the LABEL LEA) to the FMS. The FMS reports when the transport is underway, and the adapter initiates a procedure change to *Transport*.

The transport management monitors the connections to the *TransportClientManager* interfaces of the LEAs. If a connection loss is detected, or if a fault state is detected in the *LeaStateCur* variable of the interface, rerouting of transport services that are en route to the affected faulty LEA can be initiated. In this case, an alternative transport node is determined internally within the LOL, initiated by the transport management, and set at the procedure parameter *NextNode* of the transport service. The transport management then restarts the transport service in the *Rerouting* procedure. In this way, the FMS adapter detects the rerouting and forwards the destination change to the FMS. Once the FMS has accepted the new destination, its adapter initiates a procedure change to *Transport*.

### 7.4.7 6) Processing
[Figure 7.20](#figure-720-processing-of-a-logistics-object) shows the process of handling an LO at a Processing node.

##### Figure 7.20: Processing of a Logistics Object
![Processing of a Logistics Object](./images/Transport_Processing.png)

If the approached transport node is a Processing node, the transport service is coupled to it following the same principle as described in [Section 10.4.4](#744-3-coupling-the-transport-service-to-the-start-node). Processing of the LO then begins, which is signaled by a procedure change to *Processing* initiated by the transport node of the LEA. In this case, **no** handover of the LO to the LEA takes place; instead, it remains on the AGV. Once processing is complete, the next transport node to be approached is determined and set at the procedure parameter *NextNode* of the transport service. The LEA then performs a procedure change to *ProcessingSucceeded*. The transport management recognizes this and decouples the transport service from the Processing node. Subsequently, any number of additional Processing nodes can be approached in the same manner. Travel to the next transport node follows the same principle as described in [Section 10.4.6](#746-5-travel-to-the-next-node-including-rerouting).

### 7.4.8 7) Unloading the AGV
[Figure 7.21](#figure-721-unloading-the-agv) shows the AGV unloading process.

##### Figure 7.21: Unloading the AGV
![Unloading the AGV](./images/Entladung_AGV.png)

If no (further) Processing node is to be approached, the transport to the last transport node to be visited (destination node, here: the Inbound node of SH1) is coordinated following the same principle as described in [Section 10.4.6](#746-5-travel-to-the-next-node-including-rerouting). Shortly before the AGV arrives, the transport service is coupled to the transport node following the same principle as described in [Section 10.4.4](#744-3-coupling-the-transport-service-to-the-start-node). The LO is then transferred from the AGV to the SH1, which is signaled by a procedure change to *TransferToLea* initiated by the transport node of the LEA. After the successful transfer, the LEA triggers a procedure change to *TransferToLeaSucceeded*. The transport management finally decouples the transport service from the transport node and terminates it via a *Complete* command.

[^1]: The individual TN proxies in the transport management are not shown here for clarity.
