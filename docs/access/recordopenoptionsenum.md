---
title: "RecordOpenOptionsEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 44a69719-0789-a084-fb96-21468e270205

---

# RecordOpenOptionsEnum

Specifies options for opening a [Record](record-object-ado.md). These values may be combined by using OR.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adDelayFetchFields** <br/> |0x8000  <br/> |Indicates to the provider that the fields associated with the **Record** need not be retrieved initially, but can be retrieved at the first attempt to access the field. The default behavior, indicated by the absence of this flag, is to retrieve all the **Record** object fields.  <br/> |
|**adDelayFetchStream** <br/> |0x4000  <br/> |Indicates to the provider that the default stream associated with the **Record** need not be retrieved initially. The default behavior, indicated by the absence of this flag, is to retrieve the default stream associated with the **Record** object.  <br/> |
|**adOpenAsync** <br/> |0x1000  <br/> |Indicates that the **Record** object is opened in asynchronous mode.  <br/> |
|**adOpenExecuteCommand** <br/> |0x10000  <br/> |Indicates that the Source string contains command text that should be executed. This value is equivalent to the **adCmdText** option on **Recordset.Open**.  <br/> |
|**adOpenRecordUnspecified** <br/> |-1  <br/> |Default. Indicates no options are specified.  <br/> |
|**adOpenOutput** <br/> |0x800000  <br/> |Indicates that if the source points to a node that contains an executable script (such as an .ASP page), then the opened **Record** will contain the results of the executed script. This value is only valid with non-collection records.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

