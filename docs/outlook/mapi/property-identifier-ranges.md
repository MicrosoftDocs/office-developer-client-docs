---
title: "Property Identifier Ranges"
description: Summarizes the different ranges for property identifiers, describing the owner for the properties in each range.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: c01e95bb-be25-490d-880b-60674f890258
 
 
---

# Property Identifier Ranges

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The following table summarizes the different ranges for property identifiers, describing the owner for the properties in each range.
  
|**Identifier range**|**Description**|
|:-----|:-----|
|0000  <br/> |Reserved by MAPI for the special value **PR_NULL**. |
|0001 - 0BFF  <br/> |Message envelope properties defined by MAPI. |
|0C00 - 0DFF  <br/> |Recipient properties defined by MAPI. |
|0E00 - 0FFF  <br/> |Non-transmittable message properties defined by MAPI. |
|1000 - 2FFF  <br/> |Message content properties defined by MAPI. |
|3000 - 3FFF  <br/> |Properties for objects other than messages and recipients defined by MAPI. |
|4000 - 57FF  <br/> |Message envelope properties defined by transport providers. |
|5800 - 5FFF  <br/> |Recipient properties defined by transport and address book providers. |
|6000 - 65FF  <br/> |Non-transmittable message properties defined by clients. |
|6600 - 67FF  <br/> |Non-transmittable properties defined by a service provider. These properties can be visible or invisible to users. |
|6800 - 7BFF  <br/> |Message content properties for custom message classes defined by creators of those classes. |
|7C00 - 7FFF  <br/> |Non-transmittable properties for custom message classes defined by creators of those classes. |
|8000 - FFFE  <br/> |Properties defined by clients and occasionally service providers that are identified by name through the [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) and [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) methods. |
|FFFF  <br/> |Reserved by MAPI for the special error value PROP_ID_INVALID. |
   
The range between 3000 and 3FFF is reserved for properties that are not related to either messages or recipients. MAPI divides this range into sub-ranges by types of object; the following table shows this further breakdown. 
  
|**Identifier range**|**Type of property**|
|:-----|:-----|
|3000 - 33FF  <br/> |Common properties that appear on multiple objects, such as **PR_DISPLAY_NAME** and **PR_ENTRYID**. |
|3400 - 35FF  <br/> |Message store properties  <br/> |
|3600 - 36FF  <br/> |Folder and address book container properties  <br/> |
|3700 - 38FF  <br/> |Attachment properties  <br/> |
|3900 - 39FF  <br/> |Address book properties  <br/> |
|3A00 - 3BFF  <br/> |Messaging user properties  <br/> |
|3C00 - 3CFF  <br/> |Distribution list properties  <br/> |
|3D00 - 3DFF  <br/> |Profile properties  <br/> |
|3E00 - 3FFF  <br/> |Status object properties  <br/> |
   

