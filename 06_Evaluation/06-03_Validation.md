## 6.3 Validation

The term *validation* describes, according to [[DIN9000]](../08_References/README.md#din-en-iso-9000-2015), the "confirmation, through the provision of objective evidence, that the requirements for a specific intended use or application have been fulfilled." *Validation* in the sense of DSR involves examining whether artifacts are useful for achieving the intended purpose (stakeholder goal) in the intended problem context [[Wie14]](../08_References/README.md#wieringa-2014). It examines whether the *right artifacts have been developed*. While the validity of *verification* depends on the quality of the underlying requirements, the validity of *validation* is independent of the requirements.

This section validates the presented artifacts. First, an overview of the validation goal and strategy is given, followed by the results of the necessary validation steps.

#### Validation Goal and Strategy

According to [Chapter 1](../README.md#1-purpose-of-this-repository), the problem context of this work is modular production-related logistics systems. The goal is the reduction of engineering and coordination effort for these systems through automated module integration, in order to meet challenges regarding flexibility and adaptability. The validation goal is therefore to demonstrate that the presented artifacts are useful for reducing the engineering and coordination effort of modular production-related logistics systems through automated integration.

A direct comparison of the engineering and coordination effort between a conventionally engineered and an MTP-based engineered modular production-related logistics system is not possible within the scope of this work. Therefore, a descriptive validation in the sense of an *Informed Argument* per [[HMP+04]](../08_References/README.md#hevner-et-al-2004) is employed. Existing knowledge is used to develop a well-founded argument for the usefulness of the artifacts. [Figure 6.7](#figure-67-validation-strategy) shows an overview of the validation steps.

##### Figure 6.7: Validation Strategy
<img src="./images/Validierungsstrategie.svg" alt="Validation Strategy" style="max-width: 700px; width: 100%;" />

The fundamental assumption is that the MTP concept is suitable for reducing engineering and coordination effort (A). Existing MTP-based systems reveal prerequisites that must be met to achieve this reduction (B). It is then assumed that a reduction of engineering and coordination effort also applies to MLS if these prerequisites are met for the domain of production-related logistics (C). Therefore, these prerequisites are assessed in the MLS context (D). From the successful assessment, it is concluded that the artifacts described in this work can reduce engineering and coordination effort for MLS (E). These steps are described in detail below.

#### (A) Reduction of Engineering and Coordination Effort Through the MTP Concept

Over the past approximately 10 years, the MTP concept has been deployed in various demonstrator systems and productive plants, primarily in the process industry. Its suitability for reducing engineering and coordination effort has been successfully demonstrated. According to a status report by NAMUR, ProcessNet, VDMA, and ZVEI [[NAM21]](../08_References/README.md#namur-processnet-vdma-und-zvei-2021), a reduction of up to 70% was observed.

#### (B) Prerequisites for Using the MTP Concept

The reduction of engineering and coordination effort is based on the automated integration of intelligent equipment into modular systems via standardized interfaces and their description through semantic models. This results in four necessary prerequisites:

(1) **Interface definitions:** For all types of information to be exchanged between the equipment to be integrated and other systems, uniform MTP-based interface definitions must be specified.

(2) **Model definitions:** For the semantic description of interfaces and all other integration-relevant equipment information, uniform MTP-based model definitions must be specified.

(3) **Tools for generating, importing, and interpreting MTP files:** For an efficient engineering workflow, MTP files of the equipment to be integrated must be generated automatically (e.g., based on the equipment's application program). During the engineering of the modular system, MTPs must be automatically imported into and interpreted by the orchestration layer. Corresponding tools must be provided for MTP file generation, import, and interpretation.

(4) **Uniform communication technology:** For vendor-neutral interoperability between the integrated equipment and the orchestration layer, a uniform communication technology must be used across all participating systems.

In addition to these necessary prerequisites, the competence to correctly apply the MTP interfaces and models using the provided tools must also be present. This requires, above all, corresponding design rules and engineering methodologies for modular MTP-based systems.

#### (C) Fundamental Assumption of the Validation

The idea of automated integration of intelligent equipment and the underlying prerequisites are not specific to the process industry. It is therefore assumed that a reduction of engineering and coordination effort of a similar magnitude can also be achieved through the MTP concept in the domain of production-related logistics — provided the prerequisites described above are met.

#### (D) Assessment of Prerequisites for Production-Adjacent Logistics

The following sections assess the extent to which the prerequisites for the beneficial use of the MTP concept are met for the domain of production-related logistics.

**(1) Interface definitions:** The completeness and functional capability of the MTP interface definitions for production-related logistics was demonstrated through the three evaluation examples in [Section 6.1](06-01_EvaluationExamples.md). In the evaluation examples, communication between LEAs and to the superordinate LOL takes place exclusively via existing or newly defined MTP-based interfaces. From the functional capability of the evaluation examples, it is concluded that all necessary interface definitions are present and functional. The MTP files of the LEAs (see XX) further demonstrate that every interface used can be represented in an MTP file and thus made available to a superordinate LOL. This prerequisite is therefore considered *fulfilled*.
<!-- TODO: Verweis auf MTPs ergänzen -->

**(2) Model definitions:** MTP model definitions must represent all integration-relevant LEA information that a superordinate LOL requires for its functions. To demonstrate the completeness of the model definitions, the LOL implementations of the three evaluation examples in [Section 6.1](06-01_EvaluationExamples.md) were examined. [Table 6.5](#table-65-completeness-check-of-model-definitions-for-representing-relevant-lea-information-in-a-lol) lists the LEA information required in the LOL implementations and assigns model definitions through which this information can be described in an MTP. The result shows that all necessary LEA information can be represented via MTP model definitions. The MTP files of the LEAs (See XX) further demonstrate that every model definition used can be represented in an MTP file and thus made available to a superordinate LOL. This prerequisite is therefore considered *fulfilled*.
<!-- TODO: Verweis auf MTPs ergänzen -->

##### Table 6.5: Completeness Check of Model Definitions for Representing Relevant LEA Information in a LOL

<table>
  <tr>
    <th align="left">LOL Function</th>
    <th align="left">Required LEA Information</th>
    <th align="left">Model Definitions</th>
  </tr>
  <tr>
    <td align="left" rowspan="5">Cross-cutting*</td>
    <td align="left">Asset information of LEAs</td>
    <td align="left">Existing model definitions per <a href="../08_References/README.md#mtp-specification-part-1">[MTP Specification Part 1]</a></td>
  </tr>
  <tr>
    <td align="left" rowspan="4">Asset information of Logistics Lines</td>
    <td align="left">Existing model definitions per <a href="../08_References/README.md#mtp-specification-part-1">[MTP Specification Part 1]</a></td>
  </tr>
  <tr>
    <td align="left">SUC ComposedModuleTypePackage</td>
  </tr>
  <tr>
    <td align="left">RC HasExternalMtpContext</td>
  </tr>
  <tr>
    <td align="left">AT ComposedTypeRevisionType</td>
  </tr>
  <tr>
    <td align="left" rowspan="6">Order Management</td>
    <td align="left" rowspan="2">Service interfaces and order-specific parameter interfaces of LEAs</td>
    <td align="left">Existing model definitions for services and parameters per <a href="../08_References/README.md#mtp-specification-part-4">[MTP Specification Part 4]</a></td>
  </tr>
  <tr>
    <td align="left">FunctionClassificationAttributes for CES, SES, and ProductId</td>
  </tr>
  <tr>
    <td align="left" rowspan="4">Service interfaces and order-specific parameter interfaces of Logistics Lines</td>
    <td align="left">Existing model definitions for services and parameters per <a href="../08_References/README.md#mtp-specification-part-4">[MTP Specification Part 4]</a></td>
  </tr>
  <tr>
    <td align="left">FunctionClassificationAttributes for CES, SES, and ProductId</td>
  </tr>
  <tr>
    <td align="left">SUC ComposedModuleTypePackage</td>
  </tr>
  <tr>
    <td align="left">RC HasExternalMtpContext</td>
  </tr>
  <tr>
    <td align="left" rowspan="9">Parameter Management</td>
    <td align="left" rowspan="2">Product- and packaging-specific parameter sets of LEAs</td>
    <td align="left">Existing model definitions for parameters per <a href="../08_References/README.md#mtp-specification-part-4">[MTP Specification Part 4]</a></td>
  </tr>
  <tr>
    <td align="left">FunctionClassificationAttributes ProductId, LogisticsObjectStatus, ProductDataSet, PackagingId, and PackagingDataSet</td>
  </tr>
  <tr>
    <td align="left" rowspan="7">Requests for product- and packaging-specific parameter sets as well as notifications of parameter set changes</td>
    <td align="left">RC HasLogisticsInteraction</td>
  </tr>
  <tr>
    <td align="left">SUC LogisticsInteraction</td>
  </tr>
  <tr>
    <td align="left">SUC LogisticsQuestion</td>
  </tr>
  <tr>
    <td align="left">SUC ProductParameterRequest</td>
  </tr>
  <tr>
    <td align="left">SUC PackagingParameterRequest</td>
  </tr>
  <tr>
    <td align="left">SUC ProductParameterUpdatedInfo</td>
  </tr>
  <tr>
    <td align="left">SUC PackagingParameterUpdatedInfo</td>
  </tr>
  <tr>
    <td align="left" rowspan="5">HMI</td>
    <td align="left">HMI information of LEAs</td>
    <td align="left">Existing model definitions per <a href="../08_References/README.md#mtp-specification-part-2">[MTP Specification Part 2]</a></td>
  </tr>
  <tr>
    <td align="left" rowspan="4">HMI information of Logistics Lines</td>
    <td align="left">Existing model definitions per <a href="../08_References/README.md#mtp-specification-part-2">[MTP Specification Part 2]</a></td>
  </tr>
  <tr>
    <td align="left">SUC ReferencedPicture</td>
  </tr>
  <tr>
    <td align="left">SUC PictureFrame</td>
  </tr>
  <tr>
    <td align="left">RC HasExternalMtpContext</td>
  </tr>
  <tr>
    <td align="left" rowspan="13">Choreography Configurator</td>
    <td align="left" rowspan="10">Choreography-relevant information of an LEA including Input and Output List elements</td>
    <td align="left">SUC ChoreographySet</td>
  </tr>
  <tr>
    <td align="left">SUC ChoreographyParticipant</td>
  </tr>
  <tr>
    <td align="left">SUC InputList</td>
  </tr>
  <tr>
    <td align="left">SUC InputElement</td>
  </tr>
  <tr>
    <td align="left">SUC FixedInputElement</td>
  </tr>
  <tr>
    <td align="left">SUC ConfigurableInputElement</td>
  </tr>
  <tr>
    <td align="left">SUC WritableInputElement</td>
  </tr>
  <tr>
    <td align="left">SUC OutputList</td>
  </tr>
  <tr>
    <td align="left">SUC OutputElement</td>
  </tr>
  <tr>
    <td align="left">SUC ConfigurableOutputElement</td>
  </tr>
  <tr>
    <td align="left" rowspan="3">Composed MTP information**</td>
    <td align="left">SUC ComposedModuleTypePackage, AT ComposedTypeRevisionType</td>
  </tr>
  <tr>
    <td align="left">RC HasExternalMtpContext</td>
  </tr>
  <tr>
    <td align="left">SUC ReferencedPicture, SUC PictureFrame</td>
  </tr>
  <tr>
    <td align="left" rowspan="8">Transport Management</td>
    <td align="left" rowspan="7">Transport-relevant information of an LEA including its transport nodes and their types</td>
    <td align="left">SUC TransportSet</td>
  </tr>
  <tr>
    <td align="left">SUC TransportNode</td>
  </tr>
  <tr>
    <td align="left">SUC InboundNode</td>
  </tr>
  <tr>
    <td align="left">SUC OutboundNode</td>
  </tr>
  <tr>
    <td align="left">SUC InOutboundNode</td>
  </tr>
  <tr>
    <td align="left">SUC ProcessingNode</td>
  </tr>
  <tr>
    <td align="left">SUC OrderNode</td>
  </tr>
  <tr>
    <td align="left" colspan="2">*(same transport node model definitions as Material Flow Management below)*</td>
  </tr>
  <tr>
    <td align="left" rowspan="12">Material Flow Management</td>
    <td align="left" rowspan="7">Transport-relevant information of an LEA including its transport nodes and their types</td>
    <td align="left">SUC TransportSet</td>
  </tr>
  <tr>
    <td align="left">SUC TransportNode</td>
  </tr>
  <tr>
    <td align="left">SUC InboundNode</td>
  </tr>
  <tr>
    <td align="left">SUC OutboundNode</td>
  </tr>
  <tr>
    <td align="left">SUC InOutboundNode</td>
  </tr>
  <tr>
    <td align="left">SUC ProcessingNode</td>
  </tr>
  <tr>
    <td align="left">SUC OrderNode</td>
  </tr>
  <tr>
    <td align="left" rowspan="2">Product-specific parameter sets of LEAs (including default values for transport nodes to approach)</td>
    <td align="left">Existing model definitions for parameters per <a href="../08_References/README.md#mtp-specification-part-4">[MTP Specification Part 4]</a></td>
  </tr>
  <tr>
    <td align="left">FunctionClassificationAttributes ProductId, LogisticsObjectStatus, and ProductDataSet</td>
  </tr>
  <tr>
    <td align="left" rowspan="3">Requests for the next transport node to approach</td>
    <td align="left">RC HasLogisticsInteraction</td>
  </tr>
  <tr>
    <td align="left">SUC LogisticsInteraction, SUC LogisticsQuestion</td>
  </tr>
  <tr>
    <td align="left">SUC TransportNodeRequest</td>
  </tr>
</table>

\* These are basic LEA and Logistics Line information required across all LOL functions that work with LEAs or Logistics Lines.

\*\* Future choreography configurators should be able to generate, import, and edit Composed MTPs for describing line interfaces and line HMI screens. This is not yet implemented in the LOL implementations of the evaluation examples.

**(3) Tools for generating, importing, and interpreting MTP files:** The generation, import, and interpretation of MTP files is based on processing packed AutomationML files in the format described in [[MTP Specification Part 1]](../08_References/README.md#mtp-specification-part-1). With the AMLEngine [[Aut25]](../08_References/README.md#automationml-ev-2025), an official .NET library from AutomationML e.V. exists that enables processing of AutomationML files. Solutions also exist for conformant packing of MTP files according to the Open Packaging Conventions [[ISO/IEC 29500-2]](../08_References/README.md#isoiec-29500-2) (e.g., [[Mic25]](../08_References/README.md#microsoft-2025)). These libraries have proven suitable for generating and interpreting MTP files in process industry applications. No software tool yet exists for the generation and interpretation of the new model and interface definitions specified in this work. However, only AutomationML-conformant objects were used for modeling the new constructs. Developing the corresponding generation and interpretation tools is therefore an engineering task, not a research task. This prerequisite is therefore considered *fulfilled*.

**(4) Uniform communication technology:** OPC UA Client/Server has proven as the communication technology in existing MTP applications. The three evaluation examples described in [Section 6.1](06-01_EvaluationExamples.md) also use OPC UA Client/Server as the uniform standardized technology for communication between LEAs and to superordinate orchestration systems. This demonstrates that the use of a uniform communication technology is feasible. This prerequisite is therefore considered *fulfilled*.

#### (E) Conclusion

Step (D) demonstrated that, with the artifacts described in [Chapter 3](../03_Logistics_Equipment_Assemblies/03_Logistics_Equipment_Assemblies.md) through [Chapter 5](../05_Logistics_Area/05_Logistics_Area.md) and their implementation in the evaluation examples in [Section 6.1](06-01_EvaluationExamples.md), all necessary prerequisites identified in step (B) for the beneficial use of the MTP concept are also met in the domain of production-related logistics. Consequently, it can be expected that, using these artifacts, a reduction of engineering and coordination effort of a similar magnitude as in the process industry (A) can also be achieved in the domain of production-related logistics.

To actually achieve this reduction, it must be ensured that the artifacts developed in this work are applied *correctly*. This requires design rules and engineering methodologies for MLS as well as supporting tools that define the *correct* application of the artifacts and support their practical use. These methodologies, rules, and tools are not the subject of this work but are regarded as future research and development tasks ([Chapter 7](../07_Outlook/07_Outlook.md)).
