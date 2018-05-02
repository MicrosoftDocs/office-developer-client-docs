---
title: "Preparing a Recipient"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 9573f10c-66e1-4e87-93f0-89687e906b8b
description: "Last modified: July 23, 2011"
 
 
---

# Preparing a Recipient

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
A client application prepares recipients by converting their short-term entry identifiers to long-term entry identifiers and possibly adding, changing, or reordering properties. You can prepare recipients that are part of a recipient list for a message or recipients that are unrelated to a message. Typically, clients call [IAddrBook::PrepareRecips](iaddrbook-preparerecips.md) directly to translate short-term entry identifiers into long-term entry identifiers for recipients that are included in the common address dialog box. For recipients that are associated with an outgoing message, recipient preparation is handled by the name resolution process. 
  
To prepare a list of recipients, call **IAddrBook::PrepareRecips**. **PrepareRecips** accepts an [ADRLIST](adrlist.md) structure and a list of property tags. The **ADRLIST** structure contains the recipients to be prepared while the property tag list represents properties that each recipient should support. **PrepareRecips** attempts to place the properties that are included in the property tag list at the beginning of the **ADRLIST** structure. If any of the properties in the list are missing from the **ADRLIST** structure, MAPI calls the address book provider to supply them. If you only need to check for long-term entry identifiers, pass NULL for the  _lpSPropTagArray_ parameter. 
  
For example, suppose you are working with five recipients. All five recipients appear in the **ADRLIST** structure with the following properties in the following order: 
  
1. **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md))
    
2. **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
3. **PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md))
    
4. **PR_EMAIL_ADDRESS** ( [PidTagEmailAddress](pidtagemailaddress-canonical-property.md))
    
5. **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md))
    
Three other properties are included in the **ADRLIST** structure for the first two recipients. 
  
1. **PR_ACCOUNT** ( [PidTagAccount](pidtagaccount-canonical-property.md))
    
2. **PR_GIVEN_NAME** ( [PidTagGivenName](pidtaggivenname-canonical-property.md))
    
3. **PR_SURNAME** ( [PidTagSurname](pidtagsurname-canonical-property.md))
    
Because all of the recipients need to have as their first three properties **PR_ADDRTYPE**, **PR_ENTRYID**, and **PR_HOME_TELEPHONE_NUMBER** ( [PidTagHomeTelephoneNumber](pidtaghometelephonenumber-canonical-property.md)), create a property tag array with these properties and pass it and the **ADRLIST** structure to **PrepareRecips**. **PrepareRecips** calls each recipient's **IMAPIProp::GetProps** method to retrieve **PR_HOME_TELEPHONE_NUMBER** because it is not currently part of the **ADRLIST** structure. When **PrepareRecips** returns, the recipient list represents a merged list of recipients with the properties included in the **ADRLIST** structure appearing first for each recipient. 
  
The recipient list for recipients 1 and 2 includes properties in the following order:
  
1. **PR_ADDRTYPE**
    
2. **PR_ENTRYID**
    
3. **PR_HOME_TELEPHONE_NUMBER**
    
4. **PR_DISPLAY_NAME**
    
5. **PR_SEARCH_KEY**
    
6. **PR_EMAIL_ADDRESS**
    
7. **PR_ADDRTYPE**
    
8. **PR_ACCOUNT**
    
9. **PR_GIVEN_NAME**
    
10. **PR_SURNAME**
    
The recipient list for recipients 3, 4, and 5 includes properties in the following order:
  
1. **PR_ADDRTYPE**
    
2. **PR_ENTRYID**
    
3. **PR_HOME_TELEPHONE_NUMBER**
    
4. **PR_DISPLAY_NAME**
    
5. **PR_SEARCH_KEY**
    
6. **PR_EMAIL_ADDRESS**
    
7. **PR_ADDRTYPE**
    
As an alternative to calling **IAddrBook::PrepareRecips** to work with properties, call each recipient's [IMAPIProp::GetProps](imapiprop-getprops.md) method and, if necessary, its [IMAPIProp::SetProps](imapiprop-setprops.md) method. When only one recipient is involved, either technique is satisfactory. However, when multiple recipients are involved, calling **PrepareRecips** rather than the **IMAPIProp** methods saves time and, if you are operating remotely, many remote procedure calls. **PrepareRecips** processes all recipients in a single call whereas **GetProps** and **SetProps** make one call for each recipient. 
  

