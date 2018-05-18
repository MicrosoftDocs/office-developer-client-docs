---
title: "PidTagProfileServerVersion Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5d41a536-81ff-733c-2fd7-460798e057c8
description: "Last modified: March 09, 2015"
---

# PidTagProfileServerVersion Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies information about the version of Microsoft Exchange Server to which accounts in a Microsoft Outlook profile are connected.
  
## 

|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PROFILE_SERVER_VERSION  <br/> |
|Identifier:  <br/> |0x661B  <br/> |
|Property type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI profile configuration  <br/> |
   
## Remarks

A profile can specify one or more accounts that connect to an Exchange Server, but they must be connected to the same Exchange Server.
  
Versions of Outlook earlier than Microsoft Office Outlook 2007 can write to this property to store information about the version of Exchange Server to which the active profile is connected. However, the format of the version information varies for different versions of Exchange Server. For example, Outlook stores in **PR_PROFILE_SERVER_VERSION** the decimal value 6944 to represent only the major build number in the version identifier of **6.5.6944.3** for Microsoft Exchange Server 2003. For an Exchange 2007 connection, Outlook stores the major version number and the major build number in a concatenated hexadecimal representation of these numbers in the property. An Exchange 2007 version identifier of **8.0.685.24** has a major version number 8 and a major build number 685 in decimal. Converting both numbers to hexadecimal, you get 0x8 and 0x2AD. Concatenating these two numbers, Outlook stores the value 0x82AD in **PR_PROFILE_SERVER_VERSION** in hexadecimal representation. 
  
Outlook 2007 does not read or write to this property. It supports **[PR_PROFILE_SERVER_FULL_VERSION](pidtagprofileserverfullversion-canonical-property.md)**. 
  
Only one of **PR_PROFILE_SERVER_VERSION** or **PR_PROFILE_SERVER_FULL_VERSION** is likely to exist in a profile, but there is no guarantee that either always exists in a profile. Outlook does not write to either property until it has successfully connected to the Exchange Server. 
  
In the Outlook object model, you can use the **ExchangeMailboxServerVersion** property of the **NameSpace** object to find the version of Exchange Server on which the active mailbox is hosted. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

