---
title: "PidLidCustomFlag Canonical Property"
description: Outlines the PidLidCustomFlag canonical property, which is a bitmask that specifies how a message is customized, for example, saved with custom properties.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidCustomFlag
api_type:
- COM
ms.assetid: bfb7fd1e-774f-9a2f-fbbe-ba7f68ed8663
---

# PidLidCustomFlag Canonical Property

**Applies to**: Outlook 2013 | Outlook 2016
  
A bitmask that specifies how a message is customized, for example, saved with custom properties.

|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |dispidCustomFlag  <br/> |
|Long ID (LID):  <br/> |0x00008251  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |

## Remarks

To retrieve the value of this property, first use **[IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md)** to obtain the property tag, and then specify this property tag in **[IMAPIProp::GetProps](imapiprop-getprops.md)** to get the value.
  
Possible Flags are as follows:
  
****

|**Constant**|**Value**|
|:-----|:-----|
|INSP_ONEOFFFLAGS  <br/> |0x0D000000  <br/> |
|INSP_PROPDEFINITION  <br/> |0x02000000  <br/> |

When calling **IMAPIProp::GetIDsFromNames**, specify the following values for the **[MAPINAMEID](mapinameid.md)** structure pointed to by the input parameter *lppPropNames*.
  
****

|**Member**|**Value**|
|:-----|:-----|
|lpGuid:  <br/> |PSETID_Common  <br/> |
|ulKind:  <br/> |MNID_ID  <br/> |
|Kind.lID:  <br/> |dispidCustomFlag  <br/> |

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
