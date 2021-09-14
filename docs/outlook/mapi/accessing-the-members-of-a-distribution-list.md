---
title: "Accessing the Members of a Distribution List"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: f724cac8-2d5d-42bc-a15e-99f77a99ce21
description: "Last modified: July 23, 2011"
 
 
---

# Accessing the Members of a Distribution List

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 **To get the members of a distribution list**
  
1. Create a sized property tag array with the properties of the members you would like to retrieve, such as **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)), **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)), and **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md)).
    
2. Call [IAddrBook::OpenEntry](iaddrbook-openentry.md) to open the distribution list. 
    
3. Call the distribution list's **IABContainer::GetContentsTable** method to access its contents table. 
    
4. Call [HrQueryAllRows](hrqueryallrows.md) to retrieve all of the table's rows representing the members of the distribution list. 
    

