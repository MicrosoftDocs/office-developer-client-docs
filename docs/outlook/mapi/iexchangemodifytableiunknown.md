---
title: "IExchangeModifyTable  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IExchangeModifyTable
api_type:
- COM
ms.assetid: 45a73c7b-5855-4b70-866b-facb41cb3c32
description: "Last modified: March 09, 2015"
---

# IExchangeModifyTable : IUnknown

  
  
**Applies to**: Outlook 
  
Supports access to Microsoft Exchange Server table objects, specifically system access control list (SACL) table objects and rule table objects on Microsoft Exchange Server folders. This interface resembles the [IMAPITable : IUnknown](imapitableiunknown.md) interface, but it adds support for Microsoft Exchange Server-specific structures that are used to control SACLs and rules. 
  
|||
|:-----|:-----|
|Exposed by:  <br/> |None  <br/> |
|Implemented by:  <br/> |Server table objects  <br/> |
|Called by:  <br/> |MAPI and client applications  <br/> |
|Interface identifier:  <br/> |IID_IExchangeModifyTable  <br/> |
|Pointer type:  <br/> |LPEXCHANGEMODIFYTABLE  <br/> |
|Transaction model:  <br/> |Transacted  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[GetLastError](iexchangemodifytable-getlasterror.md) <br/> |Returns information about the last error that occurred in a table object.  <br/> |
|[GetTable](iexchangemodifytable-gettable.md) <br/> |Returns a pointer to an interface for a MAPI table object.  <br/> |
|[ModifyTable](iexchangemodifytable-modifytable.md) <br/> |Updates a MAPI table object.  <br/> |
   
|**Properties used to modify a rules table**|**Access**|
|:-----|:-----|
|**PR_RULE_ACTIONS** ( [PidTagRuleActions](pidtagruleactions-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_CONDITION** ( [PidTagRuleCondition](pidtagrulecondition-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_ID** ( [PidTagRuleId](pidtagruleid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_LEVEL** ( [PidTagRuleLevel](pidtagrulelevel-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_NAME** ( [PidTagRuleName](pidtagrulename-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_PROVIDER** ( [PidTagRuleProvider](pidtagruleprovider-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_PROVIDER_DATA** ( [PidTagRuleProviderData](pidtagruleproviderdata-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_SEQUENCE** ( [PidTagRuleSequence](pidtagrulesequence-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_STATE** ( [PidTagRuleState](pidtagrulestate-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RULE_USER_FLAGS** ( [PidTagRuleUserFlags](pidtagruleuserflags-canonical-property.md))  <br/> |Read-only  <br/> |
   
|**Properties used to modify a SACL table**|**Access**|
|:-----|:-----|
|**PR_MEMBER_ENTRYID** ( [PidTagMemberEntryId](pidtagmemberentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MEMBER_ID** ( [PidTagMemberId](pidtagmemberid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MEMBER_NAME** ( [PidTagMemberName](pidtagmembername-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_MEMBER_RIGHTS** ( [PidTagMemberRights](pidtagmemberrights-canonical-property.md))  <br/> |Read-only  <br/> |
   
## Remarks

To obtain the **IExchangeModifyTable** interface, call the MAPI [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method on a property of type PT_OBJECT on a folder object. When you call the **OpenProperty** method, pass the value **IID_IExchangeModifyTable** in the  _lpiid_ parameter. 
  
## See also

#### Concepts

[MAPI Interfaces](mapi-interfaces.md)

