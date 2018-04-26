---
title: "Source Property (ADO Error)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ffc6c77f-1494-d63a-d832-416faa4c6f07

---

# Source Property (ADO Error)

Indicates the name of the object or application that originally generated an error.
  
## Return Value

Returns a **String** value that indicates the name of an object or application. 
  
## Remarks

Use the **Source** property on an [Error](error-object-ado.md) object to determine the name of the object or application that originally generated an error. This could be the object's class name or programmatic ID. For errors in ADO, the property value will be **ADODB.** *ObjectName*  , where  *ObjectName*  is the name of the object that triggered the error. For ADOX and ADO MD, the value will be **ADOX.** *ObjectName*  and **ADOMD.** *ObjectName,*  respectively. 
  
Based on the error documentation from the **Source**, [Number](number-property-ado.md), and [Description](description-property-ado.md) properties of **Error** objects, you can write code that will handle the error appropriately. 
  
The **Source** property is read-only for **Error** objects. 
  

