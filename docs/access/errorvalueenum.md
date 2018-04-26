---
title: "ErrorValueEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 2af99f32-6004-1225-367c-45d693f447b8

---

# ErrorValueEnum

Specifies the type of ADO run-time error.
  
Three forms of the error number are listed:
  
- Positive decimal — the low two bytes of the full number in decimal format. This number is displayed in the default Visual Basic error message dialog box. For example, Run-time error '3707'.
    
- Negative decimal — The decimal translation of the full error number.
    
- Hexadecimal — The hexadecimal representation of the full error number. The Windows facility code is in the fourth digit. The facility code for ADO error numbers is  *A*  . For example: 0x800 ** *A* ** 0E7B. 
    
> [!NOTE]
> OLE DB errors may be passed to your ADO application. Typically, these can be identified by a Windows facility code of  *4*  . For example, 0x800 ** *4* **.... For more information about these numbers, see Chapter 16 of the  *OLE DB Programmer's Reference.* 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adErrBoundToCommand** <br/> |3707          -2146824581          0x800A0E7B  <br/> |Cannot change the **ActiveConnection** property of a **Recordset** object which has a **Command** object as its source.  <br/> |
|**adErrCannotComplete** <br/> |3732          -2146824556          0x800A0E94  <br/> |Server cannot complete the operation.  <br/> |
|**adErrCantChangeConnection** <br/> |3748          -2146824540          0x800A0EA4  <br/> |Connection was denied. New connection you requested has different characteristics than the one already in use.  <br/> |
|**adErrCantChangeProvider** <br/> |3220          -2146825068          0X800A0C94  <br/> |Supplied provider is different from the one already in use.  <br/> |
|**adErrCantConvertvalue** <br/> |3724          -2146824564          0x800A0E8C  <br/> |Data value cannot be converted for reasons other than sign mismatch or data overflow. For example, conversion would have truncated data.  <br/> |
|**adErrCantCreate** <br/> |3725          -2146824563          0x800A0E8D  <br/> |Data value cannot be set or retrieved because the field data type was unknown, or the provider had insufficient resources to perform the operation.  <br/> |
|**adErrCatalogNotSet** <br/> |3747          -2146824541          0x800A0EA3  <br/> |Operation requires a valid **ParentCatalog**.  <br/> |
|**adErrColumnNotOnThisRow** <br/> |3726          -2146824562          0x800A0E8E  <br/> |Record does not contain this field.  <br/> |
|**adErrDataConversion** <br/> |3421          -2146824867          0x800A0D5D  <br/> |Application uses a value of the wrong type for the current operation.  <br/> |
|**adErrDataOverflow** <br/> |3721          -2146824567          0x800A0E89  <br/> |Data value is too large to be represented by the field data type.  <br/> |
|**adErrDelResOutOfScope** <br/> |3738          -2146824550          0x800A0E9A  <br/> |URL of the object to be deleted is outside the scope of the current record.  <br/> |
|**adErrDenyNotSupported** <br/> |3750          -2146824538          0x800A0EA6  <br/> |Provider does not support sharing restrictions.  <br/> |
|**adErrDenyTypeNotSupported** <br/> |3751          -2146824537          0x800A0EA7  <br/> |Provider does not support the requested kind of sharing restriction.  <br/> |
|**adErrFeatureNotAvailable** <br/> |3251          -2146825037          0x800A0CB3  <br/> |Object or provider is not capable of performing requested operation.  <br/> |
|**adErrFieldsUpdateFailed** <br/> |3749          -2146824539          0x800A0EA5  <br/> |Fields update failed. For further information, examine the **Status** property of individual field objects.  <br/> |
|**adErrIllegalOperation** <br/> |3219          -2146825069          0x800A0C93  <br/> |Operation is not allowed in this context.  <br/> |
|**adErrIntegrityViolation** <br/> |3719          -2146824569          0x800A0E87  <br/> |Data value conflicts with the integrity constraints of the field.  <br/> |
|**adErrInTransaction** <br/> |3246          -2146825042          0x800A0CAE  <br/> |**Connection** object cannot be explicitly closed while in a transaction.  <br/> |
|**adErrInvalidArgument** <br/> |3001          -2146825287          0x800A0BB9  <br/> |Arguments are of the wrong type, are out of acceptable range, or are in conflict with one another.  <br/> |
|**adErrInvalidConnection** <br/> |3709          -2146824579          0x800A0E7D  <br/> |The connection cannot be used to perform this operation. It is either closed or invalid in this context.  <br/> |
|**adErrInvalidParamInfo** <br/> |3708          -2146824580          0x800A0E7C  <br/> |**Parameter** object is improperly defined. Inconsistent or incomplete information was provided.  <br/> |
|**adErrInvalidTransaction** <br/> |3714          -2146824574          0x800A0E82  <br/> |Coordinating transaction is invalid or has not started.  <br/> |
|**adErrInvalidURL** <br/> |3729          -2146824559          0x800A0E91  <br/> |URL contains invalid characters. Make sure the URL is typed correctly.  <br/> |
|**adErrItemNotFound** <br/> |3265          -2146825023          0x800A0CC1  <br/> |Item cannot be found in the collection corresponding to the requested name or ordinal.  <br/> |
|**adErrNoCurrentRecord** <br/> |3021          -2146825267          0x800A0BCD  <br/> |Either **BOF** or **EOF** is True, or the current record has been deleted. Requested operation requires a current record.  <br/> |
|**adErrNotExecuting** <br/> |3715          -2146824573          0x800A0E83  <br/> |Operation cannot be performed while not executing.  <br/> |
|**adErrNotReentrant** <br/> |3710          -2146824578          0x800A0E7E  <br/> |Operation cannot be performed while processing event.  <br/> |
|**adErrObjectClosed** <br/> |3704          -2146824584          0x800A0E78  <br/> |Operation is not allowed when the object is closed.  <br/> |
|**adErrObjectInCollection** <br/> |3367          -2146824921          0x800A0D27  <br/> |Object is already in collection. Cannot append.  <br/> |
|**adErrObjectNotSet** <br/> |3420          -2146824868          0x800A0D5C  <br/> |Object is no longer valid.  <br/> |
|**adErrObjectOpen** <br/> |3705          -2146824583          0x800A0E79  <br/> |Operation is not allowed when the object is open.  <br/> |
|**adErrOpeningFile** <br/> |3002          -2146825286          0x800A0BBA  <br/> |File could not be opened.  <br/> |
|**adErrOperationCancelled** <br/> |3712          -2146824576          0x800A0E80  <br/> |Operation has been cancelled by the user.  <br/> |
|**adErrOutOfSpace** <br/> |3734          -2146824554          0x800A0E96  <br/> |Operation cannot be performed. Provider cannot obtain enough storage space.  <br/> |
|**adErrPermissionDenied** <br/> |3720          -2146824568          0x800A0E88  <br/> |Insufficent permission prevents writing to the field.  <br/> |
|**adErrProviderFailed** <br/> |3000          -2146825288          0x800A0BB8  <br/> |Provider failed to perform the requested operation.  <br/> |
|**adErrProviderNotFound** <br/> |3706          -2146824582          0x800A0E7A  <br/> |Provider cannot be found. It may not be properly installed.  <br/> |
|**adErrReadFile** <br/> |3003          -2146825285          0x800A0BBB  <br/> |File could not be read.  <br/> |
|**adErrResourceExists** <br/> |3731          -2146824557          0x800A0E93  <br/> |Copy operation cannot be performed. Object named by destination URL already exists. Specify **adCopyOverwrite** to replace the object.  <br/> |
|**adErrResourceLocked** <br/> |3730          -2146824558          0x800A0E92  <br/> |Object represented by the specified URL is locked by one or more other processes. Wait until the process has finished and attempt the operation again.  <br/> |
|**adErrResourceOutOfScope** <br/> |3735          -2146824553          0x800A0E97  <br/> |Source or destination URL is outside the scope of the current record.  <br/> |
|**adErrSchemaViolation** <br/> |3722          -2146824566          0x800A0E8A  <br/> |Data value conflicts with the data type or constraints of the field.  <br/> |
|**adErrSignMismatch** <br/> |3723          -2146824565          0x800A0E8B  <br/> |Conversion failed because the data value was signed and the field data type used by the provider was unsigned.  <br/> |
|**adErrStillConnecting** <br/> |3713          -2146824575          0x800A0E81  <br/> |Operation cannot be performed while connecting aynchronously.  <br/> |
|**adErrStillExecuting** <br/> |3711          -2146824577          0x800A0E7F  <br/> |Operation cannot be performed while executing asynchronously.  <br/> |
|**adErrTreePermissionDenied** <br/> |3728          -2146824560          0x800A0E90  <br/> |Permissions are insufficient to access tree or subtree.  <br/> |
|**adErrUnavailable** <br/> |3736          -2146824552          0x800A0E98  <br/> |Operation failed to complete and the status is unavailable. The field may be unavailable or the operation was not attempted.  <br/> |
|**adErrUnsafeOperation** <br/> |3716          -2146824572          0x800A0E84  <br/> |Safety settings on this computer prohibit accessing a data source on another domain.  <br/> |
|**adErrURLDoesNotExist** <br/> |3727          -2146824561          0x800A0E8F  <br/> |Either the source URL or the parent of the destination URL does not exist.  <br/> |
|**adErrURLNamedRowDoesNotExist** <br/> |3737          -2146824551          0x800A0E99  <br/> |Record named by this URL does not exist.  <br/> |
|**adErrVolumeNotFound** <br/> |3733          -2146824555          0x800A0E95  <br/> |Provider cannot locate the storage device indicated by the URL. Make sure the URL is typed correctly.  <br/> |
|**adErrWriteFile** <br/> |3004          -2146825284          0x800A0BBC  <br/> |Write to file failed.  <br/> |
|**adWrnSecurityDialog** <br/> |3717          -2146824571          0x800A0E85  <br/> |For internal use only. Don't use.  <br/> |
|**adWrnSecurityDialogHeader** <br/> |3718          -2146824570          0x800A0E86  <br/> |For internal use only. Don't use.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
Only the following subsets of ADO/WFC equivalents are defined.
  
|**Constant**|
|:-----|
|AdoEnums.ErrorValue.BOUNDTOCOMMAND  <br/> |
|AdoEnums.ErrorValue.DATACONVERSION  <br/> |
|AdoEnums.ErrorValue.FEATURENOTAVAILABLE  <br/> |
|AdoEnums.ErrorValue.ILLEGALOPERATION  <br/> |
|AdoEnums.ErrorValue.INTRANSACTION  <br/> |
|AdoEnums.ErrorValue.INVALIDARGUMENT  <br/> |
|AdoEnums.ErrorValue.INVALIDCONNECTION  <br/> |
|AdoEnums.ErrorValue.INVALIDPARAMINFO  <br/> |
|AdoEnums.ErrorValue.ITEMNOTFOUND  <br/> |
|AdoEnums.ErrorValue.NOCURRENTRECORD  <br/> |
|AdoEnums.ErrorValue.NOTEXECUTING  <br/> |
|AdoEnums.ErrorValue.NOTREENTRANT  <br/> |
|AdoEnums.ErrorValue.OBJECTCLOSED  <br/> |
|AdoEnums.ErrorValue.OBJECTINCOLLECTION  <br/> |
|AdoEnums.ErrorValue.OBJECTNOTSET  <br/> |
|AdoEnums.ErrorValue.OBJECTOPEN  <br/> |
|AdoEnums.ErrorValue.OPERATIONCANCELLED  <br/> |
|AdoEnums.ErrorValue.PROVIDERNOTFOUND  <br/> |
|AdoEnums.ErrorValue.STILLCONNECTING  <br/> |
|AdoEnums.ErrorValue.STILLEXECUTING  <br/> |
|AdoEnums.ErrorValue.UNSAFEOPERATION  <br/> |
   

