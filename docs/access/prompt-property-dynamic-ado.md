---
title: "Prompt Property--Dynamic (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 6c899b03-1d1f-a81f-dc17-7205a0230af9

---

# Prompt Property--Dynamic (ADO)

Specifies whether the OLE DB provider should prompt the user for initialization information.
  
## Settings and Return Values

Sets and returns a [ConnectPromptEnum](connectpromptenum.md) value. 
  
## Remarks

 **Prompt** is a dynamic property, which may be appended to the [Connection](connection-object-ado.md) object's [Properties](properties-collection-ado.md) collection by the OLE DB provider. To prompt for initialization information, OLE DB providers will typically display a dialog box to the user. 
  
Dynamic properties of a [Connection](connection-object-ado.md) object are lost when the **Connection** is closed. The **Prompt** property must be reset before re-opening the **Connection** to use a value other than the default. 
  
> [!NOTE]
> Do not specify that the provider should prompt the user in scenarios in which the user will not be able to respond to the dialog box. For example, the user will not be able to respond if the application is running on a server system instead of on the user's client, or if the application is running on a system with no user logged on. In these cases, the application will wait indefinitely for a response and seem to lock up. 
  
 **Usage**
  
```
Set cn = New Connection
cn.Provider = "SQLOLEDB"
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user

```


