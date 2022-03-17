---
title: "DataRecordSets element (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: c75b3233-9ac5-d29c-a658-d554e86e6be4
description: "Contains all the DataRecordset elements in the document."
---

# DataRecordSets element (Visio XML)

Contains all the **DataRecordset** elements in the document. 
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[DataRecordSets_Type](datarecordsets_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |recordsets.xml  <br/> |
   
## Definition

```XML
< xs:element name="DataRecordSets" type="DataRecordSets_Type" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

None.
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataRecordSet](datarecordset-element-datarecordsets_type-complextypevisio-xml.md) <br/> |[DataRecordSet_Type](datarecordset_type-complextypevisio-xml.md) <br/> |Contains all the **DataRecordset** elements in the document. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ActiveRecordsetID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The ID of the active data recordset in the **External Data** window when the window closes, so that it can be restored the next time the window opens. |Values of the xsd:unsignedInt type. |
|DataWindowOrder  <br/> |xsd:string  <br/> |optional  <br/> |The order of the data recordsets displayed on the tabs of the **External Data** window. An ordered list of data-recordset IDs, separated by semi-colons. |Values of the xsd:string type. |
|NextID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The next available ID for a new data recordset. |Values of the xsd:unsignedInt type. |
   

