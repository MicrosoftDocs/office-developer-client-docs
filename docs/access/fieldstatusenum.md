---
title: "FieldStatusEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 49570042-8435-8618-3ba1-7006c47735e0

---

# FieldStatusEnum

Specifies the status of a **Field** object. 
  
The **adFieldPending\*** values indicate the operation that caused the status to be set, and may be combined with other status values. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adFieldAlreadyExists** <br/> |26  <br/> |Indicates that the specified field already exists.  <br/> |
|**adFieldBadStatus** <br/> |12  <br/> |Indicates that an invalid status value was sent from ADO to the OLE DB provider. Possible causes include an OLE DB 1.0 or 1.1 provider, or an improper combination of [Value](value-property-ado.md) and [Status](status-property-ado-field.md).  <br/> |
|**adFieldCannotComplete** <br/> |20  <br/> |Indicates that the server of the URL specified by [Source](source-property-ado-record.md) could not complete the operation.  <br/> |
|**adFieldCannotDeleteSource** <br/> |23  <br/> |Indicates that during a move operation, a tree or subtree was moved to a new location, but the source could not be deleted.  <br/> |
|**adFieldCantConvertValue** <br/> |2  <br/> |Indicates that the field cannot be retrieved or stored without loss of data.  <br/> |
|**adFieldCantCreate** <br/> |7  <br/> |Indicates that the field could not be added because the provider exceeded a limitation (such as the number of fields allowed).  <br/> |
|**adFieldDataOverflow** <br/> |6  <br/> |Indicates that the data returned from the provider overflowed the data type of the field.  <br/> |
|**adFieldDefault** <br/> |13  <br/> |Indicates that the default value for the field was used when setting data.  <br/> |
|**adFieldDoesNotExist** <br/> |16  <br/> |Indicates that the field specified does not exist.  <br/> |
|**adFieldIgnore** <br/> |15  <br/> |Indicates that this field was skipped when setting data values in the source. The provider set no value.  <br/> |
|**adFieldIntegrityViolation** <br/> |10  <br/> |Indicates that the field cannot be modified because it is a calculated or derived entity.  <br/> |
|**adFieldInvalidURL** <br/> |17  <br/> |Indicates that the data source URL contains invalid characters.  <br/> |
|**adFieldIsNull** <br/> |3  <br/> |Indicates that the provider returned a VARIANT value of type VT_NULL and that the field is not empty.  <br/> |
|**adFieldOK** <br/> |0  <br/> |Default. Indicates that the field was successfully added or deleted.  <br/> |
|**adFieldOutOfSpace** <br/> |22  <br/> |Indicates that the provider is unable to obtain enough storage space to complete a move or copy operation.  <br/> |
|**adFieldPendingChange** <br/> |0x40000  <br/> |Indicates either that the field has been deleted and then re-added, perhaps with a different data type, or that the value of the field that previously had a status of adFieldOK has changed. The final form of the field will modify the [Fields](fields-collection-ado.md) collection after the [Update](update-method-ado.md) method is called.  <br/> |
|**adFieldPendingDelete** <br/> |0x20000  <br/> |Indicates that the **Delete** operation caused the status to be set. The field has been marked for deletion from the **Fields** collection after the **Update** method is called.  <br/> |
|**adFieldPendingInsert** <br/> |0x10000  <br/> |Indicates that the **Append** operation caused the status to be set. The **Field** has been marked to be added to the **Fields** collection after the **Update** method is called.  <br/> |
|**adFieldPendingUnknown** <br/> |0x80000  <br/> |Indicates that the provider cannot determine what operation caused field status to be set.  <br/> |
|**adFieldPendingUnknownDelete** <br/> |0x100000  <br/> |Indicates that the provider cannot determine what operation caused field status to be set, and that the field will be deleted from the **Fields** collection after the **Update** method is called.  <br/> |
|**adFieldPermissionDenied** <br/> |9  <br/> |Indicates that the field cannot be modified because it is defined as read-only.  <br/> |
|**adFieldReadOnly** <br/> |24  <br/> |Indicates that the field in the data source is defined as read-only.  <br/> |
|**adFieldResourceExists** <br/> |19  <br/> |Indicates that the provider was unable to perform the operation because an object already exists at the destination URL and it is not able to overwrite the object.  <br/> |
|**adFieldResourceLocked** <br/> |18  <br/> |Indicates that the provider was unable to perform the operation because the data source is locked by one or more other application or process.  <br/> |
|**adFieldResourceOutOfScope** <br/> |25  <br/> |Indicates that a source or destination URL is outside the scope of the current record.  <br/> |
|**adFieldSchemaViolation** <br/> |11  <br/> |Indicates that the value violated the data source schema constraint for the field.  <br/> |
|**adFieldSignMismatch** <br/> |5  <br/> |Indicates that data value returned by the provider was signed but the data type of the ADO field value was unsigned.  <br/> |
|**adFieldTruncated** <br/> |4  <br/> |Indicates that variable-length data was truncated when reading from the data source.  <br/> |
|**adFieldUnavailable** <br/> |8  <br/> |Indicates that the provider could not determine the value when reading from the data source. For example, the row was just created, the default value for the column was not available, and a new value had not yet been specified.  <br/> |
|**adFieldVolumeNotFound** <br/> |21  <br/> |Indicates that the provider is unable to locate the storage volume indicated by the URL.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

