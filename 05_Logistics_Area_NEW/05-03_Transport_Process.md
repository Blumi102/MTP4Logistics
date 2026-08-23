### 5.3 Transport Process

##### Figure 5.9: Transport Process Model
![Transport Process Model](./images/Prozessmodell.svg)

[Figure 5.9](#figure-59-transport-process-model) shows the complete transport process. The process follows these steps:

1. **Order initiation**: A LEA signals a transport need. The Transport Management creates a transport service and assigns it an initial *NextNode* and *FinalTargetNode*. An AGV is dispatched.
2. **Transit**: The AGV travels to the target node. The Transport Management monitors AGV status via the AGV system adapter.
3. **Arrival at node**: When the AGV enters the approach zone, the transport service status transitions to *TransportAwaitRequested*. The Transport Management binds the transport service to the TK Proxy of the target node. The TK Block in the corresponding LEA becomes aware of the approaching AGV.
4. **Node confirmation or rejection**: The LEA either accepts (*TransportAwaited*) or rejects (*TransportDeclined*) the assignment. On rejection, the Transport Management unbinds the service from the proxy; on acceptance, the AGV is allowed to proceed to the node.
5. **AGV arrival and handover/processing**: When the AGV reaches the node (*TransportArrived*), the LEA orchestrates handover (transfer from/to LEA) or processing on the AGV. The appropriate transport status is set for each phase.
6. **Next node determination**: After completing the interaction, the LEA determines the next transport node (see [Section 5.5.3](#determination-of-the-next-transport-node)) and writes the ProxyId to *NextNode*. The Transport Management unbinds the service from the current proxy and dispatches the AGV to the next node.
7. **Transport completion**: When the AGV reaches the *FinalTargetNode* and the final interaction is complete, the transport service is closed.

**Rerouting**: If a LEA fault is detected, the Transport Management sets the transport service status to *Rerouting* (16#E) and calculates an alternative route.
