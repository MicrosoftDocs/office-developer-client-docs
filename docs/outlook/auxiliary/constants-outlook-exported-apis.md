---
title: "Constants (Outlook exported APIs)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 7590a30e-3fd8-7ae3-f077-c80f6cc21d7b
description: "This topic contains constant definitions for APIs that Outlook exports."
---

# Constants (Outlook exported APIs)

This topic contains constant definitions for APIs that Outlook exports.
  
## Definitions for Time Zone Support

```
const ULONG TZ_MAX_RULES                    = 0x00000001;  
const BYTE  TZ_BIN_VERSION_MAJOR            = 0x02;  
const BYTE  TZ_BIN_VERSION_MINOR            = 0x01; 
const WORD  TZRULE_FLAG_RECUR_CURRENT_TZREG = 0x0001; 
const WORD  TZRULE_FLAG_EFFECTIVE_TZREG     = 0x0002; 
const WORD  TZDEFINITION_FLAG_VALID_KEYNAME = 0x0002;
```

## Definitions for Category Support

|**Constant**|**Definition**|
|:-----|:-----|
|PCAFSIF_MSGEID_IS_SEARCH_KEY  <br/> |0x00000001  <br/> |
   
## Miscellaneous Dispatch Identifiers

Outlook exposes the following dispatch identifiers (dispids) so that developers can use [IDispatch::Invoke](http://msdn.microsoft.com/library/automat.idispatch_invoke%28Office.15%29.aspx) to access the corresponding property or method, or listen to the corresponding event. 
  
|**Associated constant**|**Dispid value**|**Description**|**Applicable interface**|
|:-----|:-----|:-----|:-----|
|**dispidFDirty** <br/> |0xF024  <br/> |Used to invoke the corresponding property on an item to verify whether the item has been modified but has not been saved.  <br/> |Item-level objects  <br/> |
|**dispidShowSenderPhoto** <br/> |0xF0D0  <br/> |Used to invoke the corresponding method on the explorer or inspector to specify whether to display a contact's picture, based on a given argument.  <br/> |Explorer or inspector  <br/> |
|**dispidBeforePrint** <br/> |0xFC8E  <br/> |Used to handle the event from the **IDispatch::Invoke** function that fires before a printing operation.  <br/> |Application  <br/> |
|**dispidEventReadComplete** <br/> |0xFC8F  <br/> |Used to handle the event from the **IDispatch::Invoke** function that fires when Outlook has completed reading the properties of the item.  <br/> |Item-level objects  <br/> |
   
## See also

#### Concepts

[Outlook exported APIs](outlook-exported-apis.md)
  
[About APIs exported by Outlook](about-apis-exported-by-outlook.md)
  
[Determine whether an Outlook item has been modified but not saved (Outlook Auxiliary Reference)](how-to-determine-whether-an-outlook-item-has-been-modified-but-not-saved-outlook.md)
  
[Specify whether to display a contact's picture in Outlook (Outlook Auxiliary Reference)](https://msdn.microsoft.com/en-us/library/office/gg262879.aspx)
  
[Available events and their dispids (Outlook exported APIs)](available-events-and-their-dispids-outlook-exported-apis.md)

