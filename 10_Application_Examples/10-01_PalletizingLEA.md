## 10.1 Application Example: Palletizing LEA
To illustrate the concepts described in the dissertation for LEA automation, this section presents an exemplary application of these concepts to a Palletizing LEA (PAL) that follows a CES-based mode of operation.

### 10.1.1 Service Specification
[Table 10.1](#table-101-profile-of-an-exemplary-palletizing-service) provides an overview of the PAL service, including its procedures, parameters, report values, and process values.

##### Table 10.1: Profile of an Exemplary Palletizing Service

<table>
  <tr>
    <td colspan="4" align="left"><strong>Palletizing Service</strong></td>
  </tr>
  <tr>
    <td colspan="4" align="left">This service is used to palletize bags onto pallets according to a defined packing pattern. The bags are always processed uniformly in accordance with specific order data.</td>
  </tr>
  <tr>
    <td colspan="4" align="left"><strong>Procedures</strong></td>
  </tr>
  <tr>
    <th align="left">Procedure ID</th>
    <th align="left">Name</th>
    <th colspan="2" align="left">Description</th>
  </tr>
  <tr>
    <td align="left">16#1</td>
    <td align="left">CES_Continuous (continuous)</td>
    <td colspan="2" align="left">Continuous palletizing of bags with an always identical packing pattern</td>
  </tr>
  <tr>
    <td align="left">16#2</td>
    <td align="left">CES_BagQuantity (self-completing)</td>
    <td colspan="2" align="left">Palletizing a defined number of bags with an always identical packing pattern</td>
  </tr>
  <tr>
    <td align="left">16#3</td>
    <td align="left">CES_PalletQuantity (self-completing)</td>
    <td colspan="2" align="left">Palletizing a defined number of pallets with an always identical packing pattern</td>
  </tr>
  <tr>
    <td colspan="4" align="left"><strong>Order-Specific Parameters (Procedure Parameters)</strong></td>
  </tr>
  <tr>
    <th align="left">Name</th>
    <th align="left">Interface Type</th>
    <th align="left">Procedure</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">ProductionId</td>
    <td align="left">StringServParam</td>
    <td align="left">16#1, 16#2, 16#3</td>
    <td align="left">Order number</td>
  </tr>
  <tr>
    <td align="left">ProductId</td>
    <td align="left">DIntServParam</td>
    <td align="left">16#1, 16#2, 16#3</td>
    <td align="left">Identifier of the product to be palletized and key for selecting product-specific parameters</td>
  </tr>
  <tr>
    <td align="left">BagQuantity</td>
    <td align="left">DIntServParam</td>
    <td align="left">16#2</td>
    <td align="left">Number of bags to be palletized</td>
  </tr>
  <tr>
    <td align="left">PalletQuantity</td>
    <td align="left">DIntServParam</td>
    <td align="left">16#3</td>
    <td align="left">Number of pallets to be palletized</td>
  </tr>
  <tr>
    <td colspan="4" align="left"><strong>Product- and Packaging-Specific Parameters (Configuration Parameters)</strong></td>
  </tr>
  <tr>
    <th align="left">Name</th>
    <th align="left">Interface Type</th>
    <th colspan="2" align="left">Description</th>
  </tr>
  <tr>
    <td align="left">ProductDataSet</td>
    <td align="left">ArrayServParam of PalletizerProductDataStruct</td>
    <td colspan="2" align="left">Array of product-specific parameter sets; contains, e.g., the packing pattern to be used</td>
  </tr>
  <tr>
    <td align="left">PackagingDataSet</td>
    <td align="left">ArrayServParam of PalletizerPackagingDataStruct</td>
    <td colspan="2" align="left">Array of packaging-specific parameter sets; contains, e.g., the dimensions of the pallets to be used</td>
  </tr>
  <tr>
    <td colspan="4" align="left"><strong>Design-Specific Parameters (Configuration Parameters)</strong></td>
  </tr>
  <tr>
    <td colspan="4" align="left">None</td>
  </tr>
  <tr>
    <td colspan="4" align="left"><strong>Report Values</strong></td>
  </tr>
  <tr>
    <th align="left">Name</th>
    <th align="left">Interface Type</th>
    <th align="left">Procedure</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">ProductName</td>
    <td align="left">StringView</td>
    <td align="left">16#1, 16#2, 16#3</td>
    <td align="left">Name of the currently packaged product type</td>
  </tr>
  <tr>
    <td align="left">PalletTypeName</td>
    <td align="left">StringView</td>
    <td align="left">16#1, 16#2, 16#3</td>
    <td align="left">Name of the currently used pallet type</td>
  </tr>
  <tr>
    <td align="left">BagCount</td>
    <td align="left">DIntView</td>
    <td align="left">16#1, 16#2, 16#3</td>
    <td align="left">Number of bags packaged so far</td>
  </tr>
  <tr>
    <td align="left">PalletCount</td>
    <td align="left">DIntView</td>
    <td align="left">16#1, 16#2, 16#3</td>
    <td align="left">Number of pallets completed so far</td>
  </tr>
  <tr>
    <td colspan="4" align="left"><strong>Process Values</strong></td>
  </tr>
  <tr>
    <th align="left">Name</th>
    <th align="left">Interface Type</th>
    <th align="left">Procedure</th>
    <th align="left">Description</th>
  </tr>
  <tr>
    <td align="left">SuccessorClearIn</td>
    <td align="left">BinProcessValueIn</td>
    <td align="left">16#1, 16#2, 16#3</td>
    <td align="left">Input for the clearance signal from a downstream LEA (relevant when using the LEA within a Logistics Line)</td>
  </tr>
  <tr>
    <td align="left">PredecessorClearOut</td>
    <td align="left">BinProcessValueOut</td>
    <td align="left">16#1, 16#2, 16#3</td>
    <td align="left">Output for the clearance signal to an upstream LEA (relevant when using the LEA within a Logistics Line)</td>
  </tr>
</table>

### 10.1.2 Mode of Operation
The mode of operation of the PAL service follows the CES operation described in the dissertation and is illustrated in [Figure 10.1](#figure-101-mode-of-operation-of-an-exemplary-palletizing-service-in-ces-mode).

##### Figure 10.1: Mode of Operation of an Exemplary Palletizing Service in CES Mode
![Mode of Operation of an Exemplary Palletizing Service in CES Mode](./images/Arbeitsweise_CES_PAL.png)

Initially, the service is in the IDLE state. Pre-population of the *ProductDataSet* and *PackagingDataSet* via the corresponding *ArrayServParam* interfaces is possible. Before the service is started, the desired procedure must also be selected and all required order-specific parameters must be set, i.e., the *ProductionId*, the *ProductId*, the *BagQuantity* (for procedure 16#2 only), and the *PalletQuantity* (for procedure 16#3 only). Based on the configured *ProductId*, the product-specific parameter set to be used is then determined from the *ProductDataSet* or by querying the LOL, and selected for processing. Using the *PackagingId* contained in the selected product-specific parameter set, the packaging-specific parameter set to be used is determined and selected in the same manner. The PAL service can then be started, and all bags belonging to the order are palletized in the EXECUTE state according to the packing pattern stored in the product parameter set. The palletizing operation is terminated when the number of bags configured via *BagQuantity* is reached (applies to procedure 16#2), when the number of pallets configured via *PalletQuantity* is reached (applies to procedure 16#3), or when the palletizing operation is ended by a *Complete* command (applies to procedure 16#1). The service can be reset to IDLE via a *Reset* command.

### 10.1.3 HMI Screen
[Figure 10.2](#figure-102-hmi-screen-of-a-palletizing-lea) shows the HMI screen of the PAL. It enables the entry of order-specific parameters, control of the LEA service, and the display of report values and process values via dynamic HMI objects in accordance with [MTP Specification Part 2](../98_References/README.md#mtp-specification-part-2). In addition, it contains an image of the PAL as a static HMI object. This image is stored in the MTP attachment of the PAL as shown in [Figure 10.3](#figure-103-image-file-of-a-palletizing-lea-within-the-mtp). It is assigned the ECLASS reference "36521201", which corresponds to the semantic reference for a palletizer. A LOL integrating this LEA can therefore decide whether to use the image from the MTP attachment or an image of a palletizer that may be available in its graphics library.

##### Figure 10.2: HMI Screen of a Palletizing LEA
![HMI Screen of a Palletizing LEA](./images/HMI_PAL_PVs.png)

##### Figure 10.3: Image File of a Palletizing LEA Within the MTP
![Image File of a Palletizing LEA Within the MTP](./images/MTP_HMI_PAL.png)
