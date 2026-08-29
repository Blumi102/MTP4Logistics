## 4.3 Vertical Integration of a Logistics Line into a Logistics Orchestration Layer

### 4.3.1 Line Interface

The Line Interface exposes the functionality of a choreographed Logistics Line to a superordinate LOL. The Logistics Line can be parametrized, controlled, and monitored via this interface as if it was a single MTP service, and should behave accordingly.

The interface of each LEA service according to [Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md#3-mtp-based-automation-of-logistics-equipment-assemblies) consists of the components shown in [Figure 4.8](#figure-48-components-of-an-lea-service-interface). Exactly one *ServiceControl* interface is a mandatory component of every MTP service according to [[PNO Part 4]](../98_References/README.md#pno-2025-part4). It provides access to the service's underlying state machine and its procedures. As optional components, the service interface also contains any number of parameters, report values, and process values, for which interfaces of various data types are defined in [[PNO Part 4]](../98_References/README.md#pno-2025-part4) and in [Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md#3-mtp-based-automation-of-logistics-equipment-assemblies).

##### Figure 4.8: Components of a LEA Service Interface
![Components of a LEA Service Interface](./images/LEA_Schnittstelle.svg)

The Line Interface is a combination of the interfaces of multiple LEA services participating in the choreography. However, not all interface components of the individual LEA services are adopted into the Line Interface. A portion of the LEA service interfaces is controlled by choreography-internal logic and is therefore not accessible from outside. [Figure 4.9](#figure-49-components-of-the-line-interface-of-a-choreographed-logistics-line) shows an example of how a Line Interface can be composed.

##### Figure 4.9: Components of the Line Interface of a Choreographed Logistics Line
![Components of the Line Interface of a Choreographed Logistics Line](./images/Linien_Schnittstelle.svg)

#### Service and procedure interfaces

Every choreography has a leading service — referred to as **Lead Service** in [[Stu26]](../98_References/README.md#stutz-2026) — which provides its state machine as the state machine of the choreography. This means the state of the Lead Service reflects the state of the entire choreography. The Lead Service also accepts commands for the choreography (e.g., start, stop) and enables procedure selection. As Lead Service, one of the LEA services already participating in the choreography can be used (**Internal Lead** in [[Stu26]](../98_References/README.md#stutz-2026)) or a separate service is included solely as Lead Service in the choreography (**External Lead** in [[Stu26]](../98_References/README.md#stutz-2026)). For Logistics Lines, an External Lead is preferred because, due to the line structure, most functions (e.g., startup sequences) are initiated at one LEA and end at another (e.g., initiation at the last LEA and orderly startup through to the first LEA). The External Lead can run on one of the LEA controllers or on an external system and must follow the concepts described in [Section 4.2](04-02_Horizontal_Integration.md#42-horizontal-integration-of-logistics-equipment-assemblies-into-a-logistics-line).

The *ServiceControl* interface of the Lead Service is adopted 1:1 as the *ServiceControl* component of the Line Interface ([Figure 4.9](#figure-49-components-of-the-line-interface-of-a-choreographed-logistics-line), "ServiceControl3"). The procedures of the Lead Service and their *ProcedureHealthView* interfaces are also adopted into the Line Interface. The choreography logic must relay commands and procedure settings at the *ServiceControl* interface to all other LEA services — referred to as **Follower Services** in [[Stu26]](../98_References/README.md#stutz-2026) — such that the choreography fulfills its intended function.

Since the Lead Service must be controllable by LOL automation or by an operator, it operates in *AutomaticExternal* or *Operator* mode according to [[PNO Part 4]](../98_References/README.md#pno-2025-part4). All Follower Services are controlled exclusively by LEA-internal logic (based on Configurable Logic) and therefore operate in *AutomaticInternal* mode. Operating modes are configured via behavioral rules in the Configurable Logic.

#### Parameter, report value, and process value interfaces

The parameters, report values, and process values of the Line Interface consist of selected parameter, report value, and process value interfaces from the LEAs participating in the choreography that are relevant for the overall functionality of the choreographed Logistics Line ([Figure 4.9](#figure-49-components-of-the-line-interface-of-a-choreographed-logistics-line), "Param1.1", "Param1.3", "RV2.2", and "PV3.2"). These interface components are adopted 1:1 into the Line Interface and can be set or further processed from outside the choreography. All remaining parameter, report value, and process value interfaces are set and processed choreography-internally as needed.

All parameters available at the Line Interface must be controllable by automated order management or an operator. They therefore operate in *AutomaticExternal* or *Operator* mode according to [[PNO Part 4]](../98_References/README.md#pno-2025-part4). All parameters that are exclusively set and processed choreography-internally are controlled by LEA-internal logic (based on Configurable Logic) and therefore operate in *AutomaticInternal* mode. The configuration of operating modes for parameters is performed via behavioral rules in the Configurable Logic.

### 4.3.2 Line HMI

For visualization and manual operation of the Logistics Line, the operator displays of the individual LEAs are combined into a Line HMI. Four different variants for this combination are distinguished according to [Table 4.2](#table-42-variants-for-combining-lea-operator-displays-into-a-line-hmi), which can also be combined with each other. To illustrate these variants, [Figure 4.10](#figure-410-individual-operator-displays-of-three-leas) shows the operator displays of three example LEAs, and the subsequent [Figures 4.11](#figure-411-line-hmi-combination-variant-1) through [4.13](#figure-413-line-hmi-combination-variants-3-and-4) show the resulting Line HMIs using the four presented combination variants.

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

### 4.3.3 Composed MTP

For automated vertical integration of a choreographed Logistics Line into a LOL, a shared MTP for the line — the **Composed MTP** — is introduced. It describes the Line Interface and the Line HMI. When a Composed MTP is imported, only the information relevant to the line is loaded into the LOL.

### 4.3.4 Re-Modeling vs. Referencing

The Line Interface and Line HMI to be modeled in the Composed MTP are composed of interface and model elements from the LEAs participating in the Logistics Line. These are already modeled in the LEA MTPs and can be reused during Composed MTP modeling. Two possible approaches exist for this reuse, which are described and evaluated in [Table 4.3](#table-43-evaluation-of-modeling-approaches-for-composed-mtps).

##### Table 4.3: Evaluation of Modeling Approaches for Composed MTPs

<table>
  <tr>
    <th align="left" colspan="2"><strong>1) Re-modeling</strong></th>
  </tr>
  <tr>
    <td align="left" colspan="2">The models and interfaces of the LEA MTPs relevant for the Line Interface and Line HMI are re-modeled in the Composed MTP model. The original LEA MTPs are not directly used for the description of the choreographed type.</td>
  </tr>
  <tr>
    <td align="left">Advantages</td>
    <td align="left">The Composed MTP closely resembles the MTP of a single LEA and can be integrated into a superordinate LOL in a very similar manner.</td>
  </tr>
  <tr>
    <td align="left">Disadvantages</td>
    <td align="left">The modeling of the Composed MTP duplicates the modeling of the LEA MTPs. Mechanisms are required to ensure consistency between the LEA MTPs and the Composed MTP. Changes require updates in both the LEA MTP and the Composed MTP.</td>
  </tr>
  <tr>
    <th align="left" colspan="2"><strong>2) Referencing</strong></th>
  </tr>
  <tr>
    <td align="left" colspan="2">The LEA MTPs are made accessible to the Composed MTP. From the Composed MTP model, models and interfaces of the LEA MTPs are referenced wherever possible. The LEA MTPs thus serve as the basis for the description of the choreographed type.</td>
  </tr>
  <tr>
    <td align="left">Advantages</td>
    <td align="left">Only the Logistics-Line-specific content is modeled in the Composed MTP; no duplicate modeling compared to the LEA MTPs. Additionally, the integrity of the referenced LEA MTP models and interfaces can be verified via the LEA MTP package signature.</td>
  </tr>
  <tr>
    <td align="left">Disadvantages</td>
    <td align="left">The referencing mechanism required for this approach is a distinctive feature of Composed MTPs compared to MTPs of individual LEAs. A LOL that can integrate LEA MTPs cannot automatically integrate Composed MTPs. Special integration mechanisms are required to resolve the references.</td>
  </tr>
</table>

> **Design decision:** **Referencing** is chosen as the modeling approach for Composed MTPs. The current MTP specification allows only one OPC UA server per MTP [[PNO Part 5.1]](../98_References/README.md#pno-2025-part51). A Composed MTP must retrieve information from multiple OPC UA servers of multiple LEAs, so special integration mechanisms beyond those for LEA MTPs are required regardless. The advantages of referencing therefore outweigh its disadvantages.

### 4.3.5 Structure of a Composed MTP

[Figure 4.14](#figure-414-basic-structure-of-a-composed-mtp) shows the basic structure of a Composed MTP. As described above, the MTP files of the LEAs participating in the Logistics Line form the modeling basis, as they already contain a large portion of the MTP components to be modeled. To reference MTP components of the LEA MTPs, these are added to the Composed MTP as attachments ([Figure 4.14](#figure-414-basic-structure-of-a-composed-mtp), "LEA MTPs"). From these MTPs, the components necessary for describing the Line Interface and the Line HMI must be selected and combined in a suitable manner. For this purpose, MTP-based semantic models in the individual aspects of the Composed MTP ([Figure 4.14](#figure-414-basic-structure-of-a-composed-mtp), "Semantic Models") are used, which resemble the semantic models of a LEA MTP.

##### Figure 4.14: Basic Structure of a Composed MTP
![Basic Structure of a Composed MTP](./images/Composed_MTP3.svg)

### 4.3.6 Referencing Mechanism

The LEA MTPs are stored in a separate folder "MTPs" in the attachment of the Composed MTP and registered in its *AttachmentSet* according to the mechanisms from [[PNO Part 1]](../98_References/README.md#pno-2025-part1) ([Figure 4.15](#figure-415-referencing-mechanism-of-a-composed-mtp), green reference). An *AttachmentGroup* is created for the LEA MTPs. It contains one instance of the *IC AttachmentReference* for each MTP, referencing the respective MTP file. These *AttachmentReferences* simultaneously describe the participant roles that must be filled by LEA instances to implement the choreographed function. The names of the *AttachmentReferences* correspond to *RoleIdents* that are also used for instance verification of choreographed functions ([Section 7.1.3](../07_MTP%20Extensions/07-01_Manifest.md#713-workflows)). According to [[PNO Part 1]](../98_References/README.md#pno-2025-part1), the attribute *refUri* contains the path to the MTP file. The attributes *DocumentType* and *MIMEType* specify the type of the attached document — for Composed MTPs, *DocumentType* is always set to "ModuleTypePackage" and *MIMEType* to "application/mtp".

<!-- TODO: Abbildung anpassen, inkl. AML-Modellierung -->
##### Figure 4.15: Referencing Mechanism of a Composed MTP
![Referencing Mechanism of a Composed MTP](./images/Composed_MTP_Referenzierung.svg)

To reference specific components of the attached LEA MTPs, two references are required as shown in [Figure 4.15](#figure-415-referencing-mechanism-of-a-composed-mtp):

**1) Context assignment to a LEA MTP:** First, a reference is made to the MTP file containing the MTP component to be referenced (external context). The *RC HasExternalMtpContext* is assigned to every object of the Composed MTP that references external objects of an attached LEA MTP. The *RC HasExternalMtpContext* uses the ID-Link mechanism. It provides a variable *ContextLink* of the *AT IDLinkAttributeType*, which references the *AttachmentReference* of the LEA MTP containing the referenced object ([Figure 4.15](#figure-415-referencing-mechanism-of-a-composed-mtp), blue reference). This context assignment is necessary because the referencing mechanisms described under point 2) are only guaranteed to be unique within a single MTP. Uniqueness of the GUIDs used is not ensured across MTP boundaries, and the LEA MTPs must not be modified.

**2) Reference to the MTP component:** The LinkedObject, ID-Link, or CustomSymbols mechanisms are used to reference the MTP component ([Figure 4.15](#figure-415-referencing-mechanism-of-a-composed-mtp), red reference). The LinkedObject mechanism relies on referencing via identical *RefID* attribute values. The ID-Link mechanism uses a variable of the *AT IDLinkAttributeType* that references the *ObjectID* of another AutomationML object. The CustomSymbols mechanism serves for referencing user-defined static HMI objects. In contrast to their previous use, these mechanisms are now also used for referencing external MTP components. However, their modeling in the Composed MTP does not differ from the existing modeling.

The referencing mechanism formed by the previous point 1) and 2) is referred to as the **ContextReference mechanism** in the following.

### 4.3.7 Aspects of a Composed MTP

A Composed MTP contains several aspects following the same basic structure as all MTPs ([Figure 4.16](#figure-416-aspects-of-a-composed-mtp)). The entry point is a *ModuleTypePackage* instance hierarchy containing the *Manifest* as the table of contents. Below it is an element of the newly introduced model definition *ComposedModuleTypePackage*, which signals that this is a Composed MTP and carries the metadata needed for type, version, and instance verification of the choreographed function.

The *Manifest* references the various aspects of the Composed MTP, each organized in a separate instance hierarchy:

- **Attachment aspect** (mandatory): contains the attached LEA MTPs and the choreography configuration.
- **Service aspect** (optional): models the Line Interface — the Lead Service *ServiceControl* interface and selected parameter interfaces — using the ContextReference mechanism to reference LEA MTP elements.
- **ProcessValue aspect** (optional): models selected process value and report value interfaces of the Line Interface using the ContextReference mechanism.
- **HMI aspect** (optional): models the Line HMI display hierarchy. Combination variant 1 uses only the ContextReference mechanism. Variant 2 uses a new model definition **PictureFrame**, which references complete displays from attached LEA MTPs and places them at a defined size and position within another display. Variants 3 and 4 use a new model definition **ReferencedPicture**, which references displays or display hierarchies from attached LEA MTPs and inserts them into the Composed MTP's display hierarchy.

The *ServerAssembly* and *DataAssembly* aspects are not required in the Composed MTP, as the relevant information is already contained in the LEA MTPs and is accessed via the ContextReference mechanism. Additional aspects (e.g., *Text*, *Alarm*, *Diagnostics*) may be added in the future.

##### Figure 4.16: Aspects of a Composed MTP
![Aspects of a Composed MTP](./images/Composed_MTP_Aspekte.svg)

#### Manifest

[Figure 4.17](#figure-417-structure-of-the-manifest-of-a-composed-mtp) shows the structure of the *Manifest* of a Composed MTP. The *Manifest* is organized under a *ModuleTypePackage* instance hierarchy according to [[PNO Part 1]](../98_References/README.md#pno-2025-part1). Below it, an instance of the newly specified *SUC ComposedModuleTypePackage* signals that this is a Composed MTP and contains the information necessary for type, version, and instance verification of composed functions. Under this instance, instances for all aspects contained in the Composed MTP are organized, each referencing its corresponding instance hierarchy via an *IC AspectSetReference*.

##### Figure 4.17: Structure of the Manifest of a Composed MTP
![Structure of the Manifest of a Composed MTP](./images/Composed_MTP_Manifest.png)

#### ServiceSet

[Figure 4.18](#figure-418-structure-of-the-serviceset-of-a-composed-mtp) shows the structure of the *ServiceSet* of a Composed MTP. This aspect semantically describes the components of the Line Interface. A service for the overall functionality of the Logistics Line is created as an instance of the *SUC Service* according to [[PNO Part 4]](../98_References/README.md#pno-2025-part4). Below it, all procedures available at the Logistics Line are modeled as instances of the *SUC Procedure*. These procedures are assigned the procedure parameters, report values, and process values present at the Line Interface as instances of the *SUC ProcedureParameter*, *SUC ReportValue*, *SUC ProcessValueIn*, or *SUC ProcessValueOut*. In addition to the procedures, all selected configuration parameters are modeled below the *Service* as instances of the *SUC ConfigurationParameter*. To enable communication with the Line Interface, the corresponding *DataAssemblies* from the LEA MTPs are assigned to this model. Based on these, all communication-relevant information can be obtained from the *ServerAssemblySets* of the LEA MTPs. The *DataAssemblies* are referenced using the ContextReference mechanism in combination with the LinkedObject mechanism.

##### Figure 4.18: Structure of the ServiceSet of a Composed MTP
![Structure of the ServiceSet of a Composed MTP](./images/Composed_MTP_ServiceSet.png)

#### ProcessValueSet

[Figure 4.19](#figure-419-structure-of-the-processvalueset-of-a-composed-mtp) shows the structure of the *ProcessValueSet* of a Composed MTP. This aspect semantically describes the process values of the Line Interface. All process values selected for the Line Interface are modeled as instances of the *SUC ProcessValueIn* or *SUC ProcessValueOut*. This enables a semantic description of the process values. As with the *ServiceSet* components, the corresponding *DataAssemblies* from the LEA MTPs are referenced using the ContextReference mechanism in combination with the LinkedObject mechanism.

##### Figure 4.19: Structure of the ProcessValueSet of a Composed MTP
![Structure of the ProcessValueSet of a Composed MTP](./images/Composed_MTP_ProcessValueSet.png)

#### HMISet

[Figure 4.20](#figure-420-modeling-of-a-line-hmi-in-the-hmiset-and-attachmentset-of-a-composed-mtp) shows the modeling of a Line HMI in the *HMISet* and *AttachmentSet* of a Composed MTP. This aspect semantically describes the components of the display hierarchy of the Logistics Line. A Line HMI can be modeled as an instance of the *SUC Picture* according to [[PNO Part 2]](../98_References/README.md#pno-2025-part2). This contains subordinate display elements following the conventions from [Chapter 3](../03_Logistics_Equipment_Assemblies_NEW/03_Logistics_Equipment_Assemblies.md#3-mtp-based-automation-of-logistics-equipment-assemblies). These can be display objects from the MTPs of the individual LEAs or new static display elements representing the specific characteristics of the Logistics Line. To reference the corresponding *DataAssemblies* of the LEA MTPs for dynamic display objects, the ContextReference mechanism in combination with the LinkedObject mechanism is used. To reference CustomSymbols from the LEA MTPs, the ContextReference mechanism in combination with the CustomSymbols mechanism is used.

Complete LEA displays can also be integrated into the Line HMI. For this purpose, the newly introduced *SUC PictureFrame* is used. It employs the ContextReference mechanism in combination with the ID-Link mechanism and provides size and position information for the *PictureFrame*, so it can be placed on a Line HMI display similarly to a *VisualObject* according to [[PNO Part 2]](../98_References/README.md#pno-2025-part2).

In addition to the Line HMI, the *HMISet* instance hierarchy can contain references to displays of the individual LEAs. For this purpose, the newly introduced *SUC ReferencedPicture* is used. It employs the ContextReference mechanism in combination with the ID-Link mechanism and enables inserting displays or entire display hierarchies from the LEA MTPs into the Composed MTP's display hierarchy. To **insert a single display**, the *ReferencedPicture* references the display to be inserted via the ID-Link mechanism. To **insert an entire display hierarchy**, the ID-Link reference is left empty — in this case, the complete display hierarchy of the referenced MTP is inserted at the position of the *ReferencedPicture*.

##### Figure 4.20: Modeling of a Line HMI in the HMISet and AttachmentSet of a Composed MTP
![Modeling of a Line HMI in the HMISet and AttachmentSet of a Composed MTP](./images/Composed_MTP_HMISet.png)

#### AttachmentSet

[Figure 4.21](#figure-421-structure-of-the-attachmentset-of-a-composed-mtp) shows the structure of the *AttachmentSet* of a Composed MTP. This aspect semantically describes the attachments of the Composed MTP. The *AttachmentSet* instance hierarchy contains all LEA MTPs attached to the Composed MTP, organized under a common *AttachmentGroup*. Additionally, the choreography configuration of the Logistics Line is stored in the attachment of the Composed MTP, so it can be loaded onto the LEAs during commissioning. Further attachments can include, for example, CustomSymbols used in the Line HMI or other line-specific documents.

##### Figure 4.21: Structure of the AttachmentSet of a Composed MTP
![Structure of the AttachmentSet of a Composed MTP](./images/Composed_MTP_AttachmentSet.png)

### 4.3.8 Verification Workflows

In [[PNO Part 1]](../98_References/README.md#pno-2025-part1) type, version, and instance verification workflows are described. In this work, these workflows are extended to cover the verification of choreographed functions and Composed MTPs:

**Type and version verification:** Type and version information of the choreographed function is stored in the Composed MTP. This enables verification that **the correct choreography configuration is loaded** on the LEAs by comparing the stored information against the configuration actually present on the controllers.

**Instance verification:** For each participant role that must be filled in a choreographed Logistics Line, the planned LEA instance is compared against the LEA instance actually installed. This is based on the instance identifier of each LEA and a role ID defined in the Composed MTP, ensuring that **the correct LEA instances are used in the Logistics Line**.

> **Note:** The MTP-based verification workflows do **not** verify whether a choreography is executable or with which parameters it operates correctly. They only verify that the correct choreography configuration is loaded and the correct LEA instances are installed.

For further details on the verification workflows please refer to [Section 7.1.3](../07_MTP%20Extensions/07-01_Manifest.md#713-workflows).
