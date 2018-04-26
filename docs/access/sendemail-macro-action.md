---
title: "SendEmail Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 84ff6b46-d239-4716-9964-5b909656d347
description: "The SendEmail action sends an e-mail message."
---

# SendEmail Macro Action

The **SendEmail** action sends an e-mail message. 
  
> [!NOTE]
> The **SendEmail** action is available only in Data Macros. 
  
## Setting

The **SendEmail** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
|**To** <br/> |Yes  <br/> |The recipients of the message whose names you want to put on the **To** line in the message.Separate the recipient names that you specify in this argument (and in the  *Cc*  and  *Bcc*  arguments) with a semicolon (;).  <br/> |
|**Cc** <br/> |No  <br/> |The message recipients whose names you want to put on the Cc ("carbon copy") line in the message.  <br/> |
|**Bcc** <br/> |No  <br/> |The message recipients whose names you want to put on the Bcc ("blind carbon copy") line in the message.  <br/> |
|**Subject** <br/> |No  <br/> |The subject of the message. This text appears on the **Subject** line in the message.  <br/> |
|**Body** <br/> |No  <br/> |The text that you want to include in the main body of the mail message. If you leave this argument blank, no additional text is included in the message.  <br/> |
   
## Remarks

The **SendEmail** action is available only in the **[After Delete](after-delete-macro-event.md)**, **[After Insert](after-insert-macro-event.md)**, and **[After Update](after-update-macro-event.md)** macro events. 
  
The **SendEmail** action does not display the message for editing. 
  

