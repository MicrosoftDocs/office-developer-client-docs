---
title: "PidTagRpcOverHttpProxyAuthScheme Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 6da78f1a-6423-460c-b3a9-fd6441df9cef
description: "Represents the authentication protocol to be used for this profile. This property can be set for either basic authentication or NT LAN Manager authentication."
---

# PidTagRpcOverHttpProxyAuthScheme Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Represents the authentication protocol to be used for this profile.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ROH_PROXY_AUTH_SCHEME  <br/> |
|Identifier:  <br/> |0x6627  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Miscellaneous  <br/> |
   
## Remarks

This property can be set for either basic authentication or NT LAN Manager (NTLM) authentication. The possible values for this property are as follow.
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**ROHAUTH_BASIC** <br/> |0x1  <br/> |Basic authentication  <br/> |
|**ROHAUTH_NTLM** <br/> |0x2  <br/> |NTLM authentication  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCFXICS]](https://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Defines the basic data structures that are used in remote operations.
    
[[MS-OXOMSG]](https://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
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

