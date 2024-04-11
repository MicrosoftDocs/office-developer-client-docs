---
title: "PROP_POP_LEAVE_ON_SERVER"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 22d7c1e8-48b9-4768-b4de-9a9f32a3aabb
description: "Specifies leaving a copy of a message on the server for a POP account."
---

# PROP_POP_LEAVE_ON_SERVER

Specifies leaving a copy of a message on the server for a POP account.
  
## Quick info

|Property |Value |
|:-----|:-----|
|Identifier:  <br/> |0x1000  <br/> |
|Property type:  <br/> |PT_DWORD  <br/> |
|Property tag:  <br/> |0x10000003  <br/> |
|Access:  <br/> |Read-only  <br/> |
   
## Remarks

The following table lists the possible values. See [Constants (Account management API)](constants-account-management-api.md) for more information on the constants. 
  
|**Possible values**|**Description**|
|:-----|:-----|
|**LEAVE_ON_SERVER** <br/> |Leaves a copy of the message on the POP server after downloading the message to a device. |
|**REMOVE_AFTER** <br/> |Removes the message from the POP server after downloading it to a device. |
|**REMOVE_ON_NUKE** <br/> |Removes the message from the POP server only after the user deletes the message from the Deleted Items folder. |
|**GET_REMOVE_AFTER_DAYS**( _ul_)  <br/> |Gets the number of days after which the message will be removed from the POP server. |
|**SET_REMOVE_AFTER_DAYS**( _days_)  <br/> |Sets the number of days after which the message will be removed from the POP server. |
   
## See also

- [Managing message downloads for POP3 accounts](managing-message-downloads-for-pop3-accounts.md) 
- [Constants (Account management API)](constants-account-management-api.md)

