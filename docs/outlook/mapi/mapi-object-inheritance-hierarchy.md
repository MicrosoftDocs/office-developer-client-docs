---
title: "MAPI Object Inheritance Hierarchy"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 3dc0b79f-e346-416d-ac81-42eba6b6d3b2
description: "Last modified: July 23, 2011"
---

# MAPI Object Inheritance Hierarchy

**Applies to**: Outlook 
  
All interfaces implemented by MAPI objects ultimately inherit from [IUnknown](http://msdn.microsoft.com/library/33f1d79a-33fc-4ce5-a372-e08bda378332%28Office.15%29.aspx), the OLE interface that enables objects to communicate. Most interfaces directly inherit from **IUnknown**, but some inherit from one of two other base interfaces: [IMAPIProp : IUnknown](imapipropiunknown.md) or [IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md). The following illustration shows the complete inheritance hierarchy in MAPI.
  
**MAPI inheritance hierarchy**
  
![MAPI inheritance hierarchy](media/amapi_06.gif)
  
## See also

- [IMAPIProp : IUnknown](imapipropiunknown.md) 
- [IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md)
- [MAPI Object and Interface Overview](mapi-object-and-interface-overview.md)

