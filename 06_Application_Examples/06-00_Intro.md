## 6 Application Examples

This chapter provides two types of examples that illustrate the concepts for production-related logistics automation described in the work.

The first type are **theoretical application examples** ([Sections 6.1](06-01_PalletizingLEA.md)–[6.4](06-04_TransportPAL-Label-SH.md)). Each example illustrates exactly one automation concept in isolation using a representative LEA or MLS configuration. They were constructed to demonstrate the concepts and their design decisions, but have not been implemented in a real system.

The second type are **industrial evaluation examples** ([Sections 6.5](06-05_BasfDemonstrator.md)–[6.7](06-07_Emulation.md)). Each example was physically implemented and tested, either at an industrial partner site or in a full PLC-based emulation. In contrast to the theoretical examples, the evaluation examples combine multiple automation concepts — LEA automation, Logistics Line choreography, and AGV-based transport — in a single system, and report findings from actual operation.

### Theoretical Application Examples

- [Section 6.1: Application Example: Palletizing LEA](./06-01_PalletizingLEA.md) — Demonstrates LEA automation using a CES-based palletizing service, including service specification, mode of operation, and HMI screen design.
- [Section 6.2: Application Example: Stretch Hood LEA](./06-02_StretchHoodLEA.md) — Demonstrates LEA automation using a service that supports both CES-based and SES-based operation, including the demand-driven SES mode of operation.
- [Section 6.3: Application Example: Bag Filling Line](./06-03_BagFillingLine.md) — Demonstrates Logistics Line automation using a choreography configuration for a three-LEA bag filling line, including vertical integration via a Lead Service and horizontal integration via Configurable Logic and Configurable Communication.
- [Section 6.4: Application Example: Transport PAL–Label–SH](./06-04_TransportPAL-Label-SH.md) — Demonstrates Logistics Area automation using the transport concept, tracing a push transport order step by step from initiation through AGV transport, processing, and final handover.

### Industrial Evaluation Examples

[Table 6.1](#table-61-implementation-of-the-artifacts-in-three-evaluation-examples) provides an overview of which artifacts are implemented in each of the three evaluation examples.

##### Table 6.1: Implementation of the Artifacts in Three Evaluation Examples

<table>
  <tr>
    <th align="left"></th>
    <th align="left">BASF</th>
    <th align="left">MoProLog</th>
    <th align="left">Emulation</th>
  </tr>
  <tr>
    <td align="left"><strong>Artifact 1 — LEA Automation</strong></td>
    <td align="left">× (CES)</td>
    <td align="left">× (CES & SES)</td>
    <td align="left">× (CES & SES)</td>
  </tr>
  <tr>
    <td align="left"><strong>Artifact 2 — Automation of Logistics Lines</strong></td>
    <td align="left">×</td>
    <td align="left"></td>
    <td align="left">×</td>
  </tr>
  <tr>
    <td align="left"><strong>Artifact 3 — Automation of Logistics Areas</strong></td>
    <td align="left"></td>
    <td align="left">×</td>
    <td align="left">×</td>
  </tr>
</table>

- [Section 6.5: Evaluation Example: BASF Demonstrator](./06-05_BasfDemonstrator.md) — Physical implementation at BASF SE Ludwigshafen. Combines CES-based LEA automation and choreography-based Logistics Line automation in a three-LEA bottle-filling system. Validates retrofitability and distributed line coordination.
- [Section 6.6: Evaluation Example: MoProLog Demonstrator](./06-06_MoProLogDemonstrator.md) — Physical implementation at BEUMER Group in Beckum. Combines CES- and SES-based LEA automation with MTP-based AGV transport integration in a Logistics Area with mixed-mode operation.
- [Section 6.7: Evaluation Example: PLC-Based Emulation](./06-07_Emulation.md) — Full PLC-based emulation without physical hardware. Combines all three artifacts — LEA automation, Logistics Line choreography, and AGV transport — in a two-process Modular Logistics System with 13 LEAs and parallel packaging processes.
