---
title: "InheritTypeEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: aa505c66-5871-10a8-35a7-cb30bb5dc21a

---

# InheritTypeEnum

Specifies how objects will inherit permissions set with [SetPermissions](setpermissions-method-adox.md).
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adInheritBoth** <br/> |3  <br/> |Both objects and other containers contained by the primary object inherit the entry.  <br/> |
|**adInheritContainers** <br/> |2  <br/> |Other containers that are contained by the primary object inherit the entry.  <br/> |
|**adInheritNone** <br/> |0  <br/> |Default. No inheritance occurs.  <br/> |
|**adInheritNoPropagate** <br/> |4  <br/> |The **adInheritObjects** and **adInheritContainers** flags are not propagated to an inherited entry.  <br/> |
|**adInheritObjects** <br/> |1  <br/> |Non-container objects in the container inherit the permissions.  <br/> |
   

