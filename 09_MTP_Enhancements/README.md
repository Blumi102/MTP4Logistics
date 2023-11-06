[< Previous](../08_Logistics_Orchestration_Layer/README.md) | [Home](../README.md) | [Next >](../10_Logistics_Aspect/README.md)

## 9 Enhancements of the Module Type Package Concept

The Module Type Package concept has originally been developed for the process industry. For a purposeful application in the context of production-related logistics, a further development is necessary, which is presented in the following sections. In course of this development, care has been taken not to change the state machine or any other existing constructs (interface definitions, model definitions and mechanisms) of the MTP concept. However, reinterpretations and reasonable specifications of new MTP constructs have been developed. This section summarizes the identified and partly already implemented reinterpretations and further developments structured according to the different sheets of VDI/VDE/NAMUR 2658 [19].

Necessary new model and interface definitions are specified in [Sections 10](../10_Logistics_Aspect/README.md), [11](../11_Choreography_Aspect/README.md) and [12](../12_Transport_Aspect/README.md). For this, the notations used in the MTP guideline are applied. The modelling of the contents of an MTP follows IEC 62714-1:2018 [20] (AutomationML standard). The newly specified model and interface definitions are marked with a red border in the corresponding figures.

### 9.1	VDI/VDE/NAMUR 2658-1

In the VDI/VDE/NAMUR 2658-1 [8] (also referred to as Sheet 1) an overview is given of the basic concepts of the Module Type Package, on which all other sheets are based. In the context of production-related logistics, the new parameter types *StructServParam* and *ArrayServParam* (see Section 3.2.2) have revealed the need for user-defined complex data types. This has been recognized not only in logistics but also in other industries. Therefore, a possibility for modelling such user-defined data types has already been incorporated and published in a revision of Sheet 1. In addition, in the context of the HMI modelling (see Section 4), content from Sheet 1 is used, specifically the possibility of adding attachments to an MTP.

### 9.2	VDI/VDE/NAMUR 2658-2

VDI/VDE/NAMUR 2658-2 [4] (also referred to as Sheet 2) presents a concept for the vendor-independent modelling of HMIs in a MTP. Because of the origin of the MTP concept from the process industry, this concept has so far been designed for P&ID-like HMIs. However, in production-related logistics machine-oriented HMIs are better suited. Section 4 therefore introduces a concept for MTP-based modelling of such HMIs.

### 9.3	VDI/VDE/NAMUR 2658-3

VDI/VDE/NAMUR 2658-3 [5] (also referred to as Sheet 3) describes a library for data objects. This refers to typical data objects of the process industry, such as valves or drives, but also general objects for displaying, monitoring, and operating values of different data types and their metadata. With regard to this sheet, two needs for action have been identified in the context of production-related logistics. 

On the one hand, data objects necessary for logistics or general unit load processes need to be added. Thereby, new interface definitions for *IndicatorElements* and *OperationElements* of Array and Struct types seem possible and reasonable. These are specified in Section 10.8. In addition, further interfaces are conceivable, but are not yet specified in this document. These include piece counts (without unit), resettable counters, time displays, drag indicator displays, etc.

On the other hand, the interfaces specified so far mainly in Sheets 3 and 4 are too extensive for most unit load processes as they occur in logistics. Therefore, approaches to simplify these interfaces are presented in Section 5.

### 9.4	VDI/VDE/NAMUR 2658-4

VDI/VDE/NAMUR 2658-4 [3] (also referred to as Sheet 4) describes a service concept for process equipment assemblies (PEAs). The automation of LEAs shall also be done using MTP-compliant services. This is based on two logistics-specific interpretations of the existing MTP state machine – an order-oriented Cyclic Execution Service (CES) and a demand-oriented Single Execution Service (SES). Thereby, the CES and SES execution types are implemented as different procedures of the logistics services within a LEA. This does not result in any adaptations of the MTP concept regarding state-based process control, only more specific interpretations of the state machine and *FunctionClassificationAttributes* for the unique identification of CES and SES procedures.

The parameterization of LEAs can basically be implemented with procedure or configuration parameters in the sense of the MTP concept. However, the parameterization of logistics services with *StructServParam* and *ArrayServParam* requires two new MTP parameter interfaces (see Section 10.8). In addition, semantic information in the form of *FunctionClassificationAttributes* should be added to all parameter interfaces (similar to those already existing at the service and procedure level). Besides the new parameter interfaces, also *ProcessValuesIns*, *ProcessValueOuts* and *ReportValues* of struct and array types seem meaningful and are specified in Section 10.8. Beyond this, for logistic applications, an interface for the transmission of layout data to labelling LEAs, e.g., in the form of a binary large object, is also required. However, this has not yet been specified in detail and will be added to this document in due course. The need for a method interface for LEAs is envisaged in the future as well for writing consistent parameter sets. The definition of such an interface is already in progress in the MTP standardization committees. In addition to parameterization on the initiative of the orchestration layer (here: LOL), as envisaged by previous MTP concepts, three defined requests from the LEAs to the LOL are useful in the context of production-related logistics (see Section 3.2.3). For these, similar to the MTP service interaction in VDI/VDE/NAMUR 2658-4 [3], a logistics interaction is provided that implements these logistics-specific requests from an LEA to the LOL.

The concepts for the enhancement of VDI/VDE/NAMUR 2658-4 [3] are presented in detail in Section 3. Associated new model definitions and interface definitions are specified in Section 10.

### 9.5	VDI/VDE/NAMUR 2658-5

VDI/VDE/NAMUR 2658-5 [21] (also referred to as Sheet 5) describes the communication of PEAs. This currently refers to the communication between PEAs and a POL. As shown in Section 6, the automation of Logistics Lines shall be implemented by the concept of Automation Services Choreographies. This concept is based on direct LEA-to-LEA communication without a LOL as a broker. For this reason, Sheet 5 must be enhanced to include the necessary specification content for direct module-to-module communication. However, these have not been specified yet.

### 9.6	VDI/VDE/NAMUR 2658-X: ChoreographySet

For the coordination of physically coupled Logistics Lines, the concept of Automation Services Choreographies is presented in Section 6. This is not yet included in the MTP standard. Accordingly, model and interface definitions for configuring choreographies do not yet exist. Section 11 therefore introduces proposals for corresponding model and interface definitions of a *ChoreographySet*. These are intended to serve as a basis for standardizing Automatization Services Choreographies in the MTP standard.

### 9.7	VDI/VDE/NAMUR 2658-X: TransportSet

Section 7 introduces a concept for the coordination of flexible transport in Logistics Areas. This is currently not yet included in the MTP standard. Accordingly, there are not yet any model and interface definitions for configuring transports and transport nodes. Section 12 presents proposals for corresponding model and interface definitions of such a transport set. These are intended to serve as a basis for standardization of flexible transports in the MTP standard.

### 9.8	Further Enhancements

Logistics-specific enhancements may also arise in other sheets of the MTP standard. For example, it may be necessary for alarms to be provided at LEA level rather than at service or control module level. In addition, logistics-specific diagnostic functions may become necessary. However, these aspects have not yet been examined in detail and may be added in future versions of this document.

[< Previous](../08_Logistics_Orchestration_Layer/README.md) | [Home](../README.md) | [Next >](../10_Logistics_Aspect/README.md)