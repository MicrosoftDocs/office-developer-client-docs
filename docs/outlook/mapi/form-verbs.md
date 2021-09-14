---
title: "Form verbs"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: a63bf0a7-24e6-4eef-98e8-3744ce5f9f2d
description: "Last modified: July 23, 2011"
---

# Form verbs

**Applies to**: Outlook 2013 | Outlook 2016 
  
A form's user interface typically offers menu items or controls that enable users to take some kind of action with the form. It is the form server's job to handle these user actions. This interface is implemented using standard Win32 APIs; writing one is just like writing other interfaces for regular Win32 programs.
  
Often, user actions are associated with verbs. A verb is the name for an action that is specific to a certain message class. For example, **Reply** is a verb that is implemented by many form servers, each of which may have a different interpretation of that verb. Verbs are sometimes referred to as commands. 
  
> [!NOTE]
> Not all menu items and controls on a form correspond to a verb. For example, a **Cancel** button does not correspond to a Cancel verb within the form server. Usually, verbs are associated with actions that are specific to a particular message class or a set of message classes. Although different message classes can support different sets of verbs, all support at least the Open verb, which displays the form's user interface and loads it with the message's property values. 
  
Verbs may take no parameters. Forms that export commands with variable parameters must use the Automation mechanisms.
  
Clients can determine which verbs are supported by a particular message class through the [IMAPIFormInfo::CalcVerbSet](imapiforminfo-calcverbset.md) method, which is implemented by the MAPI form manager. The form manager gets this information from the form's configuration file. The verb set returned by this method is used by the client to show the user which commands can be executed on a message. For example, a client might enable users to click the right mouse button over a message to display verbs applicable to that message. 
  
## See also

- [MAPI Forms](mapi-forms.md)

