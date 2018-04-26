---
title: "ADO Error Reference"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 21cec161-664a-4c18-4458-8117f4f63845
description: "The ErrorValueEnum constant describes the ADO error values. For a complete listing of these enumerated constants, including values, see Appendix B: ADO Errors. This section will examine some of the more interesting errors and explain some specific situations that can raise them, or solutions to fix the problem. Both the ErrorValueEnum constant and the short positive decimal number are listed."
---

# ADO Error Reference

The **ErrorValueEnum** constant describes the ADO error values. For a complete listing of these enumerated constants, including values, see [Appendix B: ADO Errors](appendix-b-ado-errors.md). This section will examine some of the more interesting errors and explain some specific situations that can raise them, or solutions to fix the problem. Both the **ErrorValueEnum** constant and the short positive decimal number are listed. 
  
|**Number**|**ErrorValueEnum constant**|**Description/Possible causes**|
|:-----|:-----|:-----|
|**3000** <br/> |**adErrProviderFailed** <br/> |Provider failed to perform the requested operation.  <br/> |
|**3001** <br/> |**adErrInvalidArgument** <br/> |Arguments are of the wrong type, are out of acceptable range, or are in conflict with one another. This error is often caused by a typographical error in an SQL SELECT statement. For example, a misspelled field name or table name can generate this error. This error can also occur when a field or table named in a SELECT statement does not exist in the data store.  <br/> |
|**3002** <br/> |**adErrOpeningFile** <br/> |File could not be opened. A misspelled file name was specified, or a file has been moved, renamed, or deleted. Over a network, the drive might be temporarily unavailable or network traffic might be preventing a connection.  <br/> |
|**3003** <br/> |**adErrReadFile** <br/> |File could not be read. The name of the file is specified incorrectly, the file might have been moved or deleted, or the file might have become corrupted.  <br/> |
|**3004** <br/> |**adErrWriteFile** <br/> |Write to file failed. You might have closed a file and then tried to write to it, or the file might be corrupted. If the file is located on a network drive, transient network conditions might prevent writing to a network drive.  <br/> |
|**3021** <br/> |**adErrNoCurrentRecord** <br/> |Either **BOF** or **EOF** is True, or the current record has been deleted. Requested operation requires a current record. An attempt was made to update records by using **Find** or **Seek** to move the record pointer to the desired record. If the record is not found, **EOF** will be True. This error can also occur after a failed **AddNew** or **Delete** because there is no current record when these methods fail.  <br/> |
|**3219** <br/> |**adErrIllegalOperation** <br/> |Operation is not allowed in this context.  <br/> |
|**3220** <br/> |**adErrCantChangeProvider** <br/> |Supplied provider is different from the one already in use.  <br/> |
|**3246** <br/> |**adErrInTransaction** <br/> |**Connection** object cannot be explicitly closed while in a transaction. A **Recordset** or **Connection** object that is currently participating in a transaction cannot be closed. Call either **RollbackTrans** or **CommitTrans** before closing the object.  <br/> |
|**3251** <br/> |**adErrFeatureNotAvailable** <br/> |The object or provider is not capable of performing the requested operation. Some operations depend on a particular provider version.  <br/> |
|**3265** <br/> |**adErrItemNotFound** <br/> |Item cannot be found in the collection corresponding to the requested name or ordinal. An incorrect field or table name has been specified.  <br/> |
|**3367** <br/> |**adErrObjectInCollection** <br/> |Object is already in collection. Cannot append. An object cannot be added to the same collection twice.  <br/> |
|**3420** <br/> |**adErrObjectNotSet** <br/> |Object is no longer valid.  <br/> |
|**3421** <br/> |**adErrDataConversion** <br/> |Application uses a value of the wrong type for the current operation. You might have supplied a string to an operation that expects a stream, for example.  <br/> |
|**3704** <br/> |**adErrObjectClosed** <br/> |Operation is not allowed when the object is closed. The **Connection** or **Recordset** has been closed. For example, some other routine might have closed a global object. You can prevent this error by checking the **State** property before you attempt an operation.  <br/> |
|**3705** <br/> |**adErrObjectOpen** <br/> |Operation is not allowed when the object is open. An object that is open cannot be opened. Fields cannot be appended to an open **Recordset**.  <br/> |
|**3706** <br/> |**adErrProviderNotFound** <br/> |Provider cannot be found. It may not be properly installed. The name of the provider might be incorrectly specified, the specified provider might not be installed on the computer where your code is being executed, or the installation might have become corrupted.  <br/> |
|**3707** <br/> |**adErrBoundToCommand** <br/> |The **ActiveConnection** property of a **Recordset** object, which has a **Command** object as its source, cannot be changed. The application attempted to assign a new **Connection** object to a **Recordset** that has a **Command** object as its source.  <br/> |
|**3708** <br/> |**adErrInvalidParamInfo** <br/> |**Parameter** object is improperly defined. Inconsistent or incomplete information was provided.  <br/> |
|**3709** <br/> |**adErrInvalidConnection** <br/> |The connection cannot be used to perform this operation. It is either closed or invalid in this context.  <br/> |
|**3710** <br/> |**adErrNotReentrant** <br/> |Operation cannot be performed while processing event. An operation cannot be performed within an event handler that causes the event to fire again. For example, navigation methods should not be called from within a **WillMove** event handler.  <br/> |
|**3711** <br/> |**adErrStillExecuting** <br/> |Operation cannot be performed while executing asynchronously.  <br/> |
|**3712** <br/> |**adErrOperationCancelled** <br/> |Operation has been canceled by the user. The application has called the **CancelUpdate** or **CancelBatch** method and the current operation has been canceled.  <br/> |
|**3713** <br/> |**adErrStillConnecting** <br/> |Operation cannot be performed while connecting asynchronously.  <br/> |
|**3714** <br/> |**adErrInvalidTransaction** <br/> |Coordinating transaction is invalid or has not started.  <br/> |
|**3715** <br/> |**adErrNotExecuting** <br/> |Operation cannot be performed while not executing.  <br/> |
|**3716** <br/> |**adErrUnsafeOperation** <br/> |Safety settings on this computer prohibit accessing a data source on another domain.  <br/> |
|**3717** <br/> |**adWrnSecurityDialog** <br/> |For internal use only. Don't use. (Entry was included for the sake of completeness. This error should not appear in your code.)  <br/> |
|**3718** <br/> |**adWrnSecurityDialogHeader** <br/> |For internal use only. Don't use. (Entry included for the sake of completeness. This error should not appear in your code.)  <br/> |
|**3719** <br/> |**adErrIntegrityViolation** <br/> |Data value conflicts with the integrity constraints of the field. A new value for a **Field** would cause a duplicate key. A value that forms one side of a relationship between two records might not be updatable.  <br/> |
|**3720** <br/> |**adErrPermissionDenied** <br/> |Insufficient permission prevents writing to the field. The user named in the connection string does not have the proper permissions to write to a **Field**.  <br/> |
|**3721** <br/> |**adErrDataOverflow** <br/> |Data value is too large to be represented by the field data type. A numeric value that is too large for the intended field was assigned. For example, a long integer value was assigned to a short integer field.  <br/> |
|**3722** <br/> |**adErrSchemaViolation** <br/> |Data value conflicts with the data type or constraints of the field. The data store has validation constraints that differ from the **Field** value.  <br/> |
|**3723** <br/> |**adErrSignMismatch** <br/> |Conversion failed because the data value was signed and the field data type used by the provider was unsigned.  <br/> |
|**3724** <br/> |**adErrCantConvertvalue** <br/> |Data value cannot be converted for reasons other than sign mismatch or data overflow. For example, conversion would have truncated data.  <br/> |
|**3725** <br/> |**adErrCantCreate** <br/> |Data value cannot be set or retrieved because the field data type was unknown, or the provider had insufficient resources to perform the operation.  <br/> |
|**3726** <br/> |**adErrColumnNotOnThisRow** <br/> |Record does not contain this field. An incorrect field name was specified or a field not in the **Fields** collection of the current record was referenced.  <br/> |
|**3727** <br/> |**adErrURLDoesNotExist** <br/> |Either the source URL or the parent of the destination URL does not exist. There is a typographical error in either the source or destination URL. You might have  `http://mysite/photo/myphoto.jpg` when you should actually have  `http://mysite/photos/myphoto.jpg` instead. The typographical error in the parent URL (in this case,  *photo*  instead of  *photos*  ) has caused the error.  <br/> |
|**3728** <br/> |**adErrTreePermissionDenied** <br/> |Permissions are insufficient to access tree or subtree. The user named in the connection string does not have the appropriate permissions.  <br/> |
|**3729** <br/> |**adErrInvalidURL** <br/> |URL contains invalid characters. Make sure the URL is typed correctly. The URL follows the scheme registered to the current provider (for example, Internet Publishing Provider is registered for http).  <br/> |
|**3730** <br/> |**adErrResourceLocked** <br/> |Object represented by the specified URL is locked by one or more other processes. Wait until the process has finished and attempt the operation again. The object you are trying to access has been locked by another user or by another process in your application. This is most likely to arise in a multi-user environment.  <br/> |
|**3731** <br/> |**adErrResourceExists** <br/> |Copy operation cannot be performed. Object named by destination URL already exists. Specify **adCopyOverwrite** to replace the object. If you do not specify **adCopyOverwrite** when copying the files in a directory, the copy fails when you try to copy an item that already exists in the destination location.  <br/> |
|**3732** <br/> |**adErrCannotComplete** <br/> |The server cannot complete the operation. This might be because the server is busy with other operations or it might be low on resources.  <br/> |
|**3733** <br/> |**adErrVolumeNotFound** <br/> |Provider cannot locate the storage device indicated by the URL. Make sure the URL is typed correctly. The URL of the storage device might be incorrect, but this error can occur for other reasons. The device might be offline or a large volume of network traffic might prevent the connection from being made.  <br/> |
|**3734** <br/> |**adErrOutOfSpace** <br/> |Operation cannot be performed. Provider cannot obtain enough storage space. There might not be enough RAM or hard-drive space for temporary files on the server.  <br/> |
|**3735** <br/> |**adErrResourceOutOfScope** <br/> |Source or destination URL is outside the scope of the current record.  <br/> |
|**3736** <br/> |**adErrUnavailable** <br/> |Operation failed to complete and the status is unavailable. The field may be unavailable or the operation was not attempted. Another user might have changed or deleted the field you are trying to access.  <br/> |
|**3737** <br/> |**adErrURLNamedRowDoesNotExist** <br/> |Record named by this URL does not exist. While attempting to open a file using a **Record** object, either the file name or the path to the file was misspelled.  <br/> |
|**3738** <br/> |**adErrDelResOutOfScope** <br/> |The URL of the object to be deleted is outside the scope of the current record.  <br/> |
|**3747** <br/> |**adErrCatalogNotSet** <br/> |Operation requires a valid **ParentCatalog**.  <br/> |
|**3748** <br/> |**adErrCantChangeConnection** <br/> |Connection was denied. The new connection you requested has different characteristics than the one already in use.  <br/> |
|**3749** <br/> |**adErrFieldsUpdateFailed** <br/> |Fields update failed. For further information, examine the **Status** property of individual field objects. This error can occur in two situations: when changing a **Field** object's value in the process of changing or adding a record to the database; and when changing the properties of the **Field** object itself. The **Record** or **Recordset** update failed due to a problem with one of the fields in the current record. Enumerate the **Fields** collection and check the **Status** property of each field to determine the cause of the problem.  <br/> |
|**3750** <br/> |**adErrDenyNotSupported** <br/> |Provider does not support sharing restrictions. An attempt was made to restrict file sharing and your provider does not support the concept.  <br/> |
|**3751** <br/> |**adErrDenyTypeNotSupported** <br/> |Provider does not support the requested kind of sharing restriction. An attempt was made to establish a particular type of file-sharing restriction that is not supported by your provider. See the provider's documentation to determine what file-sharing restrictions are supported.  <br/> |
   

