---
title: "Centralizing the receipt of NDRs"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: fbe1f4f6-28f8-40b8-b551-192c0ba48c18
description: "Last modified: July 23, 2011"
---

# Centralizing the receipt of NDRs

**Applies to**: Outlook 2013 | Outlook 2016 
  
**To have nondelivery reports (NDRs) arrive at a central location when multiple instances of your client are running simultaneously**
  
1. Set **PR_REPORT_ENTRYID** ([PidTagReportEntryId](pidtagreportentryid-canonical-property.md)), **PR_REPORT_NAME** ([PidTagReportName](pidtagreportname-canonical-property.md)), and **PR_REPORT_SEARCH_KEY** ([PidTagReportSearchKey](pidtagreportsearchkey-canonical-property.md)) to the appropriate values for the account that is to receive the reports. Create the entry identifier by calling [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md) if necessary. 
    
2. Understand that there are messaging systems that will ignore the account you've requested for reports and send them to the originator. Reduce the impact that this will have on administrators that will need to move reports around by:
    
- Giving your original message a distinct message class, such as IPM.Note.MSNNews. Look for incoming messages with class Report.IPM.Note.MSNNews.NDR and forward them to the account you intended reports to come to. At the same time, send email to the messaging system that ignored your nondelivery report account to communicate that it should honor the **PR_REPORT_ENTRYID** property. 
    
- Most messaging systems which do not honor **PR_REPORT_ENTRYID** will not honor the MAPI message class conventions either. Therefore, you'll receive something that looks like a note. This is a little harder to deal with because the input is so variable. Look at the subject and forward it if you find either something from a list of words that mean "undeliverable" or something from your original subject. Be prepared to tune these lists over time. 
    

