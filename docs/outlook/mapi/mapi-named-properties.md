---
title: "MAPI Named Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 464b1297-9d90-47bd-afc4-3dc63b106cb7
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Named Properties

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
MAPI provides a facility for assigning names to properties, for mapping these names to unique identifiers, and for making this mapping persistent. Persistent name to identifier mapping ensures that property names remain valid across sessions.
  
To define a named property, a client or service provider makes up a name and stores it in a [MAPINAMEID](mapinameid.md) structure. Because names are made up of a 32-bit globally unique identifier, or GUID, and either a Unicode character string or numeric value, creators of named properties can create meaningful names without fear of duplication. Names are unique and they can be used without regard to the value of their identifiers. 
  
To support named properties, a service provider implements two methods — [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) and [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) — to translate between names and identifiers and to allow its [IMAPIProp::GetProps](imapiprop-getprops.md)[IMAPIProp::SetProps](imapiprop-setprops.md) methods to retrieve and modify properties with identifiers in the named property range. The range for named property identifiers is between 0x8000 and 0xFFFE. 
  
Any object that implements the **IMAPIProp** interface can support named properties. Address book providers that allow entries from other providers to be copied into their containers and message store providers that can be used to create arbitrary message types are required to supply this support. It is an option for all other service providers. Providers that do not support named properties return MAPI_E_NO_SUPPORT from the **GetIDsFromNames** and **GetNamesFromIDs** methods and refuse to set any properties with identifiers of 0x8000 or greater, returning MAPI_E_UNEXPECTED in the **SPropProblemarray**.
  
Creating names for properties is one way for clients to define new properties for existing or custom message classes. Service providers can use named properties to expose unique features of their messaging systems. Yet another use for named properties is to provide an alternate way of referring to properties with identifiers below 0x8000. 
  
For example, a client could use code similar to the following code to retrieve the names for all of an object's named properties:
  
```
LPSPropTagArray FAR *    lppPropTags = NULL;
LPGUID                   lpPropSetGuid = NULL;
ULONG FAR *              lpcPropNames;
LPMAPINAMEID FAR * FAR * lpppPropNames;
lpMAPIProp->GetNamesFromIDs (lppPropTags,
                             lpPropSetGuid,
                             0,
                             lpcPropNames,
                             lpppPropNames);
 
```

To request all names from the PS_PUBLIC_STRINGS property set, a client would replace the NULL in the property set parameter to PS_PUBLIC_STRINGS as follows: 
  
```
LPSPropTagArray FAR *    lppPropTags = NULL;
LPGUID                   lpPropSetGuid = &amp;PS_PUBLIC_STRINGS;
ULONG FAR *              lpcPropNames;
LPMAPINAMEID FAR * FAR * lpppPropNames;
lpMAPIProp->GetNamesFromIDs (lppPropTags,
                             lpPropSetGuid,
                             0,
                             lpcPropNames,
                             lpppPropNames);
 
```

## See also

#### Concepts

[MAPI Property Overview](mapi-property-overview.md)

