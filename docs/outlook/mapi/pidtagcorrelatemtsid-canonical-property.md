---
title: "PidTagCorrelateMtsid Canonical Property"
description: Outlines the PidTagCorrelateMtsid canonical property, which contains the MTS identifier used in correlating reports with sent messages.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagCorrelateMtsid
api_type:
- HeaderDef
ms.assetid: d0fc4e91-ed90-4d27-bd23-f01e99728e2d
---

# PidTagCorrelateMtsid Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the message transfer system (MTS) identifier used in correlating reports with sent messages.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CORRELATE_MTSID  <br/> |
|Identifier:  <br/> |0x0E0D  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Exchange  <br/> |
   
## Remarks

When a transport provider encounters a submitted message with this property set to TRUE, it sets this property to the MTS identifier for that message. Following transmission, this property is stored with the message in the interpersonal message (IPM) Sent Items folder.
  
Messaging systems that support correlation by MTS identifier, such as X.400, retain the identifier as part of the transport envelope of the original message and also of any reports generated in response to it. When a report is delivered from such a messaging system, the transport provider sets this property to the original MTS identifier from the report's transport envelope. This property is then stored with the report.
  
A client application can maintain a search-results folder of all messages having this property. When a report comes in for such a message, the client can apply restrictions to the search-results folder, find the original version of the message, and correlate the original message information with the new information.
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

