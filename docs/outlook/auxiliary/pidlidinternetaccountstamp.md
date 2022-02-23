---
title: "PidLidInternetAccountStamp"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 52003a4e-1b61-2965-5204-6601652dd15b
description: "Returns the account stamp of the account that delivered the message."
---

# PidLidInternetAccountStamp

Returns the account stamp of the account that delivered the message.
  
## Quick info

|||
|:-----|:-----|
|Associated properties:  <br/> |dispidInetAcctStamp  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008581  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |

## Remarks

This property should contain the same value that is returned from the Account Management API property [PROP_ACCT_STAMP](prop_acct_stamp.md) for the account that delivered the message.
  
Message store providers expose this named property and [PidLidInternetAccountName](pidlidinternetaccountname.md) so that the following actions occur:
  
- When a user clicks **Reply to All** in an email message, Outlook removes the email address that is associated with the account and is stamped on the message from the recipient list of the reply. This behavior occurs unless this email address is the sender of the original message.
- By default, Outlook sends replies and forwarded messages through the account that is stamped on the original message.

Usually, the Outlook Protocol Manager delivers messages, and Outlook sets the **PidLidInternetAccountName** and **PidLidInternetAccountStamp** properties to indicate the account that delivered the message. However, if a message store is tightly coupled with a transport, the Outlook Protocol Manager does not deliver messages and Outlook cannot set these properties. In this scenario, Outlook calls the [IMAPIProp::GetIDsFromNames](https://msdn.microsoft.com/library/e3f501a4-a8ee-43d7-bd83-c94e7980c398%28Office.15%29.aspx) function. If the message store provider wants to expose these named properties, it should implement **IMAPIProp::GetIDsFromNames** and return property tags through the output parameter *lppPropTags*. Outlook can then call the [IMAPIProp::GetProps](https://msdn.microsoft.com/library/1c7a9cd2-d765-4218-9aee-52df1a2aae6c%28Office.15%29.aspx) method by using these property tags, and the message store provider can return the account name and stamp of the desired account.
  
To support these named properties, store providers should expect Outlook to use **IMAPIProp::GetIDsFromNames** to obtain the property tag for this property. Outlook specifies the following values for the [MAPINAMEID](https://msdn.microsoft.com/library/9a92e9cd-8282-4cf0-93af-4089b3763594%28Office.15%29.aspx) structure that corresponds to this named property, which is passed as part of the array pointed at by the input parameter  *lppPropNames*  of **IMAPIProp::GetIDsFromNames**.
  
|||
|:-----|:-----|
|lpGuid:  <br/> |PSETID_Common  <br/> |
|ulKind:  <br/> |MNID_ID  <br/> |
|Kind.lID:  <br/> |dispidInetAcctStamp  <br/> |

## See also

- [About the Account Management API](about-the-account-management-api.md)
- [Constants (Account management API)](constants-account-management-api.md)
- [PidLidInternetAccountStamp Canonical Property](https://msdn.microsoft.com/library/819179fe-e58e-415c-abc7-1949036745ee%28Office.15%29.aspx)
