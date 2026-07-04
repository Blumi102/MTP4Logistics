## MTP Extension of the ServerAssemblySet
This chapter specifies all identified extensions of the *ServerAssemblySet* and integrates them into the existing MTP specification [MTP Specification Part 5.1](../98_References/README.md#mtp-specification-part-51) and [MTP Specification Part 5](../98_References/README.md#mtp-specification-part-5), respectively.

#### Mapping Complex Data Types in OPC~UA
The specification chapters~[MTP Extension of the DataAssemblySet](#sec:AnhangDataAssemblySet), [MTP Extension of the ServiceSet](#sec:AnhangServiceSet), and [MTP Extension of the ProcessValueSet](#sec:AnhangProcessValueSet) described interface definitions with complex data types, Struct and Array. To transmit these data types via OPC~UA, not only the existing primitive data types but also the mapping of complex data types into the address space of the OPC~UA server of an LEA must be specified.

Figure~[Mapping of Structured Data Types in OPC UA Based on PNO.2025.Part5](#fig:StructOPCUA) shows the mapping of variables of **structured data types** in OPC~UA. 

![Mapping of Structured Data Types in OPC UA Based on PNO.2025.Part5](Inhalt/Abbildungen/99_Anhang/Spezifikation_LEA/Komplexe Datentypen/Komplexe_Typen_OPC_UA.drawio.png)
*Mapping of Structured Data Types in OPC UA Based on PNO.2025.Part5* {#fig:StructOPCUA}

Variables of a structured data type have a *HasTypeDefinition* to an OPC~UA *VariableType* that describes the underlying structure. This *VariableType* has a data type that is an OPC~UA *DataType*. This *DataType*, in turn, has a *StructureDefinition* that contains a list of *StructureFields*, not shown in the figure. These *StructureFields* correspond to the subordinate variables of the *VariableType* and thus to the complex data type to be mapped. This modeling of structured data types is possible with the native OPC~UA means according to [OPC 10000-3](../98_References/README.md#opc-10000-3). As a result of this dissertation, it has already been adopted into the profile *ModuleTypePackage:ServerAssemblySet.OPCUA V2.0.0* of the MTP specification [MTP Specification Part 5](../98_References/README.md#mtp-specification-part-5).

Variables with **array data types** do not require additional rules for mapping to OPC~UA. By using the multiplexing mechanism, the arrays are represented in OPC~UA in the form of primitive or structured data types. 


