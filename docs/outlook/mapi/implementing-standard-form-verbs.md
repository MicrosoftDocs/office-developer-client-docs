---
title: "Implementing Standard Form Verbs"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f89f7c58-6358-4523-9788-676f189b5e69
description: "Last modified: March 09, 2015"
 
 
---

# Implementing Standard Form Verbs

  
  
**Applies to**: Outlook 
  
MAPI defines a set of standard verbs, or actions taken when a user makes a menu selection or clicks a button, that all form viewers should support. Each verb has a constant associated with it for identification, defined in the EXCHFORM.H header file. The following table lists the standard form verbs and their associated constants:
  
|**Verb**|**Value**|
|:-----|:-----|
|Open  <br/> |EXCHIVERB_OPEN  <br/> |
|Reply  <br/> |EXCHIVERB_REPLYTOSENDER  <br/> |
|Reply to All  <br/> |EXCHIVERB_REPLYTOALL  <br/> |
|Forward  <br/> |EXCHIVERB_FORWARD  <br/> |
|Print  <br/> |EXCHIVERB_PRINT  <br/> |
|Save As  <br/> |EXCHIVERB_SAVEAS  <br/> |
|Reply to Folder  <br/> |EXCHIVERB_REPLYTOFOLDER  <br/> |
   
When a user chooses a verb, pass its constant in a call to the form's [IMAPIForm::DoVerb](imapiform-doverb.md) method to perform its corresponding action. 
  
In addition to accessing verbs through your form viewer, users can sometimes access verbs directly from the form. For example, some form objects allow the user to invoke the **Print** verb by right-clicking on the form and choosing **Print** from a context-sensitive menu. 
  

