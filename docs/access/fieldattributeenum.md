---
title: "FieldAttributeEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 2d3a541e-a437-6108-ab0e-90c7884b3df7

---

# FieldAttributeEnum

Specifies one or more attributes of a [Field](field-object-ado.md) object. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adFldCacheDeferred** <br/> |0x1000  <br/> |Indicates that the provider caches field values and that subsequent reads are done from the cache.  <br/> |
|**adFldFixed** <br/> |0x10  <br/> |Indicates that the field contains fixed-length data.  <br/> |
|**adFldIsChapter** <br/> |0x2000  <br/> |Indicates that the field contains a chapter value, which specifies a specific child recordset related to this parent field. Typically chapter fields are used with data shaping or filters.  <br/> |
|**adFldIsCollection** <br/> |0x40000  <br/> |Indicates that the field specifies that the resource represented by the record is a collection of other resources, such as a folder, rather than a simple resource, such as a text file.  <br/> |
|**adFldIsDefaultStream** <br/> |0x20000  <br/> |Indicates that the field contains the default stream for the resource represented by the record. For example, the default stream can be the HTML content of a root folder on a Web site, which is automatically served when the root URL is specified.  <br/> |
|**adFldIsNullable** <br/> |0x20  <br/> |Indicates that the field accepts null values.  <br/> |
|**adFldIsRowURL** <br/> |0x10000  <br/> |Indicates that the field contains the URL that names the resource from the data store represented by the record.  <br/> |
|**adFldLong** <br/> |0x80  <br/> |Indicates that the field is a long binary field. Also indicates that you can use the [AppendChunk](appendchunk-method-ado.md) and [GetChunk](getchunk-method-ado.md) methods.  <br/> |
|**adFldMayBeNull** <br/> |0x40  <br/> |Indicates that you can read null values from the field.  <br/> |
|**adFldMayDefer** <br/> |0x2  <br/> |Indicates that the field is deferred — that is, the field values are not retrieved from the data source with the whole record, but only when you explicitly access them.  <br/> |
|**adFldNegativeScale** <br/> |0x4000  <br/> |Indicates that the field represents a numeric value from a column that supports negative scale values. The scale is specified by the [NumericScale](numericscale-property-ado.md) property.  <br/> |
|**adFldRowID** <br/> |0x100  <br/> |Indicates that the field contains a persistent row identifier that cannot be written to and has no meaningful value except to identify the row (such as a record number, unique identifier, and so forth).  <br/> |
|**adFldRowVersion** <br/> |0x200  <br/> |Indicates that the field contains some kind of time or date stamp used to track updates.  <br/> |
|**adFldUnknownUpdatable** <br/> |0x8  <br/> |Indicates that the provider cannot determine if you can write to the field.  <br/> |
|**adFldUnspecified** <br/> |-1          0xFFFFFFFF  <br/> |Indicates that the provider does not specify the field attributes.  <br/> |
|**adFldUpdatable** <br/> |0x4  <br/> |Indicates that you can write to the field.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.FieldAttribute.CACHEDEFERRED  <br/> |
|AdoEnums.FieldAttribute.FIXED  <br/> |
|AdoEnums.FieldAttribute.ISNULLABLE  <br/> |
|AdoEnums.FieldAttribute.LONG  <br/> |
|AdoEnums.FieldAttribute.MAYBENULL  <br/> |
|AdoEnums.FieldAttribute.MAYDEFER  <br/> |
|AdoEnums.FieldAttribute.NEGATIVESCALE  <br/> |
|AdoEnums.FieldAttribute.ROWID  <br/> |
|AdoEnums.FieldAttribute.ROWVERSION  <br/> |
|AdoEnums.FieldAttribute.UNKNOWNUPDATABLE  <br/> |
|AdoEnums.FieldAttribute.UNSPECIFIED  <br/> |
|AdoEnums.FieldAttribute.UPDATABLE  <br/> |
   

