---
title: "PidTagProfileHomeServerFQDN Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 80273b50-bc16-4be2-8471-1a127b6786bb
description: "Enables Kerberos authentication of a profile configuration. Setting this property to the Domain Name of the user's directory server allows direct connection to the Domain Controller."
---

# PidTagProfileHomeServerFQDN Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Enables Kerberos authentication of a profile configuration.
  
****

|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_PROFILE_HOME_SERVER_FQDN  <br/> |
|Identifier:  <br/> |0x662A001F  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |MAPI profile configuration  <br/> |
   
## Remarks

Setting this property to the Domain Name of the user's directory server allows direct connection to the Domain Controller (DC), which is necessary for a profile that has been configured to use Kerberos authentication against Microsoft Exchange Server 2007 and earlier versions, by setting **RPC_C_AUTHN_GSS_KERBEROS** in **PR_PROFILE_AUTH_PACKAGE**.
  
> [!NOTE]
> Microsoft Exchange Server 2010 and Exchange Server 2013 handle address book calls made to the Client Access Server differently from the way in which Exchange Server 2007 and earlier versions handle them. The DSProxy process is no longer used, so Kerberos authentication may succeed. However, the client would still be communicating with the Exchange server instead of directly with the DC, which may not be desired: Setting **PR_PROFILE_HOME_SERVER_FQDN** avoids this. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCSTOR]](https://msdn.microsoft.com/library/d42ed1e0-3e77-4264-bd59-7afc583510e2%28Office.15%29.aspx)
  
> Specifies permissible operations for the core message store objects.
    
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

