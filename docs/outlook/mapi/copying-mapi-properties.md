---
title: "Copying MAPI Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: a52f4bcd-6e17-4623-a469-53be1f2758b1
 
 
---

# Copying MAPI Properties

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Clients and service providers can copy one or more of an object's properties with the following **IMAPIProp** methods and API functions: 
  
- The [IMAPIProp::CopyTo](imapiprop-copyto.md) method copies all of an object's properties to another object, optionally excluding selected properties. **CopyTo** is used for copying or moving any type of object. 
    
- The [IMAPIProp::CopyProps](imapiprop-copyprops.md) method copies selected properties of an object. **CopyProps** is used mainly with messages. When a client creates a forwarded copy of a message or a reply, **CopyProps** handles copying the appropriate properties from the original message. 
    
- The [PropCopyMore](propcopymore.md) function copies a single property value from one location to another. Use **PropCopyMore** with caution. It is possible — when copying one value at a time — to allocate many small blocks of memory and cause memory to fragment. 
    
- The [ScCopyProps](sccopyprops.md) function copies property values in bulk. **ScCopyProps** can copy property values that have been built from disjointed blocks of memory. It returns a new property array. 
    
- If the property array returned by **ScCopyProps** is to be stored on disk, use the [ScRelocProps](screlocprops.md) function to adjust the pointers. **ScRelocProps** should be called twice; once to adjust the addresses before writing the data operation and then again during the read operation. The **ScRelocProps** function assumes that the property value array was originally allocated in a single allocation. 
    
The API functions described in the preceding list copy properties in memory rather than from one object to another object. These functions are presently supported, but might not be supported in a future release.
  
## See also



[MAPI Property Overview](mapi-property-overview.md)

