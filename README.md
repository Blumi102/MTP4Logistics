# Technical Report
## Application and Extension of the Module Type Package Concept for Production-related Logistics

### Author
[Michelle Blumenstein](https://www.researchgate.net/profile/Michelle-Blumenstein), Helmut Schmidt University Hamburg

### Reviewers
Andreas Stutz, Siemens AG<br>
Mathias Maurmaier, Siemens AG<br> 
Alexander Fay, Helmut Schmidt University Hamburg<br>

### Version
Version 1, 20 September 2022

## Section 1 - Purpose of this Repository
Modular plants are gaining more and more importance in the process and manufacturing industries for creating flexible and adaptable production systems. In order not to restrict this flexibility, an equally modular and thus flexible and adaptable production-related logistics system is required. Here, the Module Type Package (MTP) concept, which is already familiar in the area of modular production, can be applied to the area of production-related logistics [1,2].

In this context, this document describes interpretations and necessary extensions of the Module Type Package concept for the field of modular production-related logistics facilities. It serves as a technical specification to describe the basic concepts of modular logistics systems and to specify necessary new MTP interfaces and model definitions. Its structure is oriented along the structure of the MTP standard with its different specification aspects.

In [Section 2](Sec2_Modular_Logistics_System/README.md), a short introduction into modular logistics systems as application context of this document is given. [Section 3](Sec3_Logistics_Equipment_Assemblies/README.md) introduces a service-based automation concept for logistics modules following the VDI/VDE/NAMUR 2658-4 [3] specifications. Extensions for the vendor-neutral Human Machine Interface description of VDI/VDE/NAMUR 2658-2 [4] are described in [Section 4](Sec4_Logistics_HMI/README.md). Based on VDI/VDE/NAMUR 2658-3 [5] [Section 5](Sec5_Complexity_Reduction_of_Interfaces) proposes some blueprints to reduce the complexity of base interfaces in the context of machines in discrete industries like logistics. In [Sections 6](Sec6_Packaging_Line/README.md) and [7](Sec7_Logistics_Area/README.md) cross-module coordination mechanisms for the automation of logistics lines and logistics areas are introduced as new MTP aspects for the area of production-related logistics. Based on all those concepts [Section 8](Sec8_Model_Definitions/README.md) defines necessary semantical enriching model definitions which can be used in the Module Type Packages of logistics modules and [Section 9](Sec9_Interface-Definitions/README.md) shows the corresponding new interface definitions. The specification part is closed with modelling rules for the Module Type Package in [Section 10](Sec10_Modelling_Rules/README.md).

Since the work on the concepts for modular logistic systems is still ongoing, the previously described con-tents are not yet fully described in this version of the document. The missing parts will follow one by one in future versions.

## References
Please find all references [here](Sec11_References/README.md).

## PDF Document of the Technical Report
The current version of the Technical Report can be downloaded as a PDF file [here](Technical_Report_MTP_Logistics_v1_Submitted.pdf).