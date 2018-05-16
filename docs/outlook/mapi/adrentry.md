---
title: "ADRENTRY"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ADRENTRY
api_type:
- COM
ms.assetid: 5fa091a4-3a84-4881-91b3-e34fd9ca6f38
description: "Last modified: March 09, 2015"
---

# ADRENTRY

  
  
**Applies to**: Outlook 
  
Describes zero or more properties that belong to a recipient.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _ADRENTRY
{
  ULONG ulReserved1;
  ULONG cValues;
  LPSPropValue rgPropVals;
} ADRENTRY, FAR *LPADRENTRY;

```

## Members

 **ulReserved1**
  
> Reserved; must be zero.
    
 **cValues**
  
> Count of properties in the property value array pointed to by the **rgPropVals** member. The **cValues** member can be zero. 
    
 **rgPropVals**
  
> Pointer to a property value array describing the properties for the recipient. The **rgPropVals** member can be NULL. 
    
## Remarks

An **ADRENTRY** structure describes properties that belong to a single recipient. The properties that are typically used to describe a recipient include the following: 
  
 **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md))
  
 **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md))
  
 **PR_EMAIL_ADDRESS** ( [PidTagEmailAddress](pidtagemailaddress-canonical-property.md))
  
 **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md))
  
When an entry identifier or **PR_ENTRYID** property appears in the [SPropValue](spropvalue.md) array for a recipient, this indicates that the recipient has been resolved. Clients call the [IAddrBook::ResolveName](iaddrbook-resolvename.md) method to make sure that all recipients in the recipient list of an outgoing message have been resolved. Only resolved recipients can be sent with messages. 
  
 **ADRENTRY** structures are typically combined to form an array for the **aEntries** member of an [ADRLIST](adrlist.md) structure. 
  
 **ADRENTRY** structures and [SRow](srow.md) structures are identical because they both contain a reserved member, an array of property values, and a count of values in the array. Whereas **ADRENTRY** structures are combined to form the **aEntries** member of an **ADRLIST** structure, **SRow** structures are combined to form the **aRow** member of an [SRowSet](srowset.md) structure. Both types of structures follow the same allocation rules, implying that an **SRowSet** structure that is retrieved from the contents table of an address book container can be cast to an **ADRLIST** structure and used as is. 
  
An **ADRENTRY** structure can be empty. For example, an **ADRENTRY** structure that is contained in the **ADRLIST** structure pointed to by the  _lppAdrList_ parameter in a call to **IAddrBook::Address** can be empty when a recipient is being removed. 
  
For more information about how to allocate memory for **ADRENTRY** structures, see [Managing Memory for ADRLIST and SRowSet Structures](managing-memory-for-adrlist-and-srowset-structures.md).
  
## See also

#### Reference

[IAddrBook::Address](iaddrbook-address.md)
  
[IMessage::ModifyRecipients](imessage-modifyrecipients.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[ADRLIST](adrlist.md)
  
[SRow](srow.md)
  
[SRowSet](srowset.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

