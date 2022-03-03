---
title: "Address Book Restrictions"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 6ace8c03-45a7-484b-8c12-516ac0e40dc2
 
 
---

# Address Book Restrictions

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Address book providers are required to support three types of restrictions on the contents tables of their containers:
  
- Ambiguous name property restrictions
    
- Instance key property restrictions
    
- Prefixed display name content restrictions
    
Ambiguous name restrictions are property restrictions using the **PR_ANR** ([PidTagAnr](pidtaganr-canonical-property.md)) property to match recipient names with entries in address book containers. The **PR_ANR** property restriction is a "best guess" type of search whereby address book providers can choose the matching property that works best for their container. For example, one address book provider might implement the **PR_ANR** restriction by matching recipient names against the **PR_ACCOUNT** ([PidTagAccount](pidtagaccount-canonical-property.md)) property of each container entry whereas another provider might use **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)).
  
MAPI recommends that implementations of the **PR_ANR** restriction strike a balance between adequate performance and user satisfaction. User satisfaction can be compromised when an address book provider implements the restriction in such a way that too few or too many matches are found. Some address book providers support what is known as a distinguished, or common, name that is not displayable in a dialog box but can match an ambiguous name restriction. 
  
A typical implementation might be to parse the recipient's display name into words, matching any entry that contains all of the words. Attention to details such as sensitivity to word position, whether nonconsecutive words are matched, and the choice of separator characters can vary. For example, if the name to be resolved is "Bill L," a typical **PR_ANR** restriction would select the following entries as matching: 
  
- Billy Larson
    
- Bill Lee
    
- Bill Logan Jr. 
    
- Sam Bill Lee
    
Instance key restrictions, or **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) property restrictions, are used in the implementation of list boxes that are used in client applications for viewing MAPI tables. Some list box implementations allow users to make multiple selections, scroll up or down, and return to the first item selected. To implement this behavior, clients call [IMAPITable::FindRow](imapitable-findrow.md), passing a property restriction on the **PR_INSTANCE_KEY** property to the method. Address book providers are required to support this restriction. 
  
Another feature of list boxes used for table viewing is the ability to position the cursor based on a set of prefix characters. As the user starts typing prefix characters, the client moves the cursor to the first item that begins with these characters. Clients implement this feature with a content restriction based on the **PR_DISPLAY_NAME** property and the FL_PREFIX fuzzy level. 
  
## See also



[MAPI Tables](mapi-tables.md)

