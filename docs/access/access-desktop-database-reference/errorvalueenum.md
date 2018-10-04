---
title: ErrorValueEnum
TOCTitle: ErrorValueEnum
ms:assetid: 2af99f32-6004-1225-367c-45d693f447b8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249058(v=office.15)
ms:contentKeyID: 48543921
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ErrorValueEnum


**Applies to**: Access 2013 | Office 2013

Specifies the type of ADO run-time error.

Three forms of the error number are listed:

  - Positive decimal — the low two bytes of the full number in decimal format. This number is displayed in the default Visual Basic error message dialog box. For example, Run-time error '3707'.

  - Negative decimal — The decimal translation of the full error number.

  - Hexadecimal — The hexadecimal representation of the full error number. The Windows facility code is in the fourth digit. The facility code for ADO error numbers is *A*. For example: 0x800***A***0E7B.


> [!NOTE]
> <P>OLE DB errors may be passed to your ADO application. Typically, these can be identified by a Windows facility code of <EM>4</EM>. For example, 0x800<STRONG><EM>4</EM></STRONG>.... For more information about these numbers, see Chapter 16 of the <EM>OLE DB Programmer's Reference.</EM></P>



<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>adErrBoundToCommand</strong></p></td>
<td><p>3707<br />
-2146824581<br />
0x800A0E7B</p></td>
<td><p>Cannot change the <strong>ActiveConnection</strong> property of a <strong>Recordset</strong> object which has a <strong>Command</strong> object as its source.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrCannotComplete</strong></p></td>
<td><p>3732<br />
-2146824556<br />
0x800A0E94</p></td>
<td><p>Server cannot complete the operation.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrCantChangeConnection</strong></p></td>
<td><p>3748<br />
-2146824540<br />
0x800A0EA4</p></td>
<td><p>Connection was denied. New connection you requested has different characteristics than the one already in use.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrCantChangeProvider</strong></p></td>
<td><p>3220<br />
-2146825068<br />
0X800A0C94</p></td>
<td><p>Supplied provider is different from the one already in use.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrCantConvertvalue</strong></p></td>
<td><p>3724<br />
-2146824564<br />
0x800A0E8C</p></td>
<td><p>Data value cannot be converted for reasons other than sign mismatch or data overflow. For example, conversion would have truncated data.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrCantCreate</strong></p></td>
<td><p>3725<br />
-2146824563<br />
0x800A0E8D</p></td>
<td><p>Data value cannot be set or retrieved because the field data type was unknown, or the provider had insufficient resources to perform the operation.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrCatalogNotSet</strong></p></td>
<td><p>3747<br />
-2146824541<br />
0x800A0EA3</p></td>
<td><p>Operation requires a valid <strong>ParentCatalog</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrColumnNotOnThisRow</strong></p></td>
<td><p>3726<br />
-2146824562<br />
0x800A0E8E</p></td>
<td><p>Record does not contain this field.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrDataConversion</strong></p></td>
<td><p>3421<br />
-2146824867<br />
0x800A0D5D</p></td>
<td><p>Application uses a value of the wrong type for the current operation.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrDataOverflow</strong></p></td>
<td><p>3721<br />
-2146824567<br />
0x800A0E89</p></td>
<td><p>Data value is too large to be represented by the field data type.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrDelResOutOfScope</strong></p></td>
<td><p>3738<br />
-2146824550<br />
0x800A0E9A</p></td>
<td><p>URL of the object to be deleted is outside the scope of the current record.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrDenyNotSupported</strong></p></td>
<td><p>3750<br />
-2146824538<br />
0x800A0EA6</p></td>
<td><p>Provider does not support sharing restrictions.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrDenyTypeNotSupported</strong></p></td>
<td><p>3751<br />
-2146824537<br />
0x800A0EA7</p></td>
<td><p>Provider does not support the requested kind of sharing restriction.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrFeatureNotAvailable</strong></p></td>
<td><p>3251<br />
-2146825037<br />
0x800A0CB3</p></td>
<td><p>Object or provider is not capable of performing requested operation.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrFieldsUpdateFailed</strong></p></td>
<td><p>3749<br />
-2146824539<br />
0x800A0EA5</p></td>
<td><p>Fields update failed. For further information, examine the <strong>Status</strong> property of individual field objects.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrIllegalOperation</strong></p></td>
<td><p>3219<br />
-2146825069<br />
0x800A0C93</p></td>
<td><p>Operation is not allowed in this context.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrIntegrityViolation</strong></p></td>
<td><p>3719<br />
-2146824569<br />
0x800A0E87</p></td>
<td><p>Data value conflicts with the integrity constraints of the field.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrInTransaction</strong></p></td>
<td><p>3246<br />
-2146825042<br />
0x800A0CAE</p></td>
<td><p><strong>Connection</strong> object cannot be explicitly closed while in a transaction.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrInvalidArgument</strong></p></td>
<td><p>3001<br />
-2146825287<br />
0x800A0BB9</p></td>
<td><p>Arguments are of the wrong type, are out of acceptable range, or are in conflict with one another.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrInvalidConnection</strong></p></td>
<td><p>3709<br />
-2146824579<br />
0x800A0E7D</p></td>
<td><p>The connection cannot be used to perform this operation. It is either closed or invalid in this context.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrInvalidParamInfo</strong></p></td>
<td><p>3708<br />
-2146824580<br />
0x800A0E7C</p></td>
<td><p><strong>Parameter</strong> object is improperly defined. Inconsistent or incomplete information was provided.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrInvalidTransaction</strong></p></td>
<td><p>3714<br />
-2146824574<br />
0x800A0E82</p></td>
<td><p>Coordinating transaction is invalid or has not started.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrInvalidURL</strong></p></td>
<td><p>3729<br />
-2146824559<br />
0x800A0E91</p></td>
<td><p>URL contains invalid characters. Make sure the URL is typed correctly.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrItemNotFound</strong></p></td>
<td><p>3265<br />
-2146825023<br />
0x800A0CC1</p></td>
<td><p>Item cannot be found in the collection corresponding to the requested name or ordinal.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrNoCurrentRecord</strong></p></td>
<td><p>3021<br />
-2146825267<br />
0x800A0BCD</p></td>
<td><p>Either <strong>BOF</strong> or <strong>EOF</strong> is True, or the current record has been deleted. Requested operation requires a current record.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrNotExecuting</strong></p></td>
<td><p>3715<br />
-2146824573<br />
0x800A0E83</p></td>
<td><p>Operation cannot be performed while not executing.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrNotReentrant</strong></p></td>
<td><p>3710<br />
-2146824578<br />
0x800A0E7E</p></td>
<td><p>Operation cannot be performed while processing event.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrObjectClosed</strong></p></td>
<td><p>3704<br />
-2146824584<br />
0x800A0E78</p></td>
<td><p>Operation is not allowed when the object is closed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrObjectInCollection</strong></p></td>
<td><p>3367<br />
-2146824921<br />
0x800A0D27</p></td>
<td><p>Object is already in collection. Cannot append.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrObjectNotSet</strong></p></td>
<td><p>3420<br />
-2146824868<br />
0x800A0D5C</p></td>
<td><p>Object is no longer valid.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrObjectOpen</strong></p></td>
<td><p>3705<br />
-2146824583<br />
0x800A0E79</p></td>
<td><p>Operation is not allowed when the object is open.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrOpeningFile</strong></p></td>
<td><p>3002<br />
-2146825286<br />
0x800A0BBA</p></td>
<td><p>File could not be opened.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrOperationCancelled</strong></p></td>
<td><p>3712<br />
-2146824576<br />
0x800A0E80</p></td>
<td><p>Operation has been cancelled by the user.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrOutOfSpace</strong></p></td>
<td><p>3734<br />
-2146824554<br />
0x800A0E96</p></td>
<td><p>Operation cannot be performed. Provider cannot obtain enough storage space.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrPermissionDenied</strong></p></td>
<td><p>3720<br />
-2146824568<br />
0x800A0E88</p></td>
<td><p>Insufficent permission prevents writing to the field.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrProviderFailed</strong></p></td>
<td><p>3000<br />
-2146825288<br />
0x800A0BB8</p></td>
<td><p>Provider failed to perform the requested operation.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrProviderNotFound</strong></p></td>
<td><p>3706<br />
-2146824582<br />
0x800A0E7A</p></td>
<td><p>Provider cannot be found. It may not be properly installed.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrReadFile</strong></p></td>
<td><p>3003<br />
-2146825285<br />
0x800A0BBB</p></td>
<td><p>File could not be read.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrResourceExists</strong></p></td>
<td><p>3731<br />
-2146824557<br />
0x800A0E93</p></td>
<td><p>Copy operation cannot be performed. Object named by destination URL already exists. Specify <strong>adCopyOverwrite</strong> to replace the object.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrResourceLocked</strong></p></td>
<td><p>3730<br />
-2146824558<br />
0x800A0E92</p></td>
<td><p>Object represented by the specified URL is locked by one or more other processes. Wait until the process has finished and attempt the operation again.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrResourceOutOfScope</strong></p></td>
<td><p>3735<br />
-2146824553<br />
0x800A0E97</p></td>
<td><p>Source or destination URL is outside the scope of the current record.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrSchemaViolation</strong></p></td>
<td><p>3722<br />
-2146824566<br />
0x800A0E8A</p></td>
<td><p>Data value conflicts with the data type or constraints of the field.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrSignMismatch</strong></p></td>
<td><p>3723<br />
-2146824565<br />
0x800A0E8B</p></td>
<td><p>Conversion failed because the data value was signed and the field data type used by the provider was unsigned.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrStillConnecting</strong></p></td>
<td><p>3713<br />
-2146824575<br />
0x800A0E81</p></td>
<td><p>Operation cannot be performed while connecting aynchronously.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrStillExecuting</strong></p></td>
<td><p>3711<br />
-2146824577<br />
0x800A0E7F</p></td>
<td><p>Operation cannot be performed while executing asynchronously.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrTreePermissionDenied</strong></p></td>
<td><p>3728<br />
-2146824560<br />
0x800A0E90</p></td>
<td><p>Permissions are insufficient to access tree or subtree.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrUnavailable</strong></p></td>
<td><p>3736<br />
-2146824552<br />
0x800A0E98</p></td>
<td><p>Operation failed to complete and the status is unavailable. The field may be unavailable or the operation was not attempted.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrUnsafeOperation</strong></p></td>
<td><p>3716<br />
-2146824572<br />
0x800A0E84</p></td>
<td><p>Safety settings on this computer prohibit accessing a data source on another domain.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrURLDoesNotExist</strong></p></td>
<td><p>3727<br />
-2146824561<br />
0x800A0E8F</p></td>
<td><p>Either the source URL or the parent of the destination URL does not exist.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrURLNamedRowDoesNotExist</strong></p></td>
<td><p>3737<br />
-2146824551<br />
0x800A0E99</p></td>
<td><p>Record named by this URL does not exist.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adErrVolumeNotFound</strong></p></td>
<td><p>3733<br />
-2146824555<br />
0x800A0E95</p></td>
<td><p>Provider cannot locate the storage device indicated by the URL. Make sure the URL is typed correctly.</p></td>
</tr>
<tr class="even">
<td><p><strong>adErrWriteFile</strong></p></td>
<td><p>3004<br />
-2146825284<br />
0x800A0BBC</p></td>
<td><p>Write to file failed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>adWrnSecurityDialog</strong></p></td>
<td><p>3717<br />
-2146824571<br />
0x800A0E85</p></td>
<td><p>For internal use only. Don't use.</p></td>
</tr>
<tr class="even">
<td><p><strong>adWrnSecurityDialogHeader</strong></p></td>
<td><p>3718<br />
-2146824570<br />
0x800A0E86</p></td>
<td><p>For internal use only. Don't use.</p></td>
</tr>
</tbody>
</table>


**ADO/WFC Equivalent**

Package: **com.ms.wfc.data**

Only the following subsets of ADO/WFC equivalents are defined.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.BOUNDTOCOMMAND</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.DATACONVERSION</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.FEATURENOTAVAILABLE</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.ILLEGALOPERATION</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.INTRANSACTION</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.INVALIDARGUMENT</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.INVALIDCONNECTION</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.INVALIDPARAMINFO</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.ITEMNOTFOUND</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.NOCURRENTRECORD</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.NOTEXECUTING</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.NOTREENTRANT</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.OBJECTCLOSED</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.OBJECTINCOLLECTION</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.OBJECTNOTSET</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.OBJECTOPEN</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.OPERATIONCANCELLED</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.PROVIDERNOTFOUND</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.STILLCONNECTING</p></td>
</tr>
<tr class="even">
<td><p>AdoEnums.ErrorValue.STILLEXECUTING</p></td>
</tr>
<tr class="odd">
<td><p>AdoEnums.ErrorValue.UNSAFEOPERATION</p></td>
</tr>
</tbody>
</table>

