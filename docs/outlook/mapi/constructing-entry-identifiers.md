---
title: "Constructing Entry Identifiers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: bc2a9116-948e-4da3-96b8-26d73bcd63c4
description: "Last modified: July 23, 2011"
 
 
---

# Constructing Entry Identifiers

  
  
**Applies to**: Outlook 
  
Entry identifiers are constructed with the [ENTRYID](entryid.md) structure. The **ENTRYID** structure is composed of a flag that describes the attributes of the entry identifier and the actual entry identifier. 
  
## ENTRYID Structure

The **ENTRYID** structure is defined as follows: 
  
```
typedef struct
{
    BYTE        abFlags[4];
    BYTE        ab[MAPI_DIM];
}  ENTRYID, FAR *LPENTRYID;
 
```

MAPI_DIM is a constant that is defined in the MapiDefs.h header file. 
  
The first byte of the 4-byte **abFlags** member describes the type and use of the entry identifier and can have the following values: 
  
- MAPI_NOTRECI — Indicates the entry identifier cannot be used as a recipient on a message.
    
- MAPI_NOTRESERVED — Indicates that other users cannot access the entry identifier.
    
- MAPI_NOW — Indicates that the entry identifier cannot be used at other times.
    
- MAPI_SHORTTERM — Indicates that the entry identifier is short-term. All other values in this byte must be set unless other uses of the entry identifier are allowed.
    
- MAPI_THISSESSION — Indicates that the entry identifier cannot be used on other sessions.
    
- MAPI_NOTRESERVED — Indicates that the entry identifier can be used by other service providers for other objects.
    
The **ab** member of entry identifiers that is created by address book and message store providers is composed of two pieces: a 16-byte [MAPIUID](mapiuid.md) structure that identifies the service provider, and a piece to identify the object. **MAPIUID** is a structure that contains a globally unique identifier, or GUID. A GUID is a byte-order-independent identifier that can be created by using the Microsoft Visual Studio **Create GUID** tool. 
  
A service provider registers its **MAPIUID** structure with MAPI during the logon process in a call to the [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md) method. When a client calls an **OpenEntry** method to access an object, MAPI uses the **MAPIUID** structure to determine which service provider can provide that access. Service providers should use the same **MAPIUID** structure for all versions of their DLL. This enables clients with the newer version to respond to messages sent and saved with the older version. 
  
The rest of the **ab** member after the 16-byte **MAPIUID** contains service-provider-specific binary data for identifying particular objects. There is no fixed size for this portion of the entry identifier. It can be any size, within reason. A service provider typically includes the following information in this part of its entry identifiers: 
  
- Version information — Because it is common for a service provider to change the format of its entry identifiers from version to version, storing version information makes it possible to quickly determine how to decipher any entry identifier.
    
- Location information — Location information is data that gives a service provider an indicator of how to locate the object represented by the entry identifier. For example, a service provider can store the disk offset for the last place in a data file that the object was stored. Because this type of information can change over time, service providers should provide multiple ways for locating objects in their entry identifiers.
    
Although service providers can recycle their entry identifiers, they should avoid this practice. If it is necessary to reuse an entry identifier, service providers should make the time period that elapses between the initial use and the reuse as long as possible. Also, the entry identifier should be reassigned to another object of the same type. That is, a particular entry identifier should not be associated first with a message and then with a folder.
  
## See also

#### Concepts

[MAPI Entry Identifiers](mapi-entry-identifiers.md)

