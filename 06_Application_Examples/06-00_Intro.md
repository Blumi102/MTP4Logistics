## 6 Application Examples

This chapter provides two types of examples that illustrate the concepts for production-related logistics automation described in the work.

The theoretical application examples for the individual artifacts are provided at the end of the respective chapters: [Section 3.9](../03_Logistics_Equipment_Assemblies_NEW/03-09_Application_Example_PalletizingLEA.md) (Palletizing LEA) and [Section 3.10](../03_Logistics_Equipment_Assemblies_NEW/03-10_Application_Example_StretchHoodLEA.md) (Stretch Hood LEA) in [Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md), [Section 4.5](../04_Logistics_Line_NEW/04-05_Application_Example_BagFillingLine.md) (Bag Filling Line) in [Chapter 4](../04_Logistics_Line_NEW/04_Logistics_Line.md), and [Section 5.8](../05_Logistics_Area_NEW/05-08_Application_Example_TransportPAL-Label-SH.md) (Transport PAL–Label–SH) in [Chapter 5](../05_Logistics_Area_NEW/05_Logistics_Area.md). Each example illustrates exactly one automation concept in isolation using a representative LEA or MLS configuration. They were constructed to demonstrate the concepts and their design decisions, but have not been implemented in a real system.

This chapter presents **industrial evaluation examples** ([Sections 6.5](06-05_BasfDemonstrator.md)–[6.7](06-07_Emulation.md)). Each example was physically implemented and tested, either at an industrial partner site or in a full PLC-based emulation. In contrast to the theoretical examples, the evaluation examples combine multiple automation concepts — LEA automation, Logistics Line choreography, and AGV-based transport — in a single system, and report findings from actual operation.

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
