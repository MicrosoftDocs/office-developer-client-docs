---
title: "Form Configuration File [Extensions] Section"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 4817e446-982d-491c-abcf-cc888a771afa
description: "Last modified: July 23, 2011"
 
 
---

# Form Configuration File [Extensions] Section

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The **[Extensions]** section lists the extended attributes of the form, typically a named property set, which are any attributes beyond the basic ones listed in the **[Description]** section of the form configuration file. Extended attributes are properties returned from calls to the **GetProps** method of the **IMAPIFormInfo** object with the high bit set in the property tag. Client applications can determine a form's extended attributes, if any, by retrieving these tags. To do so, clients call the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) method, passing in the names of the form's properties and call the [IMAPIProp::GetProps](imapiprop-getprops.md) method to get the properties. 
  
 **[Extensions]**
  
 **Extension.** _string1_ =  _string2_
  
Each extension property section defines one extension attribute using the MAPI named property syntax. The property type must be either PT_LONG or PT_STRING8. Property sets that contains named strings are not supported. The format of the **[Extension]** section is: 
  
 **[Extension.** _string2_ **]**
  
 **Type** =  _integer_
  
 **NmidPropset** =  _guid_
  
 **NmidInteger** =  _integer_
  
 **Value** =  _string_ |  _integer_
  
An example of an **[Extensions]** section and a subsequent related section is shown following. 
  
```
[Extensions]
Extension.A = 1
[Extension.1]
Type = 30
NmidPropset = {00020D0C-0000-0000-C000-000000000046}
NmidInteger = 1
Value = 11220000

```


