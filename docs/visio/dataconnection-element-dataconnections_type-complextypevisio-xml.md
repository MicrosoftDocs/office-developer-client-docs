---
title: "DataConnection element (DataConnections_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 6aab8be3-b236-029b-1df3-b6860d4f4586
description: "Abstracts communication between one or more DataRecordset elements and a non-XML data source."
---

# DataConnection element (DataConnections_Type complexType) (Visio XML)

Abstracts communication between one or more **DataRecordset** elements and a non-XML data source. 
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[DataConnection_Type](dataconnection_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |connections.xml  <br/> |
   
## Definition

```XML
< xs:element name="DataConnection" type="DataConnection_Type" minOccurs="1" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataConnections](dataconnections-elementvisio-xml.md) <br/> |[DataConnections_Type](dataconnections_type-complextypevisio-xml.md) <br/> |Contains the **DataConnection** elements for the document.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|AlwaysUseConnectionFile  <br/> |xsd:boolean  <br/> |optional  <br/> |The default value is false. See Remarks for more information.  <br/> |Values of the xsd:boolean type.  <br/> |
|Command  <br/> |xsd:string  <br/> |optional  <br/> |The command string used to query the data source.  <br/> |Values of the xsd:string type.  <br/> |
|ConnectionString  <br/> |xsd:string  <br/> |optional  <br/> |The connection string that defines the parameters necessary to connect to a data source.  <br/> |Values of the xsd:string type.  <br/> |
|FileName  <br/> |xsd:string  <br/> |required  <br/> |The name of the connection file. See Remarks for more information.  <br/> |Values of the xsd:string type.  <br/> |
|FriendlyName  <br/> |xsd:string  <br/> |optional  <br/> |A user provided name for the data connection.  <br/> |Values of the xsd:string type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The ID assigned by Visio for a given connection, unique within the document.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Timeout  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The wait time in minutes while trying to establish a connection before terminating the attempt.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

