---
title: "Transport-Neutral Encapsulation Format (TNEF)"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 98d4fe3c-3908-4cd2-bfdb-ff1874a80b24
description: "Last modified: March 12, 2013"
 
 
---

# Transport-Neutral Encapsulation Format (TNEF)

 
  
**Applies to**: Outlook 
  
TNEF is a format for converting a set of MAPI properties—a MAPI message—into a serial data stream. The TNEF functions are primarily used by transport providers that need to encode MAPI message properties for transmission through a messaging system that does not support those properties directly. For example, an SMTP-based transport uses TNEF to encode properties like **PR_SENT_REPRESENTING_NAME** ( [PidTagSentRepresentingName](pidtagsentrepresentingname-canonical-property.md)), which do not have direct representations in the structure of an SMTP message.
  
The TNEF implementation defines several TNEF-specific attributes, each of which corresponds to a particular MAPI property. These attributes are used to encode their respective MAPI properties into the TNEF stream. In addition, a special attribute is defined that can be used to encapsulate any MAPI property that does not have a specific attribute corresponding to it. The reason these attributes are defined — instead of simply using a uniform encoding method for all MAPI properties — is to enable backward compatibility with non-MAPI-compliant software that is using TNEF.
  
The remainder of this section describes the structure and syntax of a TNEF stream, the mapping between MAPI properties and TNEF attributes, and important considerations for certain TNEF attributes.
  

