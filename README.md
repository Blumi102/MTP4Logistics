[Next >](./02_Modular_Logistics_System/README.md)


<!-- TODO: Navigation im gesamten Repo -->
<!-- TODO: Bilder übersetzen -->
<!-- TODO: schauen, was aus dem Anhang noch ins Repo muss -->
<!-- TODO: verlinkungen prüfen lassen -->

# Technical Report
## Application and Extension of the Module Type Package Concept for Production-related Logistics

### Author
[Michelle Blumenstein](https://www.researchgate.net/profile/Michelle-Blumenstein), Siemens AG, PhD Candidate at Helmut Schmidt University Hamburg 

### Version
Version 3, XX August 2026

DOI: XXXX

## 1 Purpose of this Repository

This repository presents the application and extension of the Module Type Package (MTP) concept for production-related logistics. As a conceptual foundation, it introduces the condensed contents of the author's doctoral dissertation. In addition, the repository includes conceptual and practical application examples that demonstrate the developed concepts both argumentatively and through real industrial implementations. Beyond the dissertation contents, the repository contains a standardization proposal for the necessary extensions of the MTP standard in the context of production-related logistics. This proposal is being discussed in the MTP standardization bodies at the PROFIBUS & PROFINET International (PI), and parts of its contents have already been adopted into the MTP standard.

### Motivation

Increasing market volatility, product individualization, and shorter innovation cycles demand flexible and adaptable production and logistics systems. Modularization of both hardware and automation software is a key enabler for the required flexibility and adaptability. The Module Type Package (MTP) concept, originally developed for modular process plants, enables the automated integration of Process Equipment Assemblies (PEAs) and thus supports these goals. Since the flexibility enabled by the MTP concept propagates from production plants to the production-related logistics surrounding them, an equally modular and flexible logistics system is required.

### Problem

Although production-related logistics systems are already modular at the hardware level, proprietary interfaces, extensive manual coordination and engineering processes, and missing integration standards prevent the implementation of flexibility and adaptability goals. According to NAMUR Working Group 4.19 [[NE 171]](08_References/README.md#namur-ak-419-2020), integration costs for logistics modules amount to approximately €156,000 per company per year. This figure is expected to rise significantly in the context of modular production and digitalization.

### Objective

This work describes an automation concept for modular production-related logistics systems, with a focus on packaging logistics. Building on and extending existing MTP concepts, it aims to significantly reduce coordination and engineering effort through uniform, automated integration of logistics modules. The developed concepts address both the automation of individual logistics modules and their integration into an overall modular logistics system.

## Structure of the Repository

In [Section 2](02_Modular_Logistics_System/README.md) the structural levels of Modular Logistics Systems are introduced as the application context of this document. [Section 3](03_Logistics_Equipment_Assemblies/README.md) presents an MTP-based automation concept for individual Logistics Equipment Assemblies (LEAs), covering service-based automation, parameterization, process and report values, operator displays, and complexity reduction of interfaces. [Section 4](04_Logistics_Line/README.md) describes a choreography-based automation approach for Logistics Lines, addressing both horizontal integration of LEAs and their vertical integration into a superordinate orchestration layer. In [Section 5](05_Logistics_Area/README.md) an MTP-based automation concept for flexible transports in Logistics Areas is introduced, including transport management, AGV systems, and transport node concepts. [Section 6](06_Evaluation/README.md) evaluates the developed concepts from Sections 3 to 5 through prototypical implementations, requirement verification, and validation of the research goals. Based on all those concepts, [Section 7](07_MTP%20Extensions/README.md) specifies the necessary extensions to the Module Type Package standard in the context of production-related logistics, covering the Manifest, HMISet, DataAssemblySet, ServiceSet, ProcessValueSet, ServerAssemblySet, ChoreographySet, TransportSet, and a Conformity Declaration.


<!-- TODO: Link zur Dissertation wird ergänzt, sobald er öffentlich ist. -->
  

## References
Please find all references [here](./08_References/README.md).

## PDF Document of the Technical Report

### Current Version
The current version of the Technical Report can be downloaded as a PDF file [here](Technical_Report_MTP_Logistics_v2_Submitted.pdf).

### Previous Versions
- [Version 1](./99_Archive/Technical_Report_MTP_Logistics_v1_Submitted.pdf) (Release Date: 20 September 2022)
- [Version 2](./99_Archive/Technical_Report_MTP_Logistics_v1_Submitted.pdf) 
(Release Date: 06 November 2023)


[Next >](./02_Modular_Logistics_System/README.md)