## 6.2 Verification

The term *verification* describes, according to [[DIN EN ISO 9000]](../08_References/README.md#din-en-iso-9000-2015), the "confirmation, through the provision of objective evidence, that specified requirements have been fulfilled." It examines, based on identified requirements, whether *artifacts have been developed correctly*.

This section verifies the artifacts presented in [Chapter 3](../03_Logistics_Equipment_Assemblies/03_Logistics_Equipment_Assemblies.md) through [Chapter 5](../05_Logistics_Area/05_Logistics_Area.md) against the requirements defined in [Section 2.6](../02_Modular_Logistics_System/02_Modular_Logistics_System.md#26-automation-requirements). For each requirement, it is described to what extent the presented artifacts fulfill the requirement's acceptance criteria, and the fulfillment of the requirement is then assessed.

#### Artifact 1 — LEA Automation

##### Table 6.7: Verification of Artifact 1 Against Requirements

<table>
  <tr>
    <th align="left">Requirement</th>
    <th align="left">Concept</th>
    <th align="left">Evaluation</th>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LEA-1</strong> — Service-based LEA Automation</td>
    <td align="left">Each LEA exposes exactly one parameterizable MTP service following the CES or SES principle with a uniform state model (<a href="../03_Logistics_Equipment_Assemblies/03-02_Service_Based_Automation.md">Section 3.2</a>).</td>
    <td align="left">Demonstrated in all three evaluation examples. CES operation in BASF, MoProLog, and Emulation; SES operation in MoProLog and Emulation.</td>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LEA-2</strong> — Operator Screen Concept for LEAs</td>
    <td align="left">LEA-specific operator displays support static custom LEA images, dynamic service control elements, and variables with complex data types (<a href="../03_Logistics_Equipment_Assemblies/03-06_Operator_Displays.md">Section 3.6</a>).</td>
    <td align="left">HMI screens implemented all three emulation examples using WinCC Unified.</td>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LEA-3</strong> — Standardized Interfaces for LOL Communication to LEAs</td>
    <td align="left">Uniform OPC UA interfaces for service control, parameterization, and process value exchange are provided via MTP-defined address spaces (<a href="../03_Logistics_Equipment_Assemblies/03-02_Service_Based_Automation.md">Sections 3.2</a>–<a href="../03_Logistics_Equipment_Assemblies/03-05_Process_Values.md">3.5</a>).</td>
    <td align="left">Used in all three evaluation examples for LOL-to-LEA communication. Independent development by different partners in MoProLog confirms vendor neutrality.</td>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LEA-4</strong> — Standardized Information Models for Describing LEA Automation</td>
    <td align="left">All automation-relevant LEA properties are described in MTP files, including extensions for structured and array-based data types (<a href="../03_Logistics_Equipment_Assemblies/03-08_MTP_Extensions.md">Section 3.8</a>, <a href="../07_MTP%20Extensions/07-00_Intro.md">Chapter 7</a>).</td>
    <td align="left">MTP files for all LEAs of the evaluation examples generated and can be found here: 
    <!-- TODO: Link zu MTP-Dateien ergänzen. -->
    </td>
  </tr>
</table>


#### Artifact 2 — Logistics Line Automation

##### Table 6.8: Verification of Artifact 2 Against Requirements

<table>
  <tr>
    <th align="left">Requirement</th>
    <th align="left">Concept</th>
    <th align="left">Evaluation</th>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LL-1</strong> — Choreography-based Association of LEAs Forming a Logistics Line</td>
    <td align="left">LEAs within a Logistics Line are coordinated via a distributed choreography with configurable behavioral rules for procedure, parameter, process value and interlock relations (<a href="../04_Logistics_Line/04-02_Horizontal_Integration.md">Section 4.2</a>).</td>
    <td align="left">Demonstrated in BASF (CES-based line, 3 LEAs) and Emulation (CES-based bag filling line, SES-based octabin filling line).</td>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LL-2</strong> — Standardized Interfaces for Configuring Logistics Lines</td>
    <td align="left">MTP-based configuration interfaces enable a LOL configurator to establish the choreographed coupling (<a href="../04_Logistics_Line/04-02_Horizontal_Integration.md#428-interfaces-for-configuring-horizontal-interaction">Section 4.2.8</a>).</td>
    <td align="left">Choreography configurator successfully loaded configurations onto LEAs in BASF line and PLC-based Emulation.</td>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LL-3</strong> — Integration of Logistics Lines into a Higher-level LOL</td>
    <td align="left">A Line Interface and Line HMI enable vertical integration; access mode management resolves conflicts between LOL control and horizontal choreography (<a href="../04_Logistics_Line/04-03_Vertical_Integration.md">Section 4.3</a>).</td>
    <td align="left">Line HMI and vertical control via Lead Service demonstrated in BASF line and PLC-based Emulation. </td>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LL-4</strong> — Standardized Information Models for Describing the Choreography-based Automation</td>
    <td align="left">Configuration and integration interfaces are described in the ChoreographySet within MTP files (<a href="../04_Logistics_Line/04-04_MTP_Extensions.md">Section 4.4</a>, <a href="../07_MTP%20Extensions/07-07_ChoreographySet.md">Section 7.7</a>).</td>
    <td align="left">MTP files with ChoreographySet used by the choreography configurator in BASF line and PLC-based Emulation. Composed MTPs generated for all Logistics Lines of the evaluation examples. MTPs can be found here:
    <!-- TODO: Link zu MTP-Dateien ergänzen. -->
    </td>
  </tr>
</table>

#### Artifact 3 — Logistics Area Automation

##### Table 6.9: Verification of Artifact 3 Against Requirements

<table>
  <tr>
    <th align="left">Requirement</th>
    <th align="left">Concept</th>
    <th align="left">Evaluation</th>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LA-1</strong> — Standardized Interaction Between LEAs and AGV Systems</td>
    <td align="left">A Transport Management mediates between LEAs and AGV systems via MTP Transport Services. The interaction mechanism supports push and pull demands, all identified transport node types, and both static and dynamic routing (<a href="../05_Logistics_Area/05_Logistics_Area.md">Sections 5.1</a>–<a href="../05_Logistics_Area/05-05_Logistics_Equipment_Assemblies.md">5.5</a>).</td>
    <td align="left">Demonstrated in MoProLog (physical AGV, static and dynamic routing) and PLC-based Emulation (emulated AGV, all transport node types, both routing modes).</td>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LA-2</strong> — Standardized Interface for Coupling of AGV System to LEAs</td>
    <td align="left">TN Blocks in the LEA programs and TN Proxies in the Transport Management provide a uniform OPC UA-based coupling interface (<a href="../05_Logistics_Area/05-05_Logistics_Equipment_Assemblies.md">Section 5.5</a>).</td>
    <td align="left">Coupling interface used in MoProLog and PLC-based Emulation. Independent development of Transport Management and LEA software confirms interface standardization.</td>
  </tr>
  <tr>
    <td align="left"><strong>REQ-LA-3</strong> — Standardized Information Models for Describing Transport-related LEA Information</td>
    <td align="left">Transport-relevant LEA properties are described in a TransportSet within MTP files (<a href="../05_Logistics_Area/05-07_MTP_Extensions.md">Section 5.7</a>, <a href="../07_MTP%20Extensions/07-08_TransportSet.md">Section 7.8</a>).</td>
    <td align="left"> MTPs with TransportSet generated for LEAs of the PLC-based Emulation. MTP files can be found here: 
    <!-- TODO: Link zu MTP-Dateien ergänzen. -->
    </td>
  </tr>
</table>

All eleven requirements are fulfilled by the presented concepts and demonstrated in the evaluation examples.
