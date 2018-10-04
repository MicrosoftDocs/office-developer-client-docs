---
title: "PidTagProfileServerFullVersion Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8c88a625-da57-3b1d-9887-0a898b722766
description: "Last modified: March 09, 2015"
---

# PidTagProfileServerFullVersion Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies complete version and build information about the Microsoft Exchange Server to which accounts in a profile are connected.
  
## 

|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PROFILE_SERVER_FULL_VERSION  <br/> |
|Identifier:  <br/> |0x663B  <br/> |
|Property type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI profile configuration  <br/> |
   
## Remarks

A profile can specify one or more accounts that connect to an Exchange Server, but they must be connected to the same Exchange Server.
  
Versions of Outlook earlier than Microsoft Office Outlook 2007 do not support this property. For those versions of Outlook, check for the existence of **[PR_PROFILE_SERVER_VERSION](pidtagprofileserverversion-canonical-property.md)** in the profile. 
  
Generally, if the active mailbox is connected to an Exchange Server, Outlook 2007 stores complete Exchange Server version information in the **PR_PROFILE_SERVER_FULL_VERSION** property in the active profile. Outlook stores the information in an **EXCHANGE_STORE_VERSION_NUM** structure that contains the major and minor version numbers and the major and minor build numbers. For example, to store the Exchange Server version identifier of **8.0.685.24**, the major version number is 8 and minor version number is 0, and the major build number is 685 and minor build number is 24.
  
Only one of **PR_PROFILE_SERVER_VERSION** or **PR_PROFILE_SERVER_FULL_VERSION** is likely to exist in a profile, but there is no guarantee that either always exists in a profile. Outlook does not write to either property until it has successfully connected to the Exchange Server. 
  
In the Outlook object model, you can use the **ExchangeMailboxServerVersion** property of the **NameSpace** object to find the version of Exchange Server on which the active mailbox is hosted. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
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

