---
title: "DataRecordSet_Type complexType ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 59544910-6bd5-2c89-71b3-5c8ee91a1dea

---

# DataRecordSet_Type complexType ('Visio XML')

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
          <xs:complexType name="DataRecordSet_Type">
          
          <xs:sequence>
    <xs:element name="Rel"  type="Rel_Type"
     minOccurs="1"
     maxOccurs="1"
    >
    </xs:element>
    
    <xs:element name="DataColumns"  type="DataColumns_Type"
     minOccurs="1"
     maxOccurs="1"
    >
    </xs:element>
    
    <xs:element name="PrimaryKey"  type="PrimaryKey_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
    <xs:element name="RowMap"  type="RowMap_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
    <xs:element name="RefreshConflict"  type="RefreshConflict_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
    <xs:element name="AutoLinkComparison"  type="AutoLinkComparison_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
      </xs:sequence>
    <xs:attribute name="ID"
  type="xsd:unsignedInt"
     use="required"
    />
    <xs:attribute name="ConnectionID"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="Command"
  type="xsd:string"
    />
    <xs:attribute name="Options"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="TimeRefreshed"
  type="xsd:dateTime"
    />
    <xs:attribute name="NextRowID"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="Name"
  type="xsd:string"
    />
    <xs:attribute name="RowOrder"
  type="xsd:boolean"
    />
    <xs:attribute name="RefreshOverwriteAll"
  type="xsd:boolean"
    />
    <xs:attribute name="RefreshNoReconciliationUI"
  type="xsd:boolean"
    />
    <xs:attribute name="RefreshInterval"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="ReplaceLinks"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="Checksum"
  type="xsd:unsignedInt"
    />
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[AutoLinkComparison](autolinkcomparison-element-datarecordset_type-complextypevisio-xml.md) <br/> |[AutoLinkComparison_Type](autolinkcomparison_type-complextypevisio-xml.md) <br/> ||
|[DataColumns](datacolumns-element-datarecordset_type-complextypevisio-xml.md) <br/> |[DataColumns_Type](datacolumns_type-complextypevisio-xml.md) <br/> ||
|[PrimaryKey](primarykey-element-datarecordset_type-complextypevisio-xml.md) <br/> |[PrimaryKey_Type](primarykey_type-complextypevisio-xml.md) <br/> ||
|[RefreshConflict](refreshconflict-element-datarecordset_type-complextypevisio-xml.md) <br/> |[RefreshConflict_Type](refreshconflict_type-complextypevisio-xml.md) <br/> ||
|[Rel](rel-element-datarecordset_type-complextypevisio-xml.md) <br/> |[Rel_Type](rel_type-complextypevisio-xml.md) <br/> ||
|[RowMap](rowmap-element-datarecordset_type-complextypevisio-xml.md) <br/> |[RowMap_Type](rowmap_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Checksum  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|Command  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
|ConnectionID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|Name  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
|NextRowID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|Options  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|RefreshInterval  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|RefreshNoReconciliationUI  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
|RefreshOverwriteAll  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
|ReplaceLinks  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|RowOrder  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
|TimeRefreshed  <br/> |xsd:dateTime  <br/> |optional  <br/> ||Values of the xsd:dateTime type.  <br/> |
   

