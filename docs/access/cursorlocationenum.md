---
title: "CursorLocationEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 520cc738-998b-ce80-6362-0df310c40c39
---

# CursorLocationEnum

Specifies the location of the cursor service.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adUseClient** <br/> |3  <br/> |Uses client-side cursors supplied by a local cursor library. Local cursor services often will allow many features that driver-supplied cursors may not, so using this setting may provide an advantage with respect to features that will be enabled. For backward compatibility, the synonym **adUseClientBatch** is also supported.  <br/> |
|**adUseNone** <br/> |1  <br/> |Does not use cursor services. (This constant is obsolete and appears solely for the sake of backward compatibility.)  <br/> |
|**adUseServer** <br/> |2  <br/> |Default. Uses data-provider or driver-supplied cursors. These cursors are sometimes very flexible and allow for additional sensitivity to changes others make to the data source. However, some features of the [Microsoft Cursor Service for OLE DB](microsoft-cursor-service-for-ole-db-ado-service-component.md) (such as disassociated [Recordset](recordset-object-ado.md) objects) cannot be simulated with server-side cursors and these features will be unavailable with this setting.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.CursorLocation.CLIENT  <br/> |
|AdoEnums.CursorLocation.NONE  <br/> |
|AdoEnums.CursorLocation.SERVER  <br/> |
   

