## 4 Choreography-Based Automation and MTP-Based Integration of Logistics Lines

This chapter presents the choreography-based automation and MTP-based integration of Logistics Lines as the second artifact of this dissertation. Existing choreography concepts from [[Stu26]](../98_References/README.md#stutz-2026) and [[SFB+21]](../98_References/README.md#stutz-et-al-2021) are adopted and extended with newly specified MTP concepts. The application of choreography principles to Logistics Line automation was investigated in [[Ort21]](../98_References/README.md#ortmann-2021) and partially published in [[BSF+22]](../98_References/README.md#blumenstein-et-al-2022-etfa), [[BGB+23]](../98_References/README.md#blumenstein-et-al-moprolog), and [[SBF+22]](../98_References/README.md#stutz-et-al-2022). Detailed specifications of the introduced MTP extensions and a more detailed description of their application to the automation of a bag-filling Logistics Line are available in the GitHub repository of this dissertation [[Blu26]](../98_References/README.md#blumenstein-github).

### 4.1 Artifact Overview

The automation of Logistics Lines follows a choreography-based approach built on the mechanisms described in [[SFB+21]](../98_References/README.md#stutz-et-al-2021) and [[Stu26]](../98_References/README.md#stutz-2026), adapted to the context of production-adjacent logistics and extended with MTP-based interfaces and models for automated integration. A distinction is made between the **horizontal integration** of LEAs within a Logistics Line and the **vertical integration** of a choreographed Logistics Line into a superordinate LOL.

**Horizontal integration of LEAs into a Logistics Line:** Horizontal interactions between LEAs are configured by a Choreography Configurator in the LOL, resulting in a choreographed Logistics Line. To enable automated integration of LEAs into the configurator, their connectable inputs and outputs are described in the LEA-MTPs as **semantic MTP models** (Section [4.2.3](#semantic-models-for-lea-integration-into-a-choreography-configurator)). On this basis, a choreography configuration is designed and then downloaded to the LEA controllers via **MTP-based configuration interfaces** specified in the LEA-MTPs (Section [4.2.4](#interfaces-for-configuring-horizontal-interaction)). The necessary MTP-based interfaces and model definitions are grouped in the new MTP aspect *ChoreographySet* (Section [4.2.5](#choreographyset)).

**Vertical integration of Logistics Lines:** A choreographed Logistics Line is integrated into a superordinate LOL and controlled — automatically by an order management system or manually by an operator — via a shared service interface (**Line Interface**, Section [4.3.1](#line-interface)) that makes the line behave like a single MTP service. An operator display (**Line HMI**, Section [4.3.2](#line-hmi)) is also provided. The Line Interface and Line HMI are described in a shared MTP for the Logistics Line (**Composed-MTP**, Section [4.3.3](#composed-mtp)).

### 4.2 Horizontal Integration of Logistics Equipment Assemblies into a Logistics Line

#### Application Example

[Figure 4.1](#figure-41-application-example-of-a-choreographed-logistics-line) shows an example Logistics Line for bag filling and palletizing, consisting of three LEAs: a form-fill-seal machine (FFS), a conveyor (CONV), and a layer palletizer (PAL). Four types of relations between the LEAs realize the choreography-based horizontal control:

- **Parametrizing relations:** Parameters required by one LEA are observed from another. For example, the FFS reads the target bag count from the PAL and applies it to its own parameters (Figure [4.1](#figure-41-application-example-of-a-choreographed-logistics-line), (1)).
- **Procedural relations:** Service state transitions of one LEA trigger state transitions in another. For example, once the PAL service reaches EXECUTE, the CONV starts its own service (Figure [4.1](#figure-41-application-example-of-a-choreographed-logistics-line), (2)). Complex logic is also possible: if any LEA service enters STOPPED, all other services do likewise.
- **Interlocking relations:** Clearance signals are continuously passed from downstream to upstream LEAs as MTP process values, ensuring that a logistics object may only enter an LEA when it is ready (Figure [4.1](#figure-41-application-example-of-a-choreographed-logistics-line), (3)).
- **Regulating relations:** Production speeds of LEAs can be mutually adapted. Constants can also be set choreography-based, e.g., to define operating modes or fix constant parameters.

##### Figure 4.1: Application Example of a Choreographed Logistics Line with Three LEAs
![Application Example of a Choreographed Logistics Line with Three LEAs](./images/Beispiel_Linie_Interaktionen.svg)

#### System Architecture of a Choreographed Logistics Line

The technical realization follows the choreography concept from [[SFB+21]](../98_References/README.md#stutz-et-al-2021) and [[Stu26]](../98_References/README.md#stutz-2026). [Figure 4.2](#figure-42-abstract-system-architecture-of-a-choreographed-logistics-line) shows the basic architecture. Each LEA controller provides the execution context for an MTP service and the necessary base functionality for data processing and communication to participate in a choreography — referred to as an **Active Choreography Participant** in [[Stu26]](../98_References/README.md#stutz-2026). The LEA service (native control program) is extended with **Configurable Logic** — internally configured behavioral rules — and **Configurable Communication** — configurable data exchange with other LEAs.

##### Figure 4.2: Abstract System Architecture of a Choreographed Logistics Line
![Abstract System Architecture of a Choreographed Logistics Line](./images/Choreo_Abstrakte_Architektur.svg)

#### Architecture of an LEA as a Choreography Participant

[Figure 4.3](#figure-43-architecture-of-an-lea-as-a-choreography-participant) shows the detailed architecture of an Active Choreography Participant according to [[Stu26]](../98_References/README.md#stutz-2026). Every LEA following this architecture can participate in a choreography.

##### Figure 4.3: Architecture of an LEA as a Choreography Participant
![Architecture of an LEA as a Choreography Participant](./images/Architektur_ChoreoParticipant_2.svg)

#### Configurable Logic

The Configurable Logic components (green in [Figure 4.3](#figure-43-architecture-of-an-lea-as-a-choreography-participant)) enable configurable processing of available information, which can originate from within the LEA or from other LEAs. The software pattern *Configurable Logic* according to [[Stu26]](../98_References/README.md#stutz-2026) is structured as shown in [Figure 4.4](#figure-44-components-of-the-configurable-logic-software-pattern):

- **Input-List:** manages fixed outputs of the LEA service (e.g., service state, current procedure) as internal inputs, as well as values received from other LEAs as external inputs.
- **Logic-List:** manages configurable processing functions that transform values from the Input-List.
- **Output-List:** manages the results of the Configurable Logic, which are fed back into the LEA service as internal inputs (triggering state transitions or changes to process values, parameters, or report values) and can also be made available to other LEAs as external inputs.

The central *ConfigurableLogic* component controls the execution cycle: it reads from the Input-List, applies processing, and writes results to the Output-List.

##### Figure 4.4: Components of the Configurable Logic Software Pattern
![Components of the Configurable Logic Software Pattern](./images/Software_Pattern_Konfigurierbare_Logik.drawio.png)

#### Configurable Communication

The Configurable Communication components (blue in [Figure 4.3](#figure-43-architecture-of-an-lea-as-a-choreography-participant)) provide configurable inter-LEA data exchange. OPC UA Client/Server is used as the standardized communication technology, consistent with the MTP environment. Two communication variants are supported according to [[Stu26]](../98_References/README.md#stutz-2026):

- **Active reading (preferred):** values are read from another LEA's Input-List and transferred into the local Input-List.
- **Active writing:** values from the local Output-List are written into another LEA's Input-List. This variant also supports integrating non-choreography-enabled equipment via decentralized orchestration [[SFB+23]](../98_References/README.md#stutz-et-al-2023).

[Figure 4.5](#figure-45-components-of-the-configurable-communication-software-pattern) shows the components. The central *OpcUaClientServerManager* manages OPC UA connections (*UaConnections*) and, depending on the variant, read operations (*UaReaders*) or write operations (*UaWriters*). It has access to the Input- and Output-Lists. For active reading, *UaReaders* read values from other LEAs into the local Input-List. For active writing, a *ValueList* acts as a passive input channel that other LEAs can write to; these values are then forwarded to specific Input-List indices. A *PreparedConfiguration* and *ActiveConfiguration* are distinguished for all configuration elements, analogous to the Configurable Logic.

##### Figure 4.5: Components of the Configurable Communication Software Pattern
![Components of the Configurable Communication Software Pattern](./images/Software_Pattern_Konfigurierbare_Kommunikation_Übersicht.drawio.png)

#### UnionType

All values exchanged between LEAs in a Logistics Line carry the data type *UnionType* according to [[Stu26]](../98_References/README.md#stutz-2026), shown in [Figure 4.6](#figure-46-uniontype-data-type). This type holds (currently five) variables of different data types, of which one is selected as the active member at runtime. This allows the data type to be determined at runtime even on controller systems that require compile-time type definitions.

##### Figure 4.6: UnionType Data Type
![UnionType Data Type](./images/UnionType.drawio.png)

#### Semantic Models for LEA Integration into a Choreography Configurator

For a Choreography Configurator in the LOL, the contents of the Input- and Output-Lists of each LEA must be semantically identifiable. [Figure 4.7](#figure-47-structure-of-the-input-and-output-lists-of-an-lea) shows the basic structure of these lists. Three categories of elements are distinguished:

- **Fixed elements:** Hard-coded by the LEA program and immutable. Fixed inputs are outputs of the LEA service (e.g., service state); fixed outputs are inputs to the LEA service (e.g., service commands).
- **Configurable elements:** Placeholders for values to be read from (configurable inputs) or written to (configurable outputs) other LEAs. The number of configurable and writable elements is fixed at engineering time; their connections are established during choreography configuration.
- **Writable elements:** Passive placeholders in the Input-List that other LEAs can write values into (relevant for the active writing variant).

##### Figure 4.7: Structure of the Input- and Output-Lists of an LEA
![Structure of the Input- and Output-Lists of an LEA](./images/InOutputListen.svg)

To represent these contents in an MTP, the model definition *ChoreographyParticipant* is introduced to identify an LEA as a potential choreography participant. The model definitions *InputList* and *OutputList* organize the list elements. The concrete element types introduced are shown in [Table 4.1](#table-41-element-types-in-the-input-and-output-lists-of-an-lea).

##### Table 4.1: Element Types in the Input- and Output-Lists of an LEA

<table>
  <tr>
    <th align="left">Model Definition</th>
    <th align="left">Interface Definition</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left"><em>FixedInputElement</em></td>
    <td align="left"><em>UnionElement</em></td>
    <td align="left">Fixed outputs of the LEA service that serve as inputs for the Configurable Logic (e.g., service states). Not modifiable by configuration.</td>
  </tr>
  <tr>
    <td align="left"><em>FixedOutputElement</em></td>
    <td align="left"><em>UnionElement</em></td>
    <td align="left">Fixed outputs of the Configurable Logic that serve as inputs to the LEA service (e.g., service commands). Not modifiable by configuration.</td>
  </tr>
  <tr>
    <td align="left"><em>ConfigurableInputElement</em></td>
    <td align="left"><em>UnionElement</em></td>
    <td align="left">Configurable inputs for the Configurable Logic that are read from other LEAs via read operations (active reading variant). Configuration specifies the source.</td>
  </tr>
  <tr>
    <td align="left"><em>ConfigurableOutputElement</em></td>
    <td align="left"><em>UnionElement</em></td>
    <td align="left">Configurable outputs of the Configurable Logic that are written to other LEAs via write operations (active writing variant). Configuration specifies the target.</td>
  </tr>
  <tr>
    <td align="left"><em>WritableInputElement</em></td>
    <td align="left"><em>WritableUnionElement</em></td>
    <td align="left">Passive inputs for the Configurable Logic that other LEAs can write values into (active writing variant).</td>
  </tr>
</table>

#### Interfaces for Configuring Horizontal Interaction

MTP-based interfaces are required to download a choreography configuration from a Choreography Configurator into the LEA controller.

**ChoreographyParticipantManager:** To interact with the *ConfigurableLogic* component, the MTP interface definition *ChoreographyParticipantManager* is specified. It provides index-based access to the Input-, Logic-, and Output-List elements, and supports executing, stopping, and resetting a configuration. A *PreparedConfiguration* can be fully prepared before being activated, while a different *ActiveConfiguration* remains running during configuration. Both can be displayed via the interface, but only the *PreparedConfiguration* can be edited. The interface can also be embedded as a dynamic HMI element in the LEA operator display.

**OpcUaClientServerManager:** To interact with the *OpcUaClientServerManager* component, the MTP interface definition *OpcUaClientServerManager* is specified. It provides index-based access to lists of connections (*UaConnections*), read operations (*UaReaders*), write operations (*UaWriters*), and writable value fields (*ValueFields*). Connection configuration variables are based on the *UA\_Connect* and *UA\_Disconnect* interfaces of the PLCopen specification [[OPC 30001]](../98_References/README.md#opc-30001). Read and write operation configuration is based on the *UA\_ReadList* and *UA\_WriteList* interfaces [[OPC 30001]](../98_References/README.md#opc-30001). Each read operation is mapped to an Input-List index; each write operation is mapped to an Output-List index. The *PreparedConfiguration*/*ActiveConfiguration* pattern applies to all configuration elements. The interface can also be embedded as a dynamic HMI element.

**UnionElement / WritableUnionElement:** The *UnionElement* MTP interface definition enables displaying a value with a runtime-selectable data type. The *WritableUnionElement* additionally supports writing such a value, required by the active writing communication variant.

> **Note on vendor-neutral information exchange:** To enable vendor-neutral interaction between LEAs, variables of the standardized MTP-based LEA interfaces should be exchanged wherever possible. An exception is the interface of an External Lead (see Section [4.3.1](#line-interface)), for which DoRequest/DoneReply relations are recommended [[Stu26]](../98_References/README.md#stutz-2026) to handle choreography relations that start at one LEA and end at another.

#### ChoreographySet

To represent all model and interface definitions introduced in the preceding sections, a new MTP aspect *ChoreographySet* is introduced. In the *ChoreographySet*, the Input- and Output-Lists of an LEA are modeled with the elements described above. All elements of types *FixedInputElement*, *FixedOutputElement*, *ConfigurableInputElement*, and *ConfigurableOutputElement* are assigned a *UnionElement* interface; each *WritableInputElement* is assigned a *WritableUnionElement* interface. Configurable Communication is configured via an *OpcUaClientServerManager* interface, which contains one *UaReader* per *ConfigurableInputElement*, one *UaWriter* per *ConfigurableOutputElement*, and one *ValueField* per *WritableInputElement*. Configurable Logic is configured via a *ChoreographyParticipantManager* interface, which is assigned to the *ChoreographyParticipant* model definition.

### 4.3 Vertical Integration of a Logistics Line into a Logistics Orchestration Layer

#### Line Interface

The Line Interface exposes the functionality of a choreographed Logistics Line to a superordinate LOL, making the line controllable, parametrizable, and monitorable as if it were a single MTP service. [Figure 4.8](#figure-48-components-of-an-lea-service-interface) illustrates the components of an individual LEA service interface; [Figure 4.9](#figure-49-components-of-the-line-interface-of-a-choreographed-logistics-line) shows how the Line Interface is composed from selected elements of multiple LEA interfaces.

##### Figure 4.8: Components of an LEA Service Interface
![Components of an LEA Service Interface](./images/LEA_Schnittstelle.svg)

##### Figure 4.9: Components of the Line Interface of a Choreographed Logistics Line
![Components of the Line Interface of a Choreographed Logistics Line](./images/Linien_Schnittstelle.svg)

**Service and procedure interfaces:** Every choreography has a **Lead Service** [[Stu26]](../98_References/README.md#stutz-2026) whose state machine represents the state of the entire choreography. The Lead Service accepts commands (start, stop, etc.) and procedure selections for the choreography. It can be one of the LEA services already participating in the choreography (**Internal Lead**) or a separate service included solely for this purpose (**External Lead**). For Logistics Lines, an External Lead is preferred because most line functions (e.g., startup sequences) are initiated at one LEA and end at another. The External Lead can run on one of the LEA controllers or on an external system, and must implement the concepts of Section [4.2](#horizontal-integration-of-logistics-equipment-assemblies-into-a-logistics-line).

The *ServiceControl* interface of the Lead Service is adopted 1:1 into the Line Interface, along with the Lead Service procedures and their *ProcedureHealthView* interfaces. The choreography logic must relay commands and procedure settings from the Lead Service to all **Follower Services** [[Stu26]](../98_References/README.md#stutz-2026). The Lead Service operates in *AutomaticExternal* or *Operator* mode (controllable by LOL automation or operator); all Follower Services operate in *AutomaticInternal* mode (controlled exclusively by internal Configurable Logic). Operating modes are configured via behavioral rules in the Configurable Logic.

**Parameter, report value, and process value interfaces:** The parameters, report values, and process values of the Line Interface consist of selected interfaces from the participating LEAs that are relevant for the overall line function. These are adopted 1:1 into the Line Interface and can be set or monitored externally. All remaining parameters and values are handled choreography-internally. Externally accessible parameters operate in *AutomaticExternal* or *Operator* mode; internally handled parameters operate in *AutomaticInternal* mode, configured via Configurable Logic behavioral rules.

#### Line HMI

The individual LEA operator displays are combined into a shared Line HMI for operator visualization and control of the entire Logistics Line. [Figure 4.10](#figure-410-individual-operator-displays-of-three-leas) shows three example LEA displays; [Figures 4.11](#figure-411-line-hmi-combination-variant-1), [4.12](#figure-412-line-hmi-combination-variant-2), and [4.13](#figure-413-line-hmi-combination-variants-3-and-4) show the resulting Line HMIs using the four combination variants. The four variants can also be combined with each other.

##### Figure 4.10: Individual Operator Displays of Three LEAs
![Individual Operator Displays of Three LEAs](./images/Line_HMI_LEAs_Einzeln.svg)

##### Table 4.2: Variants for Combining LEA Operator Displays into a Line HMI

<table>
  <tr>
    <th align="left">Variant</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left"><strong>Variant 1:</strong> Object-level combination in one display</td>
    <td align="left">Selected display objects from individual LEA displays are arranged on the Line HMI and optionally supplemented with new static elements representing line-specific features (e.g., connecting conveyors).</td>
  </tr>
  <tr>
    <td align="left"><strong>Variant 2:</strong> Display-in-display combination</td>
    <td align="left">Complete LEA displays are embedded into the Line HMI display, producing a composite display that contains other displays.</td>
  </tr>
  <tr>
    <td align="left"><strong>Variant 3:</strong> Displays integrated into the display hierarchy</td>
    <td align="left">Complete LEA displays are inserted into the Line HMI display hierarchy, possibly at different hierarchy levels.</td>
  </tr>
  <tr>
    <td align="left"><strong>Variant 4:</strong> Display hierarchies combined</td>
    <td align="left">The complete display hierarchies of individual LEAs are integrated into the Line HMI display hierarchy, possibly at different hierarchy levels.</td>
  </tr>
</table>

##### Figure 4.11: Line HMI Combination Variant 1
![Line HMI Combination Variant 1](./images/Line_HMI_Variante_1.svg)

##### Figure 4.12: Line HMI Combination Variant 2
![Line HMI Combination Variant 2](./images/Line_HMI_Variante_2.svg)

##### Figure 4.13: Line HMI Combination Variants 3 and 4
![Line HMI Combination Variants 3 and 4](./images/Line_HMI_Variante_3_4.svg)

#### Composed-MTP

For automated vertical integration of a choreographed Logistics Line into a LOL, a shared MTP for the line — the **Composed-MTP** — is introduced. It describes the Line Interface and the Line HMI. When a Composed-MTP is imported, only the information relevant to the line is loaded into the LOL.

#### Re-Modeling vs. Referencing

The Line Interface and Line HMI are composed of interface and model elements already contained in the LEA-MTPs. Two approaches for combining them in the Composed-MTP exist:

1. **Re-modeling:** All relevant LEA-MTP elements are re-modeled within the Composed-MTP. The original LEA-MTPs are not directly used. Advantage: the Composed-MTP resembles a standard LEA-MTP and can be integrated similarly. Disadvantage: modeling is duplicated; consistency between LEA-MTPs and the Composed-MTP must be actively maintained; changes require updates in both places.

2. **Referencing:** LEA-MTPs are attached to the Composed-MTP, and elements within the Composed-MTP reference elements in the attached LEA-MTPs wherever possible. Only line-specific content is newly modeled. Advantage: no duplicate modeling; integrity of referenced elements can be verified via the LEA-MTP package signature. Disadvantage: reference resolution requires special integration mechanisms not needed for standard LEA-MTPs.

> **Design decision:** **Referencing** is chosen as the modeling approach for Composed-MTPs. The current MTP specification allows only one OPC UA server per MTP [[MTP Specification Part 5.1]](../98_References/README.md#mtp-specification-part-51). A Composed-MTP must retrieve information from multiple OPC UA servers of multiple LEAs, so special integration mechanisms are required regardless. The advantages of referencing therefore outweigh its disadvantages.

#### Structure of a Composed-MTP

[Figure 4.14](#figure-414-basic-structure-of-a-composed-mtp) shows the basic structure. The attached LEA-MTP files form the modeling basis and are referenced by the Composed-MTP's semantic models in its various aspects.

##### Figure 4.14: Basic Structure of a Composed-MTP
![Basic Structure of a Composed-MTP](./images/Composed_MTP3.svg)

#### Referencing Mechanism

The LEA-MTPs attached to the Composed-MTP are registered in its *AttachmentSet* according to [[MTP Specification Part 1]](../98_References/README.md#mtp-specification-part-1). To reference specific elements within the attached LEA-MTPs, the **ContextReference mechanism** is introduced, combining two reference steps ([Figure 4.15](#figure-415-referencing-mechanism-of-a-composed-mtp)):

1. **Context assignment to an LEA-MTP (blue reference):** A new RoleClass *HasExternalMtpContext* is assigned to all objects in the Composed-MTP that need to reference external elements of an attached LEA-MTP. This RoleClass uses the ID-Link mechanism to point to the relevant LEA-MTP in the *AttachmentSet*.

2. **Reference to the MTP element (red reference):** The existing LinkedObject, ID-Link (per [[MTP Specification Part 1]](../98_References/README.md#mtp-specification-part-1)), and CustomSymbols mechanisms — previously used for intra-MTP references — are reused in combination with the context assignment to point to elements in other MTPs. The modeling of these references is unchanged.

##### Figure 4.15: Referencing Mechanism of a Composed-MTP
![Referencing Mechanism of a Composed-MTP](./images/Composed_MTP_Referenzierung.svg)

#### Aspects of a Composed-MTP

A Composed-MTP contains several aspects following the same basic structure as all MTPs ([Figure 4.16](#figure-416-aspects-of-a-composed-mtp)). The entry point is a *ModuleTypePackage* instance hierarchy containing the *Manifest* as the table of contents. Below it is an element of the newly introduced model definition *ComposedModuleTypePackage*, which signals that this is a Composed-MTP and carries the metadata needed for type, version, and instance verification of the choreographed function.

The *Manifest* references the various aspects of the Composed-MTP, each organized in a separate instance hierarchy:

- **Attachment aspect** (mandatory): contains the attached LEA-MTPs and the choreography configuration.
- **Service aspect** (optional): models the Line Interface service control — the Lead Service interface and selected parameter interfaces — using the ContextReference mechanism to reference LEA-MTP elements.
- **ProcessValue aspect** (optional): models selected process value and report value interfaces of the Line Interface using the ContextReference mechanism.
- **HMI aspect** (optional): models the Line HMI display hierarchy. Combination variant 1 uses only the ContextReference mechanism. Variant 2 uses a new model definition **PictureFrame**, which references complete displays from attached LEA-MTPs and places them at a defined size and position within another display. Variants 3 and 4 use a new model definition **ReferencedPicture**, which references displays or display hierarchies from attached LEA-MTPs and inserts them into the Composed-MTP's display hierarchy.

The *ServerAssembly* and *DataAssembly* aspects are not required in the Composed-MTP, as the relevant information is already contained in the LEA-MTPs and accessed via the ContextReference mechanism. Additional aspects (e.g., *Text*, *Alarm*, *Diagnostics*) may be added in the future.

##### Figure 4.16: Aspects of a Composed-MTP
![Aspects of a Composed-MTP](./images/Composed_MTP_Aspekte.svg)

#### Verification Workflows

The type, version, and instance verification workflows defined in [[MTP Specification Part 1]](../98_References/README.md#mtp-specification-part-1) are extended to cover choreographed functions and Composed-MTPs:

**Type and version verification:** Type and version information of the choreographed function is stored in the Composed-MTP. This enables verification that **the correct choreography configuration is loaded** on the LEAs by comparing the stored information against the configuration actually present on the controllers.

**Instance verification:** For each participant role that must be filled in a choreographed Logistics Line, the planned LEA instance is compared against the LEA instance actually installed. This is based on the instance identifier of each LEA and a role ID defined in the Composed-MTP, ensuring that **the correct LEA instances are used in the Logistics Line**.

> **Note:** The MTP-based verification workflows do **not** verify whether a choreography is executable or with which parameters it operates correctly. They only verify that the correct choreography configuration is loaded and the correct LEA instances are installed.

### 4.4 MTP Extensions

The following MTP specification extensions are introduced for the automation of Logistics Lines. [Table 4.3](#table-43-mtp-specification-extensions-for-logistics-line-automation) provides a summary.

##### Table 4.3: MTP Specification Extensions for Logistics Line Automation

<table>
  <tr>
    <th align="left" colspan="4">Interface Definitions (Profile: ModuleTypePackage: ChoreographySet.Base V2.0.0)</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Definition</th>
    <th align="left">Description</th>
    <th align="left">Aspect</th>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC UnionElement</em></td>
    <td align="left">Interface for reading a value with a runtime-selectable data type</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC WritableUnionElement</em></td>
    <td align="left">Interface for writing a value with a runtime-selectable data type</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ChoreographyElement</em></td>
    <td align="left">Base interface for all interfaces required for choreography configuration</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ChoreographyParticipantManager</em></td>
    <td align="left">Interface for configuring and controlling the execution of Configurable Logic</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC CommunicationManager</em></td>
    <td align="left">Base interface for all Configurable Communication configuration interfaces</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC OpcUaClientServerManager</em></td>
    <td align="left">Interface for configuring and controlling OPC UA Client/Server-based Configurable Communication</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <th align="left" colspan="4">Model Definitions</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Definition</th>
    <th align="left">Description</th>
    <th align="left">Aspect</th>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>IH Choreography</em></td>
    <td align="left">Instance hierarchy for organizing all choreography-related models of an MTP</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ChoreographySet</em></td>
    <td align="left">Aspect set organizing all choreography-related model definitions</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ChoreographyParticipant</em></td>
    <td align="left">Model describing an LEA as a choreography participant</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC InputList</em></td>
    <td align="left">Model for the Input-List of an LEA</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC OutputList</em></td>
    <td align="left">Model for the Output-List of an LEA</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC InputElement</em></td>
    <td align="left">Model for an element of the Input-List</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC OutputElement</em></td>
    <td align="left">Model for an element of the Output-List</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC FixedInputElement</em></td>
    <td align="left">Fixed input element hard-coded by the LEA program</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC FixedOutputElement</em></td>
    <td align="left">Fixed output element hard-coded by the LEA program</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ConfigurableInputElement</em></td>
    <td align="left">Input element for reading a value from another LEA</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC ConfigurableOutputElement</em></td>
    <td align="left">Output element for writing a value to another LEA</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">ChoreographySet.Base V2.0.0</td>
    <td align="left"><em>SUC WritableInputElement</em></td>
    <td align="left">Passive input element that can be written by another LEA</td>
    <td align="left">ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">Manifest.Composed V2.0.0</td>
    <td align="left"><em>SUC ComposedModuleTypePackage</em></td>
    <td align="left">Base model for a Composed-MTP; signals a composed type and carries verification metadata</td>
    <td align="left">Manifest</td>
  </tr>
  <tr>
    <td align="left">Manifest.Composed V2.0.0</td>
    <td align="left"><em>AT ComposedTypeRevisionType</em></td>
    <td align="left">Attribute type for version information of a choreographed function</td>
    <td align="left">Manifest</td>
  </tr>
  <tr>
    <td align="left">Manifest.Composed V2.0.0</td>
    <td align="left"><em>RC HasExternalMtpContext</em></td>
    <td align="left">RoleClass indicating that a referenced object originates from an attached LEA-MTP</td>
    <td align="left">Manifest</td>
  </tr>
  <tr>
    <td align="left">HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC PictureFrame</em></td>
    <td align="left">Model for embedding a display from an attached LEA-MTP into another display (display-in-display, Variant 2)</td>
    <td align="left">HMI</td>
  </tr>
  <tr>
    <td align="left">HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC Picture</em> (extension)</td>
    <td align="left">Extension of the existing Picture model to support PictureFrames</td>
    <td align="left">HMI</td>
  </tr>
  <tr>
    <td align="left">HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC SemanticGroup</em> (extension)</td>
    <td align="left">Extension of the existing SemanticGroup model to support PictureFrames</td>
    <td align="left">HMI</td>
  </tr>
  <tr>
    <td align="left">HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC ReferencedPicture</em></td>
    <td align="left">Model for referencing displays or display hierarchies from attached LEA-MTPs into the Composed-MTP display hierarchy (Variants 3 and 4)</td>
    <td align="left">HMI</td>
  </tr>
  <tr>
    <td align="left">HMISet.Composed V2.0.0</td>
    <td align="left"><em>SUC HMISet</em> (extension)</td>
    <td align="left">Extension of the existing HMISet model to support ReferencedPictures</td>
    <td align="left">HMI</td>
  </tr>
  <tr>
    <th align="left" colspan="4">Workflows</th>
  </tr>
  <tr>
    <th align="left">Profile</th>
    <th align="left">Workflow</th>
    <th align="left">Description</th>
    <th align="left">Aspect</th>
  </tr>
  <tr>
    <td align="left">Manifest.Composed V2.0.0</td>
    <td align="left">Type verification</td>
    <td align="left">Verifies the type of the choreography configuration loaded on the LEAs against the type described in the Composed-MTP</td>
    <td align="left">Manifest</td>
  </tr>
  <tr>
    <td align="left">Manifest.Composed V2.0.0</td>
    <td align="left">Version verification</td>
    <td align="left">Verifies the version of the choreography configuration loaded on the LEAs against the version described in the Composed-MTP</td>
    <td align="left">Manifest</td>
  </tr>
  <tr>
    <td align="left">Manifest.Composed V2.0.0</td>
    <td align="left">Instance verification</td>
    <td align="left">Verifies that the LEA instances installed in the Logistics Line match the planned instances specified in the Composed-MTP</td>
    <td align="left">Manifest</td>
  </tr>
</table>

For the choreography-related model definitions, a new library *SUCL MTPChoreographySUCLib* is introduced. For the *RC HasExternalMtpContext*, a new library *RCL MTPRCLib* is introduced.
