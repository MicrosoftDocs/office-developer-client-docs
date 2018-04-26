---
title: "StreamOpenOptionsEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: d4bbd6be-41f1-cdf2-9d8f-b77ce83fb88e

---

# StreamOpenOptionsEnum

Specifies options for opening a [Stream](stream-object-ado.md) object. The values can be combined with an OR operation. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adOpenStreamAsync** <br/> |1  <br/> |Opens the **Stream** object in asynchronous mode.  <br/> |
|**adOpenStreamFromRecord** <br/> |4  <br/> |Identifies the contents of the  *Source*  parameter to be an already open [Record](record-object-ado.md) object. The default behavior is to treat  *Source*  as a URL that points directly to a node in a tree structure. The default stream associated with that node is opened.  <br/> |
|**adOpenStreamUnspecified** <br/> |-1  <br/> |Default. Specifies opening the **Stream** object with default options.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

