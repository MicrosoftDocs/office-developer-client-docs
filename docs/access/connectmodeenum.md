---
title: "ConnectModeEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: a15aa733-f899-5fe9-e705-67a4301706d1
---

# ConnectModeEnum

Specifies the available permissions for modifying data in a [Connection](connection-object-ado.md), opening a [Record](record-object-ado.md), or specifying values for the [Mode](mode-property-ado.md) property of the **Record** and [Stream](stream-object-ado.md) objects. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adModeRead** <br/> |1  <br/> |Indicates read-only permissions.  <br/> |
|**adModeReadWrite** <br/> |3  <br/> |Indicates read/write permissions.  <br/> |
|**adModeRecursive** <br/> |0x400000  <br/> |Used in conjunction with the other  *\*ShareDeny\**  values ( **adModeShareDenyNone**, **adModeShareDenyWrite**, or **adModeShareDenyRead** ) to propagate sharing restrictions to all sub-records of the current **Record**. It has no affect if the **Record** does not have any children. A run-time error is generated if it is used with **adModeShareDenyNone** only. However, it can be used with **adModeShareDenyNone** when combined with other values. For example, you can use " **adModeRead** Or **adModeShareDenyNone** Or **adModeRecursive** ".  <br/> |
|**adModeShareDenyNone** <br/> |16  <br/> |Allows others to open a connection with any permissions. Neither read nor write access can be denied to others.  <br/> |
|**adModeShareDenyRead** <br/> |4  <br/> |Prevents others from opening a connection with read permissions.  <br/> |
|**adModeShareDenyWrite** <br/> |8  <br/> |Prevents others from opening a connection with write permissions.  <br/> |
|**adModeShareExclusive** <br/> |12  <br/> |Prevents others from opening a connection.  <br/> |
|**adModeUnknown** <br/> |0  <br/> |Default. Indicates that the permissions have not yet been set or cannot be determined.  <br/> |
|**adModeWrite** <br/> |2  <br/> |Indicates write-only permissions.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.ConnectMode.READ  <br/> |
|AdoEnums.ConnectMode.READWRITE  <br/> |
|(There is no equivalent of AdoEnums.ConnectMode.RECURSIVE)  <br/> |
|AdoEnums.ConnectMode.SHAREDENYNONE  <br/> |
|AdoEnums.ConnectMode.SHAREDENYREAD  <br/> |
|AdoEnums.ConnectMode.SHAREDENYWRITE  <br/> |
|AdoEnums.ConnectMode.SHAREEXCLUSIVE  <br/> |
|AdoEnums.ConnectMode.UNKNOWN  <br/> |
|AdoEnums.ConnectMode.WRITE  <br/> |
   

