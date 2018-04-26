---
title: "DateCreated Property (ADOX)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: ee975bf5-7d44-a993-d1c0-077993515698
---

# DateCreated Property (ADOX)

Indicates the date the object was created.
  
## Return Values

Returns a **Variant** value specifying the date created. The value is null if **DateCreated** is not supported by the provider. 
  
## Remarks

The **DateCreated** property is null for newly appended objects. After appending a new [View](view-object-adox.md) or [Procedure](procedure-object-adox.md), you must call the [Refresh](refresh-method-ado.md) method of the [Views](views-collection-adox.md) or [Procedures](procedures-collection-adox.md) collection to obtain values for the **DateCreated** property. 
  

