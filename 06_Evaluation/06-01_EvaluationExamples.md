### 6.1 Evaluation Examples

The evaluation examples were investigated as controlled experiments (*Single Case Experiments* per [[Wie14]](../98_References/README.md#wieringa-2014), *Controlled Experiments* per [[HMP+04]](../98_References/README.md#hevner-et-al-2004)). Defined test scenarios with specific stimuli were executed on prototypical implementations, and the system reactions were observed and assessed. This allows predictions about artifact performance in real-world contexts, even though the artifacts have not yet been deployed in productive logistics systems [[Wie14]](../98_References/README.md#wieringa-2014).

[Table 6.1](#table-61-implementation-of-the-artifacts-in-three-evaluation-examples) shows which artifacts are implemented in each evaluation example. Every artifact is realized in at least two examples, demonstrating applicability across different scenarios. Each artifact was implemented in at least one physical system (BASF or MoProLog demonstrator), confirming practical feasibility with industrial control hardware.

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
    <td align="left">x (CES)</td>
    <td align="left">x (CES & SES)</td>
    <td align="left">x (CES & SES)</td>
  </tr>
  <tr>
    <td align="left"><strong>Artifact 2 — Logistics Line Automation</strong></td>
    <td align="left">x</td>
    <td align="left"></td>
    <td align="left">x</td>
  </tr>
  <tr>
    <td align="left"><strong>Artifact 3 — Logistics Area Automation</strong></td>
    <td align="left"></td>
    <td align="left">x</td>
    <td align="left">x</td>
  </tr>
</table>

For each evaluation example, the following sections describe the use case, the prototype implementation, the test scenarios and their results, and the derived findings.

### 6.1.1 BASF Demonstrator

This section describes the first evaluation example, carried out at BASF SE in Ludwigshafen. It evaluates CES-based LEA automation ([Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md)) and choreography-based Logistics Line automation ([Chapter 4](../04_Logistics_Line_NEW/04_Logistics_Line.md)).

#### Use Case

[Figure 6.1](#figure-61-basf-bottle-filling-laboratory-system-at-basf-se-ludwigshafen) shows a laboratory-scale bottle-filling system. Three physical LEAs are arranged in a Logistics Line: a Labeller (LABEL), a Filler (FILL), and a Capper (CAP). The LABEL prints plastic bottles, the FILL fills them with granulate, and the CAP seals them. The LEAs are rigidly coupled, so the material flow is fixed by the physical layout. A LOL provides orchestration functions for the system.

##### Figure 6.1: BASF Bottle-Filling Laboratory System at BASF SE Ludwigshafen
![BASF Bottle-Filling Laboratory System at BASF SE Ludwigshafen](./images/BASF_Demo.png)

#### Implementation

[Figure 6.2](#figure-62-setup-of-the-basf-demonstrator-and-implemented-logistics-process) shows the automation architecture. The system had been planned and physically built prior to this dissertation. Each module was equipped with a Siemens controller (LABEL: SIMATIC S7 CPU 1511-1 PN; FILL: SIMATIC S7 CPU 1516-3 PN/DP; CAP: SIMATIC S7 CPU 1512SP-1 PN) running a native control program for sensor and actuator interaction.

##### Figure 6.2: Setup of the BASF Demonstrator and Implemented Logistics Process
![Setup of the BASF Demonstrator and Implemented Logistics Process](./images/Basf_Demo_Prozess.svg)

As part of this evaluation, an MTP service implementation following the CES concept ([Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md)) was retrofitted around the native software of each module, turning them into LEAs. Parameterization used individual values only, as the LEAs had few parameters.

The three LEAs were integrated into a Logistics Line using the choreography concept ([Chapter 4](../04_Logistics_Line_NEW/04_Logistics_Line.md)). A Lead Service was implemented in the CAP controller. The implementations are based on prototype block libraries from Siemens AG for SIMATIC TIA Portal V17. The choreography library was extended with new function blocks for MTP-based choreography configuration.

The LOL provides a choreography configurator (NestJS/Angular application, developed in [[Kem22]](../98_References/README.md#kempin-2022)) for configuring and downloading choreography relations to the LEAs, and a line HMI screen (SIMATIC WinCC Unified) for operator control.

#### Test Scenarios

The following test scenarios were successfully executed:

- **Loading the choreography configuration:** The choreography configuration was loaded and activated on all three LEAs.
- **Setting access modes:** Access modes of LEA services and parameters were configured to control whether access is permitted only from within the choreography or also from external systems.
- **Clearance signal transmission:** Continuous clearance signals were correctly exchanged between LEAs, ensuring each LEA knew whether the downstream LEA was ready to accept logistics objects.
- **Procedure assignment:** The procedure was set at the Lead; all other LEA services adopted this setting.
- **Product ID propagation:** The product ID was set at the FILL and adopted by the other two LEAs via the choreography.
- **Start-up:** Triggered by a Start command at the Lead, the line was started from back to front (CAP -> FILL -> LABEL).
- **Drain:** Triggered by a Complete command at the Lead, the line was drained from front to back (LABEL -> FILL -> CAP).
- **Stop, Abort, Hold, Unhold, Pause, Resume, Reset:** All state transitions were successfully propagated across the line in the appropriate directions.

#### Findings

**Practical applicability:** The tests confirm the practical applicability of CES-based LEA automation and choreography-based Logistics Line automation.

**Modular line composition:** The choreography concept enables independent, choreography-capable LEAs to be combined into a Logistics Line as needed.

**Configuration without reprogramming:** Choreography rules are stored as configuration in each LEA's program without modifying or reloading the program itself. LEA development and testing are thus decoupled from line logic configuration and testing.

**Distributed coordination:** Runtime control of the Logistics Line is achieved through distributed coordination among the LEAs, enabling shortest possible reaction times (e.g., in fault scenarios). No permanent LOL connection is required; the LOL serves only for choreography configuration and line monitoring.

**Choreography design complexity:** Defining choreography rules requires careful consideration. For example, naive fault-propagation rules that push LEAs into HELD immediately when another LEA enters HELD make it impossible to restart the line, because the first LEA to recover is immediately re-faulted by the still-held peers. A solution is to trigger transitions only on rising edges rather than on state levels. Design principles and methods for ensuring correct choreography behavior are outside the scope of this work.

**Retrofitability:** The evaluation shows that MTP service interfaces and choreography capability can be retrofitted around existing native software, lowering the entry barrier for brownfield systems. Long-term, native LEA software should be redesigned to fully exploit MTP and choreography capabilities (e.g., distinguishing Hold, Stop, and Abort as escalation levels).

**Structured and array-based data types in choreographies:** Current concepts and implementations only support interconnecting primitive data types within choreographies. This is sufficient for the use cases considered in this dissertation. Should structured or array-based data types be interconnected via choreographies in the future, both connected LEAs must use identical data types. For vendor-neutral interconnection, these data types would need to be standardized and the choreography concepts extended accordingly.

### 6.1.2 MoProLog Demonstrator

This section describes the second evaluation example, carried out at BEUMER Group GmbH & Co. KG in Beckum as part of the MoProLog research project. It evaluates CES- and SES-based LEA automation ([Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md)) and MTP-based AGV transport integration ([Chapter 5](../05_Logistics_Area_NEW/05_Logistics_Area.md)).

#### Use Case

[Figure 6.3](#figure-63-moprolog-demonstrator-at-beumer-group-in-beckum) shows the demonstrator comprising three physical LEAs in a Logistics Area: a Palletizer (PAL), a Pallet Supply (PAS), and a Foil Supply (FOS). The PAL receives empty pallets from the PAS and palletizes bags according to a predefined pattern. If required, the FOS applies a foil sheet to the empty pallet beforehand. Finished pallets are transported to one of two handover positions representing virtual Stretch Hood Machines (SH1, SH2). Transports are carried out by an AGV system consisting of a fleet manager and a Transport Management function in the LOL.

##### Figure 6.3: MoProLog Demonstrator at BEUMER Group in Beckum
![MoProLog Demonstrator at BEUMER Group in Beckum](./images/MoProLog_Demo.png)

##### Figure 6.4: Structure of the MoProLog Demonstrator
![Structure of the MoProLog Demonstrator](./images/MoProLog_Demo_Prozess.svg)

#### Implementation

The three physical LEAs are based on the BEUMER paletpac palletizer [[BEU25]](../98_References/README.md#beumer-group-2025), modularized at hardware and software level into three independent LEAs. Each LEA was equipped with a Siemens controller (PAL and PAS: SIMATIC S7 CPU 1512SP-1 PN; FOS: SIMATIC S7 CPU 1510SP-1 PN).

##### Figure 6.5: Structure of the LEA Services in the MoProLog Demonstrator
![Structure of the LEA Services in the MoProLog Demonstrator](./images/MoProLog_Implementierung.svg)

The automation software of each LEA ([Figure 6.5](#figure-65-structure-of-the-lea-services-in-the-moprolog-demonstrator)) consists of a native software layer (part of the paletpac software for sensor and actuator interaction), surrounded by an MTP service implementation and Transport Node function blocks for AGV integration.

The PAL service follows the CES principle, as it continuously processes a single order type at high throughput [[BFG+21]](../98_References/README.md#blumenstein-et-al-design-principles). The PAS and FOS services follow the SES principle, since they are less loaded and their function is optionally needed depending on the product. This would also allow PAS and FOS to serve other packaging processes or to be replaced by alternative LEAs for different pallet or foil types. The two virtual Stretch Hood Machines (SH1, SH2) were implemented as SES-based services on emulated controllers (SIMATIC S7-PLCSIM Advanced).

Transport was carried out by a MAXOLUTION AGV from SEW-Eurodrive [[SEW18]](../98_References/README.md#sew-eurodrive-2018), controlled by a proprietary fleet management system from BEUMER. A prototype Transport Management was implemented as a .NET/Angular application [[Hen22]](../98_References/README.md#henkel-2022) to integrate the AGV system via MTP-based interfaces. Additional LOL functions — order management and material flow management — were provided by Fraunhofer IML. An HMI based on SIMATIC WinCC Unified enabled manual operation and monitoring.

#### Test Scenarios

Two test scenarios were successfully executed:

- **Scenario 1 — Static default routes:** A system with static material flows was assumed. Transport nodes were configured as default values in the LEA programs; orders were entered manually via the LOL HMI. Tests were conducted for two products (P1: no foil sheet; P2: foil sheet required).
- **Scenario 2 — Dynamic transport node requests:** A system with runtime-configurable material flows was assumed. A material flow management function in the LOL determined the next transport node dynamically on request. Order management in the LOL assigned packaging orders to the PAL. Tests were conducted for both products, including dynamic allocation of pallets to SH1 or SH2.

#### Findings

**Practical applicability:** The tests confirm the practical applicability of CES- and SES-based LEA automation and MTP-based AGV transport integration. Scenario 1 suits systems with low material flow variance or without dedicated material flow management. Scenario 2 suits systems requiring runtime flexibility in material routing.

**Refinements to the transport concept:** Working with the demonstrator revealed the need for refinements to the transport automation concept, targeting implementation robustness rather than the underlying interaction mechanism. These refinements have been incorporated into the transport concept in [Chapter 5](../05_Logistics_Area_NEW/05_Logistics_Area.md) and are also evaluated in the emulation ([Section 6.1.3](#613-plc-based-emulation)).

**Retrofitability:** A proprietary logistics machine (BEUMER paletpac) and a proprietary AGV (SEW MAXOLUTION) were given MTP interface wrappers with manageable effort. This keeps the entry barrier for retrofitting existing systems low. Long-term, native LEA software should be redesigned to fully exploit MTP-based modularization.

**Independent parallel development:** The LEA automation software, the AGV system, the Transport Management, and the order/material flow management were developed independently by different project partners. The uniform MTP interfaces nonetheless enabled fast and straightforward commissioning.

### 6.1.3 PLC-Based Emulation

This section describes the third evaluation example: a comprehensive MLS emulated with virtual PLCs. It evaluates the combined application of all three artifacts — LEA automation, Logistics Line choreography, and AGV transport integration — in a realistic multi-process system.

#### Use Case

The MLS serves two packaging processes — bag filling and octabin filling — executed concurrently. [Figure 6.6](#figure-66-plc-based-emulation-of-a-modular-logistics-system) shows the system layout, transport nodes, and possible material flows.

##### Figure 6.6: PLC-Based Emulation of a Modular Logistics System
![PLC-Based Emulation of a Modular Logistics System](./images/Emulation_Anwendungsbeispiel.svg)

**Bag filling process:** A CES-based Logistics Line of three LEAs — a Form-Fill-Seal machine (FFS), a Conveyor (CONV), and a Palletizer (PAL) — processes packaging orders from the LOL. Two SES-based Pallet Supplies (PAS1, PAS2) provide different pallet types on demand. An SES-based Foil Supply (FOS) optionally applies a foil layer. After palletizing, one of two SES-based Stretch Hood Machines (SH1, SH2) applies load securing. A Labeller (LABEL) provides final identification. Finished pallets are transported to a Stock (STOCK) LEA. All LEAs outside the Logistics Line are loosely coupled single LEAs served by an AGV system.

**Octabin filling process:** A CES-based Octabin Erector (OAU) erects octabins using pallets from the shared PAS LEAs. One of the SH LEAs inserts a foil inlay. An SES-based Logistics Line — Octabin Filler (OFill), Conveyor (CONV2), and Sealing Station (OSeal) — processes octabins demand-oriented as they arrive. Load securing and labelling are performed by the shared SH and LABEL LEAs. The example intentionally combines order-oriented and demand-oriented single LEAs, order-oriented and demand-oriented Logistics Lines, and shared LEAs across both processes, covering the full diversity of MLS configurations analyzed in this dissertation.

#### Implementation

The emulation uses SIMATIC S7-PLCSIM Advanced and TIA Portal V18. Each LEA runs on a virtual SIMATIC S7-1500 controller that communicates via OPC UA exactly as a real controller would. Since the focus is on communication over MTP interfaces rather than LEA-internal automation, the emulated LEAs do not differ from physical LEAs in this regard. Logistics objects are modeled virtually: handovers within Logistics Lines use binary process value interconnections; in the Logistics Area, a virtual LO is represented by its transporting AGV.

Each emulated LEA consists of a simplified function block emulating the LEA's logistics function, surrounded by an MTP service implementation. Blue LEAs in [Figure 6.6](#figure-66-plc-based-emulation-of-a-modular-logistics-system) operate in CES mode; red LEAs in SES mode. Parameterization follows the structured parameter set concept using *ProductDataSet* and *PackagingDataSet*.

The two Logistics Lines use the choreography concept with External Lead Services (LEADBag for bag filling; LEADOct for octabin filling). The CES-based bag filling line follows the same start-up and completion logic as the BASF demonstrator ([Section 6.1.1](#611-basf-demonstrator)). The SES-based octabin filling line starts up and waits in PAUSED state; upon LO arrival, the OFill switches to EXECUTE, processes the LO using its LO-specific order data received during handover, and passes the LO with its metadata (ProductionId, ProductId, LogisticsObjectId, LogisticsObjectStatus) to CONV2. Multiple LOs of different types can be processed consecutively while the line remains in EXECUTE.

Flexible transports are coordinated via a simplified AGV emulation and a Transport Management function in the LOL.

##### Table 6.2: LOL Functions in the PLC-Based Emulation

<table>
  <tr>
    <th align="left">Function</th>
    <th align="left">Description</th>
    <th align="left">Implementation</th>
  </tr>
  <tr>
    <td align="left">HMI</td>
    <td align="left">Parameter setting, command input, monitoring of LEAs and Logistics Lines</td>
    <td align="left">WinCC Unified</td>
  </tr>
  <tr>
    <td align="left">Parameter Management</td>
    <td align="left">Management and configuration of product- and packaging-specific LEA parameters</td>
    <td align="left">.NET/NestJS backend, Angular frontend (<a href="../98_References/README.md#janzen-2023">[Jan23]</a>)</td>
  </tr>
  <tr>
    <td align="left">Transport Management</td>
    <td align="left">AGV system integration and transport order management as MTP Transport Services</td>
    <td align="left">.NET backend, Angular frontend (based on <a href="../98_References/README.md#henkel-2022">[Hen22]</a>)</td>
  </tr>
  <tr>
    <td align="left">AGV Emulation</td>
    <td align="left">Emulation of one or more AGVs and their fleet manager with proprietary interface</td>
    <td align="left">.NET backend, Angular frontend</td>
  </tr>
  <tr>
    <td align="left">Choreography Configurator</td>
    <td align="left">Configuration of choreography relations for both Logistics Lines</td>
    <td align="left">NestJS/Angular (<a href="../98_References/README.md#kempin-2022">[Kem22]</a>)</td>
  </tr>
</table>

#### Test Scenarios

Ten test scenarios were successfully executed:

1. **Load choreography configurations** for both Logistics Lines; set access modes and close process value interconnections.
2. **Connect all transport-relevant LEAs** to the Transport Management.
3. **Set order-independent parameters** (product-specific, packaging-specific, and construction-specific parameter sets).
4. **Start all SES-based single LEAs**; they wait in PAUSED state for incoming logistics objects.
5. **Start the SES-based octabin filling Logistics Line**; it starts up and waits in PAUSED state.
6. **Bag filling with static routes** (Product ID 1): PAS1 -> Logistics Line (bag) -> SH2 -> LABEL -> STOCK.
7. **Bag filling with dynamic routes** (Product ID 2): PAS2 -> FOS -> Logistics Line (bag) -> SH2 -> LABEL -> STOCK. Choices of PAS2, FOS, and SH2 were determined by querying the material flow management.
8. **Octabin filling with static routes** (Product ID 3): PAS1 -> OAU -> SH1 (foil inlay) -> Logistics Line (octabin) -> SH1 (stretch hood) -> LABEL -> STOCK.
9. **Octabin filling with dynamic routes** (Product ID 4): PAS1 -> OAU -> SH2 (foil inlay) -> Logistics Line (octabin) -> SH1 (stretch hood) -> LABEL -> STOCK.
10. **Parallel bag and octabin filling**: combinations of scenarios 6+8, 7+9, and 7+8 executed concurrently.

#### Findings

**Practical applicability:** The tests confirm the practical applicability of CES- and SES-based LEA automation including structured parameterization, choreography-based Logistics Line automation, and MTP-based AGV transport integration. In particular, the SES principle is demonstrated at scale: SH1 and SH2 receive pallets of different types and states, identify each logistics object, and process it according to its *ProductId* and *LogisticsObjectStatus*. Above all, this example demonstrates the combined use of all three artifacts in a realistic, multi-process MLS.

**System design potential:** Intelligent MLS design based on the presented artifacts can increase system utilization compared to conventional systems. For example, SH1 and SH2 serve both packaging processes — applying stretch hoods for bag pallets, inserting foil inlays for octabins — instead of being dedicated to a single task. AGV-based transport reduces space requirements and increases material flow flexibility, enabling a broader product portfolio on the same system.

**Enablers for flexible MLS design:** The artifacts enable flexible MLS design because LEAs are parameterizable via standardized interfaces, AGV systems can be integrated without deep knowledge of proprietary AGV automation, material flows are configurable at runtime, and LEAs can be quickly integrated or replaced via MTP-based mechanisms.
