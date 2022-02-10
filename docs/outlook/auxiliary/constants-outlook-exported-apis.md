---
title: "Constants (Outlook exported APIs)"
manager: lindalu
ms.date: 02/09/2022
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 7590a30e-3fd8-7ae3-f077-c80f6cc21d7b
description: "Constant definitions for APIs that Outlook exports."
---

# Constants (Outlook exported APIs)

This topic contains constant definitions for APIs that Outlook exports.
  
## Definitions for Time Zone support

```cpp
const ULONG TZ_MAX_RULES                    = 0x00000001;  
const BYTE  TZ_BIN_VERSION_MAJOR            = 0x02;  
const BYTE  TZ_BIN_VERSION_MINOR            = 0x01; 
const WORD  TZRULE_FLAG_RECUR_CURRENT_TZREG = 0x0001; 
const WORD  TZRULE_FLAG_EFFECTIVE_TZREG     = 0x0002; 
const WORD  TZDEFINITION_FLAG_VALID_KEYNAME = 0x0002;
```

## Definitions for Category support

|**Constant**|**Definition**|
|:-----|:-----|
|PCAFSIF_MSGEID_IS_SEARCH_KEY |0x00000001 |
   
## Miscellaneous dispatch identifiers

Outlook exposes the following dispatch identifiers (dispids) so that developers can use [IDispatch::Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke.md) to access the corresponding property or method, or listen to the corresponding event. 
  
|**Associated constant**|**Dispid value**|**Description**|**Applicable interface**|
|:-----|:-----|:-----|:-----|
|**dispidFDirty** | 0xF024 |Used to invoke the corresponding property on an item to verify whether the item has been modified but has not been saved. |Item-level objects |
|**dispidShowSenderPhoto** | 0xF0D0 |Used to invoke the corresponding method on the explorer or inspector to specify whether to display a contact's picture, based on a given argument. |Explorer or inspector |
|**dispidBeforePrint** | 0xFC8E |Used to handle the event from the **IDispatch::Invoke** function that fires before a printing operation. |Application |
|**dispidEventReadComplete** | 0xFC8F |Used to handle the event from the **IDispatch::Invoke** function that fires when Outlook has completed reading the properties of the item. |Item-level objects |
   
## See also

- [Outlook exported APIs](outlook-exported-apis.md)
- [About APIs exported by Outlook](about-apis-exported-by-outlook.md)
- [Determine whether an Outlook item has been modified but not saved (Outlook Auxiliary Reference)](how-to-determine-if-outlook-item-has-been-modified-but-not-saved.md)
- [Specify whether to display a contact's picture in Outlook (Outlook Auxiliary Reference)](https://docs.microsoft.com/previous-versions/office/gg262879(v=office.15))
- [Available events and their dispids (Outlook exported APIs)](available-events-and-their-dispids-outlook-exported-apis.md)
