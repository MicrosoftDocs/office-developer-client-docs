---
title: "MAPI Interfaces"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 34a66cf0-b4e0-4fd5-b937-cd157888961d
description: "Last modified: March 09, 2015"
---

# MAPI Interfaces

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The documentation for each interface consists of an introductory section that includes a brief description of the interface's purpose followed by a table that contains the following information.
  
|||
|:-----|:-----|
|Header file:  <br/> |The header file where the interface is defined and that must be included when you compile your source code. |
|Exposed by:  <br/> |The object that exposes the interface. |
|Implemented by:  <br/> |A list of the components that provide an implementation of the interface. |
|Called by:  <br/> |A list of the components that typically call the methods of the interface. |
|Interface identifier:  <br/> |The interface identifier GUID. |
|Pointer type:  <br/> |The pointer type for the object that exposes the interface. |
|Transaction model:  <br/> |For interfaces derived from [IMAPIProp](imapipropiunknown.md). If nontransacted, changes take effect immediately; if transacted, changes do not take effect until [IMAPIProp::SaveChanges](imapiprop-savechanges.md) is called. |
   
Following the first table is another table that lists all the methods of this interface in vtable order. A vtable is an array of function pointers created by the compiler containing one function pointer for each method of a MAPI object. The methods are listed in the same order that they are declared. Methods inherited from other interfaces are not shown in the Vtable Order table but can be used in the same way as documented in the interface that defines them.
  
After each interface topic, the interface's methods are then documented in alphabetical order. For each method, the documentation includes a brief purpose statement, a syntax block, and the following information.
  
|**Heading**|**Content**|
|:-----|:-----|
|Parameters  <br/> |A description of each parameter in the method. |
|Return Value  <br/> |A description of the unique values that the method can return. These are the values that callers should check for in their code. |
|Remarks  <br/> |A description of why and how the method is used. |
|See Also  <br/> |Cross-references to other topics in this Reference. |
   
## See also



[MAPI Reference](mapi-reference.md)

