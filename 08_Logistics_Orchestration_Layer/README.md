[< Previous](../07_Logistics_Area/README.md) | [Home](../README.md) | [Next >](../09_MTP_Enhancements/README.md)

## 8 Logistics Orchestration Layer

Modular Logistics Systems require overarching management, coordination and monitoring functions that are handled by a Logistics Orchestration Layer (LOL). This section describes a first set of LOL functions as well as hints for their implementation.

The LOL functions shown in Table 8.1 have been derived based on functions of today's logistics control systems (mainly based on VDI 5600 [13, 14]) and the functions of today's Process Orchestration Layers (POLs) and have also been published in [15].

*Table 8.1: Functions of a Logistics Orchestration Layer*

|1) Order Management|
|-|
|The management of internally and externally initiated orders is an essential part of today's logistics control systems and is therefore also envisaged in LOLs in the same way. The MTP-based standardized LEA interfaces simplify the transmission of order information to the LEAs compared to today's logistics machines. This supports the idea of "digital customer order management" in the sense of VDI 5600-7 [14].|

|2) Asset Management|
|-|
|The asset management of today's logistics control systems is also adopted for LOLs, however, this is further developed in the direction of the asset management of POLs. In addition to the pure management of LEA types and instances, there is also simple integration and disintegration of LEAs by means of their MTPs and comprehensive monitoring, alarm management and diagnostics via standardized MTP interfaces. This supports an "adaptive machine and plant connection" in the sense of VDI 5600 7 [14].|

|3) Orchestration Configuration|
|-|
|In the context of Modular Logistics Systems, classical detailed planning and fine control, which is designed for fixed planning and non-modular logistics systems, no longer appears to be effective. Instead, the approach from POLs is used to create orchestration configurations, which can then be activated by configuration management. In the sense of VDI 5600-7 [14], this serves "dynamic detailed planning in production". Since LEAs often operate quite autonomously and largely independently of other LEAs, however, the focus of the orchestration configuration for LOLs is not on the creation of procedural sequences that are later executed by the LOL, or on cross-module regulations and interlocks. Instead, it is necessary to configure the dependencies of LEAs in Logistics Lines according to Section 6. For this purpose, a line configuration functionality is useful, which is described below and can be used by orchestration configuration. In addition, the correct parameterization of LEAs is essential. Due to the large number of parameters, this should be automated by a parameter management function described below. Parameter management supports the "assisted master data management" described in VDI 5600-7 [14].|

|4) Configuration Management|
|-|
|To manage, activate and deactivate the created orchestration configurations, configuration management is provided for LOLs similar to POLs. As with POLs, when a configuration is activated, specific LEA instances are assigned to the topology configuration placeholders. However, due to the loose chaining of LEAs in Logistics Areas, they can be flexibly assigned to the placeholders of the process configuration at runtime [16]. In this case, the assignment of a specific LEA instance to a process step is performed by operation management. The LEA instances assigned in the topology configuration are available for this purpose.|

|5) Operation Management|
|-|
|The LOL's operation management provides similar functionality to that of POLs, supplemented by the previously described function of assigning LEA instances to process steps at runtime. Operation management implements the activated orchestration configuration and thus processes orders provided by order management. The LEAs operate largely autonomously and in a decentral manner once the order has been transferred and do not have to be controlled individually by the LOL, as in the case of POLs. In the course of executing the logistics functionality, data is collected and stored. This is similar to the data acquisition and information management in today's logistics control systems. However, standardized MTP interfaces can be used for data acquisition. On the basis of this data, further tasks can be performed in line with the functions of today's logistics control systems, such as track and trace, performance analysis or quality management. Depending on the scope of these tasks in the specific application, they can be regarded as separate LOL functionalities used by the operation management or implemented directly in the operation management. Standardized MTP interfaces simplify data transfer between different applications, even across manufacturer boundaries. In this way, for example, "cross-company traceability" in the sense of VDI 5600-7 [14] can be implemented.|

|6) Material Management|
|-|
|The material management functionality of a LOL essentially comprises the same tasks as the function of the same name in today's logistics control systems. One challenge here is the MTP-based integration and coordination of flexible transport processes (e.g., based on Automated Guided Vehicles). For this purpose, the LOL provides a transport management functionality, which is described below. This includes, among other things, demand-driven ordering of material by the LEAs in the sense of "dynamic material management and transports" according to VDI 5600-7 [14].|

|7) Staff Management|
|-|
|The staff management foreseen in today's logistics control systems is also relevant for LOLs in the same way. No changes to this function are expected in the context of Modular Logistics Systems.|

|8) Energy Management|
|-|
|This LOL function is based on the energy management of today's logistics control systems. In addition, solutions for energy management in modular plants are currently being developed in the MTP environment. For example, a uniform information model for managing energy data is being developed [17] and its implementation is being investigated in the context of the MTP concept [18]. It is expected that these solutions will essentially also be suitable for LOLs. A uniform MTP-based model, which contains both process-relevant and energy-relevant information, can be used to implement integrated energy management in the sense of VDI 5600-7 [14].|

|9) Systems Management|
|-|
|In the context of LOLs, similar to POLs, a platform concept is pursued. This requires certain overarching system functions, such as user and rights management, security functions or version management of the LOL functions. These features are summarized as systems management here.|

|10) Line Configuration|
|-|
|The choreography-based Logistics Line coordination mechanism described in Section 6 requires a configuration of internal rules in each LEA that describe how the LEA should respond to changes in process variables of other LEAs. In order to integrate the choreographed Logistics Line into the LOL like a single MTP service, it is furthermore necessary to combine the MTPs of the individual LEAs into a "Composed-MTP" that describes the interface of the Logistics Line as a whole. In this context, the line configuration functionality of a LOL enables the configuration of the choreography rules and the subsequent creation of a "Composed-MTP".|

|11) Transport Management|
|-|
|The concept for Logistics Areas described in Section 7 envisages an MTP-based abstraction layer for flexible transport systems, which is provided by the LOL's transport management. This allows proprietary transport systems to be connected, aggregated, and provided to LEAs via a uniform interface. LEAs can report transport demands directly (in a decentral manner) to a transport system, which then executes them. Alternatively, it is also possible to schedule the transports in the orchestration configuration. In this case, the transports are commissioned centrally from operation management. In this case, operation management must be able to handle a variable number of MTP transport services at runtime.|

|12) Parameter Management|
|-|
|LEAs, like existing logistics machines, have a large number of parameters to adapt them to the specific application context and different products to be processed. Due to the expected fast set-up and reconfiguration of Modular Logistics Systems, the adjustment effort of these parameters increases significantly. Therefore, a parameter management functionality is provided in the LOL to perform the LEA parameterization in an automated manner as far as possible. In this way, rapid modification and updating of the parameter data sets in the LEAs and thus simple product changes and replacement of LEAs become possible. In addition to LEA parameters, management of layout data for labels also appears to make sense in the context of logistics.|

The above table describes a list of possible LOL functions. Not all these functions are necessary and available in every LOL. When implementing a LOL, it is therefore always necessary to check which functions are necessary for the given use case.

Once the functional scope of a LOL has been defined, it is still necessary to check which of the functions to be implemented need to be newly developed and which functions can be based on existing solutions. Functions 10 - 12 in the above list are specific functions of a LOL. Therefore, these functions have to be newly developed in any case, since no solutions exist for them yet. All other functions are derived from current MES or POL functions. In those cases, it must be checked whether an adaptation of the existing solutions to the special features of modular logistics described in Table 8.1 is economically possible.

A LOL should have a modular structure so that the scope of functions can be defined specifically for a particular customer or use case and existing solutions can also be integrated. A microservice architecture is a suitable solution for this purpose. Each LOL function is then implemented as one or more microservices with open interfaces, enabling information to be exchanged between the different LOL functions.

[< Previous](../07_Logistics_Area/README.md) | [Home](../README.md) | [Next >](../09_MTP_Enhancements/README.md)