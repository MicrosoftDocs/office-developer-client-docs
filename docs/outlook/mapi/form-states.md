---
title: "Form states"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: dfc9fbf1-90d4-4756-92d9-032ac56a9c50
---

# Form states

**Applies to**: Outlook 2013 | Outlook 2016 
  
Form objects can be in one of five distinct states, depending on what methods have been called in them and whether any errors have occurred in performing those methods. The states are described in the following topics:
  
- [Uninitialized State](uninitialized-state.md)
    
- [Normal State](normal-state.md)
    
- [NoScribble State](noscribble-state.md)
    
- [HandsOffAfterSave State](handsoffaftersave-state.md)
    
- [HandsOffFromNormal State](handsofffromnormal-state.md)
    
The states primarily relate to the status of the data in the form object. The different states reflect whether the data needs to be saved, whether the form object should allow modifications to the data, and what point in the process of saving the data the form is in. As such, the form states and transitions between them have more to do with your form server's implementation of [IPersistMessage : IUnknown](ipersistmessageiunknown.md) interface methods than any other. Knowledge of these states is very useful for proper implementation of the MAPI form interfaces that your form server must implement. 
  
The topics in this section describe the various states, along with the allowed actions that cause transitions to other states. Any transitions not listed in the topics are not allowed. If your form objects make disallowed transitions between states, they will not behave in the ways that messaging clients expect and could cause unpredictable client or form object behavior.
  
> [!NOTE]
> Some state transitions depend on information from previous states. Your form server will most likely have to implement a flag in its form objects to indicate whether the values of the message's properties have been changed to facilitate later state changes. 
  
## See also

- [Developing MAPI Form Servers](developing-mapi-form-servers.md)

