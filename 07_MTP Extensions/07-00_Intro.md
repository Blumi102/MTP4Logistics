
<!-- TODO: Nummerierung von Abbildungen und Tabellen glatt ziehen -->
<!-- TODO: Referenzen auf Abbildungen und Tabellen glatt ziehen -->
<!-- TODO: Nummerierung der Sections glatt ziehen -->
<!-- TODO: Texte lesen -->
<!-- TODO: Tabellen prüfen -->
<!-- TODO: Tabellenzellen linksbündig -->
<!-- TODO: Verlinkungen durch Claude prüfen lassen! -->
<!-- TODO: bei den Specs Labels vergeben, was schon übernommen wurde -->
<!-- TODO: Interface Definition durch DataSessembly definition ersetzen -->
<!-- TODO: Prüfen, ob noch etwas deutsches vorhanden ist -->
<!-- TODO: Durchgängige Nummierierung der Sections, Abbildungen und Tabellen prüfen -->
<!-- TODO: Claude fragen, ob er Inkonsistenzen in den Dokumenten findet und diese ausgeben lassen. -->
<!-- TODO: Referenzierung von Quellen überarbeiten in gleicher Weise, wie bei den Inhaltskapitel. Formatierung in CLAUDE.md hinterlegt. -->

## 7 Enhancements of the Module Type Package Concept

### Content of this Chapter

The Module Type Package concept has originally been developed for process industries. For a purposeful application in the context of production-related logistics, further development is necessary, which is presented in the following sections. In course of this development, care has been taken not to change the state machine or any other existing constructs (DataAssembly definitions, model definitions and mechanisms) of the MTP concept. However, reinterpretations and reasonable specifications of new MTP constructs have been developed. Extensions to the following aspects are described in this repository:

- [Manifest](./07-01_Manifest.md)
- [HMISet](./07-02_HMISet.md)
- [DataAssemblySet](./07-03_DataAssemblySet.md)
- [ServiceSet](./07-04_ServiceSet.md)
- [ProcessValueSet](./07-05_ProcessValueSet.md)
- [ServerAssmblySet](./07-06_ServerAssemblySet.md)
- [ChoreographySet](./07-07_ChoreographySet.md)
- [TransportSet](./07-08_TransportSet.md)

Furthermore, a [Conformity Declaration](./07-09_Conformity_Declaration.md) shows which profiles of the described aspects are needed to implement certain application scesnarios in production-related logistics.

### Formal Hints for the Specification Sections

The specifications follow the structure and style of the MTP specification. Each section presents extensions or a new specification of one MTP aspect. Each section begins with an overview of the introduced extensions, including a UML-style class diagram summarizing new model and DataAssembly definitions. This is followed by specification tables for the new definitions and detailed descriptions of new workflows.

The class diagrams follow the style of those in the MTP specification, showing only the content related to the introduced MTP extensions for production-related logistics. Newly introduced definitions are highlighted with a red border. Attributes are not shown in the diagrams but are documented in the subsequent specification tables. Italicized definitions denote abstract classes.

The specification tables follow the style of those in the MTP specification. Some have already been adopted in the MTP specification.

The specifications use AutomationML constructs according to [[IEC 62714-1](../98_References/README.md#iec-62714-1)]. The following table provides an overview of common abbreviations used throughout the specification.

| Abbreviation | AutomationML Construct |
|---|---|
| AT | AttributeType |
| ATL | AttributeTypeLibrary |
| EI | ExternalInterface |
| IC | InterfaceClass |
| ICL | InterfaceClassLibrary |
| IE | InternalElement |
| IH | InstanceHierarchy |
| RC | RoleClass |
| RCL | RoleClassLibrary |
| RR | RoleRequirement |
| SRC | SupportedRoleClass |
| SUC | SystemUnitClass |
| SUCL | SystemUnitClassLibrary |

