---
title: "Namespaces"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e39f003c-3d16-1fae-48c5-304593c41f2f

---

# Namespaces

## Namespaces

The XML persistence format in ADO uses the following four namespaces.
  
|**Prefix**|**Description**|
|:-----|:-----|
|s  <br/> |Refers to the "XML-Data" namespace containing the elements and attributes that define the schema of the current **Recordset**.  <br/> |
|dt  <br/> |Refers to the data type definitions specification.  <br/> |
|rs  <br/> |Refers to the namespace containing elements and attributes specific to ADO **Recordset** properties and attributes.  <br/> |
|z  <br/> |Refers to the schema of the current rowset.  <br/> |
   
A client should not add its own tags to these namespaces, as defined by the specification. For example, a client should not define a namespace as "urn:schemas-microsoft-com:rowset" and then write out something such as "rs:MyOwnTag." To learn more about namespaces, see [XML Namespaces](http://www.w3.org/TR/xml-names/).
  
> [!NOTE]
> The ID for the schema tag must be "RowsetSchema," and the namespace used to refer to the schema of the current rowset must point to "#RowsetSchema." 
  
Note that the prefix of the namespace, that part to the right of the colon and to the left of the equal sign, is arbitrary.
  
```
 
xmlns:rs="urn:schemas-microsoft-com:rowset" 

```

The user can define this to be any name as long as this name is consistently used throughout the XML document. ADO always writes out "s," "rs," "dt," and "z," but these prefix names are not hard-coded into the loading component.
  
## Namespaces

The XML persistence format in ADO uses the following four namespaces.
  
|**Prefix**|**Description**|
|:-----|:-----|
|s  <br/> |Refers to the "XML-Data" namespace containing the elements and attributes that define the schema of the current **Recordset**.  <br/> |
|dt  <br/> |Refers to the data type definitions specification.  <br/> |
|rs  <br/> |Refers to the namespace containing elements and attributes specific to ADO **Recordset** properties and attributes.  <br/> |
|z  <br/> |Refers to the schema of the current rowset.  <br/> |
   
A client should not add its own tags to these namespaces, as defined by the specification. For example, a client should not define a namespace as "urn:schemas-microsoft-com:rowset" and then write out something such as "rs:MyOwnTag." To learn more about namespaces, see [XML Namespaces](http://www.w3.org/TR/xml-names/).
  
> [!NOTE]
> The ID for the schema tag must be "RowsetSchema," and the namespace used to refer to the schema of the current rowset must point to "#RowsetSchema." 
  
Note that the prefix of the namespace, that part to the right of the colon and to the left of the equal sign, is arbitrary.
  
```
 
xmlns:rs="urn:schemas-microsoft-com:rowset" 

```

The user can define this to be any name as long as this name is consistently used throughout the XML document. ADO always writes out "s," "rs," "dt," and "z," but these prefix names are not hard-coded into the loading component.
  

