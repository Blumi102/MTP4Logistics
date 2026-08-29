### 4.2 Horizontal Integration of Logistics Equipment Assemblies into a Logistics Line

#### 4.2.1 Application Example

[Figure 4.1](#figure-41-application-example-of-a-choreographed-logistics-line-with-three-leas) shows an example Logistics Line for bag filling and palletizing, consisting of three LEAs: a form-fill-seal machine (FFS), a conveyor (CONV), and a layer palletizer (PAL). Four types of relations between the LEAs implement the choreography-based horizontal control:

- **Parametrizing relations:** Parameters required by one LEA are observed from another. For example, the FFS reads the target bag count from the PAL and applies it to its own parameters ([Figure 4.1](#figure-41-application-example-of-a-choreographed-logistics-line-with-three-leas), (1)).
- **Procedural relations:** Service state transitions of one LEA trigger state transitions in another. For example, once the PAL service reaches EXECUTE, the CONV starts its own service ([Figure 4.1](#figure-41-application-example-of-a-choreographed-logistics-line-with-three-leas), (2)). Complex logic is also possible: if any LEA service enters STOPPED, all other services do likewise (logical OR).
- **Interlocking relations:** Clearance signals are continuously passed from downstream to upstream LEAs as MTP process values, ensuring that a logistics object may only enter a LEA when the latter is ready ([Figure 4.1](#figure-41-application-example-of-a-choreographed-logistics-line-with-three-leas), (3)).
- **Regulating relations:** Production speeds of LEAs can be mutually adapted, e.g., the working speed of the LEAs of a Logistics Line can be adjusted to each other.
- **Constants:** Constants can also be set choreography-based. These are used, for example, to define operating modes of LEA services or to set constant parameters.

##### Figure 4.1: Application Example of a Choreographed Logistics Line with Three LEAs
![Application Example of a Choreographed Logistics Line with Three LEAs](./images/Beispiel_Linie_Interaktionen.svg)

#### 4.2.2 System Architecture of a Choreographed Logistics Line

The technical implementation of the principle described in [Section 4.2.1](#421-application-example) follows the choreography concept from [[SFB+21]](../98_References/README.md#stutz-et-al-2021) and [[Stu26]](../98_References/README.md#stutz-2026). [Figure 4.2](#figure-42-abstract-system-architecture-of-a-choreographed-logistics-line) shows the basic architecture of a choreographed logistics line. Each LEA controller provides the execution context for an MTP service and the necessary base functionality for data processing and communication to participate in a choreography — referred to as an **Active Choreography Participant** in [[Stu26]](../98_References/README.md#stutz-2026). Each LEA controller contains a service implemented by the LEA manufacturer according to [Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md#3-mtp-based-automation-of-logistics-equipment-assemblies), which represents the **Native Control Program** as defined in [[Stu26]](../98_References/README.md#stutz-2026). To implement the relations between the LEAs described in [Section 4.2.1](#421-application-example), this service is enabled to observe variables of other LEAs' services within the choreography and to behave according to their values. In [[Stu26]](../98_References/README.md#stutz-2026) internal relations (within a single LEA) and external relations (between different LEAs) are distinguished. The interactions between the LEAs of a logistics line require only external relations, which are implemented through configurable communication mechanisms — referred to as **Configurable Communication** in [[Stu26]](../98_References/README.md#stutz-2026). Additionally, each LEA contains internally configured behavioral rules that describe how the LEA should react to the signals provided by other LEAs — referred to as **Configurable Logic** in [[Stu26]](../98_References/README.md#stutz-2026).

##### Figure 4.2: Abstract System Architecture of a Choreographed Logistics Line
![Abstract System Architecture of a Choreographed Logistics Line](./images/Choreo_Abstrakte_Architektur.svg)

#### 4.2.3 Architecture of a LEA as a Choreography Participant

[Figure 4.3](#figure-43-architecture-of-an-lea-as-a-choreography-participant) shows the basic architecture of an Active Choreography Participant (hereafter referred to as **Choreography Participant**) according to [[Stu26]](../98_References/README.md#stutz-2026). Every LEA must follow this architecture to participate in a choreography. Each LEA controller contains a LEA service according to [Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md#3-mtp-based-automation-of-logistics-equipment-assemblies), which is enabled to participate in a choreography through additional software components. For this purpose, [[Stu26]](../98_References/README.md#stutz-2026) defines the design patterns **Configurable Logic** and **Configurable Communication**.

##### Figure 4.3: Architecture of a LEA as a Choreography Participant
![Architecture of a LEA as a Choreography Participant](./images/Architektur_ChoreoParticipant_2.svg)

#### 4.2.4 Configurable Logic

The Configurable Logic components (green in [Figure 4.3](#figure-43-architecture-of-an-lea-as-a-choreography-participant)) enable configurable processing of available information, which can originate from within the LEA or from other LEAs. Outputs of the LEA service serve as LEA-internal inputs of the Configurable Logic, managed in an **Input List**. Additionally, information from other LEAs is managed as LEA-external inputs in the Input List. The information in the Input List can be processed by configurable functions managed in a **Logic List**. The resulting outputs of the Configurable Logic, managed in an **Output List**, are fed back LEA-internally as inputs to the LEA service, where they can trigger state transitions or changes to process values, parameters, or report values. Furthermore, information managed in the Output List can be made available to other LEAs as LEA-external inputs. [Figure 4.4](#figure-44-components-of-the-configurable-logic-software-pattern) shows the components of the design pattern *Configurable Logic* according to [[Stu26]](../98_References/README.md#stutz-2026).

##### Figure 4.4: Components of the Configurable Logic Software Pattern
![Components of the Configurable Logic Software Pattern](./images/Software_Pattern_Konfigurierbare_Logik.drawio.png)

The central *ConfigurableLogic* component controls the execution of the Configurable Logic. It has access to the Input, Logic, and Output List. During execution, values are read from the Input List, processing is applied, and results are written to the Output List. For a more detailed description of this information model and the operation of the *ConfigurableLogic* please refer to [[Stu26]](../98_References/README.md#stutz-2026). This work also introduces the necessary data types and enumerations that describe the information model stored in the three lists.

#### 4.2.5 Configurable Communication

The Configurable Communication components (blue in [Figure 4.3](#figure-43-architecture-of-an-lea-as-a-choreography-participant)) provide configurable data exchange between LEAs within a choreography. The goal is that each LEA receives the LEA-external information it requires for executing the processing functions configured in its Logic List. To enable communication between LEAs from different manufacturers, a standardized communication technology is used. Consistent with existing concepts in the MTP environment, this work employs OPC UA Client/Server. For this communication technology, [[Stu26]](../98_References/README.md#stutz-2026) provides two communication variants — active reading and active writing. In the case of active reading, information is read from another LEA's Input List and transferred into the local Input List. In the case of active writing, information from the local Output List is written into another LEA's Input List. Additionally, active writing can be used according to [[Stu26]](../98_References/README.md#stutz-2026) and [[SFB+23]](../98_References/README.md#stutz-et-al-2023) to integrate non-choreography-enabled equipment via decentralized orchestration. To support all these variants, this work specifies MTP concepts for both active reading and active writing. However, as analyzed in [[Stu26]](../98_References/README.md#stutz-2026), the active reading variant is recommended. Therefore, this variant is particularly focused and also implemented and evaluated as part of the evaluation ([Chapter 6](../06_Application_Examples/06-00_Intro.md)). [Figure 4.5](#figure-45-components-of-the-configurable-communication-software-pattern) shows the components of the design pattern *Configurable Communication* according to [[Stu26]](../98_References/README.md#stutz-2026).

##### Figure 4.5: Components of the Configurable Communication Software Pattern
![Components of the Configurable Communication Software Pattern](./images/Software_Pattern_Konfigurierbare_Kommunikation_Übersicht.drawio.png)

The central *OpcUaClientServerManager* component manages and executes the Configurable Communication. It manages components for configuring and executing OPC UA connections (*UaConnections*) between participants as well as, depending on the communication variant, components for configuring and executing read and/or write operations (*UaReaders* and *UaWriters*, respectively). It also has access to the Input and Output Lists. For the active reading variant, configured *UaReaders* read values from other LEAs and transfer them into the local Input List. In the case of active writing, a *ValueList* additionally serves as a passive input channel that other LEAs can write to via corresponding *UaWriters*. These values are then forwarded to specific Input List indices. For a more detailed description of this information model and the operation of the components please refer to [[Stu26]](../98_References/README.md#stutz-2026). This work also introduces the necessary data types and enumerations that describe the information model of the Configurable Communication.

#### 4.2.6 UnionType

All information exchanged between the LEAs of a logistics line carries the data type *UnionType* according to the concepts in [[Stu26]](../98_References/README.md#stutz-2026), shown in [Figure 4.6](#figure-46-uniontype-data-type). The distinctive feature of this type is that it holds (currently five) variables of different data types, of which one is selected for use. This allows the data type to be determined at runtime even on controller systems that require the data type to be defined at engineering time.

##### Figure 4.6: UnionType Data Type
![UnionType Data Type](./images/UnionType.drawio.png)

#### 4.2.7 Semantic Models for LEA Integration into a Choreography Configurator

For a Choreography Configurator in the LOL, the contents of the Input and Output Lists of each LEA must be semantically identifiable. [Figure 4.7](#figure-47-structure-of-the-input-and-output-lists-of-a-lea) shows the basic structure of these lists schematically. Within these lists, fixed, configurable, and writable elements can be distinguished:

- **Fixed elements** are hard-coded by the LEA program and immutable. In the case of the Input List, these are fixed outputs of the LEA service (e.g., its state or current procedure); in the case of the Output List, these are fixed inputs to the LEA service (e.g., service commands or procedure selection).
- **Configurable elements** are placeholders for values to be read from other LEAs (in the case of the Input List) or written to other LEAs (in the case of the Output List).
- **Writable elements** are placeholders for values that are written from other LEAs into the Input List.

During LEA engineering, a fixed number of configurable and writable elements is defined, which can be connected to concrete relations with other LEAs during choreography configuration.

##### Figure 4.7: Structure of the Input and Output Lists of a LEA
![Structure of the Input and Output Lists of a LEA](./images/InOutputListen.svg)

To represent these contents in an MTP, the model definition *ChoreographyParticipant* is introduced to identify a LEA as a potential choreography participant. The MTP model definitions *InputList* and *OutputList* are introduced to represent the Input and Output Lists of the LEA, organizing corresponding *InputElements* and *OutputElements*. According to the distinction between fixed, configurable, and writable elements, the concrete model definitions of Input and Output elements shown in [Table 4.1](#table-41-element-types-in-the-input-and-output-lists-of-an-lea) are introduced. The corresponding interface definitions are described in the following [Section 4.2.8](#428-interfaces-for-configuring-horizontal-interaction).

##### Table 4.1: Element Types in the Input and Output Lists of a LEA

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

#### 4.2.8 Interfaces for Configuring Horizontal Interaction

MTP-based interfaces for configuring the Configurable Logic and the Configurable Communication are required to download a choreography configuration from a Choreography Configurator into the LEA controller.

#### Configurable Logic

[Section 4.2.3](#423-architecture-of-an-lea-as-a-choreography-participant) introduces the *ConfigurableLogic* component for controlling the execution of the Configurable Logic according to [[Stu26]](../98_References/README.md#stutz-2026). To interact with this component, the MTP interface definition *ChoreographyParticipantManager* is specified in this work. The *ChoreographyParticipantManager* interface can also be embedded as a dynamic HMI element in the LEA operator display. It provides index-based access to the elements of the Input, Logic, and Output Lists, and supports executing, stopping, and resetting a configuration. A configuration (*PreparedConfiguration*) can first be fully prepared and only activated once it is complete. During the configuration phase, a different configuration (*ActiveConfiguration*) can remain active. Both configurations can be displayed via the *ChoreographyParticipantManager* interface, but only the *PreparedConfiguration* can be edited.

#### Configurable Communication

[Section 4.2.3](#423-architecture-of-an-lea-as-a-choreography-participant) introduces the *OpcUaClientServerManager* component for controlling the execution of the Configurable Communication based on OPC UA Client/Server according to [[Stu26]](../98_References/README.md#stutz-2026). To interact with this component, a same-named MTP interface definition *OpcUaClientServerManager* is specified in this work. The *OpcUaClientServerManager* interface can also be embedded as a dynamic HMI element in the LEA operator display. It provides index-based access to lists of connections (*UaConnections*), read operations (*UaReaders*), write operations (*UaWriters*), and writable value fields (*ValueFields*). For each connection, configuration variables as well as variables for connection establishment and teardown are provided, based on the *UA\_Connect* and *UA\_Disconnect* interfaces of the PLCopen specification [[OPC 30001]](../98_References/README.md#opc-30001). For read and write operations, variables for assigning the operation to a connection and for configuring the variables to be read or written are provided, based on the *UA\_ReadList* and *UA\_WriteList* interfaces of the PLCopen specification [[OPC 30001]](../98_References/README.md#opc-30001). Each read operation is mapped to an Input List index to which the read value is transferred. Each write operation is mapped to an Output List index from which the value to be written is read. For each value field, variables for configuring the data type and displaying the current value are provided. As with the *ChoreographyParticipantManager*, a *PreparedConfiguration* and an *ActiveConfiguration* are distinguished for all configurations of connections, read and write operations, and value fields.

[Section 4.2.6](#426-uniontype) introduces the *UnionType* data type for transmitting values with runtime-definable data types according to [[Stu26]](../98_References/README.md#stutz-2026). To implement this data type, the MTP interface definition *UnionElement* is introduced, which enables displaying a value of various data types. The active writing communication variant additionally requires writing to a value with a definable data type. This is enabled by the MTP interface definition *WritableUnionElement*.

> **Note on vendor-neutral information exchange:** The Configurable Communication design pattern fundamentally enables the exchange of all information available in a LEA with other LEAs of a choreographed Logistics Line. However, to enable vendor-neutral interaction between LEAs, variables of the standardized MTP-based LEA interfaces according to [Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md#3-mtp-based-automation-of-logistics-equipment-assemblies) should be exchanged wherever possible. An exception is the interface of an External Lead (see [Section 4.3.1](04-03_Vertical_Integration.md#431-line-interface)), for which DoRequest and DoneReply relations are recommended according to [[Stu26]](../98_References/README.md#stutz-2026), enabling different start and end of a choreography relation across multiple LEA services.

#### 4.2.9 ChoreographySet

To represent the model and interface definitions introduced in [Section 4.2.7](#427-semantic-models-for-lea-integration-into-a-choreography-configurator) and [Section 4.2.8](#428-interfaces-for-configuring-horizontal-interaction), a new MTP aspect *ChoreographySet* is introduced. This section provides an overview of this aspect; a detailed description is given in the [Section 7.7](../07_MTP%20Extensions/07-07_ChoreographySet.md#77-mtp-specification-of-the-choreographyset). For integration into a Choreography Configurator, the Input and Output Lists of a LEA are modeled with the elements described in [Section 4.2.7](#427-semantic-models-for-lea-integration-into-a-choreography-configurator). All Input and Output elements of types *FixedInputElement*, *FixedOutputElement*, *ConfigurableInputElement*, and *ConfigurableOutputElement* are assigned a *UnionElement* interface. Each *WritableInputElement* is assigned a *WritableUnionElement* interface. Configurable Communication is configured via an *OpcUaClientServerManager* interface. This interface contains one *UaReader* per *ConfigurableInputElement* and one *UaWriter* per *ConfigurableOutputElement*, which can be configured according to the choreography configuration to be loaded. Additionally, this interface contains one *ValueField* per *WritableInputElement*, which other LEAs can write to. Configurable Logic is configured via a *ChoreographyParticipantManager* interface, which is assigned to the *ChoreographyParticipant* model definition. The use of the newly introduced MTP interface and model definitions for implementing choreography relations is described in the [Section 4.5.4](04-05_Application_Example_BagFillingLine.md#454-implementation-of-choreography-relations-using-the-models-and-interfaces-of-the-choreographyset) for the principles of active reading and active writing using OPC UA Client/Server.
