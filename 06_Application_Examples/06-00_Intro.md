## 6 Application Examples

This chapter provides two types of examples that illustrate the concepts for production-related logistics automation described in the dissertation.

The first type are **theoretical application examples** (Sections 10.1–10.4). Each example illustrates exactly one automation concept in isolation using a representative LEA or system configuration. They were constructed to demonstrate the concept and its design decisions, but have not been implemented in a real system.

The second type are **industrial evaluation examples** (Sections 10.5–10.7). Each example was physically implemented and tested, either at an industrial partner site or in a full PLC-based emulation. In contrast to the theoretical examples, the evaluation examples combine multiple automation concepts — LEA automation, Logistics Line choreography, and AGV-based transport — in a single system, and report findings from actual operation.

### Theoretical Application Examples

- [Application Example: Palletizing LEA](./06-01_PalletizingLEA.md) — Demonstrates LEA automation using a CES-based palletizing service, including service specification, mode of operation, and HMI screen design.
- [Application Example: Stretch Hood LEA](./06-02_StretchHoodLEA.md) — Demonstrates LEA automation using a service that supports both CES-based and SES-based operation, including the demand-driven SES mode of operation.
- [Application Example: Bag Filling Line](./06-03_BagFillingLine.md) — Demonstrates Logistics Line automation using a choreography configuration for a three-LEA bag filling line, including vertical integration via a Lead Service and horizontal integration via Configurable Logic and Configurable Communication.
- [Application Example: Transport PAL–Label–SH](./06-04_TransportPAL-Label-SH.md) — Demonstrates logistics area automation using the transport concept, tracing a push transport order step by step from initiation through AGV travel, processing, and final handover.

### Industrial Evaluation Examples

- [Evaluation Example: BASF Demonstrator](./06-05_BasfDemonstrator.md) — Physical implementation at BASF SE Ludwigshafen. Combines CES-based LEA automation and choreography-based Logistics Line automation in a three-LEA bottle-filling system. Validates retrofitability and distributed line coordination.
- [Evaluation Example: MoProLog Demonstrator](./06-06_MoProLogDemonstrator.md) — Physical implementation at BEUMER Group in Beckum. Combines CES- and SES-based LEA automation with MTP-based AGV transport integration in a Logistics Area with mixed-mode operation.
- [Evaluation Example: PLC-Based Emulation](./06-07_Emulation.md) — Full PLC-based emulation without physical hardware. Combines all three artefacts — LEA automation, Logistics Line choreography, and AGV transport — in a two-process Modular Logistics System with 13 LEAs and parallel packaging processes.
