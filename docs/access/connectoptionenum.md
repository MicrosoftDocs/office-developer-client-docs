---
title: "ConnectOptionEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 803d3fd6-93cf-85ea-eeb0-ca1bc965577d
---

# ConnectOptionEnum

Specifies whether the [Open](open-method-ado-connection.md) method of a [Connection](connection-object-ado.md) object should return after (synchronously) or before (asynchronously) the connection is established. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adAsyncConnect** <br/> |16  <br/> |Opens the connection asynchronously. The [ConnectComplete](connectcomplete-and-disconnect-events-ado.md) event may be used to determine when the connection is available.  <br/> |
|**adConnectUnspecified** <br/> |-1  <br/> |Default. Opens the connection synchronously.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.ConnectOption.ASYNCCONNECT  <br/> |
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED  <br/> |
   

