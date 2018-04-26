---
title: "RecordStatusEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 302915b8-494d-0be2-6dce-eaf91a0ea8ae

---

# RecordStatusEnum

Specifies the status of a record with regard to batch updates and other bulk operations.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adRecCanceled** <br/> |0x100  <br/> |Indicates that the record was not saved because the operation was canceled.  <br/> |
|**adRecCantRelease** <br/> |0x400  <br/> |Indicates that the new record was not saved because the existing record was locked.  <br/> |
|**adRecConcurrencyViolation** <br/> |0x800  <br/> |Indicates that the record was not saved because optimistic concurrency was in use.  <br/> |
|**adRecDBDeleted** <br/> |0x40000  <br/> |Indicates that the record has already been deleted from the data source.  <br/> |
|**adRecDeleted** <br/> |0x4  <br/> |Indicates that the record was deleted.  <br/> |
|**adRecIntegrityViolation** <br/> |0x1000  <br/> |Indicates that the record was not saved because the user violated integrity constraints.  <br/> |
|**adRecInvalid** <br/> |0x10  <br/> |Indicates that the record was not saved because its bookmark is invalid.  <br/> |
|**adRecMaxChangesExceeded** <br/> |0x2000  <br/> |Indicates that the record was not saved because there were too many pending changes.  <br/> |
|**adRecModified** <br/> |0x2  <br/> |Indicates that the record was modified.  <br/> |
|**adRecMultipleChanges** <br/> |0x40  <br/> |Indicates that the record was not saved because it would have affected multiple records.  <br/> |
|**adRecNew** <br/> |0x1  <br/> |Indicates that the record is new.  <br/> |
|**adRecObjectOpen** <br/> |0x4000  <br/> |Indicates that the record was not saved because of a conflict with an open storage object.  <br/> |
|**adRecOK** <br/> |0  <br/> |Indicates that the record was successfully updated.  <br/> |
|**adRecOutOfMemory** <br/> |0x8000  <br/> |Indicates that the record was not saved because the computer has run out of memory.  <br/> |
|**adRecPendingChanges** <br/> |0x80  <br/> |Indicates that the record was not saved because it refers to a pending insert.  <br/> |
|**adRecPermissionDenied** <br/> |0x10000  <br/> |Indicates that the record was not saved because the user has insufficient permissions.  <br/> |
|**adRecSchemaViolation** <br/> |0x20000  <br/> |Indicates that the record was not saved because it violates the structure of the underlying database.  <br/> |
|**adRecUnmodified** <br/> |0x8  <br/> |Indicates that the record was not modified.  <br/> |
   
 **ADO/WFC Equivalent**
  
AdoEnums.RecordStatus.
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.RecordStatus.CANCELED  <br/> |
|AdoEnums.RecordStatus.CANTRELEASE  <br/> |
|AdoEnums.RecordStatus.CONCURRENCYVIOLATION  <br/> |
|AdoEnums.RecordStatus.DBDELETED  <br/> |
|AdoEnums.RecordStatus.DELETED  <br/> |
|AdoEnums.RecordStatus.INTEGRITYVIOLATION  <br/> |
|AdoEnums.RecordStatus.INVALID  <br/> |
|AdoEnums.RecordStatus.MAXCHANGESEXCEEDED  <br/> |
|AdoEnums.RecordStatus.MODIFIED  <br/> |
|AdoEnums.RecordStatus.MULTIPLECHANGES  <br/> |
|AdoEnums.RecordStatus.NEW  <br/> |
|AdoEnums.RecordStatus.OBJECTOPEN  <br/> |
|AdoEnums.RecordStatus.OK  <br/> |
|AdoEnums.RecordStatus.OUTOFMEMORY  <br/> |
|AdoEnums.RecordStatus.PENDINGCHANGES  <br/> |
|AdoEnums.RecordStatus.PERMISSIONDENIED  <br/> |
|AdoEnums.RecordStatus.SCHEMAVIOLATION  <br/> |
|AdoEnums.RecordStatus.UNMODIFIED  <br/> |
   

